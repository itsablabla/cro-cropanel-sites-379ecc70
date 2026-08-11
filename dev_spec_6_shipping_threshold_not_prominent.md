# Shipping threshold not prominent — dev spec
Site: allbirds.com · Priority 6 · Medium · Effort: Low (0.5-2 days)

## Problem
Free shipping threshold is only in small copy, not near prices or decision points, leading to late-stage cost surprises.

## Evidence (from the live site)
> Free ground shipping on orders over $100

## Current state
notes: Free shipping threshold mentioned only in small copy.

## Required change
notes: Display free shipping threshold prominently near product prices and in cart.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Display free shipping threshold prominently near product prices and in cart.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_shipping_threshold_not_prominent` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
