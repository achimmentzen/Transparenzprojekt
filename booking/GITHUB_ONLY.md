# GitHub-only implementation

## What is implemented

The repository now contains the public technical contract for the booking workflow and a GitHub Actions validation workflow.

The intended flow is:

1. Public 18+ request form
2. Request validation
3. Double opt-in
4. Duplicate/plausibility check
5. Automatic organisational confirmation when all configured conditions are met
6. Calendar/appointment record
7. Cancellation/withdrawal handling

## Important GitHub platform boundary

GitHub Pages is a static hosting service. A browser form on a public GitHub Pages site must not receive a repository write token or Actions secret. Therefore a completely autonomous public intake that privately receives personal booking data, sends confirmation e-mails and writes private calendar events **cannot be implemented securely with GitHub Pages + GitHub Actions alone**.

A public GitHub-only form that writes booking details into Issues, Discussions or repository files would expose personal data in a public repository and is therefore not used.

The repository deliberately contains only the workflow specification and validation code. Real booking records must remain outside the public repository.

## Consent rule

An automated system may confirm the organisational appointment after the required opt-in steps. It must never treat an old, delegated or automated confirmation as irreversible consent to a future physical or intimate act. Consent can be withdrawn at any time.

## Production options

For a genuinely autonomous private booking backend, an external service with private storage and mail/calendar access is required. n8n is one possible option; a serverless backend is another.

This limitation is a technical property of the GitHub Pages security model, not a limitation of the booking concept itself.
