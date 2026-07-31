---
permalink: /uses/
title: "Tools & Workflows"
---

Software and tools I use for clinical AI development, evaluation, and biomedical research.

## Agents & Clinical AI

**Claude Code** - Where most of my work happens. Multi-repo orchestration, custom skills, subagents for parallel search and review.

**Claude Agent SDK** - Building harness capabilities: orchestrator/subagent structure, tool definitions, deterministic gates.

**AWS Bedrock / Azure AI Foundry** - Model access across families, useful for cross-family de-confounding.

**MCP servers** - Custom ones where the integration matters: Zotero for the shared library, a docs server for architecture knowledge.

## Evaluation

**pytest** - Regression-first. Every bug fix starts with a test that reproduces the failure through the same gate the runtime uses.

**LLM-as-judge pipelines** - Custom judges calibrated against clinician adjudication, with positive and negative controls.

**DSPy / GEPA** - Prompt optimization on held-out splits.

**Docker + AWS Fargate** - Containerized eval runs, sharded for parallelism, with cost circuit breakers.

## Data Analysis

**Python** - Primary language. Polars over pandas, plus numpy, scipy, statsmodels.

**R** - Secondary, for specialized packages (MatchIt for matching, SAIGE for genetic association testing).

**Streamlit** - Fast internal review tools for clinical adjudication workflows.

**Jupyter** - Exploratory analysis and reproducible reporting.

## Genomics & Bioinformatics

Carried over from the NIH years, still what I reach for when the question is genetic.

**PLINK2** - Genetic data QC and association testing.

**SAIGE** - Mixed model association testing at biobank scale.

**GATK** - Variant calling pipelines, parallelized with GNU parallel.

**bcftools/samtools** - VCF manipulation and processing.

## Computing Infrastructure

**Google Cloud** - dsub for batch job orchestration at scale.

**BigQuery** - OMOP CDM queries against *All of Us*.

**GNU parallel** - Simple but powerful parallelization.

## Writing & Organization

**Notion** - Research notes, literature tracking, and a daily work log.

**Zotero** - Reference management, wired into Claude via a custom MCP server.

**LaTeX** - Documents where layout matters and I want the source diffable.

---

*This page inspired by [uses.tech](https://uses.tech). Last updated July 2026.*
