# Filter form lacks submit context — dev spec
Site: allbirds.com · Priority 5 · Medium · Effort: Low (0.5-2 days)

## Problem
Filter form with many inputs but no visible submit button leaves users unsure how to apply selections, causing abandonment.

## Evidence (from the live site)
> form: inputs=97 submit= labels=['Featured', 'Most relevant', 'Best selling', 'Alphabetically, A-Z', 'Alphabetically, Z-A', 'Price, low to high', 'Price, high to low', 'Date, old to new', 'Date, new to old', 'XS']

## Current state
notes: Filter form has no visible submit button label.

## Required change
cta: Apply / Done; notes: Add a clearly labeled 'Apply' or 'Done' button to the filter form.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a clearly labeled 'Apply' or 'Done' button to the filter form.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_filter_form_lacks_submit_context` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
