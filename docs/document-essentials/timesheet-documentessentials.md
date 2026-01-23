# Document Essentials for Timesheet

This page lists the default document essentials for this doctype.

- **Cardinality** is shown in parentheses: `(1..1)` = required single value, `(0..1)` = optional, `(0..*)` = optional repeating, `(1..*)` = required repeating.
- **Items** are structural containers that group related fields (shown as indented bullets below the Item).
- Values shows allowed values when available.



- Staff.Id (1..1)
- Staff.Name (1..1)
- ConstructionSite.String (0..1)
- Customer.Name (0..1)
- Signature.Bool (0..1)
- WorkDay.Item (1..*)
  - Date
  - Start.Time
  - End.Time
  - Total.Duration
  - Info.String
