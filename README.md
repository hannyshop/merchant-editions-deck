# Merchant Editions Deck Skill

Create merchant-specific Shopify Editions decks from a Google Slides source template.

The skill helps you:

- research a merchant’s business model
- pick the 15 most relevant Shopify Editions features
- copy a source deck template without modifying the original
- trim the deck to the selected features
- add a merchant-specific summary slide
- add plain-English speaker notes: what it does, dummies version, why it matters, talk track, and question to ask

## Best for

CSMs, AEs, and merchant-facing teams preparing Shopify Editions conversations.

## Default sources

The skill currently references Spring ’26 defaults:

- Shopify Editions Spring ’26: https://www.shopify.com/editions/spring2026
- Merchant-facing cheat sheet: https://editions-cheatsheet-hannah.quick.shopify.io
- Source Google Slides deck template: https://docs.google.com/presentation/d/1lx-Z7ic7YG4RJttKC0dsX5-HLQ0l5oyA6hhvWF_e-Bk/edit

If your team uses a different template or Editions season, update the defaults in `skills/merchant-editions-deck/SKILL.md` and `references/source-slide-ids.md`.

## Install in Qlaw

If using Qlaw’s skill installer, install from this repo URL when published.

Manual install:

```
/skills/merchant-editions-deck/SKILL.md
/skills/merchant-editions-deck/references/feature-selection.md
/skills/merchant-editions-deck/references/source-slide-ids.md
```

## Example usage

```text
Create a merchant-specific Shopify Editions deck for Piglet in Bed with 15 relevant features and dummies speaker notes.
```

Or create a custom command:

```json
{
  "/editions-deck": "Create a merchant-specific Shopify Editions deck with 15 relevant features and dummies speaker notes. Use the merchant-editions-deck skill. Ask for the merchant name if I do not provide it."
}
```

## Notes

- The skill uses Google Drive/Slides APIs, so the user must grant Drive/Slides access.
- It creates a copy of the source deck and edits only the copy.
- It should not share or send the deck externally without user confirmation.
