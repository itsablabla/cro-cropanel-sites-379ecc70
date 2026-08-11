# Product price visibility unclear — dev spec
Site: allbirds.com · Priority 4 · Medium · Effort: Low (0.5-2 days)

## Problem
Multiple price values without clear association to the selected item confuse visitors about the actual cost.

## Evidence (from the live site)
> $100 $5.00 $105 $105 $105 $100

## Current state
notes: Multiple price values shown without clear association.

## Required change
notes: Clearly label primary product price and separate from shipping or other costs.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Clearly label primary product price and separate from shipping or other costs.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_product_price_visibility_unclear` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
