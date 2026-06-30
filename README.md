# Flatpak Repository (`pabmartine`)

This is a personal OSTree-based repository for distributing and hosting applications packaged in the **Flatpak** format. The repository is publicly hosted, allowing users to install and keep up-to-date applications developed by [@pabmartine](https://github.com/pabmartine).

---

## 🚀 Hosted Applications

The repository contains the following applications:

| Application | Flatpak ID | Source Code | Description |
| :--- | :--- | :--- | :--- |
| **Docks** | `com.pabmartine.Docks` | [pabmartine/docks](https://github.com/pabmartine/docks) | A customizable dock/app bar utility. |
| **LogViewer** | `com.pabmartine.LogViewer` | [pabmartine/log-viewer](https://github.com/pabmartine/log-viewer) | An interactive log and registry file viewer. |
| **Looker** | `com.pabmartine.Looker` | [pabmartine/looker](https://github.com/pabmartine/looker) | A tool for quick resource exploration and viewing. |
| **MarkdownEditor** | `com.pabmartine.MarkdownEditor` | [pabmartine/markdown-editor](https://github.com/pabmartine/markdown-editor) | A minimalist and smooth Markdown text editor with a live preview. |
| **TodoList** | `com.pabmartine.TodoList` | [pabmartine/todo-list](https://github.com/pabmartine/todo-list) | A simple and efficient application for managing to-do tasks. |

---

## 📥 How to Install and Use the Applications

Follow these steps to configure the repository on your system and install any of the listed applications.

### 1. Add the repository to Flatpak
Since this is a custom repository (which by default does not use a GPG signature), add the repository with the `--no-gpg-verify` flag:

```bash
flatpak remote-add --user --no-gpg-verify pabmartine-repo https://pabmartine.github.io/flatpak-repository/
```

### 2. List available applications
To confirm that the repository has been added correctly and see the applications it offers:

```bash
flatpak remote-ls pabmartine-repo
```

### 3. Install an application
Install the desired application using its ID. For example, to install **TodoList**:

```bash
flatpak install pabmartine-repo com.pabmartine.TodoList
```

### 4. Run the installed application
Once the installation is complete, you can launch it from your desktop's application launcher or run it from the terminal:

```bash
flatpak run com.pabmartine.TodoList
```

---

## 🛠️ Maintenance Instructions (For Developers)

If you need to update or add new applications to the repository locally, you can follow this standard workflow.

### Prerequisites
Make sure you have `flatpak` and `flatpak-builder` installed on your development system.

### 1. Build and export an application to the repository
Compile the application using its manifest and export it directly to this repository by specifying its path:

```bash
flatpak-builder --repo=flatpak-repository --force-clean build-dir com.pabmartine.AppName.json
```

### 2. Update the repository index
After adding or modifying any application, regenerate the repository's summary index files so that clients can see the changes:

```bash
flatpak build-update-repo flatpak-repository
```

### 3. Publish changes to GitHub
Add the new objects, references, and updated files, and push them to the main branch to serve them via GitHub Pages:

```bash
git add .
git commit -m "Update repository content with latest builds"
git push origin main
```