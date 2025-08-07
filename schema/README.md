# BluDoc Schema

This directory contains the JSON schema definition for BluDoc, which defines the structure, content, and constraints of BluDoc documents.

## Schema Files

- **BluDoc_Schema_V1.4.2.json**: The latest schema file for BluDoc with enhanced invoice fields for accounting, payment processing, and delivery management.
- **BluDoc_Schema_V1.4.1.json**: Previous schema version.
- **bludoc-schema_v1.4.0.json**: Legacy schema version.

## Overview

The BluDoc schema provides a standardized format for defining documents. It ensures that documents are structured correctly and consistently, making it easier to create, validate, and process them across different implementations.

### Version 1.4.2 Enhancements

The latest version (1.4.2) includes significant enhancements for invoice document processing:

- **Enhanced Accounting Fields**: Added `AccountingEntry.Item` with mandatory `AccountingText.String` for business categorization
- **Payment Processing**: New fields for `PaymentStatus.Type`, `PaymentMethod.Type`, and `Payment.Amount`
- **Referenced Documents**: Support for `ReferencedInvoice.Id` to link credit notes and related documents
- **Delivery Management**: Complete `Delivery.Contact.Item` structure for separate delivery addresses
- **Improved Validation**: Enhanced field descriptions and validation rules for invoice-specific data

## Usage

### Validating Documents

You can use the BluDoc schema to validate documents. Here's a basic example using Python with the `jsonschema` library:

```python
import json
from jsonschema import validate, ValidationError

# Load the JSON schema from a file
try:
    with open('path/to/your/BluDoc_Schema_V1.4.2.json') as schema_file:
        schema = json.load(schema_file)
except FileNotFoundError:
    print("Schema file not found. Please check the path.")
    exit()

# Load the JSON document to be validated from a file
try:
    with open('path/to/your/bludoc.json') as doc_file:
        document = json.load(doc_file)
except FileNotFoundError:
    print("Document file not found. Please check the path.")
    exit()

# Validate the JSON document against the schema
try:
    validate(instance=document, schema=schema)
    print("Document is valid.")
except ValidationError as e:
    print("Document is invalid:", e.message)
except Exception as e:
    print("An unexpected error occurred:", str(e))
```

## References

- [JSON Schema Specification](https://json-schema.org/specification.html)
- [jsonschema Library Documentation](https://python-jsonschema.readthedocs.io/)
