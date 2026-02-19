# Self-Assessment - Data Modeling

## 1 What's the difference between One-to-Many and Many-to-Many?

One-to-Many:
- One record in Table A can relate to many records in Table B.
- Each record in Table B belongs to only one record in Table A.
- Implemented using a foreign key on the "many" side.

Example:
authors → blog_posts


Many-to-Many:
- A record in Table A can relate to many records in Table B.
- A record in Table B can also relate to many records in Table A.
- Implemented using a junction table.

Example:
blog_posts ↔ tags


## 2 Why do we need a junction table for Many-to-Many?

Relational databases cannot directly store many-to-many relationships in one table.

If we tried to store multiple IDs in one column:
- It would break normalization.
- It would be hard to query and maintain.
- Referential integrity would not be enforced.

A junction table:
- Stores pairs of foreign keys.
- Keeps data normalized.
- Allows indexing and efficient querying.
- Maintains referential integrity.


## 3 When should a field be required vs optional?

A field should be required when:
- It is essential for business logic.
- A record is not valid without it.
- The system cannot function correctly without that value.

Examples:
- blog_posts.title
- blog_posts.author_id
- comments.content

A field should be optional when:
- It is not always available.
- It represents additional or future data.
- It is conditionally required.

Examples:
- publish_date
- comment_id
- bio in authors


## 4 What field type would you use for a blog post's featured image?
- I would store images in cloud storage and save only the image URL in the database.

Reason:
- Storing binary image data in the database increases size and reduces performance.
- Cloud storage is optimized for media delivery.
- The database should store only URl, not large files.

## 5 How would you model a relationship where a post has one primary author and multiple co-authors?

Primary author:
- Use blog_posts.author_id (One-to-Many).
- Each post has exactly one primary author.

Co-authors:
- Create a junction table:
  blog_posts_co_authors
  - blog_post_id (FK → blog_posts.id)
  - author_id (FK → authors.id)

This allows:
- One main author per post
- Multiple co-authors per post
- An author can be a co-author on multiple posts
