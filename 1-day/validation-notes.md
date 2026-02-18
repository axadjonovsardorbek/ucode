# Validation Notes (Activity 3.3)

## 1. Creating a record without a required field

- When the required field `name` was left empty, the record could not be created.
- The system displayed a validation message indicating that the `name` field is required.
- This shows that required field validation is properly enforced.

## 2. Entering text in a number field

- It was not possible to enter non-numeric characters into the `price` field.
- The input field accepted only numeric values.
- This indicates that type validation is handled at the input level.

## 3. Entering a negative price

- When a negative number was entered in the `price` field, no validation error was shown.
- The system allowed saving the record with a negative price.
- This suggests that there is no business rule validation preventing negative values.
