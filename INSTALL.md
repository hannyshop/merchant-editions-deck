# Install

## Option A — Qlaw skill install

Once this repo is published, install it in Qlaw with the skill installer using the repo URL.

In Qlaw:

```text
/skill
```

Then paste or search for the published skill/repo URL, depending on the current installer UI.

## Option B — Manual install

Copy these files into your Qlaw VFS:

```
/skills/merchant-editions-deck/SKILL.md
/skills/merchant-editions-deck/references/feature-selection.md
/skills/merchant-editions-deck/references/source-slide-ids.md
```

Then ask Qlaw:

```text
Create a merchant-specific Shopify Editions deck for {merchant} with 15 relevant features and dummies speaker notes.
```

## Optional custom command

Add this to `/commands.json`:

```json
{
  "/editions-deck": "Create a merchant-specific Shopify Editions deck with 15 relevant features and dummies speaker notes. Use the merchant-editions-deck skill. Ask for the merchant name if I do not provide it."
}
```
