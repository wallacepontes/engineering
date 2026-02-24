# Trunk-Based Development

## Table of Contents

- [Trunk-Based Development](#trunk-based-development)
  - [Table of Contents](#table-of-contents)
  - [Trunk-Based Development: Getting Started Guide](#trunk-based-development-getting-started-guide)
    - [1. Start With the Right Mental Model](#1-start-with-the-right-mental-model)
    - [2. Define Your Trunk (Do This First)](#2-define-your-trunk-do-this-first)
    - [3. Shrink Branch Lifetime (Critical First Step)](#3-shrink-branch-lifetime-critical-first-step)
      - [Target:](#target)
      - [Practices:](#practices)
    - [4. Make CI Non-Negotiable](#4-make-ci-non-negotiable)
      - [Minimum CI Checklist](#minimum-ci-checklist)
      - [Hard Rule](#hard-rule)
    - [5. Learn to Slice Work Thinly](#5-learn-to-slice-work-thinly)
      - [Instead of:](#instead-of)
    - [6. Introduce Feature Flags Early](#6-introduce-feature-flags-early)
      - [Use flags to:](#use-flags-to)
      - [Simple rules:](#simple-rules)
    - [7. Change How You Review Code](#7-change-how-you-review-code)
      - [Smaller PRs](#smaller-prs)
      - [Review focus:](#review-focus)
    - [8. Handle Hotfixes the TBD Way](#8-handle-hotfixes-the-tbd-way)
    - [9. Expect These Growing Pains (They’re Normal)](#9-expect-these-growing-pains-theyre-normal)
    - [10. Rollout Plan (Low Risk)](#10-rollout-plan-low-risk)
      - [Week 1–2](#week-12)
      - [Week 3–4](#week-34)
      - [Month 2+](#month-2)
    - [11. Success Signals to Watch](#11-success-signals-to-watch)
    - [One-Page Rule Summary (Print This)](#one-page-rule-summary-print-this)
    - [Final Thought](#final-thought)
  - [TDD + TBD + Feature Flags](#tdd--tbd--feature-flags)
    - [The Synergy: TDD, TBD, and Feature Flags](#the-synergy-tdd-tbd-and-feature-flags)
    - [Moving from "If-Else" to Feature Management](#moving-from-if-else-to-feature-management)
    - [The "Safety First" Workflow](#the-safety-first-workflow)
  - [Videos](#videos)
  - [References](#references)

---

## Trunk-Based Development: Getting Started Guide

Here’s a **practical, step-by-step “get started” guide to Trunk-Based Development (TBD)** you can actually apply with a real team—not theory, not dogma.

### 1. Start With the Right Mental Model

Before touching Git:

> **Your goal is not fewer branches.
> Your goal is keeping `main` releasable at all times.**

Everything else (CI, flags, habits) serves that goal.

---

### 2. Define Your Trunk (Do This First)

- Choose a single branch: `main` or `trunk`
- Protect it:

  - No direct pushes
  - CI must pass
  - At least one reviewer (optional but recommended)

**Rule of thumb**
If something breaks on `main`, it’s treated as a production incident.

---

### 3. Shrink Branch Lifetime (Critical First Step)

You do *not* need to go “full TBD” on day one.

#### Target:

* Branch lifetime: **hours, not days**
* Max: **1 day**

#### Practices:

- One task = one small change
- Merge at least once per day
- Avoid “umbrella branches” like `feature/big-refactor`

If work can’t be merged daily, it’s too big.

---

### 4. Make CI Non-Negotiable

TBD fails without strong CI.

#### Minimum CI Checklist

- Build on every commit to trunk
- Automated tests (unit at minimum)
- Fast feedback (<10 minutes ideal, <15 acceptable)

#### Hard Rule

> **A broken build stops all feature work.**

This sounds extreme—until you realize it saves weeks of downstream pain.

---

### 5. Learn to Slice Work Thinly

This is the hardest skill.

#### Instead of:

> “Implement user onboarding”

Slice into:

- Add data model
- Add API endpoint returning mock response
- Wire UI behind a flag
- Enable feature for internal users

Each slice:

- Compiles
- Passes tests
- Can be merged safely

---

### 6. Introduce Feature Flags Early

Feature flags are what make TBD viable for real products.

#### Use flags to:

- Merge incomplete features
- Hide work from users
- Decouple deploy from release

#### Simple rules:

- Every flag has an owner
- Every flag has an expiration date
- Remove flags once feature is stable

Start simple—boolean flags are enough.

---

### 7. Change How You Review Code

#### Smaller PRs

- 50–300 lines is ideal
- Reviewed in minutes, not hours

#### Review focus:

- Is this safe to merge?
- Does it keep trunk healthy?
- Is the change understandable?

Not:

- “Is this the final design?”
- “Is this perfectly optimized?”

---

### 8. Handle Hotfixes the TBD Way

No special branches.

If production breaks:

1. Fix it on trunk
2. Let CI validate
3. Deploy

This avoids divergence and “merge-back” chaos.

---

### 9. Expect These Growing Pains (They’re Normal)

You will hit:

- Flaky tests you’ve ignored for years
- Developers afraid to merge “unfinished” work
- CI becoming a bottleneck

These are **signals**, not failures.

TBD exposes problems that already existed—it doesn’t create them.

---

### 10. Rollout Plan (Low Risk)

#### Week 1–2

- Daily merges
- Smaller PRs
- CI enforcement

#### Week 3–4

- Branches < 1 day
- Feature flags introduced
- Broken builds treated seriously

#### Month 2+

- Mostly direct-to-trunk via PRs
- Deployments become routine
- Release anxiety drops

---

### 11. Success Signals to Watch

You’re doing it right when:

- Merge conflicts are rare
- PRs feel boring (good!)
- Releases stop being events
- Developers trust `main`

---

### One-Page Rule Summary (Print This)

- One trunk
- Short-lived branches
- Small changes
- Merge daily (or more)
- CI always green
- Feature flags for incomplete work
- Broken build = top priority

---

### Final Thought

Trunk-Based Development is not a Git trick.

It’s a **delivery strategy** that forces:

- Better slicing
- Better testing
- Better teamwork

Teams don’t move faster because they work harder.
They move faster because **they integrate continuously**.

---

## TDD + TBD + Feature Flags

Combining **Test-Driven Development (TDD)**, **Trunk-Based Development (TBD)**, and **Feature Flags** creates a high-velocity environment where you can deploy to production multiple times a day with incredibly low risk.

It’s a massive shift in mindset to move from "flags as a temporary fix" to "flags as the core engine of development."

### The Synergy: TDD, TBD, and Feature Flags

When you use these three together, they cover each other's blind spots:

- **TDD (The Micro-Safety Net):** Ensures that the logic of your new feature works as intended before the code even leaves your machine. It prevents "logic bugs."
- **TBD (The Integration Engine):** Prevents "merge hell" by forcing everyone to integrate their code into the main branch (trunk) daily. This ensures that your code doesn't drift away from what your teammates are building.
- **Feature Flags (The Release Valve):** Decouples **deployment** (putting code in production) from **release** (turning it on for users). Even if a bug slips through TDD and integration, it remains "dark" behind a flag, invisible to the user.

---

### Moving from "If-Else" to Feature Management

You mentioned using flags in the past to switch solutions, but modern **Feature Management Platforms** (like LaunchDarkly, Flagsmith, or Split.io) have evolved far beyond simple `if/else` statements. They allow for:

- **Canary Releases:** Roll out a feature to only 1% of users to monitor performance/error rates.
- **Kill Switches:** If a bug is detected in production, you can disable the feature instantly without a new deployment or rollback.
- **Targeting:** Enable specific features only for internal QA, beta testers, or specific regions.
- **A/B Testing:** Dynamically measure which of two solutions performs better in real-time.

### The "Safety First" Workflow

1. **Write a failing test (TDD)** for a new feature.
2. **Wrap the implementation** in a feature flag (defaulted to `OFF`).
3. **Merge to the Trunk (TBD)** as soon as the test passes.
4. **Deploy to Production.** The code is live, but the feature is dormant.
5. **Toggle the Flag** for yourself/QA in the production environment to verify.
6. **Gradual Rollout** to the rest of the users.

> **Pro-Tip:** The real secret to making this work is **Flag Hygiene**. Once a feature is 100% rolled out and stable, you must have a task to go back and delete the flag and the old code to prevent "technical debt" from piling up.

---

## Videos

- [We Tried Trunk-Based Development... The Results Were Shocking.](https://www.youtube.com/watch?v=CR3LP2n2dWw)
	> [<img src="https://img.youtube.com/vi/CR3LP2n2dWw/0.jpg" width="200">](https://www.youtube.com/watch?v=CR3LP2n2dWw "Trunk-Based Development has a reputation for being fast, fearless, and incredibly effective… but does it actually work in the real world? In this video, we have a company providing us the details of how they put Trunk-Based Development to the test — and the results genuinely surprised them. by Modern Software Engineering 32,047 views 13 minutes, 34 second")

- [Git Flow Is A Bad Idea](https://www.youtube.com/watch?v=_w6TwnLCFwA)
	> [<img src="https://img.youtube.com/vi/_w6TwnLCFwA/0.jpg" width="200">](https://www.youtube.com/watch?v=_w6TwnLCFwA "What is GitFlow and why is it a bad idea if you want to practice Continuous Delivery or Continuous Integration? GitFlow is a feature branching strategy that adds several extra layers of complexity. Git Flow is bad when we need fast feedback and a clear picture of the quality and 'releasability' of our work, so how do we adapt to get that faster feedback and a clearer picture? by Modern Software Engineering  303,047 views 16 minutes, 12 second")

---

## References

1. https://trunkbaseddevelopment.com/
2. https://dora.dev/
3. https://www.objective.com.br/insights/trunk-based-development/
4. https://launchdarkly.com/blog/introduction-to-trunk-based-development/
5. https://git-scm.com/
6. https://launchdarkly.com/blog/what-are-feature-flags/

If you want, next I can:

* Give you a **TBD checklist for team onboarding**
* Show **anti-patterns that silently kill TBD**
* Map TBD to **GitHub/GitLab settings**
* Tailor this to **enterprise / telecom / regulated environments**

Just say the word.
