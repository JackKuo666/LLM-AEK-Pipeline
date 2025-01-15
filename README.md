# LLM-AEK-Pipeline

## Introduction

`LLM-AEK-Pipeline` is an automated pipeline for extracting biochemical data from PDF files and evaluating the extraction results. This pipeline consists of three main steps:

1. **PDF to Markdown (pdf_2_md)**: Converts PDF files to Markdown format.
2. **LLM Data Extraction (LLM_extract_data)**: Extracts key data from Markdown files using large language models (LLMs).
3. **Evaluate Extracted Data (evaluate_extracted_data)**: Compares the extracted data with ground truth to assess the extraction accuracy.

## Installation

Ensure the required dependencies are installed:

```bash
pip install -r requirements.txt
```

## Usage

### 1. PDF to Markdown

Convert PDF files to Markdown format and handle documents exceeding 50 pages.

```python
from extract_pipeline import pdf_2_md
pdf_2_md()
```

### 2. LLM Data Extraction

Extract key data from Markdown files and save it in the response folder.

```python
from extract_pipeline import LLM_extract_data
LLM_extract_data()
```

### 3. Evaluate Extracted Data

Compare the extracted data with ground truth to assess accuracy.

```python
from extract_pipeline import evaluate_extracted_data
evaluate_extracted_data()
```

## Directory Structure
```
.
├── analyze_code         # Code for analyzing extracted data 
│
├── data
│   ├── pdf             # PDF files to be processed
│   ├── md              # Converted Markdown files
│   ├── txt             # Extracted text files
│   ├── response        # Extracted data files
│   └── results         # Evaluation results
│
├── prompt              # Prompt files
│   ├── p_3_2_0806.txt  # Prompt for data extraction
│   └── p_2_0826.txt    # Prompt for evaluation
│
├── s1_pdf_2_md         # PDF to Markdown conversion pipeline
│   ├── ocr_mathpix.py  # High-performance PDF to Markdown conversion
│   ├── ocr_pymupdf.py  # Free but less effective PDF to text conversion
│   ├── readme.md       # Usage instructions
│   └── readme_pymupdf.md  # Instructions for text conversion logic
│
├── s2_LLM_extract_data # LLM data extraction pipeline
│   ├── LLM_data_extraction.py  # Main logic for data extraction
│   └── readme.md               # Usage instructions
│
├── s3_evaluate_extracted_data # Evaluation pipeline
│   ├── evaluate_extracted_data.py  # Main logic for evaluation
│   └── readme.md                  # Usage instructions
│
├── extract_pipeline.py  # Main processing logic
├── readme.md            # Project overview
└── requirements.txt     # Dependency list
```

## Parameter Descriptions

### `pdf_2_md()`

- **data_folder_dir**: Path to the data folder, default is `"data/"`.
- **pdf_folder_dir**: Path to the PDF folder, default is `"data/pdf"`.
- **md_folder_dir**: Path to the Markdown folder, default is `"data/md"`.

### `LLM_extract_data()`

- **md_folder**: Path to the Markdown folder, default is `"data/md/"`.
- **response_folder**: Path to the response folder, default is `"data/response/"`.
- **prompt_extract_dir**: Path to the extraction prompt file, default is `"prompt/p_3_2_0806.txt"`.
- **prompt_merge_dir**: Path to the merging prompt file, default is `"prompt/p_2_0826.txt"`.

### `evaluate_extracted_data()`

- **response_dir**: Path to the folder containing LLM extraction results, default is `'data/response/prompt_p_3_2_0806_claude-3-5-sonnet-20240620_128k_stream_max_tokens_8192_temperature_0.1'`.
- **ground_truth_dir**: Path to the ground truth file, default is `'data/ground_truth/km_kcat_all.csv'`.
- **seq**: Delimiter, default is `"|"`.
- **order**: Target column index, default is `-7`.
- **have_dir**: Whether subdirectories exist, default is `0`.

## analyzing extracted data 
# TODO

## Logging

The script uses the `logging` module for recording logs. By default, the log level is set to `INFO`. You can adjust the log level as needed.

```python
import logging
logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')
```

## Notes

1. Ensure all paths and filenames are correct.
2. Complete the `pdf_2_md` step successfully before running `LLM_extract_data`.
3. Complete the `LLM_extract_data` step successfully before running `evaluate_extracted_data`.

## Contact

For questions or suggestions, contact [[menghao.guo.319@gmail.com](mailto:menghao.guo.319@gmail.com)] or submit a GitHub issue.

---

Thank you for using `LLM-AEK-Pipeline`! We hope it helps you efficiently process and analyze biochemical data.