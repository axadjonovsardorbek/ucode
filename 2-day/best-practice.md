# Data Modeling Best Practices

## 1 When to use One-to-Many vs Many-to-Many?

### One-to-Many (1 → M)
Use when:
- One parent record can have many child records
- Each child belongs to exactly one parent

Examples:
- authors (1) → blog_posts (M)
- blog_posts (1) → comments (M)
- categories (1) → blog_posts (M)

Storage in DB:
- Foreign key is stored on the "many" side (child table), e.g. blog_posts.author_id.


### Many-to-Many (M ↔ M)
Use when:
- A record in Table A can link to many records in Table B
- And Table B can link back to many records in Table A

Examples:
- blog_posts ↔ tags
- students ↔ courses
- users ↔ roles

Storage in DB:
- Use a junction table (pivot) containing two foreign keys:
  blog_posts_tags(blog_post_id, tag_id)


## 2 How to name tables (singular vs plural)?

Pick one convention and keep it consistent across the project.

Common conventions:
- Plural table names: authors, blog_posts, tags (popular in many systems)
- Singular table names: author, blog_post, tag (also common)

Recommendation:
- Use plural for tables and singular for columns:
  - tables: blog_posts, authors, categories
  - columns: author_id, category_id

Junction table naming:
- Use both table names combined:
  - blog_posts_tags
  - users_roles


## 3 When to create a separate table vs add fields?

Add fields to the same table when:
- Data is 1-to-1 with the entity and always belongs to it
- It is not repeating and not a separate "entity"

Examples:
- blog_posts.title, blog_posts.published, blog_posts.views

Create a separate table when:
- The data repeats (one post has many images/comments)
- Need history/audit (revisions, logs)
- Need Many-to-Many (junction table)
- The data has its own lifecycle and metadata (created_at, owner, status)

Examples:
- comments (many comments per post)
- images (many images per post)
- post_revisions (history of changes)
- blog_posts_tags (junction)


## 4 How to handle optional relationships?

Optional relationship means the foreign key can be NULL.

Use optional relationships when:
- The relation is not always present
- You don't want to block record creation

Examples:
- publish_date can be NULL if a post is not published yet
- comment_id can be NULL if comment is a top-level comment (no parent)
- category_id/author_id can be optional only if business rules allow it

Best practices:
- If optional, allow NULL and handle it in UI/API (show "None" or hide block).
- If required by business logic, enforce NOT NULL + validation.
- For soft delete systems, consider how deleted referenced rows are handled.


## 5 What makes a good primary key?

A good primary key should be:
- Unique and never changes (immutable)
- Always present (NOT NULL)
- Fast for indexing and joins
- Not based on business meaning that might change

Common choices:
- Auto-increment integer (simple, fast, readable)
- UUID (good for distributed systems and security, harder to read)

Best practices:
- Keep PK separate from business identifiers (like email, title, slug).
- Use UNIQUE constraints for business identifiers:
  - tags.slug unique
  - categories.slug unique
- Index foreign keys (author_id, category_id, blog_post_id) for performance.
