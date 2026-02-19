Table blog_posts {
  id integer [primary key]
  title varchar [not null]
  content varchar [not null]
  published bool
  publish_date timestamp
  views integer
  category_id integer [not null]
  author_id integer [not null]
  created_at timestamp
  updated_at timestamp
  deleted_at bigint
}

Table authors {
  id integer [primary key]
  first_name varchar
  last_name varchar
  email email [not null]
  bio varchar
  is_active bool
  created_at timestamp
  updated_at timestamp
  deleted_at bigint
}

Table users {
  id integer [primary key]
  author_id integer [not null]
}

Table tags {
  id integer [primary key]
  name varchar [unique, not null]
  slug varchar [unique, not null]
  color varchar
  created_at timestamp
  updated_at timestamp
  deleted_at bigint
}

Table blog_posts_tags {
  id integer [primary key]
  blog_post_id integer [not null]
  tag_id integer [not null]
  created_at timestamp
  updated_at timestamp
  deleted_at bigint
}

Table categories {
  id integer [primary key]
  name varchar [unique, not null]
  slug varchar [unique, not null]
  description varchar
  created_at timestamp
  updated_at timestamp
  deleted_at bigint
}

Table comments {
  id integer [primary key]
  blog_post_id integer [not null]
  author_email email [not null]
  author_name varchar
  content varchar [not null]
  approved bool
  comment_id integer
  created_at timestamp
  updated_at timestamp
  deleted_at bigint
}

Table images {
  id integer [primary key]
  image varchar [not null]
  blog_post_id integer [not null]
  author_id integer [not null]
  created_at timestamp
  updated_at timestamp
  deleted_at bigint
}

Table post_revisions {
  id integer [primary key]
  last_title varchar [not null]
  last_content varchar [not null]
  category_id integer [not null]
  blog_post_id integer [not null]
}


Ref: blog_posts.category_id > categories.id
Ref: blog_posts.author_id > authors.id

Ref: users.author_id > authors.id

Ref: blog_posts_tags.blog_post_id > blog_posts.id
Ref: blog_posts_tags.tag_id > tags.id

Ref: comments.blog_post_id > blog_posts.id
Ref: comments.comment_id > comments.id

Ref: images.blog_post_id > blog_posts.id
Ref: images.author_id > authors.id

Ref: post_revisions.blog_post_id > blog_posts.id
Ref: post_revisions.category_id > categories.id

authors (1) ───< (M) blog_posts >───(1) categories
   |                 |
   |                 ├───< (M) comments
   |                 |        ^
   |                 |        |
   |                 |     (1)|───< (M) comments   (reply threads)
   |                 |
   |                 ├───< (M) images
   |                 |
   |                 ├───< (M) post_revisions
   |                 |
   |                 └───< (M) blog_posts_tags >───(M) tags
   |
   └───< (M) users



# Blog Data Model - Table Purposes

## authors
Stores author profile information (name, email, bio, active status).  
Used as the creator for blog posts and images.

## users
Represents application users that are linked to an author record via author_id.  
Used when the system separates authentication users from author profiles.

## categories
Stores blog categories (name, slug, description).  
Each blog post belongs to one category.

## blog_posts
Main table that stores blog post content and metadata:
- title, content
- published flag and publish_date
- views counter
- relations to category and author
Also includes timestamps and deleted_at for soft delete behavior.

## tags
Stores reusable tag entities (name, slug, optional color).  
Used to label/group posts.

## blog_posts_tags
Junction (pivot) table for many-to-many relationship between blog_posts and tags.  
Each row links one blog post to one tag.

## comments
Stores comments for blog posts:
- blog_post_id links comment to a post
- author_email/author_name store commenter identity (not necessarily a registered user)
- approved flag for moderation
- comment_id is a self-reference for threaded replies (parent comment)

## images
Stores image records:
- image field holds image URL/path
- blog_post_id links image to a specific post
- author_id tracks which author uploaded/owns the image

## post_revisions
Stores edit history/snapshots for blog posts:
- last_title and last_content keep previous versions
- blog_post_id links revision to a post
- category_id stores category at the time of revision
Used to track changes over time (versioning).


✅ End of Day Checklist
✅Created at least 5 tables
✅Used 8+ different field types
✅Implemented One-to-Many relationship (authors-posts)
✅Implemented Many-to-Many relationship (posts-tags)
✅Created junction table
✅Added sample data to all tables
✅Created complete data model diagram
✅Tested all relationships
✅Completed all documentation