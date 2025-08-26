# Laravel12-Commands-Reference-Chatgpt

This repository is a **reference playbook** for Laravel 12 commands, artisan scripts, database migrations, SQL references, Git workflows, and reusable templates — all generated and maintained with the help of **ChatGPT**.

The purpose is to provide a **clear system of prompts (commands)** that can be reused whenever I want ChatGPT to generate code or documentation for Laravel projects.

---

## 📂 Repository Structure

- **commands-cheatsheet.md** → Full list of templates, artisan commands, SQL references, and usage examples  
- **laravel12/** → Laravel specific notes and examples  
- **git/** → GitHub workflow commands and PR templates  
- **db/** → Database schemas, migration references, seeder examples  
- **templates/** → Web & API templates, CRUD references, policies, requests  
- **notes/** → General notes, references, and extra explanations  

---

## 🚀 How to Use with ChatGPT

1. **Open the `commands-cheatsheet.md` file.**  
   This file contains all the templates, artisan commands, and one-line shortcuts.

2. **Copy the prompt you need** and paste it into ChatGPT.  
   Example:
   ```
   Use template for web:
   Resource: Brand
   Table: brands
   Options: CRUD, SoftDeletes=on, Requests, Policy, Routes
   Notes: add index search by name, slug
   ```

   👉 ChatGPT will generate the **Model, Controller, Migration, Policy, Requests, and Routes** automatically.

3. **Use SQL Description templates** when you want to add comments or descriptions to tables and columns.  
   Example:
   ```
   Add description to column:
   Table: users
   Column: is_active
   Description: Flag to show if user account is active or not
   ```

4. **Use Artisan command references** to quickly recall the usage of Laravel CLI commands.  
   Example:
   ```
   Artisan command: make:model Brand -mcr
   ```

   👉 ChatGPT will explain the command, its usage, and generate related files.

5. **Use Function templates** when you need custom functions inside your models or helpers.  
   Example:
   ```
   Write me function:
   Name: uploadImage
   Purpose: handle file upload and save path to database
   Details: resize to 600px and return URL
   ```

6. **Use Comment/Reference Blocks** to keep your code organized with reusable comment headers.  
   Example:
   ```
   Write me block:
   Type: comment
   Title: Custom Functions (Put at the end of the Model)
   ```

7. **Follow Git workflow templates** to create branches, commits, and pull requests consistently.  
   Example:
   ```
   Git init & first push:
   Repo: aalrashaid/Laravel12-Commands-Reference-Chatgpt
   Branch: main
   Message: Initial commit with README and folders
   ```

---

## 🔹 One-Line Shortcuts

At the bottom of `commands-cheatsheet.md` you’ll find **short one-line prompts** for quick use. Example:

- `Use the new Template.md and create brands.md`  
- `Create migration: Table: brands Fields: - name:string unique - slug:string unique SoftDeletes=on`  
- `Artisan command: make:model Brand -mcr`  
- `Write me function: uploadImage => handle file upload and save path to DB`  
- `Add description to column: users.is_active => 'Flag to show if user account is active or not'`  

---

## ✨ Purpose

This project is not a tutorial.  
It is a **personal & shared reference guide** to work faster and more consistently with Laravel 12 by leveraging ChatGPT as a coding assistant.  
Every new command, template, or block I use can be added here for future reuse.

---
