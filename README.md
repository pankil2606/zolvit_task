# Invoice Data Extraction

This Python script extracts invoice data from PDF files and saves it to a CSV file. It uses regular expressions to parse key invoice details such as invoice number, invoice date, customer name, and amounts.

## Table of Contents
- [Requirements](#requirements)
- [Usage](#usage)
- [Functionality](#functionality)
- [License](#license)

## Requirements

- Python 3.x
- Libraries:
  - `pdfplumber`
  - `csv`
  - `re`
  - `os`

You can install the required library using pip:

```bash
pip install pdfplumber
```

## Usage

### Prepare Your PDF Files:

- Place all your PDF invoices in a ZIP file.
- Update the `zip_file_path` variable in the script to point to your ZIP file location.
- The script will extract the contents of the ZIP file into a specified directory.

```python
import zipfile
import os

# Path to the ZIP file in Colab (for example, from your Google Drive)
zip_file_path = '/content/sample_data/zolvit.zip'  # Replace with your actual ZIP file path

# Directory where you want to extract the contents
extract_to_dir = '/content/extracted_folder/'  # Replace with your desired extraction path

# Create the directory if it doesn't exist
os.makedirs(extract_to_dir, exist_ok=True)

# Extract the ZIP file
with zipfile.ZipFile(zip_file_path, 'r') as zip_ref:
    zip_ref.extractall(extract_to_dir)

print(f"Files extracted to: {extract_to_dir}")
```

## Output

The script will generate a CSV file named `invoice_data_2.csv` in the same directory as the script. This file contains the extracted invoice details.

## Functionality

The script performs the following tasks:

### Extract Invoice Data:

- Reads PDF files from the specified directory.
- I have only extracted important data as per business requrement there is no need to extract the company data as it is same for all
- Uses `pdfplumber` to extract text from each PDF page.
- Applies regex patterns to extract key information such as:
  - **Invoice Number**
  - **Invoice Date**
  - **Due Date**
  - **Customer Name**
  - **Taxable Amount**
  - **CGST and SGST amounts**
  - **Total Amount**
  - **Total Discount**
  - **Total Items/Qty**
  - **Amount in Words**
    



### Save Extracted Data:

- Writes the extracted data into a CSV file.

### Print Accuracy:

- Calculates and displays the accuracy of data extraction for each field.
