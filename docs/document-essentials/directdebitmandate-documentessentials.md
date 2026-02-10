# Document Essentials for DirectDebitMandate

This page lists the default document essentials for this doctype.

- **Cardinality** is shown in parentheses: `(1..1)` = required single value, `(0..1)` = optional, `(0..*)` = optional repeating, `(1..*)` = required repeating.
- **Items** are structural containers that group related fields (shown as indented bullets below the Item).



- Mandate.Id (0..1)
- Mandate.Date (0..1)
- Creditor.Id (0..1)
- BankAccount.Item (0..1)
  - Bank.Iban
  - Bank.Bic
  - Bank.Id
  - Account.Id
- Payer.Contact.Item (1..1)
  - Contact.Name
  - Contact.Street
  - Contact.ZipCode
  - Contact.City
  - Contact.Phone
  - Contact.Email
- AccountHolder.Contact.Item (0..1)
  - Contact.Name
  - Contact.Street
  - Contact.ZipCode
  - Contact.City
  - Contact.Phone
  - Contact.Email
- Receiver.Contact.Item (0..1)
  - Contact.Name
  - Contact.Street
  - Contact.ZipCode
  - Contact.City
  - Contact.Phone
  - Contact.Email
