---
name: verify-sender-trust
description: Verify whether the sender or named organization behind a flyer, advertisement, email, direct mail, invitation, notice, campaign, seminar, survey, donation request, job offer, or other solicitation is trustworthy. Use when Codex needs to investigate clues in a received message, corroborate them against independent official or public sources, trace affiliations up to a publicly trusted organization, and report evidence, gaps, and risk.
---

# Verify Sender Trust

## Core Rule

Verify by building an evidence chain from the received content to independent trusted sources. Do not decide from visual polish, sender claims, search snippets, reviews, or one matching website alone.

Separate two questions throughout the investigation:

- Does the named organization exist and appear legitimate?
- Is this specific notice, offer, sender address, payment route, link, event, or representative actually connected to that organization?

Treat verification as successful only when the trail reaches one of:

- An official website or document controlled by the claimed organization.
- A public authority, regulator, court, government registry, school, hospital, listed company, or comparable institution.
- A clearly documented parent, affiliate, contractor, or event partner relationship from an official source.

## Workflow

1. Preserve the original artifact context.
   - Identify the medium: email, flyer, ad, postcard, SMS, social ad, website, PDF, screenshot, or call note.
   - Extract exact visible identifiers: organization names, brands, people, domains, email addresses, phone numbers, postal addresses, registration numbers, event names, campaign names, QR/link destinations, bank accounts, app names, and dates.
   - Keep the difference between what the artifact claims and what has been independently verified.

2. Generate candidate entities.
   - Split names into sender, sponsor, operator, agency, venue, payment recipient, domain owner, and public institution.
   - Watch for local subsidiaries, trade names, abbreviations, translated names, and lookalike domains.
   - When a QR code or short link is present, expand it safely without submitting forms or credentials.
   - Treat phone numbers, bank accounts, payment usernames, crypto addresses, tracking URLs, and reply-to addresses as separate entities that also need verification.

3. Check high-signal official sources first.
   - Claimed organization's official site: news, campaign pages, events, contact pages, press releases, domain ownership cues, and published phone/email.
   - Public registries: corporation registry, charity/nonprofit registry, regulator license lookup, school/hospital/government listings, professional license lookup, procurement or partner listings.
   - Official partner sources: venue event pages, municipality pages, chamber/association pages, parent company pages, grant/sponsor pages.
   - For email, compare the From domain, reply-to, links, SPF/DKIM/DMARC headers if available, and official contact domains.
   - For ads or social posts, look for an official landing page, advertiser disclosure, verified account links, and whether the account links back to the same official domain.

4. Build a corroboration chain.
   - Start from a clue in the artifact and connect each hop with a source that independently states the relationship.
   - Prefer official source A naming entity B over entity B merely claiming affiliation with A.
   - Record the exact relationship proven at each hop, for example "city page lists this seminar and names X as contractor" or "university page links to this registration domain."
   - Require the chain to cover the risky action requested from the user: payment, login, donation, attendance, application, download, personal data submission, or reply.

5. Investigate mismatch and risk signals.
   - Domain age, typo domains, mismatched payment recipient, free-mail sender for institutional claims, pressure tactics, secrecy, unusual payment methods, credential requests, unverifiable phone numbers, copied logos, inconsistent addresses, missing legal disclosures, and claims absent from official pages.
   - Treat absence of evidence carefully: say what was searched and what was not found, but do not overstate.

6. Decide and report conservatively.
   - Use "verified" only when the evidence chain reaches a trusted source and confirms the specific solicitation, channel, and requested user action.
   - Use "partially verified" when the named organization exists or a related event exists, but the specific sender, link, payment route, representative, or requested action is not confirmed.
   - Use "not verified" when no trusted source confirms the sender or solicitation.
   - Use "high risk" when there are material contradictions, impersonation signs, unsafe payment/credential requests, official warnings, or a payment/data request that bypasses official channels.
   - If the evidence proves only organization existence, say "organization exists; this solicitation is not verified."

## Source Standards

Prefer sources in this order:

1. Official public-sector, regulator, school, hospital, exchange, court, or registry pages.
2. The claimed organization's official domain, filings, annual reports, press releases, or verified social profile that links back to the official domain.
3. Official pages from named partners, venues, sponsors, payment processors, or parent organizations.
4. Reputable news or archival sources only as supporting context, not as the final trust anchor.
5. Reviews, forums, SEO directory pages, scraped company profiles, and ads only as weak leads.

When browsing, open the source pages. Do not rely on search result snippets. Cite links used in the final answer.

Prefer current sources for active offers, campaigns, events, warnings, leadership, contact details, and license status because these can change. If using archived or old sources, label them as historical.

## Safety Boundaries

- Do not submit personal information, payment details, login credentials, or forms to test legitimacy.
- Do not contact the sender unless the user explicitly asks and approves the message.
- Do not click suspicious downloads. If an attachment must be inspected, prefer metadata, safe text extraction, or sandboxed viewing.
- Do not claim an organization is fraudulent unless evidence supports it; use "not verified" or "risk indicators" when appropriate.
- If the artifact involves medical, legal, financial, immigration, employment, tax, or government benefits, require stronger official confirmation before calling it verified.
- If the user may lose money, access, legal status, health coverage, employment opportunity, or sensitive personal data, recommend using a contact path found independently on an official site, not a phone number or link from the artifact.

## Output Format

Use this concise structure unless the user asks for another format:

```markdown
Conclusion: Verified / Partially verified / Not verified / High risk

What I verified:
- [Claim or relationship] -> [trusted source]
- [Whether the specific solicitation/channel/action is confirmed]

Evidence chain:
1. Artifact clue: [exact clue]
2. Source: [official/public source and what it confirms]
3. Source: [next hop if needed]

Unresolved or risky points:
- [Gap, mismatch, or risk signal]
```

If evidence is mixed, put the most decision-relevant gap in the conclusion paragraph, not only in the details.
