# 📘 Commands Cheatsheet (Laravel 12 Reference with ChatGPT)
# commands-cheatsheet.md v1.0
This cheatsheet is a complete reference for generating Laravel 12 code, SQL references, artisan commands, Git workflow, and reusable templates using ChatGPT prompts.  
Use it as a **living playbook** to keep everything consistent and fast.

---

## 1) Documentation Templates  
**Template: `Template.md`**
```
Use the new Template.md and create <table_name>.md
```
**Example:**  
```
Use the new Template.md and create brands.md
```

---

## 2) Web Resources (MVC – Web)  
**Template: `template/web`**
```
Use template for web:
Resource: <SingularName>
Table: <plural_name>
Options: CRUD, SoftDeletes=<on|off>, Requests, Policy, Routes
Notes: <extra notes>
```
**Example:**  
```
Use template for web:
Resource: Brand
Table: brands
Options: CRUD, SoftDeletes=on, Requests, Policy, Routes
Notes: add index search by name, slug
```

---

## 3) API Resources  
**Template: `template/api`**
```
Use template for api:
Resource: <SingularName>
Table: <plural_name>
Options: CRUD, SoftDeletes=<on|off>, Requests, Policy, Routes
API: ResourceCollections, Pagination=<per_page>, Filters=<fields>
```
**Example:**  
```
Use template for api:
Resource: Category
Table: categories
Options: CRUD, SoftDeletes=on, Requests, Policy, Routes
API: ResourceCollections, Pagination=15, Filters=name,slug
```

---

## 4) Update Templates  
**Template: `template/update`**
```
Update template <web|api>:
Change: <describe the modification>
```
**Example:**  
```
Update template api:
Change: add default sorting by created_at desc, allow ?search= on name,slug
```

---

## 5) SQL Table & Column Descriptions  
**Template: `template/sql-description`**
```
Add description to table or column:
Table: <table_name>
Column: <column_name or null>
Description: <your text>
```

### Example – Table Description
```
Add description to table:
Table: brands
Description: Stores all brand names, slugs, and status for products
```

👉 MySQL:
```sql
ALTER TABLE `brands` COMMENT = 'Stores all brand names, slugs, and status for products';
```

👉 Laravel Migration:
```php
Schema::create('brands', function (Blueprint $table) {
    $table->id();
    $table->string('name')->comment('Brand display name');
    $table->string('slug')->unique()->comment('Unique slug for brand');
    $table->boolean('is_active')->default(true)->comment('Is brand active?');
    $table->timestamps();
});
DB::statement("ALTER TABLE `brands` COMMENT 'Stores all brand names, slugs, and status for products'");
```

### Example – Column Description
```
Add description to column:
Table: users
Column: is_active
Description: Flag to show if user account is active or not
```

👉 MySQL:
```sql
ALTER TABLE `users`
MODIFY `is_active` TINYINT(1) NOT NULL DEFAULT 1 COMMENT 'Flag to show if user account is active or not';
```

👉 Laravel Migration:
```php
$table->boolean('is_active')
      ->default(true)
      ->comment('Flag to show if user account is active or not');
```

---

## 6) Models + Custom Functions Block  
**Template: `template/model`**
```
Create/Update model:
Name: <ModelName>
Table: <plural_name>
SoftDeletes=<on|off>
Add Custom Functions:
- <function_name>() => <short description>
```
**Example:**  
```
Create/Update model:
Name: Brand
Table: brands
SoftDeletes=on
Add Custom Functions:
- uploadImage(path) => store & attach to media column
- scopeActive() => where('is_active', true)
```

👉 Always end with:
```php
/* ========== Custom Functions (Put at the end of the Model) ========== */
```

---

## 7) Migrations  
**Template: `template/migration`**
```
Create migration:
Table: <plural_name>
Fields:
- <name>: <type>(args) [nullable|unique|index|default=...]
SoftDeletes=<on|off>, Timestamps=<on|off>
```
**Example:**  
```
Create migration:
Table: brands
Fields:
- name: string unique
- slug: string unique
- is_active: boolean default=true
SoftDeletes=on, Timestamps=on
```

---

## 8) Requests (Store/Update)  
**Template: `template/requests`**
```
Create requests for <Resource>:
Store Rules: <rules>
Update Rules: <rules>
Authorize: <policy|true|false>
```
**Example:**  
```
Create requests for Brand:
Store Rules: name required|string|max:120; slug required|string|max:140|unique:brands,slug
Update Rules: name sometimes|string|max:120; slug sometimes|string|max:140|unique:brands,slug,{{id}}
Authorize: policy
```

---

## 9) Policy  
**Template: `template/policy`**
```
Create policy for <Resource> with abilities:
index, view, create, update, delete, restore, forceDelete
```
**Example:**  
```
Create policy for Brand with abilities: all
```

---

## 10) Routes  
**Template: `template/routes`**
```
Add routes <web|api> for <Resource>:
Type: resource
Middleware: <list or default>
Prefix: <optional>
```
**Example:**  
```
Add routes web for Brand:
Type: resource
Middleware: auth
```

---

## 11) Git Commands (Workflow)  
**Template: `template/git`**
```
Git init & first push:
Repo: <owner>/<repo>
Branch: main
Message: <commit message>

Create feature branch:
Name: feature/<name>
Message: <commit message>

Open PR:
Base: develop
Head: feature/<name>
Title: <title>
Description: <short description>
```

---

## 12) README Sections  
**Template: `template/readme`**
```
Update README:
Section: <Structure|HowToUse|Contribution|Purpose>
Action: <add|rewrite|append>
Content: <text>
```

---

## 13) Artisan Commands  
**Template: `template/artisan`**
```
Run artisan command:
php artisan <command>
```

**Examples:**
```
php artisan make:model Brand -mcr
php artisan make:policy BrandPolicy --model=Brand
php artisan migrate:fresh --seed
php artisan queue:table
php artisan breeze:install
```

---

## 14) Custom Functions  
**Template: `template/function`**
```
Write me function:
Name: <function_name>
Purpose: <short description>
Details: <optional extra notes>
```
**Example:**  
```
Write me function:
Name: uploadImage
Purpose: handle file upload and save path to database
Details: should accept path, resize to 600px, and return URL
```

---

## 15) Comment / Reference Blocks  
**Template: `template/block`**
```
Write me block:
Type: <comment|reference|custom>
Title: <short title for block>
Notes: <optional notes>
```

**Example – Comment Block:**  
```
Write me block:
Type: comment
Title: Custom Functions (Put at the end of the Model)
```

👉 Output:
```php
/* ========== Custom Functions (Put at the end of the Model) ========== */
/**
 * Notes:
 * - Add any custom functions here
 */
```

---



---



## 16) Resource Definition (Name + Table)  
**Template: `template/resource`**
```
Add commands-cheatsheet.md # [Name]

**Description:**
[General description of the Name]

---

## Table (Markdown)

**Description:** General description of the table

| Column      | Type           | Description                    | Mass Assignment | Relationships |
| ----------- | -------------- | ------------------------------ | --------------- | -------------- |
| id          | BIGINT (PK)    | Primary key                    | —               |                |
| name        | VARCHAR(150)   | Example: Name of the record    | fillable        |                |
| slug        | VARCHAR(150)   | URL-friendly unique identifier | fillable        |                |
| description | TEXT NULL      | Optional description text      | fillable        |                |
| is_active   | TINYINT(1)     | Active flag (true/false)       | fillable        |                |
| created_at  | TIMESTAMP      | Record creation time           | —               |                |
| updated_at  | TIMESTAMP      | Record update time             | —               |                |
| deleted_at  | TIMESTAMP NULL | Soft delete timestamp          | —               |                |

---

## Relationships (High-Level)

* [List the relationships here manually for quick reference]
```

---

### 📘 Example Usage
```
Add commands-cheatsheet.md # Brand

**Description:**
This table stores all brands available in the catalog for product association.
```

## 🔹 One-Line Shortcuts
- **Doc:** `Use the new Template.md and create <table>.md`  
- **Web:** `Use template for web: Resource:<X> Table:<xs> Options:CRUD,SoftDeletes=on,Requests,Policy,Routes`  
- **API:** `Use template for api: Resource:<X> Table:<xs> Options:CRUD,SoftDeletes=on,Requests,Policy,Routes API:ResourceCollections,Pagination=15,Filters:name,slug`  
- **SQL Table Description:** `Add description to table: brands => 'Stores all brand names, slugs, and status for products'`  
- **SQL Column Description:** `Add description to column: users.is_active => 'Flag to show if user account is active or not'`  
- **Model:** `Create/Update model: Name:<X> Table:<xs> SoftDeletes=on Add Custom Functions: - scopeActive() - uploadImage(path)`  
- **Migration:** `Create migration: Table:<xs> Fields: - name:string unique - slug:string unique SoftDeletes=on`  
- **Requests:** `Create requests for <X>: Store Rules: ... Update Rules: ... Authorize: policy`  
- **Policy:** `Create policy for <X> with abilities: all`  
- **Routes:** `Add routes <web|api> for <X>: Type: resource Middleware: auth`  
- **Git:** `Git init & first push: Repo:<owner/repo> Branch: main Message: ...`  
- **README:** `Update README: Section:<Purpose> Action: append Content: <...>`  
- **Artisan:** `Artisan command: make:model Brand -mcr`  
- **Function:** `Write me function: uploadImage => handle file upload and save path to DB`  
- **Block:** `Write me block: Type: comment Title: Custom Functions`  

---
