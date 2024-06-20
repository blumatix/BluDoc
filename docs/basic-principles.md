# Basic Principles
## Generic
BLU DOC defines a basic, generic structure that can describe any digital document.

## One BluDoc per Document
One BluDoc represents one document. A BluDoc descrition of a pdf document including e.g. an invoice and a delivery note requires 2 BluDoc jsons to describe both documents.Hint: if a file contains multiple documents which belong together (e.g. invoice and delivery note), those additional documents could be handled as "attachments" in the future.

## Supports Common Business Documents
Additionally, it provides pre-defined DocumentEssential schemas for general purpose business documents to ease data exchange between companies (e.g. universal schema for invoice, quotations, etc.).

## Concise, Readable
BluDoc content and structure is easy to read and understand.

## Optional
BluDoc provides a structure. To what extent you use it is up to you, the json schema includes mainly optional elements.

## Redundancy is ok
For human readability and ease of processing information within different elements of BluDoc can be redundant but must be consistent.
