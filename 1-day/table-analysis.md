# Table Analysis

## Table Name
products

## Number of Fields
6 fields

## Field Details

1. id
   - Type: Integer (Auto-increment)
   - Required: Yes (Primary Key)

2. name
   - Type: Text
   - Required: Yes

3. description
   - Type: Text
   - Required: No (Optional)

4. price
   - Type: Float (Number)
   - Required: No (assumed optional unless specified)

5. in_stock
   - Type: Boolean
   - Required: No (Optional)

6. category_id
   - Type: Integer (Foreign Key)
   - Required: No (assumed optional unless specified)
   - References: category(id)

---

## Relationships

- The products table has a relationship with the category table.
- category_id in products references id in category.
- This represents a one-to-many relationship:
  - Many products can belong to one category.

---

# Related Table: category

## Fields

1. id
   - Type: Integer (Auto-increment)
   - Required: Yes (Primary Key)

2. name
   - Type: Text
   - Required: Yes
