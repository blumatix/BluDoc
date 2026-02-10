# Document Essentials for BankStatement

This page lists the default document essentials for this doctype.

- **Cardinality** is shown in parentheses: `(1..1)` = required single value, `(0..1)` = optional, `(0..*)` = optional repeating, `(1..*)` = required repeating.
- **Items** are structural containers that group related fields (shown as indented bullets below the Item).



- BankStatement.Date (1..1)
- BankAccount.Item (1..*)
  - Bank.Iban
  - Bank.Bic
  - Bank.Id
  - Account.Id
- Sender.Contact.Item (0..1)
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
- Balance.Amount (1..1)
