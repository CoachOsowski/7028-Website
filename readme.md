````markdown
# 7028 Website (Hugo)

This repository contains the source code for the 7028 website, built with [Hugo](https://gohugo.io/) and deployed automatically from GitHub.

---

## 📦 Setup (First Time on a New Computer)

1. **Install Git**
   - [Download Git](https://git-scm.com/downloads) and install.
   - Verify:  
     ```bash
     git --version
     ```

2. **Install Hugo Extended**
   - On Windows (with [Scoop](https://scoop.sh/)):  
     ```powershell
     scoop install hugo-extended
     ```
   - Or with [winget](https://learn.microsoft.com/en-us/windows/package-manager/winget/):  
     ```powershell
     winget install Hugo.Hugo.Extended
     ```
   - On macOS:  
     ```bash
     brew install hugo
     ```
   - Verify:  
     ```bash
     hugo version
     ```

3. **Clone the repository**
   ```bash
   git clone https://github.com/<YOUR_USERNAME>/<REPO_NAME>.git
   cd <REPO_NAME>
````

4. **Run locally**

   ```bash
   hugo server -D
   ```

   Open [http://localhost:1313](http://localhost:1313) to preview.

---

## 📝 Adding New Pages

1. Run the `hugo new` command:

   ```bash
   hugo new posts/my-new-page.md
   ```

   * Files are created in `content/posts/`.
   * By default, new files have `draft: true` in the front matter.
     Set `draft: false` when ready to publish.

2. Add images:

   * Place images in `static/img/`.
   * Reference them in Markdown like:

     ```markdown
     ![Alt text](/img/myphoto.jpg)
     ```

3. Commit and push:

   ```bash
   git add .
   git commit -m "Add new page"
   git push
   ```

---

## 🎨 Switching & Downloading Themes

1. Browse themes: [https://themes.gohugo.io/](https://themes.gohugo.io/)

2. Add a theme (example: Ananke):

   ```bash
   git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
   ```

3. Update `config.toml`:

   ```toml
   theme = "ananke"
   ```

4. Test:

   ```bash
   hugo server -D
   ```

5. Commit and push changes.

---

## 🛠 Editing Themes

* Themes live in the `themes/` folder.

* To **edit styles, layouts, or partials**:

  * Change files inside `themes/<theme-name>/`.
  * Or, copy a file from the theme into your project’s `layouts/` folder and modify it (this overrides the theme’s version).

    * Example:
      If the theme has `themes/ananke/layouts/_default/single.html`, copy it to `layouts/_default/single.html` and edit.

* For CSS/JS customizations:

  * Many themes let you add your own files in `/assets/` or override SCSS variables.
  * Check the theme’s documentation.

---

## 🚀 Deployment

* Pushing to `main` triggers GitHub Actions:

  * Builds the site with Hugo.
  * Deploys the output (`/public`) to Bluehost via FTP/SFTP.

No manual deploy step is needed — just `git push`.

---

## 🔑 Common Commands

* Run local server:

  ```bash
  hugo server -D
  ```
* Build site (production):

  ```bash
  hugo --minify
  ```
* Add new page:

  ```bash
  hugo new posts/my-page.md
  ```

---

## 📚 Resources

* [Hugo Documentation](https://gohugo.io/documentation/)
* [Hugo Themes](https://themes.gohugo.io/)
* [GitHub Docs](https://docs.github.com/)

```

---

Would you like me to also include **Bluehost-specific deployment instructions** (secrets, GitHub Actions workflow, etc.) in this README, or keep it focused just on editing/content?
```
