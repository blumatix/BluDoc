# Document Essentials for Order

This page lists the default document essentials for this doctype.

- **Cardinality** is shown in parentheses: `(1..1)` = required single value, `(0..1)` = optional, `(0..*)` = optional repeating, `(1..*)` = required repeating.
- **Items** are structural containers that group related fields (shown as indented bullets below the Item).
- Values shows allowed values when available.



- Order.Id (1..1)
- Order.Date (1..1)
- Sender.Id (0..1)
- Receiver.Id (0..1)
- Sender.VatId (0..1)
- Delivery.Contact.Item (0..1)
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
- Invoice.Contact.Item (0..1)
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
- Line.Item (1..*)
  - Article.Id
  - DeliveryDate.Item
  - Quantity.Decimal
  - ReceiverArticle.Id
  - Unit.SmallAmount
  - Unit.Type
