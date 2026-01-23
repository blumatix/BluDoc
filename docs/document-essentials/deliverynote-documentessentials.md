# Document Essentials for DeliveryNote

This page lists the default document essentials for this doctype.

- **Cardinality** is shown in parentheses: `(1..1)` = required single value, `(0..1)` = optional, `(0..*)` = optional repeating, `(1..*)` = required repeating.
- **Items** are structural containers that group related fields (shown as indented bullets below the Item).
- Values shows allowed values when available.



- DeliveryNote.Id (1..1)
- DeliveryNote.Date (1..1)
- Sender.VatId (0..1)
- Sender.Id (0..1)
- ReceiverOrder.Id (0..1)
- BankAccount.Item (0..*)
  - Bank.Iban
  - Bank.Bic
  - Bank.Id
  - Account.Id
- Line.Item (1..*)
  - Position.Id
  - Article.Id
  - ReceiverArticle.Id
  - ArticleDescription.String
  - Quantity.Decimal
  - Unit.Type
  - Charge.String
  - Origin.Country
  - CustomsTariff.Id
- Contact.Item (0..*)
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
  - Contact.Fax
- Sender.Contact.Item (1..1)
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
  - Contact.Fax
- Receiver.Contact.Item (1..1)
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
  - Contact.Fax
