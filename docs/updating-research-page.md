# How to Update the Research Page

The research page on zjelveh.github.io lists your publications and working papers. This document explains how to update it.

## File Location

The research page is located at:
```
_pages/research.md
```

## Page Structure

The file uses standard Markdown with YAML front matter at the top:

```yaml
---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---
```

The content is organized into three sections:
1. **Peer-Reviewed** - Published papers in peer-reviewed journals
2. **Working Papers** - Papers in progress or under review
3. **Other** - Other publications (e.g., AER P&P, workshop papers)

## Entry Format

Each entry follows this format:

```markdown
- [Paper Title](URL_TO_PAPER)
  - **With**: Coauthor1, Coauthor2, and Coauthor3
  - **Abstract**: Abstract text here...
```

If there's no link yet, omit the brackets and URL:
```markdown
- Paper Title
  - **With**: Coauthor1 and Coauthor2
  - **Abstract**: Abstract text here...
```

### Important Formatting Notes

1. **Indentation**: Use 2 spaces for sub-items (With, Abstract)
2. **Links**: Use Markdown link format `[Title](URL)`
3. **Journal names**: Use italics with asterisks: `*Journal Name*`
4. **Working paper versions**: Add a separate line for working paper links:
   ```markdown
   - [Paper Title](published_url) (*Journal Name*, Year)
     - [Working Paper Version](working_paper_url)
     - **With**: ...
   ```

## Adding a New Entry

1. Open `_pages/research.md` in a text editor
2. Find the appropriate section (Peer-Reviewed, Working Papers, or Other)
3. Add a new entry following the format above
4. Entries within each section appear in the order listed (typically newest first)

## Moving a Paper from Working Papers to Peer-Reviewed

When a working paper gets accepted:
1. Remove the entry from the "Working Papers" section
2. Add it to the "Peer-Reviewed" section with the journal name and year
3. Optionally keep a link to the working paper version

## Example: Updating an Existing Entry

Before (working paper):
```markdown
- Paper Title
  - **With**: Coauthor1 and Coauthor2
  - **Abstract**: Old abstract...
```

After (now published):
```markdown
- [Paper Title](https://journal.com/paper) (*Journal Name*, 2025)
  - [Working Paper Version](https://ssrn.com/paper)
  - **With**: Coauthor1 and Coauthor2
  - **Abstract**: Updated abstract...
```

## Previewing Changes Locally

If you have Jekyll installed, you can preview changes locally:
```bash
cd ~/Dropbox/zjelveh.github.io
bundle exec jekyll serve
```
Then visit http://localhost:4000/research/

## Deploying Changes

The site is hosted on GitHub Pages. To deploy:
```bash
cd ~/Dropbox/zjelveh.github.io
git add _pages/research.md
git commit -m "Update research page"
git push
```

Changes typically appear on the live site within a few minutes.
