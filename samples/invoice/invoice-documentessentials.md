# Document Essentials for Invoice

## Basic Invoice Information
- Contract.Id
- Invoice.Id
- Invoice.Date
- Invoice.Type
- Currency
- ReceiverOrder.Id
- ReceiverOrder.Date
- DeliveryNote.Id

## Delivery Information
- DeliveryDate.Item:
    - Delivery.Date
    - DeliveryPeriodStart.Date
    - DeliveryPeriodEnd.Date

## Contact Information
- Sender.VatId
- Receiver.VatId
- Sender.Contact.Item:
    - Contact.Name
    - Attention.Name
    - Contact.Street
    - Contact.ZipCode
    - Contact.City
    - Contact.Region
    - Contact.Country
    - Contact.Website
    - Contact.Email
    - Contact.Phone
- Receiver.Contact.Item:
    - Contact.Name
    - Attention.Name
    - Contact.Street
    - Contact.ZipCode
    - Contact.City
    - Contact.Region
    - Contact.Country
    - Contact.Website
    - Contact.Email
    - Contact.Phone
- Contact.Item:
    - Contact.Name
    - Attention.Name
    - Contact.Street
    - Contact.ZipCode
    - Contact.City
    - Contact.Region
    - Contact.Country
    - Contact.Website
    - Contact.Email
    - Contact.Phone

## Banking Information
- BankAccount.Item:
    - Bank.Iban
    - Bank.Bic
    - Bank.Id
    - Account.Id

## Financial Information
- GrandTotal.Amount
- Vat.Item:
    - Vat.Rate
    - Net.Amount
    - Vat.Amount

## Payment Information
- Due.Item:
    - Due.Date
    - Due.Duration
- Payment.Discount.Item:
    - Due.Item:
        - Due.Date
        - Due.Duration
    - Discount.Item:
        - Discount.Rate
        - Discount.Amount
- PaymentReference.Id

## New Enhanced Fields (v1.4.2)

### Referenced Documents
- ReferencedInvoice.Id

### Accounting Information
- AccountingEntry.Item:
    - AccountingText.String (MANDATORY - always required)

### Payment Processing
- PaymentStatus.Type (Paid, Partially_Paid, Open, Overdue, Cancelled, Unclear)
- PaymentMethod.Type (Cash, Creditcard, Debitcard, Direct_Debit, Bank_Transfer, Paypal, Voucher, Mixed, Other)
- Payment.Amount

### Delivery Contact
- Delivery.Contact.Item:
    - Contact.Name
    - Attention.Name
    - Contact.Street
    - Contact.ZipCode
    - Contact.City
    - Contact.Region
    - Contact.Country
    - Contact.Website
    - Contact.Email
    - Contact.Phone

## Field Descriptions

### Basic Information
- **Contract.Id**: Contract number referenced by the invoice
- **Invoice.Id**: Unique identifier of the invoice
- **Invoice.Date**: Issue date of the invoice
- **Invoice.Type**: Type classification (Invoice, CreditMemo, Other)
- **Currency**: Main currency for all invoice amounts (ISO 4217)

### New Enhanced Fields Details
- **ReferencedInvoice.Id**: Original invoice number for credit notes or related documents
- **AccountingText.String**: Mandatory field for categorizing invoice content (e.g., "Baubedarf", "IT-Services", "Beratungsleistungen")
- **PaymentStatus.Type**: Current payment status of the invoice
- **PaymentMethod.Type**: Method used or to be used for payment
- **Payment.Amount**: Actual payment amount (may differ from GrandTotal for partial payments)
- **Delivery.Contact.Item**: Separate delivery address when different from billing address

### Special Notes
- **AccountingText.String** is mandatory and must always contain a meaningful business category
- **Delivery.Contact.Item** should only be populated when explicitly marked as delivery address and different from receiver address
- **Payment.Amount** may differ from **GrandTotal.Amount** in cases of partial payments, deposits, or split payments
