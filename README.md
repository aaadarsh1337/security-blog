# security-blog

Personal security writing by **Adarsh Pillai (@aaadarsh1337)** — malware analysis, reverse engineering notes, defensive workflows, and lab experiments.

**Live:** [https://aaadarsh1337.github.io/blog/](https://aaadarsh1337.github.io/blog/)

Source of truth for posts that get rendered into the portfolio site under `/blog/`.

---

## What this is

Public notebook for technical security writing. Not CTF writeups (those live in [ctf-writeups](https://github.com/aaadarsh1337/ctf-writeups)). Focus:

- Malware analysis methodology & notes
- Reverse engineering observations
- Defensive notes and threat-intel takeaways
- Practical experiments from the lab

No live payloads. Analysis-only.

---

## Layout

```text
security-blog/
└── posts/
    └── malware-analysis/
        ├── template.md          # copy this for a new post (draft: true)
        └── your-post.md         # set draft: false to publish
```

The portfolio builder **requires** `posts/` to exist. Posts live under `posts/<category>/`. Root-level files outside `posts/` are ignored.

---

## Writing a new post

1. Copy the template:

```bash
cp posts/malware-analysis/template.md posts/malware-analysis/my-sample.md
```

2. Edit frontmatter — at minimum set `title`, `date`, `summary`, `tags`, and `draft: false`.

3. Push to `main`. The portfolio **Build security blog** workflow rebuilds `/blog/` automatically (see below).

---

## Auto-rebuild

Pushes to `main` that touch `posts/**` fire `.github/workflows/deploy.yml`, which sends a `blog-updated` repository dispatch to `aaadarsh1337/aaadarsh1337.github.io`. That repo’s **Build security blog** workflow then regenerates `/blog/` and commits the output.

**One-time setup** — add a repository secret in this repo:

| Secret | Value |
|--------|--------|
| `PORTFOLIO_DISPATCH_TOKEN` | Classic PAT with `repo` scope (or a fine-grained PAT that can dispatch on the portfolio repo) |

Without the secret, the notify workflow fails with a clear error. Fallback: the portfolio workflow also runs daily (`15 5 * * *`) and can be run manually from **Actions → Build security blog**.

---

## Current posts

_None published yet — add a non-draft post under `posts/`._

---

## Style notes

- Defensive framing first
- Step-by-step methodology over screenshots of payloads
- Short, dense, command-and-reasoning heavy

---

## Related

| Repo / Page | Purpose |
|-------------|---------|
| [aaadarsh1337.github.io](https://github.com/aaadarsh1337/aaadarsh1337.github.io) | Portfolio + live blog |
| [ctf-writeups](https://github.com/aaadarsh1337/ctf-writeups) | Challenge walkthroughs |
| [threat-harbour](https://github.com/aaadarsh1337/threat-harbour) | Live SSH honeypot intel |
| [tryhackme-lab-notes](https://github.com/aaadarsh1337/tryhackme-lab-notes) | Lab artifacts |

---

## Author

**Adarsh Pillai**  
`@aaadarsh1337` · `jackthereaper1337` · `Hasher2009`  
Offensive security · reverse engineering · CTFs  
[Portfolio](https://aaadarsh1337.github.io/) · [GitHub](https://github.com/aaadarsh1337)
