# [Web beginnings] — Website Studio

Our shared repo for building websites for clients and selling them. This README explains how we work together so we don't overwrite each other's work, and how a site goes from first message to launched and paid for.

https://xdiv01.github.io/sushi/

## Who we are

| Name | Role | Contact |
|------|------|---------|
| [Tarik Hromo] |
| [Imran Oprasic] |

Roles aren't strict. We both review each other's work.

## What's in this repo

```
.
├── README.md              ← you are here
├── templates/             ← starter sites we reuse (restaurant, barber, portfolio...)
│   └── restaurant/
├── clients/               ← one folder per client
│   └── client-name/
│       ├── index.html
│       ├── assets/        ← logo, photos, fonts (only files we have permission to use)
│       ├── NOTES.md       ← what the client asked for, contact, prices, deadlines
│       └── README.md      ← how to edit and deploy this specific site
├── docs/
│   ├── checklist.md       ← pre-launch checklist (copy of the one below)
│   ├── contract-template.md
│   └── pricing.md
└── .gitignore
```

Most of our sites are plain HTML, CSS and JavaScript in a single folder, so they can be hosted for free almost anywhere. If a project needs a framework, note it in that client's `README.md`.

## Getting started

```bash
git clone [repo-url]
cd [repo-name]
```

Open a site's `index.html` in your browser to preview it. For anything with maps, forms or fonts, preview through a tiny local server so it behaves like the real web:

```bash
cd clients/client-name
python3 -m http.server 8000      # then open http://localhost:8000
```

## How we work in git

**Rule 1: never work directly on `main`.** `main` is always the version that is safe to show or deploy.

**Rule 2: one branch per task.** Name it `type/short-description`:

```
site/new-client-name       ← building a new site
fix/mobile-menu-overflow   ← fixing something
update/client-name-prices  ← client changed content
template/barber-shop       ← new reusable template
```

**Daily flow**

```bash
git checkout main
git pull                          # get the latest first
git checkout -b site/new-client   # start your branch

# ...work...

git add .
git commit -m "Add menu tabs and mobile layout"
git push -u origin site/new-client
```

Then open a **Pull Request** on GitHub. The other person looks it over (see checklist) and merges it. If you're both in a hurry, at least read the diff once before merging.

**Commit messages:** short, present tense, say what changed.
Good: `Fix call button on small phones`. Bad: `stuff`, `final`, `final2`.

**If we both edited the same file** git will flag a conflict when merging. Don't panic. Open the file, keep the right parts, delete the `<<<<<<<` markers, then commit. Talk to each other first so it rarely happens: tell the other person which client you're working on.

## Starting a new client site

1. Copy the closest template: `cp -r templates/restaurant clients/client-name`
2. Create `clients/client-name/NOTES.md` with: business name, contact, what they asked for, price agreed, deadline.
3. Collect the client's real info and put it in. Don't guess at hours, prices, phone numbers or menus. Ask, or get them in writing.
4. Build on a branch, open a PR, get a review.
5. Send the client a preview link and ask for changes in one batch, not piecemeal.

## Permissions and content (important)

We only build and publish sites for clients who have **agreed to it**, and we only use things we're allowed to use.

- Get the client's OK, even a message, before using their name, logo, photos or menu.
- Never use photos, logos, text or fonts we don't have rights to. Use the client's own files, free stock photos with a licence that allows commercial use, or our own.
- Don't invent reviews, ratings or testimonials. Link to real ones or ask the client for approved quotes.
- Don't copy another business's site or branding.
- Never commit passwords, API keys or private customer data. Keep them out of the repo.

## Before a site goes live (checklist)

**Content**
- [ ] Business name, address, phone, hours and prices checked against what the client sent
- [ ] Every phone number, email and link tested
- [ ] Spelling checked in every language on the site
- [ ] Client has approved the final version in writing

**Phones and speed**
- [ ] Looks right on a small phone (about 360px wide), a tablet and a laptop
- [ ] No sideways scrolling
- [ ] Buttons big enough to tap, text readable without zooming
- [ ] Images compressed (aim for well under 300 KB each)
- [ ] Opens fast on mobile data

**Quality**
- [ ] Page title and description set (for Google)
- [ ] Map, menu, and contact buttons work
- [ ] Works in Chrome, Safari and Firefox
- [ ] Keyboard and screen-reader basics: image `alt` text, sensible headings, good contrast

**Launch**
- [ ] Domain points to the site, HTTPS is on
- [ ] Client has the login for their domain and hosting (or we've agreed we manage it)
- [ ] We've saved a copy of the final files in this repo

## Deploying

Easiest free options for static sites:

- **Netlify**: drag the client's folder onto the dashboard, or connect the repo and set the publish folder to `clients/client-name`.
- **Cloudflare Pages** or **GitHub Pages**: also free and simple.

Domains are bought through a registrar (for `.ba` ask the local registrar or the client's host). Put the client's name on the domain account where possible so they own it.

## From first message to getting paid

1. **Enquiry**: ask what they need, who their customers are, and what they have (logo, photos, text).
2. **Quote**: agree scope and price in writing. List what's included (pages, languages, changes) and what costs extra.
3. **Deposit**: take [50%] upfront before starting.
4. **Build**: first preview within [x] days. Allow [2] rounds of changes.
5. **Launch**: final payment, then deploy and hand over.
6. **After**: offer a monthly care plan for updates, hosting and fixes: [price].

Keep a simple written agreement (`docs/contract-template.md`) covering: what we build, price and payment dates, how many changes are included, who owns the domain, who owns the code after payment, and how to cancel.

## Pricing (fill in)

| Package | Includes | Price |
|---------|----------|-------|
| One-page site | Mobile-friendly, contact buttons, map | [ ] KM |
| Business site | Up to 5 sections, menu/services, 2 languages | [ ] KM |
| Care plan | Content updates, hosting help, fixes | [ ] KM / month |

## Git cheat sheet

| I want to... | Command |
|--------------|---------|
| See what changed | `git status` and `git diff` |
| Get the latest code | `git checkout main && git pull` |
| Start a branch | `git checkout -b site/name` |
| Save my work | `git add . && git commit -m "message"` |
| Upload my branch | `git push -u origin site/name` |
| Switch branch | `git checkout branch-name` |
| Undo changes to a file (not yet committed) | `git restore file.html` |
| Undo my last commit but keep the changes | `git reset --soft HEAD~1` |
| See history | `git log --oneline` |

## `.gitignore` suggestion

```
.DS_Store
node_modules/
.env
*.log
*.zip
```

## Useful tools

- Editor: VS Code
- Images: Squoosh (compress), unsplash.com / pexels.com (free photos, check the licence)
- Testing: Chrome DevTools (device toolbar), PageSpeed Insights, WAVE (accessibility)
- Hosting: Netlify, Cloudflare Pages, GitHub Pages
