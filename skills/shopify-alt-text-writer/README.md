# shopify-alt-text-writer

A free Agent Skill that writes alt text for your Shopify product images. It **looks at each photo** and describes what's actually in it: the angle, the detail, the colour, the model. Then it gives you a CSV you can import into Shopify.

Give it a store URL, a product URL, or your product export CSV (Products > Export). That's all it needs.

## Why

- Screen-reader users hear alt text in place of your product photos. Blank, or "IMG_4471", tells them nothing.
- Search engines use alt text to understand images.
- Many stores have none. Others have the product title or the file name repeated on every photo.
- Shopify's public `/products.json` doesn't include alt text, so you can't easily see the problem. This skill checks each product's real alt text first.

## What you get

- Alt text for each image: 60–125 characters, product name once, colour or variant, and what this specific photo shows. No "image of", no keyword stuffing.
- It keeps good existing alt text and redoes weak ones (blank, title only, file name, or the same text on several photos). Facts worth keeping, like "Model is 5'10", wearing size S", are kept.
- `<store>-alt-text-shopify-import.csv` uses Shopify's own column names (`URL handle, Title, Product image URL, Image position, Image alt text`).
- `<store>-alt-text-review.csv` shows old vs new for every image.
- `<store>-alt-text-paste-by-hand.csv` for products with variant images (where the photo changes per colour), where pasting in the admin is safer than a CSV import.
- Safe-apply steps: back up first, then test on one product.
- Big catalogs run in batches of about 40 images. It tells you exactly how far it got.

## Before / after (real tests, 2026-10-03; store and product names removed)

| Photo | Before | After |
|---|---|---|
| Flip flop, back (a large DTC footwear brand) | *(empty)* | `Back of the dusty pink women's flip flop with the brand logo embossed on the heel` |
| Flip flop, sole (same store) | *(empty)* | `Sole of the dusty pink women's flip flop, with a pattern of concentric oval grooves` |
| Lip stain how-to (a cosmetics brand) | *(empty)* | `Peel-off lip stain how-to on a model's lips: 1 line with the stain, 2 peel it off, 3 shine with gloss` |

We checked each "after" against the actual photo.

## Install

- **Claude Code:** copy this folder to `~/.claude/skills/shopify-alt-text-writer/`, then ask: *"Write alt text for the product images on mystore.com"*.
- **claude.ai:** zip this folder, then go to Settings > Capabilities > Skills > Upload. Then upload your product export CSV with the request. If the sandbox can't download your photos, it writes from your product data and tells you so.
- The helper script is Python 3, standard library only. Without a shell, the skill fetches product data and photos directly, for up to about 10 products per run.

## Limits

- It describes what it can see and what your product data says. It won't invent materials or features.
- Importing alt text by CSV re-imports your images. Test on one product first. For products with variant images (the photo changes per colour), paste the alt text by hand. The skill lists those products for you.

---

Made by Kai Ventura. We tested this skill on real public Shopify stores before release.

The paid **Store Ops Pack** for Shopify store owners (AI-agent readiness audit for your store, product description rewriter, SEO fixer with collection pages, support macros, chargeback responses, BFCM campaign kit) is here: https://venturekaizen.gumroad.com

Not affiliated with Shopify Inc.
