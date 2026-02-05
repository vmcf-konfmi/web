---
title: Annotation Guideline Template
slug: annotation-guideline-template
status: publish
post_type: page
---

# Annotation Guideline Template

Use this template to create clear, concise annotation guidelines for your project. Distribute to annotators before they begin labeling. A well-written guideline saves time and improves consistency.

## 1. Project Overview

**Project Title**: [Name of the project or dataset]

**Scientific Goal**: [Brief summary of what you're measuring or classifying — e.g., "Segment individual nuclei in confocal Z-stacks to quantify nuclear morphology and fluorescence intensity."]

**Image Type**: [Modality, magnification, typical image size — e.g., "Confocal Z-stacks, 63× oil immersion, 1024×1024 pixels, 8-bit grayscale, Channel: DAPI (nuclei)."]

**Expected Outcome**: [What the labels will be used for — e.g., "Train a Cellpose instance segmentation model; validate by comparing predicted vs. manual nuclear areas."]

---

## 2. Annotation Task Definition

### What to label?
- **Object(s)**: [e.g., "Individual nuclei" or "Cell boundaries" or "Spots/puncta"]
- **Label format**: [e.g., "Instance masks" or "Point coordinates" or "Bounding boxes"]
- **Classes** (if multi-class):
  - Class A: [definition]
  - Class B: [definition]
  - etc.

### What NOT to label?
- [e.g., "Nuclei at image borders (touching edge)" or "Debris or artifacts <5 pixels"]
- [e.g., "Overlapping or touching cells (only if ambiguous; otherwise best-effort separation)"]

### Ambiguous cases — decision rule
- **If nuclei touch or overlap**: [e.g., "Separate along visible boundary; if unclear, use domain expert adjudication."]
- **If signal is faint or noisy**: [e.g., "Include if nucleus is visible in raw data; threshold at ~50% of brightest nuclei."]
- **If object is partially outside FOV**: [e.g., "Include if >50% of nucleus is visible; trace the visible portion."]

---

## 3. Annotation Process (Step-by-Step)

### Step 1: Open image in annotation software
- Software: [e.g., "FIJI/ImageJ with Trainable Weka Segmentation plugin" or "Napari" or "QuPath"]
- Load: [e.g., "File → Open → select .tif file"]
- Adjust display: [e.g., "Image → Adjust → Levels to enhance contrast; use LUT='Gray'"]

### Step 2: Inspect raw data
- Check signal-to-noise ratio and background levels.
- Identify obvious objects to label.
- Note any artifacts or unexpected patterns → flag for domain expert if needed.

### Step 3: Create labels
- **For masks**: trace object boundaries using the polygon/freehand tool. Ensure closed regions; save as integer labels (1 = object 1, 2 = object 2, etc., 0 = background).
- **For points**: place a single point at the object center or tip. Record coordinates (x, y) or use software's native format.
- **For scribbles**: draw a short line through the object interior; used by some semi-automatic tools.

### Step 4: Self-QC (before saving)
- [ ] Check that all obvious objects are labeled.
- [ ] Verify labels do not overlap (unless intentional for ambiguous cases).
- [ ] Confirm label format matches expected output (masks are integer, no gaps, etc.).
- [ ] Flag any questionable regions with a note (e.g., "faint signal — check with expert").

### Step 5: Save
- Save as: [e.g., "image_name_mask.tif (16-bit, integer labels)" or "image_name_points.csv (x, y columns)"]
- Store in: [e.g., "project_folder/annotations/"]

---

## 4. Common Mistakes & How to Avoid Them

| Mistake | Example | Fix |
|---------|---------|-----|
| **Over-segmentation** | Labeling small noise as separate objects | Use size threshold (e.g., "only label objects >20 pixels") |
| **Under-segmentation** | Merging two touching cells into one label | Carefully trace boundaries; separate if two distinct centers visible |
| **Border objects** | Including/excluding nuclei at image edge inconsistently | Decide upfront: include if >50% visible, or exclude entirely |
| **Contrast adjustment** | Using extreme levels to reveal hidden objects | Use moderate adjustments only; annotate what you see in raw data |
| **Forgetting metadata** | Not recording image acquisition parameters | Record exposure, laser power, pinhole size in a log or README |

---

## 5. Example Annotations

### Good example
- **Image**: [file name]
- **Description**: [e.g., "Well-separated nuclei in DAPI channel; clear boundaries; 8 nuclei labeled with IDs 1–8."]
- **File**: [link to annotated_example.tif or screenshot]

### Ambiguous example
- **Image**: [file name]
- **Description**: [e.g., "Two touching nuclei (IDs 1–2) separated along faint boundary; domain expert approved."]
- **File**: [link to example_ambiguous.tif or screenshot]

### Edge case (excluded)
- **Image**: [file name]
- **Description**: [e.g., "Nucleus at image border (ID removed); too little visible area."]
- **File**: [link to example_excluded.tif or screenshot]

---

## 6. Quality Assurance & Feedback

### Self-check before submission
- [ ] All objects labeled consistently?
- [ ] Labels match the decision rules in section 2?
- [ ] File format and naming correct?
- [ ] Any ambiguous regions flagged and ready for expert review?

### Analyst will check
- [ ] ~5–10% sample of your annotations for inter-annotator agreement.
- [ ] Provide feedback within [X days]; expect ~[Y%] agreement target on IoU or Cohen's kappa.

### If disagreement is high
- Analyst will hold a calibration meeting to clarify guidelines.
- Annotator may re-do a subset or discuss ambiguous cases with domain expert.

---

## 7. Contact & Questions

- **Annotation lead**: [Name, email]
- **Domain expert (ambiguous cases)**: [Name, email]
- **Bioimage analyst (technical support)**: [Name, email]
- **Expected response time**: [e.g., "24–48 hours during business days"]

If you're unsure, flag it and ask — it's better to clarify early than spend time on incorrect labels!

---

## 8. Timeline & Milestones

| Milestone | Target Date | Notes |
|-----------|------------|-------|
| Guidelines finalized | [Date] | All annotators trained |
| Pilot (20–50 images) | [Date] | Test per-image time; refine guidelines if needed |
| Calibration meeting | [Date] | Discuss ambiguous cases and edge cases |
| Bulk annotation | [Date] – [Date] | Production labeling |
| Inter-annotator QC | [Date] | 10–20% double-annotated for agreement check |
| Final review & sign-off | [Date] | Domain expert approves held-out validation set |

---

## Appendix: Software-Specific Tips

### FIJI / ImageJ
- Use **Edit → Selection → Create Selection** to convert drawn regions to binary masks.
- Export masks as **16-bit TIFF** with sequential labels (1, 2, 3, ...).
- Plugin: **Trainable Weka Segmentation** provides semi-automatic assistance.

### Napari
- Use **Image → Labels** layer for mask annotation.
- Keyboard shortcut: **E** for eraser, **Shift** for pan.
- Export labels: **File → Export** as TIFF or NPY.

### QuPath
- Use **Annotations → Add annotations → Brush** for free-form tracing.
- **Measurements → Export annotations** to CSV or GeoJSON.
- Supports hierarchical classification (e.g., "Nucleus → Type A / Type B").

### Ilastik
- Train classifier on a few example objects.
- Use **Interactive segmentation** mode to refine predictions interactively.
- Export: **File → Export As → Label Image (TIFF)**.

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | [Name] | Initial guideline |
| 1.1 | [Date] | [Name] | Added ambiguous case examples |
| — | — | — | — |
