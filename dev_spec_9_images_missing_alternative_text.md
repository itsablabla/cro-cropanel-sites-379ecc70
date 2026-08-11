# Images missing alternative text — dev spec
Site: allbirds.com · Priority 9 · Medium · Effort: Low (0.5-2 days)

## Problem
3 of 43 images carry no alt attribute, losing both assistive technology support and the image-search traffic the alt text earns.

## Evidence (from the live site)
> Measured on the live homepage: 3 of 43 <img> elements have no alt attribute.

## Current state
notes: 3 images with no alt attribute

## Required change
notes: Add descriptive alt text; use alt="" only for decorative images.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add descriptive alt text; use alt="" only for decorative images.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_images_missing_alternative_text` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
