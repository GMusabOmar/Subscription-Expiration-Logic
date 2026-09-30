# 🧩 Subscription Expiration Logic with Status Badges, Grace Period, Threshold Rules, and Real Date Handling (Modern UI)

## 🗝️ Introduction

Subscription systems must follow clear business rules: when does access end, what counts as “valid”, how do we treat grace periods, and when do we warn the user before expiration?

This project demonstrates how to build a fully client-side subscription status checker using HTML, CSS, and JavaScript. The user enters a start date, selects a plan, adjusts business rules (inclusive end date, grace days, expiring-soon threshold), and instantly gets a clear ✅/⚠️/❌ status with key dates and a days-left countdown.

## 🧩 Project Overview

This is a single-page subscription rules simulator with a split layout:

- 🔹 **Left side:** inputs + business rule toggles (plan, grace, threshold, mode).
- 🔹 **Right side:** results panel showing status badge, end date, grace end, and final valid-until date.

It’s designed to mimic real SaaS logic used in course platforms, memberships, and billing systems.

## 🧬 Core Concepts

### 🔹 Date-Only Logic (Timezone-Safe)

- ➡️ All comparisons are done using “date only” values (midnight).
- ➡️ Prevents time-of-day and timezone offsets from breaking expiration rules.

### 🔹 Plan End Date Calculation (Two Modes)

- ➡️ **Fixed-days mode:** weekly/monthly/quarterly/yearly are treated as 7/30/90/365 days.
- ➡️ **Calendar-based mode:** monthly = +1 real month, quarterly = +3 months, yearly = +1 year.

### 🔹 Inclusive vs Exclusive End Date

- ➡️ **Inclusive ✅** means the user is still valid on the end date itself.
- ➡️ **Exclusive ❌** means validity ends the day before the end date.

### 🔹 Grace Period Handling

- ➡️ After expiration, the user can remain “IN GRACE” 🕒 for a set number of days.
- ➡️ Useful for real systems (late renewal, payment retries, support exceptions).

### 🔹 Expiring Soon Threshold

- ➡️ If days left ≤ threshold, status becomes “EXPIRING SOON” ⚠️.
- ➡️ This simulates renewal reminders and warning banners.

### 🔹 Status Decision Engine (Business Rules)

- ➡️ **ACTIVE ✅** if today is within valid range.
- ➡️ **EXPIRING SOON ⚠️** if active but close to end.
- ➡️ **IN GRACE 🕒** if expired but still within grace window.
- ➡️ **EXPIRED ❌** if outside both validity and grace.

### 🔹 Clear UI Feedback + Badges

- ➡️ A badge shows the status type with matching colors.
- ➡️ A message box explains what the result means in plain language.

### 🔹 Demo + Reset Workflow

- ➡️ “Demo” fills realistic values (start 20 days ago + grace + thresholds).
- ➡️ “Clear” resets rules and outputs for clean retesting.

## 🔗 Interconnection Between Concepts

- 🔹 Date-only comparisons → consistent results → no timezone bugs.
- 🔹 End-date calculation mode → different business models → flexible subscription rules.
- 🔹 Inclusive end date → fairness in access → fewer customer complaints.
- 🔹 Grace period → better retention → smoother renewal flow.
- 🔹 Soon threshold → early warnings → fewer unexpected expirations.
- 🔹 Status badge + details line → transparency → easier debugging and support.

## 🏁 Conclusion

This project is a practical “subscription logic engine” built entirely on the front-end.

By combining accurate date handling, flexible plan rules, inclusive/exclusive policies, grace periods, expiring-soon thresholds, and strong UI feedback, it provides a real-world foundation you can reuse in SaaS platforms, course websites, and membership systems.
