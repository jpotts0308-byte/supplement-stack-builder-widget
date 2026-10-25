# React widget specification — draft v0

## Purpose
Let adults select a shopping category and compare **verified supplier-label information**. Never calculate personal doses or declare a supplement stack safe/effective. Shopify embedding is future work and requires merchant authorization.

## Inputs
1. Shopping category: hydration drink, protein product, workout drink, or browse all.
2. Product preferences: format and flavor, optional ingredient exclusions (processed locally only).
3. Confirmation: user understands that product labels must be reviewed and this is not personalized health advice.

Avoid asking for diagnoses, medication names, pregnancy status, age/date of birth, or identifiable health information. No email collection in this phase.

## Public-safe component sketch
`<StackExplorer catalog={approvedCatalog} />` with components `CategoryPicker`, `IngredientExclusions`, `ProductComparison`, `LabelStatusNotice`, `Disclaimer`. The caller must supply preapproved label metadata; no hardcoded real 321 Blastoff formulas.

## Product schema
`{id, displayName, category, flavor, ingredients, allergens, labelSource, verifiedAt, approvedForDisplay, productPageUrl}`. A missing, unverified, or disallowed entry is hidden and reported as unavailable for verified comparison. Escape all user and source text; only use vetted merchant URLs.

## Selection policy
- Filter by category and user exclusions; exclude unknown ingredient lists rather than assuming safe.
- Show candidates without efficacy, compatibility, dosage, or revenue-optimized rankings.
- Never compute stack sizes, doses, caffeine totals, timing, or ingredient interactions.
- Clicking an item opens its product label details only after review. No automatic cart, purchase, posting, email, analytics, or API actions.

## UX states
Loading; no approved catalog; filter results; unknown ingredient details; review-required; user comparison. Always distinguish informational matches from recommendations.

## Human gates before release
Verified current physical Supplement Facts and supplier data for every SKU; actual ingredient/allergen/serving details; scientific claim review, FDA/FTC advertising and labeling review; accessibility and responsive UX testing; consumer privacy review; Shopify permissions and merchant owner approval; public deployment and affiliate-link disclosure approval.

## Notice
This tool is for general product information, not medical advice. Read the official product label and consult a qualified healthcare professional before using dietary supplements, especially with medications or medical conditions. No disease-treatment, prevention, cure, or weight-loss claims.
