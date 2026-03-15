# PDFFeatureAnalyzer
Python program to extract structural and content features from PDF files for analysis, developed during MSc research. Focused on data cleaning, feature engineering, and preparing datasets for machine learning.
PDF Feature Extraction Pipeline
# Overview

This project implements a Python pipeline for extracting general and structural features from PDF files and exporting them into a structured dataset for analysis.

The system processes a folder containing PDF files and generates a CSV dataset containing various characteristics of each document. These features can later be used for data analysis, anomaly detection, or machine learning applications such as malicious document detection.

This code was originally developed by Maryam Issakhani in 2021 as part of research work under the supervision of Dr. Arash Habibi Lashkari.

## Features Extracted

The pipeline extracts two categories of features:

#### 1. General Features (Python-based)

These are extracted directly using Python and the PyMuPDF (fitz) library.

Examples include:

`PDF file size

Metadata size

Number of pages

Number of objects

Title length

Encryption status

Number of embedded files

Number of images

Presence of extractable text`

These features are computed programmatically from the PDF structure.

#### 2. Structural Features

Structural indicators are extracted using the open-source PDFiD tool.

#### Examples include counts of:

obj

stream

xref

trailer

startxref

encrypt

JavaScript

OpenAction

EmbeddedFile

AcroForm

JBIG2Decode

and other PDF structural markers

Because PDFiD does not provide a Python API, the tool is executed through system commands and its output is parsed automatically during runtime.

### Dataset Creation

The script processes an entire folder of PDFs and generates a structured dataset.

### Example workflow:

Input folder contains multiple PDF files

The script extracts features from each document

Results are compiled into CSV format

## Final output:

result.csv

Each row corresponds to one PDF file and contains its extracted features.

This process was used to generate a dataset from approximately 500 PDF files.

## Requirements

Linux operating system

Python 3

Required Python packages:

`pip install PyMuPDF`
`pip install fitz`


The PDFiD tool must also be available in the project directory.

## Usage

Navigate to the project directory and run:

`python3 pdf_feature_extractor.py path-to-pdf-folder`

Example:

`python3 pdf_feature_extractor.py dataset/pdfs`


The script will analyze all PDF files in the folder and generate:

result.csv

## Notes on Implementation

At the time of development (2021), the PDFiD tool did not expose a usable Python API, so structural feature extraction required invoking the tool via system calls and parsing its output. While this approach is not the most efficient, it allowed integration of structural PDF analysis into the automated pipeline.

## Applications

This type of feature extraction pipeline can support:

malicious PDF detection

document classification

cybersecurity research

feature engineering for machine learning

dataset generation for security analytics
