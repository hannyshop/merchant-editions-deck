---
name: merchant-editions-deck
description: Create merchant-specific Shopify Editions decks from a source template, including 15 relevant features and plain-English speaker notes. Use when asked to summarise Shopify Editions for a merchant, recreate an Editions deck, tailor a Google Slides deck, or add notes explaining what features do and why they matter.
---

# Merchant Editions Deck

Use this skill when you are asked for a merchant-specific Shopify Editions summary or deck, especially requests like:

- “summarise the best features from latest Shopify Editions for [merchant]”
- “recreate this deck highlighting 15 relevant features”
- “add dummies notes to the slides”
- “make this bespoke to a merchant”

## Standard inputs

Default sources unless the user says otherwise:

- Editions source: `https://www.shopify.com/editions/spring2026`
- Merchant-facing cheat sheet: `https://editions-cheatsheet-hannah.quick.shopify.io`
- Source deck template: `https://docs.google.com/presentation/d/1lx-Z7ic7YG4RJttKC0dsX5-HLQ0l5oyA6hhvWF_e-Bk/edit`

## Mandatory rules

1. **Never modify the source deck.** Always copy it first with Drive `files.copy`.
2. **Always tailor to the merchant’s actual business model.** Do quick merchant research first: live site, web search, known account context, or user-provided context.
3. **Always add speaker notes when requested. If the user asks for “dummies notes”, make them plain-English and merchant-specific.** Notes should be simple enough for a non-product person to use live.
4. **Keep the final deck practical.** Aim for intro + contents + summary + section dividers + 15 feature slides + Q&A.
5. **Do not send/share/post the deck anywhere without the user’s explicit approval.** Creating a copy in the authenticated user’s Google Drive is okay when they ask for the deck.

## Required skills/references to load

Before creating/editing files or decks:

- Load `qi` for file/editing conventions.
- Load `google-api` and `google-api/references/drive.md` before copying Google Slides.
- Load this skill before executing the workflow.
- Load `code-execution` before using `run_code`.

## Workflow

### 1. Understand the merchant

Pull a concise merchant profile using web search and/or the merchant website:

- Category and products
- Business model: DTC, B2B, retail, international, marketplaces, subscriptions, gifting, etc.
- Catalogue complexity: variants, sizes, colours, bundles, product data needs
- Growth context: markets, stores, wholesale, international expansion
- Likely pain points: search, checkout, inventory, promos, returns, accounts, loyalty, local payments

Use this to create the merchant lens, e.g.:

> “Lens: UK + US growth • premium homeware discovery • variants/sets • gifting • stores + omnichannel”

### 2. Pull the Editions feature universe

Use the merchant-facing cheat sheet first because it is already merchant-facing and grouped by outcome. If needed, fetch the Shopify Editions page as backup.

Recommended sections:

- AI & Agentic Commerce
- Retail / Omnichannel
- Conversion, Identity & Customer Experience
- Global Scale, Payments & Operations
- Analytics & Measurement

### 3. Choose 15 relevant features

Pick features based on the merchant lens, not generic novelty. Prefer features with a clear business outcome and call talk track.

Use [references/feature-selection.md](references/feature-selection.md) for feature fit guidance.

### 4. Copy the source deck

Use Drive copy:

```js
google_api({
  url: "https://www.googleapis.com/drive/v3/files/1lx-Z7ic7YG4RJttKC0dsX5-HLQ0l5oyA6hhvWF_e-Bk/copy?fields=id,name,webViewLink,mimeType",
  http_method: "POST",
  body: { name: "{Merchant} – Shopify Editions Spring ’26 Feature Highlights" },
  scopes: ["https://www.googleapis.com/auth/drive"]
})
```

### 5. Trim the copied deck

Source deck has known slide IDs. Keep:

- Cover: `g3dcd59d3831_0_83`
- What is Editions: `g338bcf69926_0_220`
- Table of contents: `g271984988c2_0_1249`
- Relevant section dividers
- 15 selected feature slides
- Q&A: `g3e74193cdab_0_118`

Add a custom merchant summary slide after TOC with 3 columns:

1. Discovery / product data
2. Conversion / retention / promos
3. Global / ops / retail / analytics, depending on merchant

Update the cover with:

- `{Merchant} × Shopify Editions Spring ’26`
- `15 relevant features to discuss`
- Merchant lens line

Update TOC labels to match the selected feature themes.

### 6. Add dummies speaker notes

For each selected feature slide, add speaker notes in this structure:

```text
Paw notes — {Feature name}

What it does:
{Plain-English product explanation.}

Dummies version:
{One simple analogy or example.}

Why this matters for {Merchant}:
{Specific merchant relevance.}

Talk track:
“{One sentence you can say live.}”

Question to ask:
“{Discovery question.}”
```

Also add notes to the summary and divider slides to help Hannah transition sections.

### 7. Verify

After editing:

- Fetch deck metadata via Slides API.
- Confirm title, slide count, and slide order.
- Parse a small slide text map if needed.
- Confirm the deck link to the user.

Do not over-explain; give the user:

- Deck link
- 15 features included
- Top 5 to talk about live
- Optional opening line

## Known useful source slide IDs

See [references/source-slide-ids.md](references/source-slide-ids.md) for common slide IDs from the Spring ’26 template.
