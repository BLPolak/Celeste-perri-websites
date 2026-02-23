# Celeste Perri Websites — Project Context

## Repo
`BLPolak/Celeste-perri-websites` on GitHub.

## Sites in this repo

| Domain | Folder | Language | Notes |
|--------|--------|----------|-------|
| celesteperri.com | `/` (root) | English | Placeholder page |
| celesteperri.nl | `nl/` | Dutch (default) + EN toggle | Same design, language toggle top-right |

## Repo structure
```
/
├── index.html          # .com site (English)
├── celeste-bg.jpeg     # Shared background photo
├── nl/
│   ├── index.html      # .nl site (Dutch + EN toggle)
│   └── celeste-bg.jpeg # Copy of background photo for .nl deploy
└── .github/workflows/
    └── deploy.yml      # Deploys both sites on push to main
```

## Deploy workflow
- Trigger: push to `main` branch, or manually via Actions → Run workflow
- Two steps: Deploy .com site (English), Deploy .nl site (Dutch)
- FTP server: `194.213.127.95` (mijndomein.nl, Plesk)
- `.com` uses secrets `FTP_USERNAME` / `FTP_PASSWORD`
- `.nl` uses secrets `FTP_USERNAME_NL` / `FTP_PASSWORD_NL` (FTP account: `f_000add8b`)
- `.com` deploys repo root (excluding `nl/`, `.git/`, `.github/`) → `/httpdocs/`
- `.nl` deploys `nl/` folder → `/httpdocs/` (on the `.nl` FTP account's root)

## Git / PR flow
- I (Claude) cannot push directly to `main` — pushes are blocked by design
- Workflow: I make changes → push to a `claude/` branch → you merge the PR on GitHub → deploy fires automatically
- Branch names follow the pattern: `claude/<description>-<session-id>`

## Design conventions
- Fonts: Cormorant Garamond (headings, italic), Jost (body/labels) via Google Fonts
- Colours: cream `#f5f1eb`, ink `#1a1814`, muted `#8a8680`, accent `#c8a96e`
- Subtle background photo at 12% opacity with cream fade top/bottom
- Grain overlay (SVG noise)
- Minimal, elegant aesthetic — no heavy UI elements

## Other domains on the same hosting account
The following domains exist on mijndomein.nl but are managed in separate repos:
- `inaugust.nl`
- `inaugustbook.com`
- `polak.amsterdam`
