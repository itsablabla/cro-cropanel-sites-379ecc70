# Late shipping delay disclosure — dev spec
Site: allbirds.com · Priority 7 · Medium · Effort: Low (0.5-2 days)

## Problem
Shipping delay notice appears only in small page copy, discovered too late in the browsing journey, causing frustration.

## Evidence (from the live site)
> Due to increased demand, orders may take up to 30 days to ship.

## Current state
notes: Shipping delay notice in small page copy.

## Required change
notes: Surface shipping delay notice earlier, e.g., on product pages near add-to-cart.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Surface shipping delay notice earlier, e.g., on product pages near add-to-cart.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_late_shipping_delay_disclosure` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
