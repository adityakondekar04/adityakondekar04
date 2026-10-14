# GitHub Profile Setup Guide — adityakondekar04

This repository (`adityakondekar04/adityakondekar04`) is a GitHub special profile repository. When public and named identically to your GitHub username, the root `README.md` is rendered directly at `https://github.com/adityakondekar04`.

---

## 1. Repository Architecture

```text
adityakondekar04/
├── .github/
│   └── workflows/
│       └── snake.yml       # Contribution snake generation workflow
├── README.md               # Visual profile displayed on GitHub
└── SETUP.md                # Deployment, permission, and maintenance guide
```

### Branch Roles
- **`main`**: Contains the source files (`README.md`, `SETUP.md`, `.github/workflows/snake.yml`).
- **`output`**: Managed automatically by the GitHub Actions workflow. Contains only the generated SVG assets:
  - `github-snake.svg` (light mode / default palette)
  - `github-snake-dark.svg` (GitHub dark mode palette `#0D1117`)

---

## 2. Commit and Push to GitHub

Ensure your local files are committed and pushed to the remote repository:

```bash
# Verify git status
git status

# Stage the updated files
git add README.md SETUP.md .github/workflows/snake.yml

# Commit changes
git commit -m "chore: upgrade profile design, technical skills, and snake workflow"

# Ensure the main branch is set
git branch -M main

# Verify remote configuration
git remote -v
# If needed, set origin:
# git remote add origin https://github.com/adityakondekar04/adityakondekar04.git

# Push to GitHub
git push -u origin main
```

---

## 3. Enable Required GitHub Actions Permissions

By default, GitHub restricts GitHub Actions workflows to read-only access. To allow the contribution snake workflow to push generated SVGs to the `output` branch using the built-in `GITHUB_TOKEN`, you must grant write permissions:

1. In your browser, open your repository: `https://github.com/adityakondekar04/adityakondekar04`
2. Navigate to **Settings** (top navigation bar).
3. In the left sidebar under **Code and automation**, click **Actions** → **General**.
4. Scroll down to the **Workflow permissions** section.
5. Select **Read and write permissions**.
6. Click **Save**.

> [!IMPORTANT]
> No Personal Access Token (PAT) is required. The workflow relies solely on the repository's built-in `GITHUB_TOKEN` with the `contents: write` permission configured above.

---

## 4. Run the Contribution Snake Workflow

The workflow is configured with three triggers:
- **Automatic push trigger:** Automatically triggers whenever `.github/workflows/snake.yml` is updated on `main`.
- **Scheduled cron trigger:** Runs daily at `00:17 UTC` (`17 0 * * *`) to keep contributions up to date.
- **Manual trigger (`workflow_dispatch`):** Allows on-demand regeneration at any time.

### How to Run Manually:
1. Navigate to the **Actions** tab of the repository (`https://github.com/adityakondekar04/adityakondekar04/actions`).
2. In the left workflow list, click **Generate Contribution Snake**.
3. In the banner above the workflow run list, click the **Run workflow** dropdown.
4. Ensure `Branch: main` is selected, then click the green **Run workflow** button.
5. Refresh the page after 15–30 seconds. A green checkmark indicates successful generation.
6. Verify the `output` branch exists in your branch dropdown and contains both `github-snake.svg` and `github-snake-dark.svg`.

---

## 5. Verification & Live Profile Inspection

Once the workflow finishes:

1. Visit your public profile: `https://github.com/adityakondekar04`.
2. Verify the following components:
   - **Header & Typing Animation:** Displays the rotating titles smoothly with dark theme accenting.
   - **About Me & Recognitions:** Highlights education, hackathons (15+), and awards (Innoventure MIT Alandi, NLPC 2026, Navonmesh DESPU 2026).
   - **Technical Skills:** Categorized breakdown with compact icon grid (`perline=8`).
   - **Featured Projects:** Summaries of TalvoAI, StockSense, and DealFlow360.
   - **GitHub Activity Cards:** Dark theme statistics and top languages cards matching `#0D1117`.
   - **Contribution Snake Animation:** Dynamically rendered snake traversing your contribution activity graph.

---

## 6. Troubleshooting & Notes

- **Snake image shows a broken link or 404:**
  The `README.md` points to `raw.githubusercontent.com/.../output/github-snake-dark.svg`. This path will return 404 until the Actions workflow has completed successfully at least once and created the `output` branch. Follow Step 4 to run it manually.
- **Workflow fails with 403 (Permission denied):**
  Ensure you enabled **Read and write permissions** under **Settings → Actions → General → Workflow permissions** (Step 3).
- **Scheduled workflow delays:**
  GitHub Actions cron schedules can experience queue delays during high server traffic. Manual execution via `workflow_dispatch` can be used whenever immediate updates are desired.
- **Third-Party Services Availability:**
  The typing SVG animation and GitHub stats cards utilize public services (`readme-typing-svg.demolab.com`, `skillicons.dev`, and `github-readme-stats.vercel.app`). All markdown image tags include descriptive `alt` text to ensure accessibility and fallback readability during network latency or maintenance windows.
- **Adding Project Links:**
  As TalvoAI, StockSense, or DealFlow360 repositories are made public, update the markdown bullet points in `README.md` to link directly to their repositories (e.g. `[**TalvoAI**](https://github.com/adityakondekar04/talvoai)`).
