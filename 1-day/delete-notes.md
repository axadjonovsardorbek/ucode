## Activity 6.1: Safe Delete Practice

### Test Record Created:
"DELETE ME - Test Product"

### Delete Process:
1. The test product was created successfully.
2. The delete option was selected.
3. The record was deleted without any errors or difficulties.

### Observations:
- No noticeable confirmation difficulty during deletion.
- The item was immediately removed from the list view.
- The deleted item could not be found in the main table view.
- There was no visible trash/archive section in the UI.

---

## Activity 6.2: Understanding Delete Behavior

### Soft Delete vs Hard Delete

Ucode uses a **soft delete** mechanism.

- Records are not permanently removed from the database.
- Instead, a `deleted_at` field is used to mark records as deleted.
- Active records are filtered with `deleted_at`.

### Can Deleted Items Be Recovered?

- Yes.
- Since soft delete is used, deleted records can be recovered.
- Recovery is possible because the data still exists in the database with a `deleted_at`.

### What Happens If a Referenced Item Is Deleted?

- If a referenced record is deleted using soft delete:
  - No foreign key error occurs.
  - The system does not block the deletion.
  - Because the record still exists in the database (only marked as deleted).

- If hard delete were used:
  - The database would require cascade delete or would throw a foreign key constraint error.
  - Referenced records would either block deletion or require `ON DELETE CASCADE`.

---

## Conclusion

- Ucode implements soft delete for safer data management.
- This prevents immediate permanent data loss.
- It also avoids foreign key constraint conflicts during deletion.
