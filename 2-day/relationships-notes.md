## What is a One-to-Many relationship?

A One-to-Many relationship means:
- One record in Table A can be related to multiple records in Table B.
- Each record in Table B is related to only one record in Table A.


## Blog Example

- One Author can write many Blog Posts.
- Each Blog Post belongs to only one Author.


## Real-World Examples

1. One User → Many Orders
2. One Category → Many Products
3. One Course → Many Students
4. One Company → Many Employees
5. One Course → Many Lessons


## How is this stored in the database?

One-to-Many relationships are stored using a foreign key.

Example:

authors table:
- id (Primary Key)

blog_posts table:
- id
- author_id (Foreign Key referencing authors.id)


# Activity 2.4 - Relationship Testing (authors ↔ blog_posts)

## 1. Creating Blog Posts
- Created 3 new blog_posts records.
- Each post was assigned to a different author.
- Author was selected from a dropdown reference field.

Result:
Forward relationship (blog_posts → authors) works correctly.


## 2. Viewing an Author Record
- Opened author detail view.
- Related blog posts were NOT displayed directly inside the author record.

To see posts of a specific author:
- Navigated to blog_posts table.
- Applied filter: author = <selected author>.

Result:
Posts can be viewed only by filtering blog_posts.

Observation:
Reverse relationship view (authors → blog_posts list) is not automatically shown in this Ucode configuration.


## 3. Editing a Blog Post
- When editing a blog post, the author field appears as a reference selector.
- The UI displays existing authors information in a dropdown list.
- Selecting a different author successfully updates the posts author reference.

Result:
Author selection works correctly through reference dropdown.


## What is a Many-to-Many relationship?
A Many-to-Many relationship means:
- One record in Table A can relate to many records in Table B.
- One record in Table B can also relate to many records in Table A.

Example:
- A blog post can have many tags.
- A tag can belong to many blog posts.


## Real-World Examples
1. Students ↔ Courses  
   - One student can enroll in many courses.  
   - One course can have many students.

2. Products ↔ Categories  
   - One product can belong to multiple categories.  
   - One category can contain many products.

3. Users ↔ Roles  
   - One user can have multiple roles.  
   - One role can be assigned to many users.

4. Movies ↔ Actors  
   - One movie has many actors.  
   - One actor plays in many movies.

5. Orders ↔ Products  
   - One order contains many products.  
   - One product can appear in many orders.


## Why do we need a Junction Table?
Databases cannot directly store many-to-many relationships in a single table.

If we tried:
- Storing multiple IDs inside one column would break normalization.
- It would be hard to query and maintain.

So we create a separate table called a junction table.

Example:

blog_posts
- id

tags
- id

blog_posts_tags (junction table)
- blog_post_id (FK → blog_posts.id)
- tag_id (FK → tags.id)

The junction table stores combinations of relationships.
Each row represents one link between a blog post and a tag.
