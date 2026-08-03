# DOSS Lab Directory

A searchable web directory of labs, personnel, equipment, and research interests across the Division of Surgical Sciences at the University of Virginia.

## What's in this repository

Everything is in a single file: **`index.html`**. It contains the site's HTML, CSS, JavaScript, data, and all 15 PI photos embedded directly. No separate folders, no external dependencies, no build step.

## Deploying to GitHub Pages

1. **Create a new repository** on GitHub (e.g. `doss-labs`).
2. **Upload `index.html`** — drag it into the repository, or use the command line (see below).
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set the source to **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
5. Wait 30–60 seconds. Your site will be published at:

   ```
   https://<your-github-username>.github.io/doss-labs/
   ```

That's it. Any future commit to `main` will re-deploy the site automatically.

### Command-line deployment

```bash
git init
git add index.html README.md
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<username>/doss-labs.git
git push -u origin main
```

Then enable Pages as described above.

## Local preview

Double-click `index.html` to open it in any browser — no server required. Everything works from `file://`.

## Updating the site

All content (labs, personnel, equipment references, and photos) lives inside `index.html`. Two ways to update:

### Quick edit for personnel data

Open `index.html` in a text editor and search for `"site-data"`. Right after that tag is a big JSON block with all lab data. Each lab has a `"personnel"` array — add, remove, or edit entries there, save, commit, push.

### Updating a PI photo

Photos are embedded as **base64 data URIs** inside the JSON block (you'll see long strings that start with `data:image/jpeg;base64,`). To change one:

1. Open a terminal and run:
   ```bash
   base64 -i new-photo.jpg -o photo.txt
   ```
   (On macOS: `base64 -i new-photo.jpg > photo.txt`)

2. Open `photo.txt` and copy its contents.
3. In `index.html`, find the lab's `"photos"` entry and replace the existing base64 string with your new one. The format is:
   ```
   "photos": ["data:image/jpeg;base64,PASTE_YOUR_BASE64_HERE"]
   ```
4. Save, commit, push.

**Tip:** Photos should be resized to roughly 200px tall before encoding to keep the file size reasonable.

## Features

- **Live search** on the Directory (people) and Equipment pages — as-you-type filtering, matches highlighted
- **Individual lab pages** with PI photo(s) and personnel listings
- **Deep-linkable URLs** — e.g. `#/directory?q=vascular` or `#/lab/tsung-lab` can be bookmarked or shared
- **Mobile responsive** — works on phones and tablets
- **No tracking, no cookies, no external services** — pure static HTML

## Credits

Built for the Division of Surgical Sciences, University of Virginia. Typography via [Fraunces](https://fonts.google.com/specimen/Fraunces) and [Inter](https://fonts.google.com/specimen/Inter) from Google Fonts.
