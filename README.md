# BluDoc

BluDoc is a human-readable, AI-minded format to describe any business document.
Use the schema files and samples in this repo to validate and explore BluDoc.

## Samples
- [classification](samples/classification)
- [invoice](samples/invoice)
- [order](samples/order)
- [orderconfirmation](samples/orderconfirmation)
- [quotation](samples/quotation)
- [timesheet](samples/timesheet)

## Document Essentials
- [All document details](docs/document-essentials/all-document-details.md)
- [BankStatement](docs/document-essentials/bankstatement-documentessentials.md)
- [DeliveryNote](docs/document-essentials/deliverynote-documentessentials.md)
- [DirectDebitMandate](docs/document-essentials/directdebitmandate-documentessentials.md)
- [Invoice](docs/document-essentials/invoice-documentessentials.md)
- [Order](docs/document-essentials/order-documentessentials.md)
- [OrderConfirmation](docs/document-essentials/orderconfirmation-documentessentials.md)
- [Timesheet](docs/document-essentials/timesheet-documentessentials.md)

## Schemas
- [BluDoc_Schema_V1.0.0.json](schema/BluDoc_Schema_V1.0.0.json)
- [BluDoc_Schema_V1.1.0.json](schema/BluDoc_Schema_V1.1.0.json)
- [BluDoc_Schema_V1.2.0.json](schema/BluDoc_Schema_V1.2.0.json)
- [BluDoc_Schema_V1.3.0.json](schema/BluDoc_Schema_V1.3.0.json)
- [BluDoc_Schema_V1.3.1.json](schema/BluDoc_Schema_V1.3.1.json)
- [BluDoc_Schema_V1.4.0.json](schema/BluDoc_Schema_V1.4.0.json)
- [BluDoc_Schema_V1.4.1.json](schema/BluDoc_Schema_V1.4.1.json)
- [BluDoc_Schema_V1.4.2.json](schema/BluDoc_Schema_V1.4.2.json)
- [BluDoc_Schema_V1.5.0.json](schema/BluDoc_Schema_V1.5.0.json)

## Basic Principles

## Generic
BluDoc defines a basic, generic structure that can describe any digital document.

## One BluDoc per Document
One BluDoc represents one document. A BluDoc description of a PDF file containing e.g. an invoice and a delivery note requires **two** BluDoc JSONs to describe both documents.

If a file contains multiple documents which belong together (e.g. invoice and delivery note), those additional documents could be handled as “attachments” in the future.

## Supports Common Business Documents
Additionally, BluDoc provides pre-defined **DocumentEssentials** schemas for common business documents to ease data exchange (e.g. universal schema for invoices, quotations, etc.).

## Concise, Readable
BluDoc content and structure is easy to read and understand.

## Optional
BluDoc provides a structure. To what extent you use it is up to you; the JSON schema includes mainly optional elements.

## Redundancy is ok
For human readability and ease of processing, information within different elements of BluDoc can be redundant, but it must be consistent.

## Docs
- [Datatypes & normalization](docs/BluDoc%20Datatypes%20and%20Normalization.md)

