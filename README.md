# Literary Voyage — app files

Map the books you've read, watch a bookworm crawl your reading year, and share your year in books.

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `countries-110m.json` | World map shapes |
| `manifest.json` | Lets phones install it like an app (name, icon, colours) |
| `sw.js` | Keeps the app working offline |
| `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` | App icons |

## How it differs from the Claude version

- **Book lookups are free, with no AI:** [Open Library](https://openlibrary.org) finds the book (author, year, pages, genre), and [Wikidata](https://www.wikidata.org) finds where the story is set. If no setting is found, the author's country is used. If neither is found, the reader picks the country from a list.
- **Scan** reads the barcode (ISBN) on the back of the book. Cover photos aren't supported.
- **Books are saved on the reader's own phone** (in the browser). There are no accounts yet.
- **Sharing:** on phones, Share opens the real share sheet with the video attached, so readers can pick Instagram, TikTok, WhatsApp and so on. On computers, the video downloads.

## Step 1: put it online (free, about 10 minutes)

### Option A: Netlify Drop (easiest)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. You get a link like `https://something.netlify.app`. Sign up (free) to keep it and rename it.

### Option B: GitHub Pages
1. Create a new public repository, for example `literary-voyage`.
2. Upload all the files in this folder.
3. Go to Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/root`.
4. Your app is at `https://YOUR-USERNAME.github.io/literary-voyage/`.

## Step 2: install it on a phone

- **iPhone (Safari):** open the link → Share button → **Add to Home Screen**.
- **Android (Chrome):** open the link → menu ⋮ → **Install app**.

It opens full-screen with its own icon, like a normal app.

## Step 3: App Store and Google Play (when you're ready)

The same files can be wrapped as a store app with **Capacitor** (free, by Ionic):

```bash
npm init -y
npm install @capacitor/core @capacitor/cli @capacitor/ios @capacitor/android
npx cap init "Literary Voyage" com.yourname.literaryvoyage --web-dir=www
mkdir www && cp index.html countries-110m.json manifest.json sw.js icon-*.png www/
npx cap add ios && npx cap add android
npx cap open ios      # opens Xcode (needs a Mac)
npx cap open android  # opens Android Studio
```

What you'll need:
- **Apple Developer Program:** US$99 a year, plus a Mac with Xcode, to publish on the App Store.
- **Google Play Console:** US$25 one-time, to publish on Google Play.
- A **privacy policy** page: the app keeps books on the device and sends only book titles to Open Library and Wikidata.

## Ideas for the paid version later

- Accounts and syncing across devices (for example Supabase or Firebase)
- AI lookups for hard-to-find settings (needs a small server to keep the API key private)
- Past years, extra passport covers, and the one-tap "Share to Instagram Stories" that native apps can do
