# Field Configuration Options - blog_posts

## 1 Required vs Optional (title)
Action:
- blog_posts.title field set to **Required**.

Result:
- When trying to create a blog post without a title, the system did not allow saving.
- UI showed a message reminding that the title is required.

Conclusion:
- Required validation works at create time.


## 2 Default Values (views = 0)
Action:
- Created a blog post without entering any value in the **views** field.

Result:
- views was automatically set to **0**.

Conclusion:
- views has a default value of 0 (either configured in Ucode or set at DB level).


## 3 Unique Constraint (title unique?)
Action:
- Enabled **Unique** for blog_posts.title.
- Tried creating another blog post with the same title.

Result:
- Creation was blocked with an error like: "This title already exists".

Conclusion:
- Unique constraint works and prevents duplicate titles.


## 4 Hidden Fields (hide)
Action:
- Tested hiding some fields using the **Hide-Field** option.

Result:
- Hidden fields were not visible in the UI.

Conclusion:
- Ucode supports hiding fields from UI.


## 5 Read-only (content field)
Action:
- Set blog_posts.content field to **Disabled**.

Result:
- Field became readable only and could not be edited.
- Edit controls/input were disabled for content.

Conclusion:
- Read-only mode works and blocks editing from the admin UI.
