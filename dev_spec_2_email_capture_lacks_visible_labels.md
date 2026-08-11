# Email capture lacks visible labels — dev spec
Site: allbirds.com · Priority 2 · Medium · Effort: Low (0.5-2 days)

## Problem
Email signup forms without visible labels create ambiguity and friction, reducing form completion.

## Evidence (from the live site)
> form: inputs=1 submit=Sign Up labels=[]
> form: inputs=1 submit=Get Notified labels=['Email']

## Current state
cta: Sign Up / Get Notified; notes: Input fields lack visible labels; one form has no label, another has 'Email'.

## Required change
cta: Sign Up / Get Notified; notes: Add visible labels like 'Email address' to all email input fields.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add visible labels like 'Email address' to all email input fields.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_email_capture_lacks_visible_labels` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
