[README.md](https://github.com/user-attachments/files/31194751/README.md)
# Brick Demolition — website

Two static pages for the App Store listing's **Support URL** and **Marketing URL**.

```
index.html      marketing / product page
support.html    support + FAQ + privacy policy (anchor #privacy)
style.css       shared styles
assets/         app icon and screenshots (~700 KB total)
```

No build step, no dependencies, no external requests — no CDN, no web fonts, no analytics. It uses
the system font stack and works offline. Total page weight is under 1 MB.

---

## Deploying to GitHub Pages

1. Create a repository, e.g. `brick-demolition-site`.
2. Copy the contents of this folder into it (`index.html` at the repo root).
3. Commit and push to `main`.
4. In the repository: **Settings → Pages → Source → Deploy from a branch**, branch `main`, folder
   `/ (root)`. Save.
5. Wait a minute for the first build. Your URLs will be:

```
https://<username>.github.io/brick-demolition-site/
https://<username>.github.io/brick-demolition-site/support.html
```

A user-site repo named `<username>.github.io` serves from the root instead, giving shorter URLs.

---

## What to put in App Store Connect

| Field | URL |
|---|---|
| Support URL *(required)* | `.../support.html` |
| Marketing URL *(optional)* | `.../` |
| Privacy Policy URL *(required)* | `.../support.html#privacy` |

**Your current Support URL is dead.** The live listing points at
`http://web.me.com/nashcraft1/Ashcraft_Iphone_Apps/Brick_Demolition.html` — MobileMe, which Apple
shut down in 2012. It fails to connect. Replacing it is both a review risk removed and a trust
signal gained.

---

## Before you publish

**The contact email is `nashcraft1@gmail.com`,** used in three places on `support.html` (the contact
box and two links). It is your App Store account address, so it was the sensible default — but it
will be on a public page, which invites spam. A dedicated alias such as `support@yourdomain` or a
`+` alias like `nashcraft1+brickdemolition@gmail.com` is worth considering. Search and replace to
change it.

**Check the response-time claim.** The contact box says "Usually within 2–3 days". Change or remove
it if that is not a promise you want to make.

**The privacy policy is accurate as written**, and that was verified rather than assumed: the app
has no Swift Package dependencies, links only Apple frameworks, contains no analytics or advertising
SDKs, and stores only the high score locally in `UserDefaults`. If a third-party SDK is ever added,
the policy must be revised.

The effective date reads 18 August 2026. Update it whenever the policy changes.

---

## Keeping it current

Screenshots are in `assets/`, downscaled to 1200 px wide and saved as JPEG at quality 82. To
refresh them after a visual change, capture at full size and run:

```bash
sips -Z 1200 new-shot.png --out tmp.png && sips -s format jpeg -s formatOptions 82 tmp.png --out assets/shot-1.jpg && rm tmp.png
```

`shot-1.jpg` is the start screen and is the one showing the Game Center Leaderboard button — it was
deliberately re-captured after that feature landed, so it stays consistent with the leaderboard
claims made further up the page.
