# Eagle Mart website

A single-page site for Eagle Mart, apparel manufacturer and exporter, Sialkot, Pakistan.
No build step, no dependencies, nothing to install.

**Product photos load straight from a folder.** Put a picture in
`images/products` and it appears on the site. You don't edit any code.

## What's in here

```
index.html            the whole site
image-list.json       a list of your pictures, kept up to date for you
images/
  logo.*              the mark in the top bar (square)
  hero.*              the big photo at the top (tall portrait)
  about.*             the photo in the About section (tall portrait)
  products/           every photo in here shows in the product grid
.github/              the small job that keeps image-list.json current
README.md             this file
```

## Putting it online (GitHub Pages)

1. Create a **public** repository on github.com.
2. Upload everything in this folder, keeping the folder structure. The easiest
   way is GitHub's **Add file → Upload files**, then drag the whole folder in.
3. Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder
   `/ (root)`. Save.
4. After a minute your site is live at
   `https://yourusername.github.io/your-repo-name`.

## Adding a product

1. Go to `images/products` in your repository.
2. **Add file → Upload files**, drag your photo in, commit.
3. Refresh the site. The product is there.

That's it. Removing a photo removes the product. There's no list to keep in sync.

### The filename becomes the product name

| Filename | Shows as |
| --- | --- |
| `Navy Bomber Jacket.jpg` | **Navy Bomber Jacket** |
| `03 Navy Bomber Jacket.jpg` | **Navy Bomber Jacket** — the `03` only sets the position in the grid |
| `03 Navy Bomber Jacket__Poly twill 260 GSM. Sizes S-3XL.jpg` | **Navy Bomber Jacket** with the detail line underneath |

Two underscores `__` separate the name from the detail line. Both parts are
optional extras — a plain filename works fine on its own.

Products are sorted by filename, so numbering them `01`, `02`, `03` gives you
full control of the order. Leave the numbers off and they sort alphabetically.

### Formats and sizes

`jpg`, `jpeg`, `png`, `webp`, `gif`, `avif`, `bmp` and `svg` all work.

One catch: iPhone photos saved as **`.heic` will not display in any browser**.
Set your phone's camera format to *Most Compatible* (Settings → Camera →
Formats), or convert the files to jpg before uploading.

For the best result, product photos should be portrait at roughly 4:5
(about 800 × 1000 pixels) with the garment centred — the page crops anything
else to 4:5 from the middle. Keep each file under about 300 KB so the page
stays quick. Hero and about photos look best as taller portraits, around
900 × 1400.

### Changing the hero, about or logo photo

Drop a file named `hero`, `about` or `logo` into `images/` with any extension
you like — `hero.jpg`, `hero.png`, `hero.webp` all work. If one is already
there, delete the old one so there's only one file per name.

## The text tile at the end of the grid

The last tile lists things you make but have no photo for yet. To change it,
open `index.html`, scroll to the bottom and edit the `MADE_TO_ORDER` list.
Set `SHOW_MADE_TO_ORDER = false` to hide that tile.

## If you move to your own domain

The site works out which repository it's in from the `github.io` address. On a
custom domain like `eaglemart.com` it can't do that, so open `index.html`,
scroll to the bottom, and fill in these two lines once:

```js
var GITHUB_USER = 'yourusername';
var GITHUB_REPO = 'your-repo-name';
```

## Things to check before you promote the site

The trade terms and the fabric table are **placeholders** and need to match
what you actually offer:

- The five figures in the strip under the hero: minimum order, sampling time,
  bulk lead time, terms, shipping origin.
- The whole fabric and weight table in the Specifications section.
- The city, if you are not based in Sialkot. It appears in the page title,
  the hero, the About section, the contact list and the footer.

## Contact details used

Changing any of these means a find-and-replace across `index.html`:

- `eaglemart0040@gmail.com`
- `923187940976` (inside the `wa.me` WhatsApp links)
- `+92 318 7940976` (the displayed version)
- `https://www.instagram.com/eaglemart0040`

The quote form has no server behind it. It opens the visitor's own mail app or
WhatsApp with their details filled in, which is why it works on GitHub Pages.

## How the folder reading works, briefly

The page asks GitHub's public API what files are in `images/products` and builds
the grid from the answer. No key or account setup is needed for a public
repository. If that call is ever unavailable, the page falls back to
`image-list.json`, which the included GitHub Action regenerates every time you
upload a photo. You don't have to do anything for either of these.
