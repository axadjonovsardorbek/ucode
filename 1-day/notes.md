# Day 1 - Ucode Foundations

## 1. What is Ucode?

- Ucode is a Backend-as-a-Service (BaaS) platform that automatically generates APIs from a database schema.
- It uses database introspection to analyze tables, relationships, and constraints.
- Unlike traditional CMS, it does not render frontend pages; it provides backend services.
- It is designed for developers building apps.
- CRUD operations are easily performed without queries

## Menu: What can you do here?
- Manage folders and organize tables inside folders.
- Access Tables, Items, and Settings.
- Control and manage the overall project structure.

## Tables: How many tables exist?
- Currently, there are 2 main tables:
  - person
  - roles
- Tables can be organized inside folders.
- New tables can be created inside specific folders.

## Items: What are items?
- Items are the records (rows) inside a table.
- For example, in the person table, each user is an item.
- The person table contains fields such as:
  - name
  - phone_number
  - login
  - password
  - role
  - email
  - image
  - gender
  - birthday

## Settings: What settings are available?
- Account Settings
- Project Settings
- Advanced Settings
- Project configuration and management options are available here.


## Activity 2.3: View Sample Data

### How is data organized?

- Data is organized in a table format.
- Each row represents one item.
- Each column represents a field of the product.
- When clicking on a specific product, it opens a dedicated detail page for that item.

### What information can you see?

- All fields related to the selected product are displayed on one page.
- This includes:
  - id
  - name
  - description
  - price
  - in_stock
  - category_id
- The detail view allows both viewing and editing the product information.
- The item can be updated directly from the same page.

# Bonus Challenges

## 🚀 Speed Challenge

- I was able to create 10 product records in approximately 5 minutes.
- This shows that the interface is efficient and optimized for fast data entry.
- Low-code significantly speeds up CRUD operations compared to manual SQL-based workflows.

## ⌨️ Keyboard Shortcuts

- Ctrl + Z → Undo last action
- Ctrl + Shift + Z → Redo action


# Daily Reflection

## What was the most useful thing you learned today?

The most useful thing I learned today was working with a low-code platform.
This was my first time using a low-code system, and it was interesting to see how CRUD operations can be performed without writing SQL queries manually.

## What was most challenging?

The most challenging part was understanding how the system manages validation and delete behavior behind the scenes.
Since everything is abstracted, it requires thinking differently compared to writing raw backend code.

## What do you want to learn more about?

I would like to learn more about:
- How low-code platforms generate APIs automatically.
- How backend logic works internally in such systems.
- How to build and integrate APIs using low-code tools.
- How database introspection is implemented technically.


✅ End of Day Checklist

✅Successfully logged into Ucode
✅Explored all main navigation sections
✅Understood database introspection concept
✅Created at least 6 new records
✅Tested data validation
✅Performed search and filter operations
✅Updated existing records
✅Deleted records safely
✅Completed all documentation files