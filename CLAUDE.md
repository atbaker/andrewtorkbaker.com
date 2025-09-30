# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a minimal personal website for Andrew Tork Baker, built as a static site with Vite and Tailwind CSS v4. It consists of two pages: a landing page and a resume page, hosted on GitHub Pages.

## Development Commands

```bash
npm install          # Install dependencies
npm run dev          # Start dev server at localhost:5173
npm run build        # Build for production (outputs to dist/)
npm run preview      # Preview production build locally
```

## Architecture

### Site Structure

- **Two HTML pages**: `index.html` (landing) and `resume.html` (resume)
- **Shared styles**: `src/style.css` contains Tailwind imports and custom styles
- **Multi-page build**: Vite is configured to build both HTML files (see `vite.config.js`)
- **Static assets**: Located in `public/` directory, including photo and resume PDF

### Tailwind CSS v4 Setup

This project uses Tailwind CSS v4, which has a different setup than v3:

- **Vite plugin required**: `@tailwindcss/vite` plugin is used in `vite.config.js`
- **CSS import**: Styles are imported with `@import "tailwindcss"` in `src/style.css`
- **No config file**: Tailwind v4 doesn't use `tailwind.config.js`

### Print Stylesheet

The resume page has extensive print-specific styles in `src/style.css` under `@media print`:

- Designed to fit content on 2 printed pages
- Significantly reduced font sizes, margins, and spacing compared to web view
- Elements with `.no-print` class (navigation links) are hidden when printing
- Page break controls to keep sections together

**Workflow for PDF generation**:
1. Run `npm run dev`
2. Open `http://localhost:5173/resume.html` in browser
3. Use browser's "Print to PDF" feature (⌘+P / Ctrl+P)
4. Save updated PDF to `public/Andrew Tork Baker - Resume.pdf`

### SEO and Indexing

- **Landing page**: Has meta description, is indexed by search engines
- **Resume page**: Has `<meta name="robots" content="noindex" />` to keep contact info private

## Deployment

- **Auto-deploy**: GitHub Actions workflow (`.github/workflows/deploy.yml`) builds and deploys to GitHub Pages on every push to `main`
- **GitHub Pages configuration**: Must be set to "GitHub Actions" source in repo settings
- **Custom domain**: Configured via Cloudflare A, AAAA, and CNAME records pointing to GitHub Pages
