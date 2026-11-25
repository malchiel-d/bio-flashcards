# Grade 12 Biology – Unit 1 & 2 Test (PWA)

A dark-mode quiz that runs offline once installed. Answer every question correctly in a row –
a wrong answer (or revealing the answer) sends you back to Question 1. Answer options are
shuffled every time a question opens.

No build step: it's plain static files.

```
index.html             the app
questions.js           the 115 questions (edit this to change content)
manifest.webmanifest   install info (name, icons, colours)
sw.js                  service worker (offline support)
vercel.json            headers for Vercel
icons/                 app icons
```

## Deploy: GitHub → Vercel

1. **Put it on GitHub**
   ```bash
   cd bio-flashcards-pwa
   git init
   git add .
   git commit -m "Bio test PWA"
   git branch -M main
   git remote add origin https://github.com/<your-username>/bio-flashcards.git
   git push -u origin main
   ```
   (Create the empty repo on github.com first.)

2. **Import into Vercel**
   - Go to https://vercel.com/new and pick the GitHub repo.
   - Framework Preset: **Other**. Leave Build Command and Output Directory empty.
   - Click **Deploy**. You'll get a `https://<name>.vercel.app` URL.

3. **Install it**
   - **iPhone (Safari):** Share → *Add to Home Screen*.
   - **Android (Chrome):** menu → *Install app* / *Add to Home screen*.
   - **Desktop (Chrome/Edge):** install icon in the address bar.

Open it once online so it can cache itself; after that it works offline.

## Updating

Edit `questions.js` or `index.html`, then **bump `VERSION` in `sw.js`** (e.g. `v1` → `v2`),
commit and push. Vercel redeploys automatically and installed copies pick up the new version
the next time they're opened online.

## Notes

- "Furthest question reached" is stored in the browser's localStorage on each device.
- To test locally: `npx serve .` (service workers need `http://localhost` or HTTPS).
