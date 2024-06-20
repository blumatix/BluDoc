# BluDoc Schema

This directory contains the JSON schema definition for BluDoc, which defines the structure, content, and constraints of BluDoc documents.

## Schema File

- **bludoc_dchema_v1.4.0.json**: The schema file for BluDoc.

## Overview

The BluDoc schema provides a standardized format for defining documents. It ensures that documents are structured correctly and consistently, making it easier to create, validate, and process them across different implementations.

## Usage

### Validating Documents

You can use the BluDoc schema to validate documents. Here's a basic example using Python with the `jsonschema` library:

1. **Install jsonschema**:
   ```sh
   pip install jsonschema

2. **Validate a document**:
import json
from jsonschema import validate, ValidationError

# Load the schema
with open('schema/bludoc_schema.json') as schema_file:
    schema = json.load(schema_file)

# Load a document to validate
with open('samples/sample1.json') as doc_file:
    document = json.load(doc_file)

# Validate the document
try:
    validate(instance=document, schema=schema)
    print("Document is valid.")
except ValidationError as e:
    print("Document is invalid:", e.message)

## References

- [JSON Schema Specification](https://json-schema.org/specification.html)
- [jsonschema Library Documentation](https://python-jsonschema.readthedocs.io/)
