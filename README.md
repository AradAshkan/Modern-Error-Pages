# Modern Error Pages (403, 404, 500) with Dark/Light Theme & Multi-language Support

This project provides **modern and responsive 403, 404, and 500 error pages** that are fully customizable.
It supports **dark/light themes** and **multi-language support** (Persian and English). All texts and user settings are managed via separate configuration files (`config.json` and `lang.json`), making it easy to maintain and extend.
### 📹 Showcase

<details>
  <summary>View Screenshots</summary>
 <img width="750" height="450" alt="LightMode" src="https://github.com/user-attachments/assets/70b7c00a-b190-4b73-9817-8f6c9083ce5a" /> <img width="750" height="450" alt="DarkMode" src="https://github.com/user-attachments/assets/8b48f697-97b5-4437-8462-50fd7ddd58ba" />
</details>


---

## 📁 Project Structure

```
project-root/
│
├─ errors/
│   ├─ 403.html
│   ├─ 404.html
│   └─ 500.html
├─ setting/
│   ├─ config.json
│   └─ lang.json
└─ .htaccess  (optional)
```

---

## ⚙️ Settings

### 1. `config.json`

Located in the `setting` folder, this file controls the **theme and language** when the page loads:

```json
{
  "theme": "dark",      // Initial theme: "dark" or "light"
  "language": "fa"      // Initial language: "fa" (Persian) or "en" (English)
}
```

* `theme` → `"dark"` or `"light"`
* `language` → `"fa"` or `"en"`

---

### 2. `lang.json`

All text for the error pages is stored in `setting/lang.json`:

```json
  "en": {
    "403": { "title": "Forbidden", "message": "You don't have permission to access this page.", "button": "Go back home" },
    "404": { "title": "Page Not Found", "message": "It seems this page does not exist or has been removed.", "button": "Go back home" },
    "500": { "title": "Internal Server Error", "message": "Something went wrong on the server. Please try again later.", "button": "Go back home" }
  }
}
```

✅ Adding a new language or modifying text is as simple as updating this file.

---

### 3. HTML Pages

* Each page (403.html, 404.html, 500.html in the `errors/` folder) is **modern, responsive, and animated**.
* The theme and language are applied based on the configuration files.
* Floating animation on the error number and a hover effect on the button are included.
* A single shared HTML file can be used for all errors with a variable `errorCode` in JS.

---

### 4. `.htaccess` (Optional, for Apache servers)

You can use `.htaccess` to automatically load the correct error page:

```apache
# Enable URL rewriting
RewriteEngine On

# Error documents
ErrorDocument 403 /errors/403.html
ErrorDocument 404 /errors/404.html
ErrorDocument 500 /errors/500.html

# Restrict direct access to configuration files
<FilesMatch "^setting/(config|lang)\.json$">
    Require all denied
</FilesMatch>
```

* If you do not have `.htaccess` or are using a different server, you can link the error pages manually.
* The `<FilesMatch>` section prevents direct access to your config and language files for security.

---

### 5. How to Use

1. Place all files in your project directory.
2. Ensure the paths to `config.json` and `lang.json` in the JS match the `setting/` folder.
3. Set the `errorCode` variable in JS for the appropriate error page (403, 404, or 500).
4. Upload to the server. The pages are ready to use.

---

### 6. Customization

* **Change colors:** Update CSS variables `--accent`, `--bg-light`, `--bg-dark`.
* **Add languages:** Edit `lang.json`.
* **Change theme:** Update `config.json` or add a theme toggle button in the HTML.

---
