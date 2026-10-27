# Eagle Mart website

A single-page site for Eagle Mart, apparel manufacturer and exporter, Sialkot, Pakistan.
No build step, no dependencies. Upload the folder and it runs.

## What's in here

```
index.html          the whole site
images/
  logo.webp         the eagle mark, shown in the top bar (square)
  hero.webp         the big photo at the top (tall portrait)
  about.webp        the photo in the About section (tall portrait)
  product-1.webp    product grid photos, 4:5 portrait
  product-2.webp
  product-3.webp
  product-4.webp
  product-5.webp
```

## Putting it online (GitHub Pages)

1. Create a public repository on github.com.
2. Upload `index.html` and the `images` folder, keeping the folder structure.
3. Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`. Save.
4. After a minute your site is at `https://yourusername.github.io/your-repo-name`.

## Swapping a photo

Replace the file in `images/` and keep the same filename. Nothing in `index.html`
needs to change. If you use a different filename, update the matching line in
the catalogue (see below).

Photo guidance:

- **Product photos**: portrait, 4:5 shape, around 800 x 1000 pixels. The page
  crops anything else to 4:5 from the centre, so keep the garment centred.
- **Hero and about photos**: portrait, around 900 x 1400 pixels.
- **Logo**: square, around 500 x 500 pixels.
- Save as `.webp` or `.jpg`, under about 200 KB each, so the page stays fast.

## Adding, removing or reordering products

Open `index.html` and scroll to the bottom. Just above the closing `</body>`
you'll find a block marked **YOUR CATALOGUE**. It looks like this:

```js
var CATALOGUE = [
  {
    image: 'images/product-1.webp',
    alt:   'Rose and white colour-blocked women’s tracksuit, jacket and jogger.',
    name:  'Women’s colour-block tracksuit',
    spec:  'Stand collar, panelled sleeve, tapered jogger. Poly tricot, 240–260 GSM. Sizes XS–XXL.'
  },
  ...
];
```

- **To add a product**: put the photo in `images/`, then copy one `{ ... }` block,
  paste it into the list, and change the four lines. Make sure every block except
  the last one ends with a comma.
- **To remove one**: delete its whole `{ ... }` block.
- **To reorder**: move blocks up or down. The page follows this order.

The four fields are:

| Field   | What it does |
| ------- | ------------ |
| `image` | path to the photo |
| `alt`   | plain description of the photo, read aloud by screen readers and shown if the image fails to load |
| `name`  | the product heading |
| `spec`  | the line of detail under it: construction, fabric, weight, sizes |

Below the catalogue there's a second list, `MADE_TO_ORDER`, for items you produce
but have no photo for yet. It becomes the last tile in the grid. Set
`SHOW_MADE_TO_ORDER = false` to hide that tile.

## Linking to a full catalogue PDF

If you have a catalogue PDF, drop it in the folder as `catalogue.pdf` and change
the "Ask for the full catalogue" link in the `madeToOrder` function from
`href="#contact"` to `href="catalogue.pdf" target="_blank"`.

## Things to check before you promote the site

The trade terms and the fabric table are **placeholders** and need to match what
you actually offer:

- The five figures in the strip under the hero: minimum order, sampling time,
  bulk lead time, terms, shipping origin.
- The whole fabric and weight table in the Specifications section.
- The city, if you are not based in Sialkot. It appears in the page title, the
  hero, the About section, the contact list and the footer.

## Contact details used

Changing any of these means a find-and-replace across `index.html`:

- `eaglemart0040@gmail.com`
- `923187940976` (used in the `wa.me` WhatsApp links)
- `+92 318 7940976` (the displayed version)
- `https://www.instagram.com/eaglemart0040`

The quote form has no server behind it. It opens the visitor's own mail app or
WhatsApp with the details filled in, which is why it works on GitHub Pages.
