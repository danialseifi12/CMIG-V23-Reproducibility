# CMIG-V23-Reproducibility
Reproducibility code and supporting research data for patient-block conformal calibration in adaptive radiotherapy.
# Reproducibility Repository — Patient-Block Conformal Calibration in Adaptive Radiotherapy

**Research code and supporting numerical data for the manuscript**

*Patient-block conformal calibration of probabilistic deformable image registration uncertainty in adaptive radiotherapy*

**Target journal:** Computerized Medical Imaging and Graphics (CMIG)  
**Repository release:** V23 — Research code and data archive

## 1. Overview

This repository provides the analysis scripts, numerical inputs, reference outputs, verification tests, and supporting documentation associated with the study.

It is intended to help reviewers independently inspect and rerun the released numerical analyses.

**The submitted manuscript, supplementary document, cover letter, title page, highlights, and final publication artwork are not included in this repository.**

The complete research archive is available here:

**[CMIG_V23_GITHUB_CODE_REPOSITORY.zip](CMIG_V23_GITHUB_CODE_REPOSITORY.zip)**

The archive is distributed as a ZIP file. Reviewers should download and extract it to access the scripts, data, and detailed documentation.

## 2. Repository Contents

After extraction, the archive contains the following main components:

```text
CMIG_V23_Code_Repository/
│
├── README.md
├── requirements.txt
├── run_verification.py
├── verify_package.py
├── verify_public_archive.py
├── verify_calibration.py
├── CHECKSUMS.csv
├── SOURCE_DATA_PRESERVATION.json
│
├── 02_Reproducibility_Package/
│
└── 02_Research_Data_and_Code/
    └── Patient_Block_DIR_Reproducibility/
        ├── Core_Statistical_Reproduction/
        ├── Dose_Constraint_Decision_Analysis/
        ├── Analysis_Specific_Verification/
        ├── Numerical_Source_Verification/
        ├── Release_Reconciliation/
        └── CANONICAL_ANALYSIS_LAYERS.md
```

The included components support verification of calibration, longitudinal statistical models, endpoint-level interval scores, uncertainty propagation summaries, dose reconciliation, coded patient linkage, and selected bootstrap analyses.

Detailed analysis-specific documentation is provided inside the archive.

## 3. Installation and Requirements

**Recommended environment:** Python 3.12.

Create and activate a virtual environment:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
```

Install the required packages:

```bash
python -m pip install -r requirements.txt
```

After the initial installation, the supplied numerical verification workflow does not require internet access.

## 4. Reproducing the Analyses

First, verify the integrity of the downloaded package:

```bash
python verify_package.py
```

Check that publication documents are excluded and protected scientific inputs are unchanged:

```bash
python verify_public_archive.py
```

Run the complete numerical verification workflow:

```bash
python run_verification.py
```

The supplied verification report records:

| Verification component | Reported result |
|---|---|
| Numerical and code verification components | 20/20 PASS |
| Python regression tests | 60/60 PASS |
| Protected scientific input tables | 38 preserved |
| Publication-document exclusion | PASS |

The main runner invokes the nested verification workflow and generates execution reports, including:

`VERIFICATION_RUN_REPORT.json`

`RUN_ENVIRONMENT.json`

These reports document the results and software environment.

**Important:** Some output files may be regenerated during execution. The complete-package checksums should therefore be verified before running the analyses.

For subsequent checks of immutable source data, use:

```bash
python verify_package.py --static
```

## 5. Scientific Reproducibility Scope

The archive supports numerical verification of the released derived-data analyses, including:

- Patient-block calibration and associated numerical checks.
- Adjusted longitudinal model refitting and four-test Holm adjustment.
- Endpoint-level interval scores and controlled-reference containment.
- Documented dose-layer reconciliation.
- Coded patient and registration linkage.
- Source-level summaries and selected bootstrap verification.
- Historical intermediate numerical replay.

The included lightweight response-replay checkpoint is **not equivalent to the original clinical registration network**.

The archive does not contain native clinical DICOM images, original clinical registration-model weights, or the complete native clinical image-to-dose implementation.

Consequently, these scripts do not independently reproduce the entire clinical imaging and radiotherapy workflow from raw patient images.

The controlled-reference interval-score, intermediate-replay, and dose-decision analyses also have distinct recorded dose-coordinate conventions.

See `CANONICAL_ANALYSIS_LAYERS.md` and `RECONCILIATION_METHOD.md` inside the archive for further details.

## 6. Data Integrity

The repository includes integrity-verification mechanisms based on SHA-256 checksums.

`CHECKSUMS.csv` records the delivered package snapshot.

`SOURCE_DATA_PRESERVATION.json` identifies protected scientific input tables.

The provided scripts distinguish between the original delivered files and outputs regenerated during verification.

Reviewers are encouraged to preserve the original archive before executing the analysis scripts.

## 7. Data Availability and Ethical Considerations

The archive contains coded, patient-level derived research data.

Public availability and reuse remain subject to the applicable institutional data-sharing permissions, ethics requirements, and privacy protections.

Directly identifying clinical information, native clinical imaging data, and restricted institutional materials are not provided.

Requests concerning restricted data or reuse permissions should be directed to the corresponding author.

## 8. Citation

Researchers using this resource should cite the corresponding article once its final bibliographic details become available.

The exact GitHub repository version or commit used for reproduction should also be identified.

No DOI is currently assigned to this repository.

## 9. Contact and Reproducibility Questions

For questions regarding numerical verification, please specify the relevant script, input data, expected output, and software environment.

Detailed methodological and computational information is available in the nested README files included in the downloadable archive.
