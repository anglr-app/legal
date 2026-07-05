# Anglr — Legal documents site

Static site hosting the **Privacy Policy** and **Terms & Conditions** for the Anglr
fishing-diary app, in Greek (primary) and English (secondary). Designed to be served from
GitHub Pages and linked from the app's onboarding screen and the app-store listings.

## Structure

```
index.html          Landing page (language + document chooser)
style.css           Shared styling (light/dark aware)
.nojekyll           Serve files as-is (no Jekyll processing)
el/privacy.html     Πολιτική Απορρήτου
el/terms.html       Όροι & Προϋποθέσεις
en/privacy.html     Privacy Policy
en/terms.html       Terms & Conditions
```

Preview locally by opening `index.html` in a browser (double-click). All links are relative.

## BEFORE PUBLISHING — fill in the placeholders

Every document contains two placeholder tokens that MUST be replaced (search & replace
across all five HTML files):

| Token                 | Replace with                                                        |
|-----------------------|---------------------------------------------------------------------|
| `__CONTROLLER_NAME__` | The data controller's full legal name (currently you, as a private individual). |
| `__CONTACT_EMAIL__`   | The dedicated public contact/privacy email (e.g. a Gmail alias).     |

The effective date is set to **5 July 2026** — update it on the day you actually publish.

## Deploy to GitHub Pages

1. Create the repository (public) — for a clean root URL name it `anglr-legal.github.io`.
2. Push these files:
   ```
   git init
   git add .
   git commit -m "Add Anglr legal documents (privacy + terms, EL/EN)"
   git branch -M main
   git remote add origin https://github.com/<org-or-user>/<repo>.git
   git push -u origin main
   ```
3. In the repo: **Settings -> Pages -> Build and deployment -> Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
4. After ~1 minute the site is live. Note the four URLs — they go into the app and the store
   listings:
   - `<base>/el/privacy.html`, `<base>/el/terms.html`
   - `<base>/en/privacy.html`, `<base>/en/terms.html`

## Wire into the app

- Onboarding legal text (`onboarding_name_screen.dart`): the two link taps open the URL that
  matches the app locale, via `url_launcher`. The Copyright link is removed (folded into the
  Terms); drop the `onboarding_name_copyrightPolicy` ARB key and the `{copyright}` placeholder.
- Put the **Privacy Policy** URL into Google Play Console and App Store Connect.

## Legal note

These documents were drafted to reflect what the app actually does, but they are not legal
advice. Have a Greek lawyer review them once, especially before subscriptions/payments go live.
