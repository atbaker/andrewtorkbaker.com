# andrewtorkbaker.com

Andrew Baker's personal site - a minimal static site built with Vite and Tailwind CSS.

## Development

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Deployment

The site automatically deploys to GitHub Pages via GitHub Actions when you push to the `main` branch.

### Initial GitHub Pages Setup

1. Go to your repository Settings → Pages
2. Under "Build and deployment", set Source to "GitHub Actions"
3. The site will be available at `https://andrewtorkbaker.com` (once DNS is configured)

### Cloudflare DNS Configuration

To use your custom domain `andrewtorkbaker.com`:

1. In Cloudflare DNS settings, add the following records:
   - **A records** pointing to GitHub Pages IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - **AAAA records** (IPv6) pointing to:
     - `2606:50c0:8000::153`
     - `2606:50c0:8001::153`
     - `2606:50c0:8002::153`
     - `2606:50c0:8003::153`
   - Proxy status: Proxied (orange cloud)

2. In GitHub repository Settings → Pages → Custom domain, enter `andrewtorkbaker.com` and save

## Tech Stack

- **Vite** - Build tool and dev server
- **Tailwind CSS v4** - Styling
- **Inter** - Primary font (Google Fonts)
- **GitHub Actions** - CI/CD pipeline
- **GitHub Pages** - Hosting

## Project Structure

```
├── public/              # Static assets (images, etc.)
├── src/
│   ├── style.css       # Global styles and Tailwind imports
│   └── main.js         # JavaScript entry point
├── index.html          # Landing page
├── resume.html         # Resume page
└── .github/
    └── workflows/
        └── deploy.yml  # GitHub Actions deployment workflow
```

## Updating Resume PDF

When you update the resume content in `resume.html`, regenerate the PDF:

1. Run the dev server: `npm run dev`
2. Open `http://localhost:5173/resume.html` in your browser
3. Use the browser's "Print to PDF" feature (⌘+P on Mac, Ctrl+P on Windows)
4. Save the PDF as `public/Andrew Tork Baker - Resume.pdf` (replacing the existing file)
5. The print stylesheet will automatically optimize the layout to fit on 2 pages
