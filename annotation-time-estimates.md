---
title: Annotation Time Estimates
slug: annotation-time-estimates
status: publish
post_type: page
---

# Project types and user expectations

This section explains what the bioimage analyst does, what we expect from the user - annotator and the domain expert, and realistic minimum/maximum annotation time estimates per project type.

## Roles & responsibilities

- **Bioimage Analyst**: lead technical work — prepare annotation guidelines, provide example annotations, run training and validation, tune pipelines, perform QC, and deliver scripts/models/reports.
- **Annotator (User - PI / Scientist)**: produce labels (masks, points, scribbles) following the analyst's guidelines, perform initial self-QC, and flag ambiguous cases.
- **Domain Expert (User - PI / Scientist)**: resolve ambiguous cases, review and accept validation results, and provide biological interpretation and acceptance criteria.

## Practical annotation expectations (per project type)

Each entry lists: annotation type, per-image annotation time range, recommended image counts, and resulting user time (min → max). Times assume a single annotator; parallel annotation reduces calendar time but multiplies total person-hours.

### 1) Workflow / macro design (ImageJ, QuPath, simple Python)
If needed:
- Annotation type: example ROIs, spot-checks (not full masks).
- Per-image time: 1–10 minutes.
- Images needed: 5–50 representative images.
- User time:
	- Minimum: 5 images × 1 min = 5 minutes.
	- Typical: 20 images × 5 min = ~1.5 hours.
	- Maximum: 50 images × 10 min = ~8.5 hours.
- People: 1 annotator + 1 domain expert reviewer for edge cases.

### 2) Tool review / reproducibility check
For benchmarking or comparison:
- Annotation type: ground-truth masks or measurement labels for benchmarking subset.
- Per-image time: 5–30 minutes (mask complexity dependent).
- Images needed: 10–100 (benchmark subset 10–30; robust check 50–100).
- User time:
	- Minimum: 10 × 5 min = ~50 minutes.
	- Typical: 30 × 15 min = ~7.5 hours.
	- Maximum: 100 × 30 min = ~50 hours.
- People: 1–2 annotators; include independent reviewer for 10–20% to estimate agreement.

### 3) Transfer learning / fine-tuning (Cellpose, Stardist, ilastik, etc.)
- Annotation types & per-image time:
	- Full instance masks: 5–30 minutes per image (dense fields are slower).
	- Sparse labels (points/scribbles): 1–5 minutes per image.
- Images needed:
	- Minimal feasibility: 20–50 annotated images (small domain shift).
	- Practical fine-tune: 100–400 images.
	- Robust generalization: 500–2000+ images/instances for high heterogeneity.
- User time (single annotator):
	- Minimal: 20 images × 5 min = ~1.7 hours.
	- Typical: 200 × 10 min = ~33 hours (~5 workdays).
	- Heavy: 800 × 20 min = ~34 workdays.
- Annotators: 1 trained annotator for pilot; 2–3 for production (throughput + agreement), plus domain expert adjudication.
- Notes: expect 3–10 annotate→train→validate iterations; budget 20–40% extra time for rework.

### 4) Tool development / training from scratch / large projects
- Annotation type: extensive full masks, multi-class labels, hierarchical annotations, curated QA.
- Per-image time: 10–60 minutes (task complexity determines time).
- Images needed: often 1,000s of images/instances for robust models.
- User time:
	- Pilot: 100 × 15 min = ~25 hours.
	- Production labeling: 1,000 × 25 min = ~52 workdays (single annotator).
	- Full projects: multiple person-months (team effort).
- Annotators: larger teams (3–10) with dedicated QA and domain expert adjudication.

## Annotation workflow & QA (recommended expectations)
- Analyst provides a concise annotation guideline (1–2 pages) and 10 exemplar annotated images before bulk annotation.
- Run a pilot (20–50 images) to measure per-image time and clarify ambiguous cases.
- Reserve 10–20% of images for domain expert adjudication.
- Have a second annotator label 10–20% of data to measure inter-annotator agreement (IoU/Cohen's kappa).
- Use active learning / pre-labeling to prioritize uncertain images and reduce total annotation need.
- Plan for parallel annotators only with calibration meetings and shared examples to maintain consistency.

## Quick single-annotator time summary
- Workflow/macro: < 2 hours.
- Small benchmark / transfer pilot: 2–10 hours.
- Transfer fine-tuning: 20–100+ hours (spread across days/weeks).
- From-scratch development: 200–500+ hours (team effort; months).


