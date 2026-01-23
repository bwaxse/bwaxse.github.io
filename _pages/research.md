---
permalink: /research/
title: "Research"
---

## Overview

My path to computational infectious diseases began in molecular biology—studying how myosin VI facilitates autophagy and intercellular communication through quantitative microscopy. During residency at the University of Chicago, I discovered that computational methods could directly enhance patient care. This led me to NIAID and Josh Denny's lab at NHGRI, where I paired clinical experience with expertise in computable phenotyping. The work that emerged focuses on a central problem: how do we extract research-grade phenotypes from messy clinical data to enable discovery at scale?

## Research Philosophy

My work sits at the intersection of informatics, clinical medicine, and genomics—a space where careful phenotyping and thoughtful data harmonization enable discovery at scale. I'm committed to building methods that are both methodologically rigorous and clinically useful, with a particular focus on infectious disease where EHR-based approaches are underutilized despite the complexity and vulnerability of affected populations.

## Current Projects

**Long COVID Phenotyping and Wearable Risk Prediction**
Developing EHR-based phenotype definitions for post-acute sequelae of SARS-CoV-2 infection (PASC, Long COVID). The challenge here isn't just identifying who has Long COVID—it's distinguishing persistent post-infection functional impairment from coincident conditions in noisy EHR data. I'm using temporal phenotyping approaches (Cox proportional hazards PheWAS) to create a Long COVID risk score that achieves 94% AUROC. By integrating EHR data and wearable activity metrics, this work demonstrates how precise phenotyping can improve discovery for this vulnerable population.

**Computable Phenotypes for Respiratory Infectious Disease**
With collaborators at NIAID and USUHS, I developed the first multi-component computable phenotype for respiratory viral infections, integrating laboratory results, billing codes, and antiviral prescriptions. This work revealed critical performance differences across viruses—something investigators need to consider before implementing phenotypes for research. The phenotype achieves positive predictive values >0.76 across all viruses while matching CDC surveillance trends, validating that EHR data can capture infectious disease at population scale.

**Genetic Susceptibility to Respiratory Infection**
Building on refined phenotyping, I'm conducting genome-wide association studies examining how human genetic variation influences susceptibility to respiratory infections and other infectious disease outcomes. Here, we think precise phenotyping + large biobank datasets = discovery of biological mechanisms at human-scale.

## Collaboration and Mentorship

My work is fundamentally collaborative. I benefit from strategic mentoring relationships spanning biostatistics, genomics, and clinical informatics. I'm actively involved with the Infectious Diseases Informatics Interest Group (IDIIG) at IDSA and I helped start a Health Informatics Journal Club at NHGRI, because I believe the intersection of ID and informatics is still early—and because these conversations push all of us to ask better questions.

My research also includes collaborations on those that work on rare disease genetics, sarcoidosis genomics with refined phenotyping, HPV disease, methodological development for laboratory value standardization within OMOP CDM, and more.

## Publications

[Link to Google Scholar](https://scholar.google.com/citations?user=16OEFu8AAAAJ) • [ORCID](https://orcid.org/0000-0001-5086-3419)

*Selected recent work:*
**Waxse BJ**, Rao S. Data science for pediatric infectious disease: utilizing COVID-19 as a model. *Curr Opin Infect Dis.* 2025;38(5):493-498. [PMID: 40748012](https://pubmed.ncbi.nlm.nih.gov/40748012/)

**Waxse BJ**, Bustos Carrillo FA, Tran TC, Mo H, Ricotta EE, Denny JC. Computable phenotypes to identify respiratory viral infections in the *All of Us* research program. *Sci Rep.* 2025;15(1):18680. [PMID: 40437102](https://pubmed.ncbi.nlm.nih.gov/40437102/)

Goleva SB, Williams A, Schlueter DJ, Keaton JM, Tran TC, **Waxse BJ**, Ferrara TM, Cassini T, Mo H, Denny JC. Racial and ethnic disparities in antihypertensive medication prescribing patterns and effectiveness. *Clin Pharmacol Ther.* 2024;116(6):1544-1553. [PMID: 39051523](https://pubmed.ncbi.nlm.nih.gov/39051523/)

Mo H, Channa Y, Ferrara TM, **Waxse BJ**, Schlueter DJ, Tran TC, Awan AH, Goleva SB, Williams A, Babbar A, Stubblefield O, Keaton JM, Larson EA, Wilke RA, Denny JC. Hyponatremia associated with the use of common antidepressants in the All of Us Research Program. *Clin Pharmacol Ther.* 2025;117(2):534-543. [PMID: 39540435](https://pubmed.ncbi.nlm.nih.gov/39540435/)

## Presentations and Mentoring

**Selected Recent Talks**
- **AMIA 2024**: Identification and Validation of Common Respiratory Infections in *All of Us*
- **IDWeek 2025**: Higher Step Count is Associated with Reduced Risk of Long COVID

I'm actively mentoring students and fellows on phenotyping projects that explore how methodological choices (EHR alone, survey alone, or combined approaches) dramatically affect genomic discovery—work that's often invisible but critical for robust research design.

## Tools and Resources

**[Scholia.fyi](https://scholia.fyi)** - An AI-powered platform I built to improve how we engage with primary literature. The premise: reading papers carefully matters, but modern AI can accelerate critical appraisal. Scholia provides structured analysis of methodology, interpretation of results, and identification of limitations—it root's you in the fundamentals when you're reading dozens of papers, and it's focused on what you learn during the conversation. Built from the observation that as a clinician-scientist, I was spending disproportionate time on literature review and let's face it, there's just too much to read these days. What I don't want to do is surrender all reading to LLMs, so let's do it together. 

**OMOP Implementation Resources** - Documentation and reusable pipelines for large-scale EHR data extraction and phenotyping in the _All of Us_ Research Program, available upon request.

**GWAS Pipeline Templates** - Production-ready code for multi-ancestry GWAS using SAIGE and METAL, including distributed computing setup via dsub on Google Cloud.
