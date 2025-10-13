# BluDoc Datatypes and Normalization

## 1. Introduction

Datatypes define the semantic nature of extracted details in BluDoc.  
They ensure consistent normalization, validation, and interpretation across all document types and enable LLM-based extraction models to produce structured, machine-processable results.

### Why Datatypes Matter

Datatypes play a central role in BluDoc because they link semantic meaning with machine-readability.  
Each detail extracted from a document is not only identified by name but also by its datatype, which provides the following advantages:

- **Improved LLM extraction quality** —  
  When the extraction prompt includes datatype information, language models better understand the expected structure and value domain.  
  They can distinguish between similar details (e.g., `Invoice.Date` vs. `Delivery.Date`) and output results in normalized formats.

- **Centralized normalization** —  
  Each datatype defines one normalization rule (e.g., `Date → YYYY-MM-DD`, `Amount → decimal with '.' separator`).  
  This ensures consistent results across all document types, regardless of how values appear on the page.

- **Automated post-processing** —  
  Downstream systems can rely on normalized values for comparison, validation, or aggregation.  
  Formatting differences on the document (such as `12.3.2025`, `12/03/25`, or `March 12, 2025`) no longer matter.

- **Clear and expressive naming** —  
  Using the datatype as the final segment of the detail identifier (e.g., `Invoice.Id`, `Payment.Amount`, `Issuer.Iban`)  
  makes each detail name self-descriptive and semantically stable across languages.

- **Extensibility and reuse** —  
  Central datatype definitions can be extended with new normalization logic or reused across different document types,  
  ensuring consistency and maintainability of the overall BluDoc schema.

### Hierarchical Details: The Item Datatype

The **Item** datatype is a special structural element that enables hierarchies and repeating groups.  
Unlike atomic datatypes (Date, Amount, Name), an `Item` serves as a container for related child details.

**Use cases:**
- Invoice line items (each with Description, Quantity, Amount)
- VAT breakdowns (each with Rate, Base, Tax)
- Multiple contact persons or addresses

An `Item` has no normalized value itself — it exists to group related details into structured, hierarchical objects.

**Example:** `Line.Item` contains `Description.String`, `Quantity.Decimal`, `Total.Amount`

### Detail Identifier
Each detail in BluDoc has a unique identifier composed of one or more descriptive segments,  
where the Datatype always forms the final segment of the name.

Examples: `Issuer.Name`, `Invoice.Date`, `GrandTotal.Amount`, `Vat.Rate`, `Account.Iban`, `Document.Version`.

---

## 2. BluDoc Datatypes and Normalization

The following categorization serves organizational purposes only and has no semantic significance.  
Alternative groupings may be equally valid, and the structure can be modified or extended at any time as requirements evolve.

---

### 2.1 Primitive Types
| Datatype | Description | Normalized Format | Pattern / Rule | Example (raw → normalized) | Detail Identifier Example | Unit / Precision |
|-----------|-------------|-------------------|----------------|-----------------------------|---------------------------|------------------|
| **Bool** | Boolean value (true/false) | `true` or `false` (lowercase) | Lowercase boolean strings | `Yes → "true"`<br>`No → "false"`<br>`1 → "true"`<br>`0 → "false"`<br>`X → "true"`<br>`checked → "true"` | `TaxExempt.Bool`, `Paid.Bool`, `Approved.Bool` | — |
| **Int** | Integer number | Integer | | `00123 → "123"` | `Quantity.Int` | — |
| **Decimal** | Decimal number | Decimal number | `.` as decimal separator | `12,5 → "12.5"` | `Rate.Decimal` | — |
| **String** | Free text (paragraphs, notes, multi-line) | Text string (multi-line allowed) | Content preserved as-is | `Delivery will be delayed.` → `"Delivery will be delayed."` | `Notes.String`, `Description.String` | — |
| **Bytes** | Binary content (e.g. images) | Base64-encoded string | | `[binary image data] → "iVBORw0KGgo...AASUVORK5CYII="` | `Attachment.Bytes` | — |
| **Type** | Categorical value | Enum value | Enumerated values (controlled vocabulary) | `Credit Note → "CreditNote"` | `Document.Type` | — |
| **Version** | Version number of a document or schema | `x.y.z` (dot-separated) | `x.y.z` | `v1-2-3 → "1.2.3"` | `Document.Version` | — |
| **Language** | Language code | ISO 639-1 code (2 lowercase letters) | ISO 639-1 ([link](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)) | `english → "en"` | `Document.Language` | — |

---

### 2.2 Numeric and Temporal

**Note:** All numeric datatypes are normalized without leading zeros and without group separators.

| Datatype | Description | Normalized Format | Pattern / Rule | Example (raw → normalized) | Detail Identifier Example | Unit / Precision |
|-----------|-------------|-------------------|----------------|-----------------------------|---------------------------|------------------|
| **SmallAmount** | Decimal with four digits precision | Decimal number (4-digit precision) | `.` as decimal separator | `9,0009 → "9.0009"`<br>`123 → "123.0000"` | `Unit.SmallAmount` | Precision: 4 |
| **Amount** | Monetary amount | Decimal number (2-digit precision) | `.` as decimal separator | `€1.234,50 → "1234.50"`<br>`-100,- → "-100.00"`<br>`one hundred pesos → "100.00"` | `GrandTotal.Amount` | Precision: 2 |
| **Rate** | Percentage rate (percent sign removed) | Decimal percentage (1-digit precision) | `.` as decimal separator, ≤ `100.0` | `20 % → "20.0"`<br>`.19 → "19.0"` | `Vat.Rate` | Precision: 1 |
| **Date** | Calendar date | `YYYY-MM-DD` | ISO 8601 ([link](https://en.wikipedia.org/wiki/ISO_8601)) | `12.3.2025 → "2025-03-12"` | `Invoice.Date` | — |
| **Timestamp** | Date and time with timezone | `YYYY-MM-DDTHH:mm:ss.sss±hhmm` | ISO 8601 datetime ([link](https://en.wikipedia.org/wiki/ISO_8601)) | `12.03.2025 14:33 CET → "2025-03-12T14:33:00.000+0100"` | `Created.Timestamp` | — |
| **Duration** | Time duration | Integer | Unit must be specified in detail name (Days/Hours) | `30 days → "30"`<br>`2 hours → "2"` | `DueDays.Duration`, `WorkingHours.Duration` | Unit: days or hours |
| **Mileage** | Vehicle mileage or odometer reading | Integer | Numeric value without unit | `45,000 km → "45000"`<br>`12.500 km → "12500"`<br>`8000 miles → "8000"` | `Vehicle.Mileage`, `Odometer.Mileage` | Unit: km (or miles, context-dependent) |

---

### 2.3 Financial
| Datatype | Description | Normalized Format | Pattern / Rule | Example (raw → normalized) | Detail Identifier Example | Unit / Precision |
|-----------|-------------|-------------------|----------------|-----------------------------|---------------------------|------------------|
| **Currency** | Currency code | ISO 4217 code (3 letters) | 3 chars, ISO 4217 ([link](https://en.wikipedia.org/wiki/ISO_4217)) | `Euro → "EUR"` | `Invoice.Currency` | — |

---

### 2.4 Identification

**Note:** All datatypes in this section are normalized to uppercase, without spaces and without line breaks.

| Datatype | Description | Normalized Format | Pattern / Rule | Example (raw → normalized) | Detail Identifier Example | Unit / Precision |
|-----------|-------------|-------------------|----------------|-----------------------------|---------------------------|------------------|
| **Id** | Unique identifier | Alphanumeric string | case-preserved; no line breaks | `inv-12345 → "inv-12345"` | `Invoice.Id` | — |
| **VatId** | Value-added tax identifier | Alphanumeric string (country prefix + number) | Country prefix + normalized id | `AT U12345678 → "ATU12345678"` | `Issuer.VatId` | — |
| **TaxId** | General tax identification number (non-VAT) | Alphanumeric string | Uppercase, without spaces and line breaks | `123/4567/8901 → "123/4567/8901"`<br>`12-3456789 → "12-3456789"`<br>`tax id: 987654321 → "987654321"` | `Sender.TaxId`, `Receiver.TaxId` | — |
| **Iban** | International bank account number | Alphanumeric string | 15 to 34 chars | `AT61 1904 3002 3457 3201 → "AT611904300234573201"` | `Account.Iban` | — |
| **Bic** | Bank identifier code | Alphanumeric string | 8 or 11 chars | `sphkat2bxxx → "SPHKAT2BXXX"` | `Account.Bic` | — |

---

### 2.5 Contact and Address

**Note:** All datatypes in this section are normalized without line breaks.

| Datatype | Description | Normalized Format | Pattern / Rule | Example (raw → normalized) | Detail Identifier Example | Unit / Precision |
|-----------|-------------|-------------------|----------------|-----------------------------|---------------------------|------------------|
| **Name** | Person or organization name | Text string | | `Müller GmbH → "Müller GmbH"` | `Issuer.Name` | — |
| **Street** | Street and house number | Text string | Normalized spacing | `Main St. 12 / 3 → "Main St. 12/3"` | `Contact.Street` | — |
| **ZipCode** | Postal code | Alphanumeric string | Country-specific format | `A-5020 → "5020"`<br>`SW1A 1AA → "SW1A1AA"` | `Contact.ZipCode` | — |
| **City** | City name | Text string | | `Salzburg → "Salzburg"` | `Contact.City` | — |
| **Region** | State, province, or administrative division within a country | Text string | | `Salzburg → "Salzburg"` | `Contact.Region` | — |
| **Country** | Country code | 2 uppercase letters | ISO 3166-1 alpha-2 ([link](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)) | `Austria → "AT"` | `Contact.Country` | — |
| **Phone** | Telephone number | E.164 format | E.164 ([link](https://en.wikipedia.org/wiki/E.164)) | `0664 1234567 → "+436641234567"` | `Contact.Phone` | — |
| **Email** | Email address | Email address (lowercase) | RFC 5322 ([link](https://www.rfc-editor.org/rfc/rfc5322)) | `Hans.Peter@Example.com → "hans.peter@example.com"` | `Contact.Email` | — |
| **Website** | Website address (URL) | URL (lowercase host) | Lowercase host, scheme ensured | `WWW.Example.COM → "https://www.example.com"` | `Contact.Website` | — |

---

### 2.6 Structural
| Datatype | Description | Normalized Format | Pattern / Rule | Example (raw → normalized) | Detail Identifier Example | Unit / Precision |
|-----------|-------------|-------------------|----------------|-----------------------------|---------------------------|------------------|
| **Item** | Structural container for grouping related details | Hierarchical container | Groups nested details with their own datatypes into structured objects | — | `Line.Item`, `Vat.Item` | — |

---

*End of document.*