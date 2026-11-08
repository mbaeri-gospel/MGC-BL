# MGC-BOOK-LAB — Manual Library Edition

A static, responsive PDF library designed for GitHub Pages. The original dark-purple visual design and the five supplied PDF resources are preserved.

## What's included

- Search across resource titles, descriptions and categories.
- Category filters generated automatically from the resource cards.
- Read-online and download links for each PDF.
- Responsive layout for desktop, tablet and mobile.
- No database, server, build step, or admin account required.
- Five existing MG-FINTECH and PROJORA PDFs.

## Add a PDF resource manually

1. Open the `mgc-book-lab` folder on your computer.
2. Copy your PDF into `documents/`. You may create a descriptive subfolder, for example `documents/artificial-intelligence/`.
3. Open `index.html` in a code editor (VS Code, Notepad++, or another plain-text editor).
4. Find the `documentGrid` section and the large comment beginning `ADD A NEW RESOURCE`.
5. Copy the example `<article class="card"> ... </article>` from inside that comment and paste it immediately above the `emptyState` element.
6. Replace all example values:
   - `data-title`: resource title used by search.
   - `data-category`: category used by the automatic filter.
   - `data-description`: short searchable description.
   - The visible category, heading and description text.
   - Both `href` values with the relative path to your PDF.
7. Save `index.html` and open it in a browser to test the new card, category, search, read and download links.

### Example

If the file is `documents/artificial-intelligence/AI-Mastery-Guide.pdf`, use this path in **both** links:

```html
href="documents/artificial-intelligence/AI-Mastery-Guide.pdf"
```

Use forward slashes (`/`) in paths, even on Windows. File and folder names are case-sensitive after deployment on GitHub Pages. Avoid special characters in filenames; prefer letters, numbers, hyphens and underscores.

## Add a category

You do not need to edit the filter buttons. Simply give a new resource card a new category name in `data-category`, for example:

```html
data-category="Artificial Intelligence"
```

Use exactly the same category text in the card's visible `<div class="category">` label. The filter button and category count are generated automatically from the cards when the page loads. To rename a category, update the `data-category` and visible label on every card in that category.

## Add a cover image (optional)

1. Put the image in `covers/`, for example `covers/AI-Mastery-Guide.jpg`.
2. Replace the card's gradient cover block with:

```html
<div class="cover">
  <span class="format">PDF</span>
  <img src="covers/AI-Mastery-Guide.jpg"
       alt="AI Mastery Guide cover"
       style="width:100%;height:100%;object-fit:cover;position:absolute;inset:0;">
</div>
```

## Deploy or update on GitHub Pages

1. Extract this ZIP.
2. Upload the **contents** of the `mgc-book-lab` folder to the root of your GitHub repository (so `index.html` is at the repository root).
3. Commit the changes to your publishing branch.
4. In GitHub, open **Settings → Pages** and select **Deploy from a branch**, your branch (commonly `main`), and `/(root)`.
5. Save and wait for the Pages deployment to finish.

For later updates, upload the changed `index.html` and new/updated files in `documents/` or `covers/`, then commit.

## Important privacy and hosting note

“Private management” means only you edit the files through your local computer and your GitHub account; this static site has no public admin panel. It does **not** make the published library private. GitHub Pages is public-facing hosting: anyone with the site URL can view and download published PDFs. Do not publish confidential, personal, copyrighted or otherwise restricted documents unless you have the rights and intend them to be public.

## Troubleshooting

- A PDF link fails: check the exact filename, capitalization and relative path; ensure the PDF was committed to GitHub.
- A category is missing: confirm the card has a non-empty `data-category` value and that its card markup is inside `#documentGrid`.
- A card does not appear: check that the new `<article>` is not inside the HTML comment and is placed before the `emptyState` element.
- GitHub Pages shows an old version: confirm the latest commit and check the Pages deployment status; refresh after deployment completes.

## Five-language interface

The library interface includes a language selector for:

- English (`en`)
- French (`fr`)
- German (`de`)
- Spanish (`es`)
- Simplified Chinese (`zh`)

Choose a language from the selector in the top navigation. The navigation, headings, search placeholder, category labels, resource descriptions, read/download actions, result count, empty-state message and about section are translated. The five supplied PDF files themselves are not translated; the language selector changes the website interface and the catalogue text only. Product and project names such as MG-FINTECH and PROJORA remain unchanged.

### Translate a resource you add later

New manual resource cards are displayed in English by default. To translate a new card too:

1. Give the card a unique identifier, for example `data-resource-id="my-new-guide"`.
2. Add that identifier to the `resourceTranslations` object in the script, under `fr`, `de`, `es` and `zh`.
3. For each language, provide an array in this order: `[translated title, translated category, translated description]`.
4. If the new category is shared by multiple resources, add its English-to-translated category name to `categoryTranslations` for each language. The card-specific category translation takes priority.
5. Save and test all five language choices.

Example entry (add the same ID to the card's `data-resource-id`):

```js
fr: {
  "my-new-guide": ["Titre traduit", "Catégorie traduite", "Description traduite"]
}
```

The PDF filenames and links do not change when visitors switch languages. The language selector does not translate the contents of the PDF files.


## Branding and curator profile
- The site brand is **MGC-BL**. Its SVG logo is `favicon.svg`, also used as the browser favicon.
- The curator portrait is `covers/mbaeri-gospel-chinomso.webp`; the name displayed below it is **Mbaeri Gospel Chinomso**.
- To replace the portrait later, overwrite that image file with your new portrait using the same filename, or update the image `src` in `index.html`.
