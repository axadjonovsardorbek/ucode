# Bonus Challenges - Completed

## 1 Self-Referencing Comments (parent-child replies)
Implemented:
- comments.comment_id → comments.id

Behavior:
- A comment can reference another comment as its parent (reply thread).
- Parent comment can have multiple child comments (One-to-Many self relationship).

## 2 Users Table linked to Authors
Implemented:
- users.author_id → authors.id

Purpose:
- Separate app users from author profiles while keeping them connected.


## 3 Media: Images Table for Featured Images
Implemented:
- images.blog_post_id → blog_posts.id
- images.author_id → authors.id
- images.image (required) stores image URL/path

Behavior:
- Each blog post can have multiple images.
- Each image is associated with an author (uploader/owner).


## 4 Advanced: post_revisions for Edit History
Implemented:
- post_revisions.blog_post_id → blog_posts.id
- post_revisions.category_id → categories.id
- post_revisions.last_title, post_revisions.last_content (required)

Purpose:
- Store previous versions of a post (title/content/category) for history.