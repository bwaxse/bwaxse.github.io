---
title: "Using Claude Code for Genomic Pipeline Optimization: A KIR Mapper Case Study"
date: 2025-01-23T14:00:00-05:00
categories:
  - Blog
  - Bioinformatics
tags:
  - Claude Code
  - Bioinformatics
  - Pipeline Optimization
  - KIR Mapping
  - Parallel Processing
  - Debugging
---

As a physician-scientist with clinical and lab experience, I know how to ask answerable questions, structure experiments, and evaluate results carefully. But I didn't have the computing skills to do everything I wanted. Two years ago, large language models changed that. By pasting code into Claude.ai, I could generate entire classes and SQL queries that did exactly what I needed. It was inefficient at times—for instance, Claude didn't know much about polars initially—but it worked, and I knew this was the work I wanted to do.

At the end of last year, I discovered Claude Code. I was blown away. I built a command-line tool to efficiently evaluate primary literature using LLMs, which eventually became [Scholia.fyi](https://scholia.fyi)—releasing in the next few weeks. When I returned to work in January, it was clear Claude Code would also take my informatics to the next level.

This is the first in a series of posts about using Claude Code for data analysis and scientific work. I found plenty of resources on building [apps](https://www.youtube.com/@avtharai) or [websites](https://www.youtube.com/@PatrickOakleyEllis) with [Claude Code](https://www.youtube.com/watch?v=gv0WHhKelSE), but not much on bioinformatics and science. My hope is to create a community of Claude Code-literate scientists who keep humans in the loop and amplify what we can do.

This first example involves scaling a KIR gene mapping pipeline from 40 samples to 200,000+. Beyond optimizing machine types (Claude Code helped me find a 30% cheaper parallelized setup), I consistently hit a wall around 100-200 samples. The tool worked fine at small scale but failed predictably in production. This is a story about debugging something outside my expertise and learning where Claude Code genuinely helps.

<!--more-->

## The Setup

I'm working with [kir-mapper](https://github.com/erickcastelli/kir-mapper), which aligns KIR genes from whole-genome sequencing. The pipeline orchestrates several tools:

1. GATK PrintReads converts CRAM to BAM, extracting the KIR region
2. kir-mapper map aligns reads to KIR references
3. (Later) ncopy, genotype, haplotype call variants

The strategy was simple: run 5 samples in parallel using GNU parallel, process them in 100-200 sample batches. This should be efficient. Instead, the pipeline stalled reliably at sample 99/100 or 199/200.

## The Pattern

The failure was consistent but puzzling:

- 40-sample run: succeeded
- 64-sample run: succeeded
- 100-sample run: stalled at 99/100
- 199-sample run: stalled at 198/199
- 200-sample run: stalled at 199/200

Always at or near the last sample. This suggested something systematic—not random failure, not resource exhaustion, but something about how the parallel queue itself was behaving.

I first analyzed memory and disk usage throughout the runs with Claude Code. We never exhausted resources. That ruled out the obvious culprits. Beyond that, I was stuck. File conflicts in parallel execution was a hypothesis, but debugging GNU parallel internals isn't my area, and I'd never written low-level code to know where to look.

## Where Claude Code Helped

I gave Claude the problem, access to the kir-mapper source code, and access to my base and parallelization scripts. It did something I couldn't have done efficiently: read through thousands of lines of C++ and identify where temporary files were created.

Here's what it found in map_dna.cpp (lines 1473-1474):

```cpp
string v_sai1 = v_output + "tmp1.sai ";
string v_sai2 = v_output + "tmp2.sai ";
```

Compare with how SAM files are named (line 1134):

```cpp
string outsamtmp = v_output + v_sample + *i + ".tmp.sam";
```

The difference is stark: SAM files include the sample name. The temporary BWA index files do not. When five samples run in parallel, they all write to the same `tmp1.sai` and `tmp2.sai` files. File locks accumulate. After a certain number of jobs queue up, GNU parallel hits an internal limit and stops accepting new ones.

This explained an interesting observation: GATK worked fine, even though it also runs in parallel. The difference isn't parallelization strategy—both GATK and kir-mapper use GNU parallel with 5 samples at a time. The difference is how they handle temporary files. GATK apparently names its temp files in a way that avoids collisions (or writes them elsewhere), whereas kir-mapper creates those shared `tmp1.sai` and `tmp2.sai` files that all samples contend for. When file locks accumulate on those shared temp files, the GNU parallel queue hits its limit and stops accepting new jobs.

Could I have figured this out alone? Eventually, probably. But it would have taken substantially longer. Could I have abandoned parallelization and forfeited 30% savings, also yes. The key was that Claude could quickly parse unfamiliar C++ and identify the pattern.

## Two Fixes

With the diagnosis in hand, I implemented two complementary fixes:

**Fix 1: Per-sample output directories.** Instead of all samples writing to a shared output directory:

```bash
local sample_output="./kir_output/${person_id}"
mkdir -p "$sample_output"

kir-mapper map \
    -bam "${person_id}_chr19.bam" \
    -sample "${person_id}" \
    -output "$sample_output" \
    -threads $THREADS_PER_SAMPLE 2>&1
```

Each sample now gets its own subdirectory. The `tmp1.sai` and `tmp2.sai` files for sample A don't collide with those for sample B.

**Fix 2: 25-sample sub-batches.** Even with per-sample directories, sending 100 jobs through GNU parallel at once keeps you near that queue limit. So instead of:

```bash
seq 1 100 | parallel -j 5 'run_kirmap {}'
```

We process in sub-batches:

```bash
BATCH_SIZE=25

while [ $idx -le $NUM_SAMPLES ]; do
    BATCH_END=$((idx + BATCH_SIZE - 1))
    if [ $BATCH_END -gt $NUM_SAMPLES ]; then
        BATCH_END=$NUM_SAMPLES
    fi

    seq $idx $BATCH_END | parallel -j 5 'run_kirmap_with_env {}'
    idx=$((BATCH_END + 1))
done
```

25 jobs stays well below the queue limit and within the ballpark of successful runs.

## Why This Matters

Many of us build bioinformatics pipelines with deep domain expertise but without systems-level knowledge. You understand your science (genomics, epidemiology, medicine) but orchestrating multiple tools, managing parallel job queues, and debugging temporary file handling is a different domain entirely.

Claude Code was useful here specifically because:

1. It could read large codebases quickly and extract relevant sections
2. It could reason about file I/O patterns and concurrency issues
3. It helped me iterate through multiple approaches and find the best

What it didn't do: it didn't magically know the answer. I had to provide the logs, frame hypotheses, and verify its analysis myself. The diagnosis made sense conceptually, so I checked the source code to confirm. That verification step is critical, but we're already used to this in science.

## When It's Actually Useful

If you're considering Claude Code for bioinformatics, the wins come from:

- **Code analysis**: Reading unfamiliar source code to find issues
- **Prototyping approaches**: Testing multiple strategies before committing
- **Architecture**: Designing cleaner pipeline structure (mine went from 6 stages to 3)
- **Getting through the tedium**: I've also used it to construct new cohorts, an easy but tedious process

The important caveats:

- You still need domain knowledge to evaluate suggestions
- Verify diagnoses yourself, especially for system behavior
- Use it as a thought partner, not a substitute for critical thinking
- If something doesn't make sense, push back and ask for more detail

## The Result

The pipeline now processes all samples in a batch successfully, maintains parallelization efficiency, and scales to multiple ancestries. More importantly, I understand why it failed and what the fixes address. That understanding is what matters for extending the code later, and approaching similar tasks in the future.

---

If you're building scientific pipelines and hit problems outside your expertise, try Claude Code. Frame questions clearly, give it access to relevant code, and validate its analysis. The combination of clear problem statements, access to source code, and iterative refinement creates a solid workflow for technical debugging.

I'll be writing more about how I'm using Claude Code for data analysis work. If you have questions or want to share how you're using it, I'd be interested to hear.
