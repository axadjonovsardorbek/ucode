# Field Types Analysis - field_types_demo table

## 1. string type
Validation:
- Accepts short text only
- Usually has length limit
- Cannot store large paragraphs

When to use:
- Product name
- Title
- Username
- Short labels


## 2. text type
Validation:
- Allows large content
- No strict character limit
- Accepts multiline input

When to use:
- Description
- Blog content
- Comments


## 3. integer type
Validation:
- Accepts whole numbers only
- Rejects letters or decimal values

When to use:
- Quantity
- Age
- Count


## 4. decimal/float type
Validation:
- Accepts decimal or float numbers
- Rejects text input

When to use:
- Prices
- Percentages
- Ratings


## 5. boolean type
Validation:
- Accepts only true/false values

When to use:
- In Purchase
- Is Active


## 6. date type
Validation:
- Accepts valid calendar date
- No time component
- Rejects invalid date formats

When to use:
- Birth date
- Expiration date
- Event date


## 7. datetime type
Validation:
- Accepts date + time
- Requires proper format
- Useful for timestamps

When to use:
- Created at
- Updated at


## 8. email type
Validation:
- Must follow email format
- Rejects invalid formats

When to use:
- Contact informations
- Login and register


## 9. url type
Validation:
- Must follow URL format
- Rejects invalid links

When to use:
- Website urls
- Product urls
- Image urls
- API endpoints


## 10. json type
Validation:
- Must be valid JSON structure
- Rejects malformed JSON
- Can store nested structured data

When to use:
- Metadata
- Dynamic objects