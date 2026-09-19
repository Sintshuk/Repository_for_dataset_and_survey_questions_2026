# Supplementary material — privacy personas (IoT survey)

Anonymized artifact for the double-blind submission. It contains the de-identified survey
responses, the survey instrument, the 33 clustering features with their construct codes and
domain grouping, the 15-question onboarding subset, and the cluster-count metric scan.

## Files

| File | Contents |
|------|----------|
| `final_preprocessed_dataset_clustering_for_privacy_personas.xlsx` | De-identified, preprocessed survey responses (n=510). |
| `dataset_with_33_features_marked_clustering_for_privacy_personas.xlsx` | The 33 clustering features: row 1 = construct code (QA_1…QP_7), row 2 = full item wording, following rows = coded responses, plus the assigned cluster. |
| `Questionaire_complete_set.pdf` | Full survey instrument (all 58 items across seven sections). |
| `selective_set_33_questions_clustering.pdf` | The 33 items used for clustering. |
| `Qualtrics_survey_preview` | Link to the live Qualtrics survey preview. |
| `onboarding_15.csv` | The 15-question onboarding subset, ranked by Random-Forest importance (see the paper, Lightweight persona assignment). |
| `metric_scan_over_k.csv` | Internal indices, minimum-cluster share, and resample ARI for k = 2…10 (see the paper, choosing the number of clusters). |
| `heldout_assignability.csv` | Held-out / nested cross-validation accuracy of the persona classifier (full 33, nested top-15, fixed paper-15), backing the selection-bias check. |
| `ordinal_robustness.csv` | ARI between the deployed partition and re-clusterings under ordinal-appropriate representations (incl. Spearman-rank PCA, ARI 0.735), backing the dimensionality/interval-treatment check. |
| `assignment_confidence.csv` | Accuracy by assignment-confidence decile on held-out users, backing the confidence-aware assignment result. |

## Response coding

All 33 clustering features are integer-coded. **32 items use a 1–5 scale** (five-point Likert
agreement, four-point frequency, or five-point willingness, per the instrument); **`QP_5`
(privacy–functionality trade-off, single choice) is coded 0–4.** For the Comfort domain score,
the three control-*concern* items `QCT_7`, `QCT_8`, `QCT_9` are reverse-scored so that higher
always means more comfortable. Non-clustering columns in the raw workbook may use 0 for
"device not used / not shown"; the 33 clustering features contain no such placeholders.

## The 33 features: code, survey item, domain, scale

Five thematic domains aggregate the 33 items into the per-persona profiles used in the paper.


### Awareness (QA)

| Code | Qualtrics ID | Gloss | Scale |
|------|--------------|-------|-------|
| QA_1 | Q6_1 | aware a privacy policy exists for the device | 1–5 |
| QA_2 | Q6_2 | aware of the policy's purpose | 1–5 |
| QA_3 | Q13_1 | aware of the opt-out option | 1–5 |
| QA_4 | Q13_2 | aware of the privacy-by-default option | 1–5 |
| QA_5 | Q15_1 | aware of on-device privacy choices | 1–5 |
| QA_6 | Q17_1 | aware of the right to access | 1–5 |

### Comprehension (QC)

| Code | Qualtrics ID | Gloss | Scale |
|------|--------------|-------|-------|
| QC_1 | Q11_1 | understand what data is collected | 1–5 |
| QC_2 | Q11_2 | understand how data is used | 1–5 |
| QC_3 | Q11_3 | understand retention duration | 1–5 |
| QC_4 | Q12_1 | can identify personal data | 1–5 |
| QC_5 | Q12_2 | understand collection purpose | 1–5 |
| QC_6 | Q12_3 | can identify sensitive data | 1–5 |
| QC_7 | Q12_4 | understand sensitive-data purpose | 1–5 |
| QC_8 | Q12_5 | understand who data is shared with | 1–5 |

### Privacy behaviours (QPB)

| Code | Qualtrics ID | Gloss | Scale |
|------|--------------|-------|-------|
| QPB_1 | Q19_1 | accept policies without reading | 1–5 |
| QPB_2 | Q19_3 | stopped using a device over privacy | 1–5 |
| QPB_3 | Q19_4 | declined a purchase over privacy | 1–5 |

### Comfort (QCT)

| Code | Qualtrics ID | Gloss | Scale |
|------|--------------|-------|-------|
| QCT_1 | Q22_1 | comfort: data for targeted ads | 1–5 |
| QCT_2 | Q22_2 | comfort: data for personalized content | 1–5 |
| QCT_3 | Q22_3 | comfort: sharing with manufacturer | 1–5 |
| QCT_4 | Q22_4 | comfort: sharing with third parties | 1–5 |
| QCT_5 | Q22_5 | comfort: sharing with government | 1–5 |
| QCT_6 | Q22_6 | comfort: use to improve services | 1–5 |
| QCT_7 | Q23_1 | concern: lack of control (reverse-scored) | 1–5 |
| QCT_8 | Q23_2 | concern: data combination across sources (reverse-scored) | 1–5 |
| QCT_9 | Q23_3 | concern: AI-based decisions (reverse-scored) | 1–5 |

### Preferences (QP)

| Code | Qualtrics ID | Gloss | Scale |
|------|--------------|-------|-------|
| QP_1 | Q15_2 | want personalized privacy advice | 1–5 |
| QP_2 | Q17_2 | have used the right to access | 1–5 |
| QP_3 | Q17_3 | interested in the right to access | 1–5 |
| QP_4 | Q19_2 | would pay a premium for privacy | 1–5 |
| QP_5 | Q24 | privacy-vs-functionality trade-off | 0–4 |
| QP_6 | Q25_1 | prefer privacy-by-default (personal) | 1–5 |
| QP_7 | Q25_2 | prefer privacy-by-default (sensitive) | 1–5 |

## Reproducing the personas

Personas are six clusters from K-Means (k=6, Euclidean) on a two-component PCA of the 33
standardized features; assignment for new users uses nearest-centroid on the 15 onboarding
items. Full method, parameters, and results are in the paper.

