# Invoice Samples

This folder contains various samples and documentation for the Invoice document type. Below is an overview of the contents available in this directory:

## Contents

- `muster_rechnung_de-AT.pdf`: A PDF document containing a sample Invoice in German/Austrian format.
- `muster_rechnung_de-AT.json`: The JSON sample of this Invoice document.
- `invoice-documentessentials.md`: Documentation outlining the available document essentials of an Invoice document.

## Overview

### Invoice Document (PDF)

The `muster_rechnung_de-AT.pdf` file provides a sample Invoice document in German/Austrian format. This sample can be used as a reference for the structure and content of a typical Invoice document.

### JSON Sample

The `muster_rechnung_de-AT.json` file contains a JSON representation of the Invoice document. This sample demonstrates how an Invoice document can be structured in JSON format according to the BluDoc standards. The sample includes comprehensive invoice data extraction including:

- Basic invoice information (ID, date, type)
- Contact details for sender and receiver
- Payment information and bank account details
- Line items with descriptions and amounts
- VAT calculations and totals
- Delivery information
- Accounting and payment status details

### Documentation

The `invoice-documentessentials.md` file provides detailed information about the essential components of an Invoice document. It includes descriptions of key fields such as invoice identification, contact information, payment details, delivery addresses, accounting categorization, and all structured data elements that can be extracted from invoice documents.

## Usage

### Viewing the Documents

- **PDF Document**: Open `muster_rechnung_de-AT.pdf` with any PDF viewer (e.g., Adobe Acrobat Reader, web browsers).

### JSON Sample

To view the JSON sample, you can use any text editor or JSON viewer. The sample can also be used in your applications to test JSON parsing and validation against the Invoice schema.

### Documentation

Read the `invoice-documentessentials.md` file to understand the structure and requirements of the Invoice document. This file provides essential details that are crucial for creating and validating Invoice documents, including the new enhanced fields for accounting, payment processing, and delivery management.
