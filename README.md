# Langxu Bai — Personal Homepage

This repository contains the source code for Langxu Bai's personal academic
homepage. It presents a short biography, research interests, selected work,
talks, and links to academic profiles.

The site is designed for GitHub Pages and is intentionally kept small: it uses
plain HTML and CSS, with no JavaScript framework, package manager, or build
toolchain.

## Technical Approach

The website follows a zero-build static-site approach:

1. `index.html` provides the page structure, content, metadata, and external
   links.
2. `style.css` defines the visual system, layout, publication components,
   responsive behavior, and automatic dark mode.
3. The browser loads Google Fonts directly from Google Fonts.
4. GitHub Pages can serve the files from the repository root without generating
   a separate production bundle.

The request flow is therefore:

```text
GitHub Pages
    └── index.html
        ├── style.css
        └── Google Fonts
```

This approach keeps deployment simple and makes the site easy to maintain. The
trade-off is that repeated content and page-wide changes must be edited directly
in HTML rather than through templates or a content-management system.

## Project Structure

```text
.
├── index.html    # Canonical homepage source and entry point
├── style.css     # Layout, typography, dark mode, and responsive styles
├── index.md      # Early Markdown draft retained as a content reference
└── README.md     # Project documentation
```

`index.html` is the source of truth for the published homepage. Changes made
only to `index.md` are not automatically copied into the HTML page.

## Local Development

### Prerequisites

- Git
- A modern web browser
- Python 3 for the recommended local preview server

No Node.js installation or dependency setup is required.

### Clone the Repository

```bash
git clone https://github.com/langxubai/langxubai.github.io.git
cd langxubai.github.io
```

### Preview Locally

Start a local static-file server from the repository root:

```bash
python3 -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000) in a browser. Stop the
server with `Ctrl+C`.

Opening `index.html` directly also works for most edits, but a local HTTP server
more closely matches the behavior of GitHub Pages and is recommended when
testing links and assets.

## Build and Compilation

There is no compilation step. The checked-in HTML and CSS files are already the
production artifacts served by the browser.

In other words, the complete build procedure is:

```bash
# No install command
# No build command
python3 -m http.server 8000
```

Before publishing, verify the page at both desktop and mobile widths and check
the browser console for missing files or invalid links. Because the stylesheet
uses `prefers-color-scheme`, it is also useful to test both light and dark
system themes.

## Editing the Site

- Update biography, contact details, links, publications, and talks in
  `index.html`.
- Update colors, spacing, typography, responsive rules, or dark-mode styles in
  `style.css`.
- Put new local assets in a clearly named directory such as `images/` and
  reference them with relative URLs, for example `images/profile.jpg`.
- Keep paths case-sensitive, because GitHub Pages runs on a case-sensitive
  environment.

The current HTML includes placeholders for a profile image, CV, Google Scholar
profile, publications, and talks. Replace placeholder links such as `href="#"`
before treating the site as complete.

## Deployment

The repository name follows GitHub's user-site convention:
`langxubai.github.io`. It can be published directly from the repository root
through GitHub Pages.

For a branch-based GitHub Pages configuration:

1. Open the repository's **Settings → Pages**.
2. Choose **Deploy from a branch** as the source.
3. Select the `main` branch and the `/ (root)` directory.
4. Push changes to `main`.

Once GitHub Pages finishes deploying, the site should be available at
[https://langxubai.github.io](https://langxubai.github.io).

Because the site has no build step, no GitHub Actions workflow is required for
the current architecture.
