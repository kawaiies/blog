# Currex Blog CMS - Complete Installation Guide

> Version 1.0 | Last updated: June 17, 2026

---

## 1. System Overview

Currex Blog CMS is a lightweight blog content management system.

### Features
- No database required (files-based storage)
- Visual editor (Quill rich text editor)
- Admin panel for managing posts, pages, menus
- One-click static site generation
- Free hosting on GitHub Pages
- Amazon affiliate link support built-in

---

## 2. Prerequisites

### Required Software
- **Windows PC** with internet connection
- **Node.js** (JavaScript runtime)

### Optional
- **GitHub account** for deploying to GitHub Pages
- **Git** (for GitHub Desktop or git commands)

---

## 3. Installing Node.js

### Step 1: Download
1. Open browser, go to https://nodejs.org/
2. Click the LTS version (left side, recommended)
3. Download the Windows installer (.msi file)

### Step 2: Install
1. Double-click the downloaded .msi file
2. Click Next through the installer
3. Accept the license terms
4. Keep default installation path
5. Click Install
6. Wait for completion, click Finish

### Step 3: Verify Installation
1. Press `Win + R`, type `cmd`, press Enter
2. Type: `node -v` and press Enter
3. If you see a version number (e.g., v18.20.8), Node.js is installed correctly
4. Also verify npm: `npm -v`

---

## 4. Setting Up the Project

### Option A: From ZIP File
1. Extract the project ZIP file to a folder (e.g., `C:\MyBlog\`)
2. Open Command Prompt (cmd)

### Option B: From GitHub
```
git clone https://github.com/yourusername/currex.git
cd currex
```

### Install Dependencies
1. In Command Prompt, navigate to the project folder:
```
cd C:\path\to\currex
```
2. Install packages:
```
npm install
```
3. Wait for completion (you'll see "added xxx packages")

If installation is slow:
```
npm install --registry=https://registry.npmmirror.com
```

---

## 5. Starting the System

### Start Server
In the project folder, run:
```
node app.js
```

You should see:
```
Currex Blog running at http://localhost:4000
Admin panel: http://localhost:4000/admin
```

### Access the Website
- **Homepage**: http://localhost:4000
- **Admin Panel**: http://localhost:4000/admin

### Stop the Server
Press `Ctrl + C` in the Command Prompt, then type `Y`.

---

## 6. Admin Login

### Login Page
Open http://localhost:4000/admin in your browser.

### Default Credentials
- Username: `admin`
- Password: `admin123`

> IMPORTANT: Change the password before going live!

### Change Password
Open `app.js` and find:
```
var ADMIN_PASS = process.env.ADMIN_PASS || 'admin123';
```
Change `admin123` to your new password.

---

## 7. Admin Panel Overview

After logging in, you'll see the dashboard with these menu items:

| Menu | Function |
|------|----------|
| Dashboard | Site statistics overview |
| Posts | Manage blog articles |
| Pages | Manage standalone pages |
| Menus | Manage navigation menus |
| Sidebar | Manage sidebar widgets |
| Settings | Site configuration |
| Build Site | Generate static HTML |
| Logout | Exit admin panel |

---

## 8. Publishing Articles

### Create New Post
1. Click **Posts** → **New Post**
2. Fill in the fields:
   - **Title**: Article title (required)
   - **Slug**: URL alias (auto-generated, can edit)
   - **Excerpt**: Short summary for listing page
   - **Content**: Article body (visual editor)
   - **Author**: Author name
   - **Category**: e.g., Review, Guide, News
   - **Tags**: Comma-separated (e.g., running, insoles)
   - **Cover Image**: Image URL
   - **Published**: Check to publish immediately

### Using the Editor
The built-in editor supports: bold, italic, headings, lists, links, images.
Just type and format directly - WYSIWYG.

### Save & Publish
Click **Save** button. Published articles appear on the site immediately.

### Edit & Delete
In **Posts** list, click **Edit** to modify, **Delete** to remove.

---

## 9. Creating Pages

### Create New Page
1. Click **Pages** → **New Page**
2. Fill in:
   - **Title**: Page title
   - **Slug**: URL (e.g., `about` → `/about`)
   - **Content**: Page content
   - **Published**: Check to publish

### Pages vs Posts
- **Pages**: For static content (About, Contact, FAQ)
- **Posts**: For blog articles with dates, categories, tags

---

## 10. Managing Menus

1. Click **Menus**
2. Three menu areas:
   - **Main Menu**: Top navigation
   - **Footer Menu**: Bottom links
   - **Resources Menu**: Resource links
3. Add items by entering **Label** and **URL**
4. Click corresponding **Save Menu** button

---

## 11. Managing Sidebar

1. Click **Sidebar**
2. Add widgets (text, HTML, etc.)
3. Set title and content
4. Check **Enabled** to activate
5. Click **Save**

---

## 12. Site Settings

Click **Settings** to configure:
- Site Title
- Site Description
- Site URL
- Posts Per Page
- Author Name / Email
- Social Media Links

---

## 13. Deploying to GitHub Pages

### Step 1: Generate Static Site
1. In admin panel, click **Build Site**
2. "Site built successfully!" confirms success
3. Files are in the `static-site/` folder

### Step 2: Create GitHub Repository
1. Go to https://github.com and sign in
2. Click **+** → **New repository**
3. Repository name: `yourusername.github.io` (e.g., `kawaiies.github.io`)
4. Set to **Public**
5. Click **Create repository**

### Step 3: Upload Files (Using GitHub Desktop)

GitHub Desktop is recommended for beginners.

1. Download from https://desktop.github.com/ and install
2. Open GitHub Desktop, sign in to your GitHub account
3. Click **File** → **Clone repository**
4. Select the repository you just created
5. Choose a local folder and click **Clone**
6. Copy ALL files from `static-site/` folder into the cloned folder
7. In GitHub Desktop, you'll see changed files
8. Enter a commit message (e.g., "Initial deploy")
9. Click **Commit to main**
10. Click **Push origin** (top right)

### Step 4: Enable GitHub Pages
1. Go to your repository on github.com
2. Click **Settings** → **Pages**
3. Under **Source**, select **Deploy from a branch**
4. Branch: `main`, folder: `/ (root)`
5. Click **Save**
6. Wait 1-2 minutes
7. Your site is live at: https://yourusername.github.io

---

## 14. FAQ

### Q1: Port already in use
Error: `port 4000 is already in use`

Solution: Change the port in `app.js`:
```
var PORT = process.env.PORT || 4000;
```
Change `4000` to another number (e.g., `3000`).

### Q2: CSS/styles not loading
Press `Ctrl + F5` to force refresh browser cache.

### Q3: How to backup data
Simply copy the entire `data/` folder.

### Q4: Site broken on GitHub Pages
Wait 1-2 minutes after pushing. Check `static-site/` for `index.html`.

### Q5: How to set Amazon affiliate links
Format: `https://www.amazon.com/dp/ASIN?tag=your-tag`
Example: `https://www.amazon.com/dp/B079J11LBY?tag=prettydani-20`

---

## Quick Reference

### Commands
```
# Start the system
cd C:\path\to\currex
node app.js

# Generate static site
node app.js --build

# Install dependencies
npm install

# Check Node.js version
node -v
```

### File Structure
```
currex/
  app.js              Server entry point
  data/               Content storage
    posts/            Blog articles (.md)
    pages/            Pages (.json)
  views/              HTML templates
  public/             Static assets
  lib/                Helper functions
  static-site/        Generated static site
  node_modules/       Dependencies (auto)
```

---

> Tip: If something goes wrong, check the Command Prompt for error messages. Most issues are caused by being in the wrong folder or missing dependencies.
