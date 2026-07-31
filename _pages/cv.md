---
title: "CV"
permalink: /cv/
layout: single
author_profile: true
toc: true
toc_sticky: true
---

[Download the current résumé (PDF)](/assets/waxse-resume.pdf){: .btn .btn--primary}

## Professional Summary

Physician-engineer working on production clinical AI and the systems that measure it. At Doctronic I design and ship capabilities inside a multi-agent medical harness (diagnostic interview, prescription refill, emergency surveillance) and build the evaluation infrastructure that gates them. Producing a plausible clinical agent is cheap; knowing whether it works is not, and that's critical in medicine. Board-certified in internal medicine, pediatrics, and infectious diseases, with first-author work in computable phenotyping across 500M+ clinical observations.

## Technical Skills

**Agentic Systems:** Multi-agent orchestrator/sub-agent architectures, Claude Agent SDK, deep-agent harnesses, tool-use design, deterministic safety gates and completion contracts, context engineering, latency optimization
{: .notice}

**Evaluation & Measurement:** LLM-as-judge design and calibration, simulated-patient fidelity instruments, pre-registered study design, benchmark contamination detection, inter-rater reliability and paired significance testing; CRAFT-MD, HealthBench, MedQA-CS, OSCE/PACES rubrics
{: .notice}

**Retrieval:** BM25, hybrid dense+sparse with RRF, HyDE, agentic retrieval loops, DSPy, GEPA optimization, gold-set construction, recall@k / precision@k
{: .notice}

**Programming & Analytics:** Python, SQL, Polars, R, Docker, AWS (Bedrock, Fargate, S3), Azure AI Foundry, Google BigQuery, MCP servers, dsub, Google Batch
{: .notice}

**Statistical Methods:** GWAS, PheWAS, phenotype risk scores, regression, propensity score matching, survival analysis
{: .notice}

**Healthcare Data:** OMOP CDM, ICD, CPT, SNOMED, LOINC, RxNorm, ATC, FDA NDC, EHR phenotyping, cohort development
{: .notice}

## Experience

### Senior Clinical Context Engineer
**Doctronic** | Mar 2026 – Present

- Co-designing the next-generation consultation architecture: an orchestrator coordinating specialized sub-agents, patient thread decoupled from agent thread, and safety enforced through deterministic contracts rather than prompt instruction
- Built the diagnostic interview capability (ranked differential with supporting and refuting evidence, plus next-best-question reasoning) and the gate that keeps any diagnostic statement from reaching a patient without a produced differential
- Built the prescription refill flow mirroring the production state-regulated pipeline: renewal-safety interview, parallel safety engines over drug monographs, a monograph resolver behind a drift guard, and a deterministic fill-versus-escalate decision
- Designed the guardian sentinel, splitting emergency surveillance out of diagnostic reasoning into an always-on parallel track
- Found a contamination in a published benchmark where simulated patients disclosed their own artificiality to the diagnosing model, inflating scores; shipped a three-axis patient-fidelity judge as an upstream gate on every downstream result
- Ran an end-to-end evaluation of clinical guidance retrieval, building a 300-case gold standard from real patient conversations; findings drove the architecture the production team adopted
- Wrote or revised the clinical flag criteria for eight emergency presentations, with boolean flag-combination logic and per-question exemplars
- Own technical interviewing and take-home design for clinical context engineering hires

### Research Data Scientist
**National Human Genome Research Institute, NIH** | Aug 2023 – Mar 2026

- Used Claude Code to orchestrate concurrent research projects across multiple disease domains (respiratory viruses, sarcoidosis, HPV-associated anal disease, long COVID, adverse drug events)
- Architected distributed computing pipelines processing 155 survey-item PheWAS jobs and 26 ancestry-stratified GWAS using Google Batch/dsub
- Developed phenotype risk score for long COVID prediction (AUC 0.94) that outperforms semi-supervised approaches, integrating wearable device data with EHR records
- Built and validated computable phenotyping algorithms for 8 respiratory pathogens achieving 79-97% PPV; first-author publication in *Scientific Reports* (2025)
- Led multi-investigator projects spanning EHR-survey phenotype comparison for genetic discovery, clinical risk factor identification, and genetic variant validation

### Infectious Diseases Clinical Fellow
**National Institute of Allergy and Infectious Diseases, NIH** | Jul 2021 – Mar 2026

- Managed complex infectious disease cases, building the clinical grounding that now informs my agent and criteria design work
- Board certified in Internal Medicine, Pediatrics, and Adult Infectious Diseases

### Medicine-Pediatrics Resident
**University of Chicago Medicine** | Jun 2017 – Jun 2021

- Conducted retrospective EHR analysis identifying differential treatment responses in septic shock using machine learning-derived patient subgroups (American Thoracic Society Conference 2020)
- Completed Summer Program in Outcomes Research Training (SPORT) fellowship

### Graduate Student
**NIH-Cambridge Scholars Programme, University of Cambridge** | Aug 2010 – Nov 2016

- Developed quantitative analysis pipelines for microscopy image data
- First-author publication in *Journal of Cell Science*; co-authored *Nature Cell Biology*

## Education

| Degree | Institution | Year |
|--------|-------------|------|
| Infectious Diseases Fellowship | NIAID, NIH | 2021–Mar 2026 |
| Medicine-Pediatrics Residency | University of Chicago | 2017–2021 |
| MD | UT Southwestern Medical School | 2008–2017 |
| PhD, Clinical Biochemistry | NIH, University of Cambridge | 2010–2016 |
| BA, Biology & Chemistry | Texas Christian University | 2004–2008 |

## Selected Publications

Pradhan A, **Waxse BJ**, Matias WR, et al. Evaluation of four large language models on complex, infectious disease case scenarios. *medRxiv*. 2026. [DOI](https://doi.org/10.64898/2026.07.14.26358021)

Fulda ES, **Waxse BJ**, Goleva SB, et al. 11 million days of longitudinal wearable data reveal novel future health insights. *medRxiv*. 2026. [DOI](https://doi.org/10.64898/2026.01.29.26344899)

**Waxse BJ**, Bustos Carrillo FA, Tran TC, Mo H, Ricotta EE, Denny JC. Computable phenotypes to identify respiratory viral infections in the All of Us research program. *Scientific Reports*. 2025;15(1):18680. [DOI](https://doi.org/10.1038/s41598-025-02183-9)

**Waxse BJ**, Rao S. Data Science for Pediatric Infectious Disease: Utilizing COVID-19 as a Model. *Current Opinion in Infectious Diseases*. 2025;38(5):493-498. [DOI](https://doi.org/10.1097/QCO.0000000000001139)

Goleva SB, Williams A, Schlueter DJ, Keaton JM, Tran TC, **Waxse BJ**, et al. Racial and Ethnic Disparities in Antihypertensive Medication Prescribing Patterns. *Clin Pharmacol Ther*. 2024;116(6):1544-1553.

[Full publication list on NCBI](https://www.ncbi.nlm.nih.gov/myncbi/1Fa7ffOzjhiQv/bibliography/public/)
{: .notice--info}

## Selected Presentations

- **Waxse BJ**, et al. A Long COVID Phenotype Risk Score Reveals Decreased Steps and Elevated Resting Heart Rate Before and After Infection. *AMIA Amplify 2026*, Podium.
- **Waxse BJ**, et al. Higher Step Count is Associated with Reduced Risk of Long COVID. *IDWeek 2025*, Podium.
- **Waxse BJ**, Tran TC, Mo H, Denny JC. Identification and Validation of Common Respiratory Infections in All of Us. *AMIA Annual Symposium*, Podium. November 2024.

## Contact

📧 bennettwaxse@gmail.com | 📍 Denver, CO

[GitHub](https://github.com/bwaxse){: .btn .btn--primary} [LinkedIn](https://linkedin.com/in/waxse){: .btn .btn--primary}
