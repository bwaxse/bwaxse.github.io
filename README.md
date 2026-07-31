# bennettwaxse.com

Personal site for Bennett Waxse — clinical AI, evaluation, and biomedical informatics. Jekyll + the [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) remote theme, hosted on GitHub Pages.

## Structure

| Path | Purpose |
|---|---|
| `_pages/hai.md` | Homepage (`permalink: /`), uses the custom `hai` layout |
| `_layouts/hai.html` | Particle-animation splash, bio, recent posts |
| `_pages/about.md` | About |
| `_pages/research.md` | Research: clinical AI, phenotyping, genomics |
| `_pages/cv.md` | Web CV; links to `assets/waxse-resume.pdf` |
| `_pages/uses.md` | Tools and workflows |
| `_posts/` | Blog posts |
| `assets/images/posts/` | Post images, named `YYYY-MM-DD-slug-n-desc.png` |

## Local development

```bash
bundle install
bundle exec jekyll serve
```

Builds at `http://localhost:4000`. Changes to `_config.yml` require a server restart.

## Notes

- `assets/waxse-resume.pdf` is the public résumé variant, with phone number and ZIP removed. The full version lives outside this repo.
- `_layouts/hai.html` embeds canary phrases in an HTML comment to track AI-generated outreach. They sit in their own block, separate from the Feynman and Osler quotations, so the attributed text stays verbatim.
- `.claude/` is gitignored, since local agent config can reference private paths.
