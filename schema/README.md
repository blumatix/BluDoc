# BluDoc Schema

This directory contains the JSON schema definition for BluDoc, which defines the structure, content, and constraints of BluDoc documents.

## Schema File

- **bludoc_schema_v1.4.0.json**: The schema file for BluDoc.

## Overview

The BluDoc schema provides a standardized format for defining documents. It ensures that documents are structured correctly and consistently, making it easier to create, validate, and process them across different implementations.

## Usage

### Validating Documents

You can use the BluDoc schema to validate documents. Here's a basic example using Python with the `jsonschema` library:

```python
import json
from jsonschema import validate, ValidationError

# Load the JSON schema from a file
try:
    with open('path/to/your/bludoc-schema_v1.4.0.json') as schema_file:
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
