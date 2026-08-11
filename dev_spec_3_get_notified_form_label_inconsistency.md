# Get Notified form label inconsistency — dev spec
Site: allbirds.com · Priority 3 · Medium · Effort: Low (0.5-2 days)

## Problem
Inconsistent labeling between 'Get Notified' and 'Sign Up' forms on the same page confuses users and undermines trust.

## Evidence (from the live site)
> form: inputs=1 submit=Get Notified labels=['Email']
> form: inputs=1 submit=Sign Up labels=[]

## Current state
cta: Get Notified / Sign Up; notes: One form has a label, the other does not.

## Required change
cta: Get Notified / Sign Up; notes: Standardize form labeling across all email capture forms.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Standardize form labeling across all email capture forms.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_get_notified_form_label_inconsistency` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
