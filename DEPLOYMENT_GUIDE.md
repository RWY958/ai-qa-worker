# AI Virtual QA Worker — Deployment Guide

## Prerequisites

Before you start, make sure you have these installed on your machine:

1. **Node.js** (v18 or later) — download from https://nodejs.org
2. **Git** — download from https://git-scm.com
3. **A GitHub account** — sign up at https://github.com (free)

To verify your installations, open a terminal (Command Prompt / PowerShell on Windows, Terminal on Mac) and run:

```
node --version
git --version
```

Both should return version numbers. If not, install them first.

---

## Step 1: Set Up the Project Locally

Open your terminal and navigate to where you want the project:

```bash
cd Desktop
```

Copy the entire `ai-qa-worker` folder (provided to you) to your Desktop, then enter it:

```bash
cd ai-qa-worker
```

Install all dependencies:

```bash
npm install
```

This will take 1-2 minutes. It downloads React, Tailwind, Recharts, and other libraries.

Test that it works locally:

```bash
npm run dev
```

You should see output like:

```
  VITE v5.x.x  ready in xxx ms

  ➜  Local:   http://localhost:5173/
```

Open that URL in your browser. You should see the landing page. Press `Ctrl+C` to stop the server.

---

## Step 2: Push to GitHub

### 2a. Create a new GitHub repository

1. Go to https://github.com/new
2. Repository name: `ai-qa-worker`
3. Keep it **Public** (required for free Vercel hosting)
4. Do NOT initialize with README (we already have files)
5. Click **Create repository**
6. You'll see a page with setup instructions — keep this page open

### 2b. Push your code

In your terminal (still inside the `ai-qa-worker` folder), run these commands one by one:

```bash
git init
```

```bash
git add .
```

```bash
git commit -m "Initial commit - AI Virtual QA Worker"
```

```bash
git branch -M main
```

```bash
git remote add origin https://github.com/YOUR_USERNAME/ai-qa-worker.git
```

**IMPORTANT:** Replace `YOUR_USERNAME` with your actual GitHub username.

```bash
git push -u origin main
```

If prompted, enter your GitHub username and password (or personal access token).

Refresh your GitHub repo page — you should see all the project files there.

---

## Step 3: Deploy to Vercel

### 3a. Create a Vercel account

1. Go to https://vercel.com/signup
2. Click **Continue with GitHub**
3. Authorize Vercel to access your GitHub account
4. Select **Hobby** (free plan)
5. Enter your name and click **Continue**

### 3b. Import your project

1. You'll land on the Vercel dashboard
2. Click **Add New** → **Project**
3. You'll see a list of your GitHub repos
4. Find `ai-qa-worker` and click **Import**

### 3c. Configure and deploy

Vercel will auto-detect it's a Vite project. Verify these settings:

| Setting | Value |
|---------|-------|
| Framework Preset | Vite |
| Build Command | `npm run build` |
| Output Directory | `dist` |

These should be auto-filled. If not, enter them manually.

5. Click **Deploy**
6. Wait 1-2 minutes for the build to complete
7. You'll see a **Congratulations!** screen with a preview of your site

### 3d. Access your live site

Your app is now live at a URL like:

```
https://ai-qa-worker.vercel.app
```

(The exact URL depends on availability — Vercel may add random characters.)

Click the preview or the URL to see your live site.

---

## Step 4: Custom Domain (Optional)

If you want a custom domain like `qa-worker.yourcompany.com`:

1. Go to your project on the Vercel dashboard
2. Click **Settings** → **Domains**
3. Enter your domain name and click **Add**
4. Vercel will show you DNS records to add
5. Go to your domain registrar and add the DNS records
6. Wait for propagation (usually 5-30 minutes)

---

## Updating Your App

After making changes to the code:

```bash
git add .
git commit -m "Description of changes"
git push
```

Vercel automatically redeploys on every push — your live site updates within 1-2 minutes.

---

## Troubleshooting

### "npm install" fails
- Make sure you have Node.js v18+ installed
- Try deleting `node_modules` folder and `package-lock.json`, then run `npm install` again

### "git push" asks for password and fails
- GitHub no longer accepts passwords. Create a Personal Access Token:
  1. Go to GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)
  2. Generate new token with `repo` scope
  3. Use this token as your password when pushing

### Vercel build fails
- Check the build logs in the Vercel dashboard (Deployments → click the failed deployment)
- Most common issue: missing dependencies — make sure `package.json` has all required packages
- Verify the Output Directory is set to `dist` (not `build`)

### Blank page after deploy
- Make sure the Output Directory in Vercel is set to `dist`
- Check browser console for errors (F12 → Console tab)

---

## Project Structure

```
ai-qa-worker/
├── index.html              ← Entry HTML file
├── package.json            ← Dependencies and scripts
├── vite.config.js          ← Vite configuration
├── tailwind.config.js      ← Tailwind CSS configuration
├── postcss.config.js       ← PostCSS configuration
├── .gitignore              ← Files to exclude from Git
└── src/
    ├── main.jsx            ← React entry point
    ├── index.css           ← Tailwind imports + global styles
    └── App.jsx             ← The full application (landing + dashboard)
```
