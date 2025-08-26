# Template.md

This is the **base template reference** used with ChatGPT to generate CRUD resources, policies, requests, migrations, and models in Laravel 12.

Use this file as the **starting point** for creating new resource markdown files (e.g., `brands.md`, `categories.md`).

---

## 📝 Structure

Each resource file should include the following sections:

1. **Resource Information**
   - Name (Singular)
   - Table (Plural)
   - Options (CRUD, SoftDeletes, Requests, Policy, Routes)

2. **Migration**
   - Table fields with types, constraints, and defaults
   - Add SQL description for table and columns if needed

3. **Model**
   - Fillable attributes
   - Relationships
   - Custom Functions Block (placed at the end of the model)

4. **Requests**
   - StoreRequest rules
   - UpdateRequest rules
   - Authorization (Policy or Boolean)

5. **Policy**
   - Permissions for index, view, create, update, delete, restore, forceDelete

6. **Controller**
   - Web or API style (decide based on template)
   - CRUD methods
   - API: ResourceCollections, Pagination, Filters if applicable

7. **Routes**
   - Web or API routes
   - Middleware and Prefix options

8. **Git Notes (optional)**
   - Suggested branch name
   - Commit message

---

## 📘 Example Usage

### Command to create a new resource file:
```
Use the new Template.md and create brands.md
```

### brands.md would include:
- Migration for `brands` table with fields (name, slug, is_active)
- Model `Brand` with SoftDeletes and custom functions
- Store/Update Requests with validation rules
- Policy for Brand with all abilities
- Controller with CRUD methods
- Routes (web resource with auth middleware)
- SQL Descriptions for table and columns

---

## 🔹 One-Line Prompt Example
```
Use template for web:
Resource: Brand
Table: brands
Options: CRUD, SoftDeletes=on, Requests, Policy, Routes
Notes: add index search by name, slug
```

---

This ensures **consistency** across all Laravel 12 resources created using ChatGPT.
