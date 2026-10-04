# Shopify Store Skills

Five free [Agent Skills](https://agentskills.io) for Shopify store owners. Each one does a single store chore from start to finish and gives you something you can paste or import into Shopify without editing.

They work in Claude Code, claude.ai and any other agent that reads `SKILL.md` files. The helper scripts are plain Python 3 with no extra packages.

| Skill | Give it | You get |
|---|---|---|
| [shopify-alt-text-writer](skills/shopify-alt-text-writer) | Your store URL, a product URL, or your product export CSV | Alt text for every product image, written while looking at the photo. Comes as a Shopify import CSV, a review sheet, and a paste-by-hand list for products with variant images |
| [shopify-policy-checker](skills/shopify-policy-checker) | Your store URL | A scored audit of your refund, shipping, privacy, terms and contact policies. It flags missing items and contradictions with your FAQ and banners, and gives fixes you can paste |
| [product-title-cleaner](skills/product-title-cleaner) | Your store, a collection URL, or a product export CSV | One consistent title pattern across your catalogue, as a `URL handle,Title` import CSV (changed rows only). It never creates duplicate titles |
| [agent-ready-quick-check](skills/agent-ready-quick-check) | Your store URL | A 6-check scorecard of how well AI shopping agents (ChatGPT, Perplexity, Gemini, Copilot, Claude) can read your store. Each check is compared with 99 Shopify stores we audited in October 2026 |
| [review-reply-drafter](skills/review-reply-drafter) | Your reviews (pasted, CSV, or a public review page) | A reply for each review, matched to its tone. It never promises refunds you didn't approve, and it flags reviews that need you personally |

## Before and after

These come from real test runs on public Shopify stores. Product names are changed or removed.

**Alt text** (checked against the photo)

| Before | After |
|---|---|
| *(empty)* | `Sole of the dusty pink women's flip flop, with a pattern of concentric oval grooves` |
| `Product mockup` (the same on all 8 photos) | `Back of the oversized t-shirt in Faded Bone, with a blackletter slogan print across the shoulders` |

**Product titles**

| Before | After | Fix |
|---|---|---|
| `Dark Roast, Cold Brew Coffee, Oat Milk` | `Dark Roast Cold Brew Coffee - Oat Milk` | one separator |
| `House Blend Coffee (12oz Ground)` | `House Blend Ground Coffee (12 oz)` | word order, unit format |
| `Born To Roam Tee` | `Born to Roam Tee` | title case |

**Policy check** (paraphrased)

- **Found:** the refund window "usually" applies and depends on the payment processor. Product pages promise "no questions asked", but the policy excludes items that aren't in their original condition.
- **Fix:** one clear window, written as text you can paste, with blanks only for facts the owner must fill in.

**AI-agent quick check** (an outdoor-apparel store)

- **Your store passes 2 of 6.** The median store in our 99-store study passes 3 of 6.
- **Shipping & returns in structured data:** a gap. 0 of 5 product pages have it, and only 12% of study stores pass.
- **Star rating:** a gap. It loads only by JavaScript, so agents reading the page don't see it.

**Review reply**

- **Review:** "…1/3 of the product had leaked into the packaging during shipping. Good product. Poor packaging."
- **Reply:** "[Name], we're sorry your cologne arrived with about a third of it leaked into the packaging. Glad the scent itself still won you over. Email [support email] with your order number and a photo, and we'll [REMEDY: replacement / refund / store credit; owner to choose]."

## Install

**Claude Code** (plugin marketplace):
```
/plugin marketplace add proskillpacks/shopify-store-skills
/plugin install store-owner-free-skills@proskillpacks
```

**skills.sh** (Claude Code, Codex, Cursor, Gemini CLI and other SKILL.md agents):
```
npx skills add proskillpacks/shopify-store-skills
```

**claude.ai:**
1. Download one folder from `skills/` and zip it, so the zip contains the folder itself.
2. Go to Settings > Capabilities > Skills > Upload.
3. For the alt text writer and the title cleaner, attach your product export CSV (Shopify admin > Products > Export) to your request.

**Manual:**
```
git clone https://github.com/proskillpacks/shopify-store-skills
cp -r shopify-store-skills/skills/* ~/.claude/skills/
```

Then ask in plain words, for example:
- *"Check the store policies on mystore.com"*
- *"Write alt text for my product images"*
- *"Clean up my product titles and give me an import CSV"*
- *"Draft replies to these reviews"*
- *"Is my store ready for AI shopping agents? mystore.com"*

## How we test

We run every skill on real public Shopify stores, using their public product data, policy pages and reviews. We never use invented data. We score each run against a written rubric and keep fixing the skill until every test scores at least 8/10.

Nothing here posts or changes anything in your store. You review the output and apply it yourself.

## More skills

These five are free under the MIT licence. If they save you time, the paid **Store Ops Pack** for Shopify store owners has six more:
- an AI-agent readiness audit for your store
- a product description rewriter
- an SEO fixer that does a full SEO pass, including collection pages
- support macros
- chargeback responses
- a BFCM campaign kit

Get it at https://proskillpacks.gumroad.com.

Made by **Pro Skill Packs**. Updates on X: [@KaiVenturaBuild](https://x.com/KaiVenturaBuild). Found a wrong output? Open an issue with the input you used and what went wrong.

Not affiliated with or endorsed by Shopify Inc. Shopify is a trademark of Shopify Inc.

## License

MIT
