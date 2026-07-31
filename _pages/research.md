---
permalink: /research/
title: "Research"
---

## Overview

My path to clinical AI began in molecular biology—studying how myosin VI facilitates autophagy and intercellular communication through quantitative microscopy. During residency at the University of Chicago, I discovered that computational methods could directly enhance patient care. That led me to NIAID and Josh Denny's lab at NHGRI, where I paired clinical experience with expertise in computable phenotyping, working on a central problem: how do we extract research-grade phenotypes from messy clinical data to enable discovery at scale?

I'm now at Doctronic, working on a related problem one layer up. Building an AI system that reasons about a patient is increasingly tractable. Knowing whether it does so correctly is not—and the measurement problem turns out to be where most of the difficulty actually lives.

## Research Philosophy

Careful definition is the bottleneck. In phenotyping, the hard part was never the model; it was deciding what counted as a case and proving the definition held. In clinical AI, the hard part is the same: an evaluation is a claim about what "correct" means, and a benchmark that rewards the wrong behavior will happily certify a system that shouldn't ship.

Both halves of my work come back to instruments. I'm interested in methods that are rigorous enough to trust and concrete enough to act on, and in the failure mode where a plausible number goes unchallenged because nobody predicted what it should have been.

## Clinical AI: Agents and Evaluation

**Evaluating Conversational Diagnostic AI**
Multi-turn clinical conversation is hard to score. The patient is simulated, the doctor is an agent, the transcript is long, and the thing you care about—did this reach a safe disposition—isn't a single labeled field. I work on evaluation infrastructure for this setting: LLM-as-judge pipelines calibrated against physician adjudication, deterministic metrics for routing and disposition, and datasets built around conversations that change intent partway through.

The recurring lesson is that the instrument fails more often than the model. In one case, simulated patients were disclosing their own artificiality to the diagnosing model, which inflated benchmark scores until we detected and characterized it; patient fidelity is now a gate on every downstream result. In another, per-case clinical data never reached the simulated patient's prompt at all, invalidating a whole family of prior runs. Neither showed up as an implausible number. That's precisely why they survived so long.

**Agent Architecture for Clinical Reasoning**
How should a medical agent be structured so that safety holds by construction rather than by instruction? I work on capabilities inside a multi-agent harness—a diagnostic interview subagent that produces a ranked differential with supporting and refuting evidence, deterministic completion gates that prevent ungrounded clinical claims from reaching a patient, and emergency surveillance split into a parallel track so red-flag detection isn't entangled with the working diagnostic theory.

**Clinical Knowledge Retrieval**
Grounding a clinical agent means retrieving the right guidance, fast and cheaply enough to run on every turn. I built a 300-case gold standard from real patient conversations and evaluated retrieval architectures against it. The most interesting result was mechanistic: the winning approach's advantage came from query-side diversity and selection, not from agentic iteration—and richer context for the selector actively hurt performance.

## Earlier Work: Phenotyping and Genomics

**Long COVID Phenotyping and Wearable Risk Prediction**
EHR-based phenotype definitions for post-acute sequelae of SARS-CoV-2 infection (PASC, Long COVID). The challenge isn't just identifying who has Long COVID—it's distinguishing persistent post-infection functional impairment from coincident conditions in noisy EHR data. I used temporal phenotyping approaches (Cox proportional hazards PheWAS) to build a Long COVID risk score achieving 94% AUROC, integrating EHR data with wearable activity metrics. Now a preprint: [11 million days of longitudinal wearable data reveal novel future health insights](https://doi.org/10.64898/2026.01.29.26344899).

**Computable Phenotypes for Respiratory Infectious Disease**
With collaborators at NIAID and USUHS, I developed the first multi-component computable phenotype for respiratory viral infections, integrating laboratory results, billing codes, and antiviral prescriptions. This work revealed critical performance differences across viruses—something investigators need to consider before implementing phenotypes for research. The phenotype achieves positive predictive values >0.76 across all viruses while matching CDC surveillance trends, validating that EHR data can capture infectious disease at population scale.

**Genetic Susceptibility to Respiratory Infection**
Building on refined phenotyping, I conducted genome-wide association studies examining how human genetic variation influences susceptibility to respiratory infections and other infectious disease outcomes. The premise: precise phenotyping plus large biobank datasets yields discovery of biological mechanisms at human scale.

## Collaboration and Mentorship

My work is fundamentally collaborative. I've benefited from mentoring relationships spanning biostatistics, genomics, and clinical informatics. I helped start the Infectious Diseases Informatics Interest Group (IDIIG) at IDSA and established a Health Informatics Journal Club at NHGRI, because the intersection of ID and informatics is still early—and because those conversations push all of us to ask better questions.

My research also includes collaborations spanning rare disease genetics, sarcoidosis genomics with refined phenotyping, HPV disease, and methodological development for laboratory value standardization within OMOP CDM.

## Publications

[Link to Google Scholar](https://scholar.google.com/citations?user=16OEFu8AAAAJ) • [ORCID](https://orcid.org/0000-0001-5086-3419)

*Selected recent work:*
Pradhan A, **Waxse BJ**, Matias WR, Mercaldo S, Bowman K, Nutt C, Kanjilal S, Hillis JM. Evaluation of four large language models on complex, infectious disease case scenarios. *medRxiv.* 2026. [DOI](https://doi.org/10.64898/2026.07.14.26358021)

Fulda ES, **Waxse BJ**, Goleva SB, Tran TC, Taylor HJ, et al. 11 million days of longitudinal wearable data reveal novel future health insights. *medRxiv.* 2026. [DOI](https://doi.org/10.64898/2026.01.29.26344899)

**Waxse BJ**, Rao S. Data science for pediatric infectious disease: utilizing COVID-19 as a model. *Curr Opin Infect Dis.* 2025;38(5):493-498. [PMID: 40748012](https://pubmed.ncbi.nlm.nih.gov/40748012/)

**Waxse BJ**, Bustos Carrillo FA, Tran TC, Mo H, Ricotta EE, Denny JC. Computable phenotypes to identify respiratory viral infections in the *All of Us* research program. *Sci Rep.* 2025;15(1):18680. [PMID: 40437102](https://pubmed.ncbi.nlm.nih.gov/40437102/)

Goleva SB, Williams A, Schlueter DJ, Keaton JM, Tran TC, **Waxse BJ**, Ferrara TM, Cassini T, Mo H, Denny JC. Racial and ethnic disparities in antihypertensive medication prescribing patterns and effectiveness. *Clin Pharmacol Ther.* 2024;116(6):1544-1553. [PMID: 39051523](https://pubmed.ncbi.nlm.nih.gov/39051523/)

Mo H, Channa Y, Ferrara TM, **Waxse BJ**, Schlueter DJ, Tran TC, Awan AH, Goleva SB, Williams A, Babbar A, Stubblefield O, Keaton JM, Larson EA, Wilke RA, Denny JC. Hyponatremia associated with the use of common antidepressants in the All of Us Research Program. *Clin Pharmacol Ther.* 2025;117(2):534-543. [PMID: 39540435](https://pubmed.ncbi.nlm.nih.gov/39540435/)

## Presentations and Mentoring

**Selected Recent Talks**
- **AMIA Amplify 2026**: A Long COVID Phenotype Risk Score Reveals Decreased Steps and Elevated Resting Heart Rate Before and After Infection
- **IDWeek 2025**: Higher Step Count is Associated with Reduced Risk of Long COVID
- **AMIA 2024**: Identification and Validation of Common Respiratory Infections in *All of Us*

I've mentored students and fellows on phenotyping projects exploring how methodological choices (EHR alone, survey alone, or combined approaches) dramatically affect genomic discovery—work that's often invisible but critical for robust research design.

## Tools and Resources

**Scholia.fyi** *(2025–2026, retired)* - An AI-powered platform I built to improve how we engage with primary literature. The premise: reading papers carefully matters, but modern AI can accelerate critical appraisal. Scholia provided structured analysis of methodology, interpretation of results, and identification of limitations—rooting you in the fundamentals when you're reading dozens of papers, focused on what you learn during the conversation. Built from the observation that I was spending disproportionate time on literature review, and there's simply too much to read now. What I didn't want was to surrender reading to LLMs entirely, so the design kept the human in the loop. Retired in March 2026 when I moved to Doctronic.

**OMOP Implementation Resources** - Documentation and reusable pipelines for large-scale EHR data extraction and phenotyping in the _All of Us_ Research Program, available upon request.

**GWAS Pipeline Templates** - Production-ready code for multi-ancestry GWAS using SAIGE and METAL, including distributed computing setup via dsub on Google Cloud.
