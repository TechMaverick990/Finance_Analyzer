# How to Publish Finance Analyser to GitHub

Follow these steps in order. You only need to do the one-time setup once.

---

## Step 1 — Install Git (if not already installed)

**Windows:** Download and install from https://git-scm.com/download/win  
**Mac:** Run `xcode-select --install` in Terminal  
**Linux:** `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora)

Verify it works:
```bash
git --version
```

---

## Step 2 — Create a GitHub Account

1. Go to https://github.com
2. Click **Sign up** and create a free account
3. Verify your email address

---

## Step 3 — Create a New Repository on GitHub

1. Log in to GitHub
2. Click the **+** icon in the top-right corner → **New repository**
3. Fill in the form:
   - **Repository name:** `finance-analyser` (or any name you like)
   - **Description:** `Personal finance expense tracker with interactive charts`
   - **Visibility:** Public (free) or Private
   - **Do NOT** check "Add a README file" — you already have one
4. Click **Create repository**
5. Copy the repository URL shown — it will look like:
   ```
   https://github.com/YOUR_USERNAME/finance-analyser.git
   ```

---

## Step 4 — Configure Git with Your Identity

Open a terminal (Command Prompt, PowerShell, or Terminal on Mac/Linux) and run:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Use the same email address you registered with on GitHub.

---

## Step 5 — Navigate to the Project Folder

In your terminal, change directory to where the project is saved on your computer. For example:

```bash
cd "C:\Users\YourName\Documents\Finance Analyser"
```

Or on Mac/Linux:
```bash
cd ~/Documents/Finance\ Analyser
```

---

## Step 6 — Initialize Git and Push to GitHub

Run these commands one by one in the project folder:

```bash
# Initialize a new git repository
git init

# Add all project files to staging
git add .

# Create the first commit
git commit -m "Initial commit — Finance Analyser app"

# Rename the default branch to main
git branch -M main

# Link your local project to the GitHub repository
# (replace with the URL you copied in Step 3)
git remote add origin https://github.com/YOUR_USERNAME/finance-analyser.git

# Push your code to GitHub
git push -u origin main
```

GitHub will ask for your username and password. For the password, you need to use a **Personal Access Token** (not your account password) — see the note below.

---

## Note: GitHub Personal Access Token (PAT)

GitHub no longer accepts account passwords over HTTPS. You need to create a token:

1. Go to https://github.com/settings/tokens
2. Click **Generate new token (classic)**
3. Give it a name like `finance-analyser-token`
4. Set expiration to 90 days (or No expiration)
5. Check the **repo** scope checkbox
6. Click **Generate token**
7. Copy the token immediately — GitHub will only show it once
8. Use this token as your "password" when Git asks for it

**Optional — store the token so you don't have to re-enter it:**
```bash
git config --global credential.helper store
```
Then push once and enter your username + token — Git will remember it.

---

## Step 7 — Verify It Worked

Refresh your GitHub repository page in the browser. You should see all the files:

```
finance-analyser/
├── src/
├── public/
├── README.md          ✅
├── LICENSE            ✅
├── CONTRIBUTING.md    ✅
├── .gitignore         ✅
├── package.json
├── vite.config.ts
└── ...
```

---

## Step 8 — Making Future Updates

Whenever you make changes and want to save them to GitHub:

```bash
# See what files changed
git status

# Stage all changes
git add .

# Commit with a description of what changed
git commit -m "Add dark mode toggle" 

# Push to GitHub
git push
```

---

## Optional: Deploy as a Live Website (GitHub Pages)

You can host the app for free on GitHub Pages so anyone can use it in their browser:

1. Run the build locally:
   ```bash
   pnpm build
   ```
2. Install the deploy tool:
   ```bash
   pnpm add -D gh-pages
   ```
3. Add this to `package.json` under `"scripts"`:
   ```json
   "deploy": "gh-pages -d dist"
   ```
4. Add this line to `package.json` (top level):
   ```json
   "homepage": "https://YOUR_USERNAME.github.io/finance-analyser"
   ```
5. Also update `vite.config.ts` to set the base path:
   ```typescript
   export default defineConfig({
     base: '/finance-analyser/',
     plugins: [react()],
   })
   ```
6. Deploy:
   ```bash
   pnpm deploy
   ```
7. In your GitHub repository → **Settings** → **Pages** → set Source to `gh-pages` branch

Your app will be live at:
```
https://YOUR_USERNAME.github.io/finance-analyser
```

---

## Files Included in the Repository

| File | Purpose |
|------|---------|
| `README.md` | Project description, setup instructions, feature list |
| `LICENSE` | MIT open-source license |
| `CONTRIBUTING.md` | Guide for other developers who want to contribute |
| `.gitignore` | Tells Git which files to ignore (node_modules, dist, etc.) |
| `package.json` | Project dependencies and scripts |
| `src/App.tsx` | Main app UI and logic |
| `src/utils.ts` | CSV parsing and auto-categorization rules |
| `src/types.ts` | TypeScript type definitions |

---

## Files NOT Uploaded (handled by .gitignore)

These are excluded from Git and will be regenerated locally:

- `node_modules/` — reinstalled with `pnpm install`
- `dist/` — rebuilt with `pnpm build`
- `bundle.html` — rebuilt with the bundle script
- `.parcel-cache/` — Parcel build cache
- `.env` files — keep secrets out of GitHub
