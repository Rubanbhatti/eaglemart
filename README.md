# Eagle Mart website

A single-page B2B site for Eagle Mart, apparel manufacturer and exporter,
Sialkot, Pakistan. No build step, no dependencies, nothing to install.

**You never type a product name.** Drop photos into a folder and the page
gives each product a style code automatically: EM-001, EM-002, EM-003.

## Adding a product

1. In your repository go to `images/products`.
2. **Add file → Upload files**, then type the folder in the file name box,
   for example `07/front.jpg`, and drag the photo in. Add the second photo
   as `07/back.jpg`. Commit.
3. Refresh the site. The product is there as **EM-007**, and hovering the
   photo shows the back.

Rules, all of them:

- **One folder per product.** The folder's position sets the order on the
  page and the style code.
- **First photo = front, second = back.** Sorted by filename, so `1.jpg`
  and `2.jpg` works. If a filename contains the word `front` or `back`,
  that wins regardless of order.
- **One photo is fine.** The card just won't flip.
- **Three or more** all show in the large pop-up view.

### Category filter (optional)

Put a word after the number in the folder name and it becomes a category
label on the card, with filter buttons above the grid:

```
images/products/01 Tracksuits/
images/products/05 Jackets/
images/products/06 Hoodies/
```

The filter buttons only appear once you have two or more categories.

### Don't want folders?

Drop photos loose into `images/products` instead. They pair up two at a
time in filename order — first is front, second is back. Upload them in
pairs and it works out.

### Changing the style code prefix

Open `index.html`, find `var STYLE_PREFIX = 'EM-';` near the bottom and
change it. `EM-001` becomes whatever you set.

## The three fixed photos

Drop these into `images/` with any extension:

| File | Where it shows | Shape |
| --- | --- | --- |
| `logo.*` | top bar | square, about 500 × 500 |
| `hero.*` | the big photo at the top | tall portrait, about 900 × 1400 |
| `about.*` | the About section | tall portrait |

Delete the old one so there's only one file per name.

## Formats

`jpg`, `jpeg`, `png`, `webp`, `gif`, `avif`, `bmp` and `svg` all display.

**`.heic` does not work in any browser.** If you shoot on iPhone, set
Settings → Camera → Formats to *Most Compatible* before your next shoot,
or convert the files to jpg first.

Product photos look best portrait at 4:5 (about 800 × 1000 pixels) with the
garment centred — the page crops anything else to 4:5 from the middle. Keep
each file under about 300 KB so the page stays quick.

## What's on the page

- Hero, trade terms strip, and a scrolling capabilities band
- Product grid with front/back flip, category filter, and a pop-up viewer
  with arrow keys and swipe
- **Add to enquiry** on each product. Buyers tick the styles they want; the
  selection follows them to the quote form and into the email or WhatsApp
  message. It survives a page refresh.
- Private label and OEM capabilities
- Four-stage ordering process
- Size chart with a centimetres / inches switch
- Fabric and weight reference table
- Shipping routes and incoterms
- FAQ
- About, contact details, and a quote form that opens the visitor's own
  mail app or WhatsApp

## Putting it online (GitHub Pages)

1. Create a **public** repository on github.com.
2. Upload everything in this folder, keeping the structure.
3. Settings → Pages → Source: *Deploy from a branch*, branch `main`,
   folder `/ (root)`. Save.
4. After a minute the site is live at
   `https://yourusername.github.io/your-repo-name`.

The repository must be public for the page to read its own image folder.

On a custom domain like `eaglemart.com` the page can't work out which
repository it belongs to, so fill in these two lines in `index.html` once:

```js
var GITHUB_USER = 'yourusername';
var GITHUB_REPO = 'your-repo-name';
```

## Things to correct before you promote the site

These are **placeholders I wrote as plausible industry defaults**. They need
to match what you actually offer:

- The five figures in the strip under the hero: minimum order, sampling
  time, bulk lead time, incoterms, shipping origin.
- The **size chart** in the Sizing section. Measure your own block and put
  your real numbers in. Buyers order against this.
- The **fabric and weight table** in the Fabrics section.
- The **shipping routes table**: transit times and ports.
- The **FAQ answers**, especially the payment terms and the MOQ.
- The city, if you are not based in Sialkot. It appears in the page title,
  the hero, the About section, the contact list and the footer.

## Contact details used

Find and replace these in `index.html` if any change:

- `eaglemart0040@gmail.com`
- `923187940976` (inside the `wa.me` WhatsApp links)
- `+92 318 7940976` (the displayed version)
- `https://www.instagram.com/eaglemart0040`

## How the folder reading works

The page asks GitHub's public API what's inside `images/products` and builds
the grid from the answer. No key or setup needed for a public repository.
If that call is ever unavailable it falls back to `image-list.json`, which
the included GitHub Action regenerates every time you upload a photo. Both
run themselves.
