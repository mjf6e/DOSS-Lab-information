# DOSS Lab Directory

A searchable web directory of labs, personnel, equipment, and research interests across the Division of Surgical Sciences at the University of Virginia.

## What's in this repository

```
├── index.html      Self-contained site (HTML + CSS + JS + data all in one file)
├── photos/         Principal Investigator headshots
└── README.md       This file
```

Everything the site needs is in `index.html` and the `photos/` folder. No build step, no server, no dependencies — just static files.

## Deploying to GitHub Pages

1. **Create a new repository** on GitHub (e.g. `doss-labs`). It can be public or private (private requires a paid plan for Pages).
2. **Upload these files** to the repository — either drag-and-drop in the browser or `git push` from the command line.
3. Go to **Settings → Pages** on the repository.
4. Under **Build and deployment**, set the source to **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
5. Wait 30–60 seconds. The site will be published at:

   ```
   https://<your-github-username>.github.io/doss-labs/
   ```

That's it. Any future commit to `main` will re-deploy the site automatically.

### Command-line deployment

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<username>/doss-labs.git
git push -u origin main
```

Then enable Pages as described above.

## Updating the site

### Add or change a PI photo

1. Drop the new photo into the `photos/` folder. Recommended: **JPEG, ~200px tall**, portrait orientation, face in the upper half of the frame.
2. Open `index.html` and find the block near the top that starts with `<script id="site-data" type="application/json">`.
3. In the JSON data, find the lab whose photo you're changing, and update the `"photos"` array to include the new filename (e.g. `"Kibbe_1.jpg"`).
4. Save and push.

### Add or update personnel

Edit the same JSON block inside `index.html`. Each lab has a `"personnel"` array with entries like:

```json
{
  "name": "Xinyu Zhou",
  "assets": "Zeiss Stellaris 5 confocal microscope, …",
  "expertise": "IHC/IF/ICC, advanced microscopy, …",
  "interests": "Cardiac and skeletal muscle biology …"
}
```

Add, remove, or edit entries as needed. The search and directory views will update automatically.

## Local preview

You can double-click `index.html` to preview it in any browser — no server required.

## Features

- **Live search** on the Directory (people) and Equipment pages — as-you-type filtering, matches highlighted in the results
- **Individual lab pages** with PI photo(s), personnel, and equipment
- **Deep-linkable URLs** — e.g. `#/directory?q=vascular` or `#/lab/tsung-lab` can be bookmarked or shared
- **Mobile responsive** — works on phones and tablets
- **No tracking, no cookies, no external services** — pure static HTML

## Credits

- Data source: DOSS Lab Information workbook
- Design & implementation: built for the Division of Surgical Sciences, University of Virginia
- Typography: [Fraunces](https://fonts.google.com/specimen/Fraunces) (display) + [Inter](https://fonts.google.com/specimen/Inter) (body) via Google Fonts
