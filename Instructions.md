تم يا عزوز ✅
هذا نص جاهز تلصقه في خانة **Instructions** لمشروعك “Level 12 Template”. حطيته مختصر وواضح مثل اللي بالصورة، ويغطي الـ Generic + Web + API + Reference + Install.

---

# Instructions — Laravel 12 Template

**English used**

1. Use this template and create \[table\_name].md
2. Use the new Template.md and create \[table\_name].md
3. Update the Template.md code with \[description]
4. Explain \[section] in Template.md
5. Add \[section\_name] section to Template.md
6. Create Cheat Sheet for Template instructions

**Web / API**

7. Use Template for web and create \[table\_name].md
8. Update Template for web and use \[description]
9. Use Template for api and create \[table\_name].md
10. Update Template for api and use \[description]

**Reference template**

11. This is the reference template (for web/api/generic)
12. Use this reference template and create \[table\_name].md
13. Update the reference template code with \[description]
14. Add \[section\_name] section to the reference template
15. Based on the reference template, create \[specific\_code\_or\_feature]

**Install (operations)**

16. Use this template to install \[operations\_name]
17. Use this template to install \[operations\_name] with \[description]

---

## Output shape for any `[table_name].md`

* **Migration** – table, columns, indexes, FKs
* **Model** – `HasFactory, SoftDeletes`, `$fillable`, casts, relations +

  ```
  /* ========== Custom Functions (Put at the end of the Model) ========== */
  ```
* **Requests** – `Store[Table]Request`, `Update[Table]Request` (rules + authorize)
* **Policy** – abilities (viewAny, view, create, update, delete, restore, forceDelete)
* **Controller** – CRUD using the Requests
* **Routes** –

  * API: `Route::apiResource('[tables]', [Table]Controller::class);`
  * Web: `Route::resource('[tables]', [Table]Controller::class);`
* **Helpers** – scopes: `withTrashed`, `onlyTrashed`, `restore`
* **Notes** – implementation remarks

**Conventions**

* Laravel 12, PHP 8.x.
* Model: singular StudlyCase. Table: plural snake\_case.
* Form Requests `authorize(): true` unless specified.
* Use SoftDeletes by default.

**Examples**

```
Use Template for api and create brands.md
Use Template for web and create orders.md
Use this template to install authentication operations
```

---

إذا تبي أطلع لك ملف `Template-Cheat-Sheet.md` بنفس المحتوى هذا أجهزه لك الحين 👌
