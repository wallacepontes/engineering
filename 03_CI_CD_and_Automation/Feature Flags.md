# Feature Flags

## Table of Contents

- [Feature Flags](#feature-flags)
  - [Table of Contents](#table-of-contents)
  - [1. What are Feature Flags?](#1-what-are-feature-flags)
    - [How They Work](#how-they-work)
    - [How They Relate to Commits](#how-they-relate-to-commits)
    - [Pros vs Cons](#pros-vs-cons)
  - [2. Feature Flags vs Feature Toggles (Are they different?)](#2-feature-flags-vs-feature-toggles-are-they-different)
  - [3. Are Feature Flags more than just toggles?](#3-are-feature-flags-more-than-just-toggles)
  - [4. Types of Feature Flags (Senior-Level Classification)](#4-types-of-feature-flags-senior-level-classification)
    - [1️⃣ **Release Flags**](#1️⃣-release-flags)
    - [2️⃣ **Experiment Flags (A/B Testing)**](#2️⃣-experiment-flags-ab-testing)
    - [3️⃣ **Operational Flags**](#3️⃣-operational-flags)
    - [4️⃣ **Permission / Entitlement Flags**](#4️⃣-permission--entitlement-flags)
    - [5️⃣ **Configuration Flags**](#5️⃣-configuration-flags)
  - [5. How to Build Feature Flags Like a Senior Dev](#5-how-to-build-feature-flags-like-a-senior-dev)
    - [🔹 1. Separate Decision from Behavior](#-1-separate-decision-from-behavior)
    - [🔹 2. Flags Must Be Observable](#-2-flags-must-be-observable)
    - [🔹 3. Flags Must Be Killable](#-3-flags-must-be-killable)
    - [🔹 4. Flags Have a Lifecycle](#-4-flags-have-a-lifecycle)
    - [🔹 5. Avoid Flag Debt (Very Senior Concern)](#-5-avoid-flag-debt-very-senior-concern)
  - [6. Build vs Buy (Senior Trade-off)](#6-build-vs-buy-senior-trade-off)
    - [Build your own when:](#build-your-own-when)
    - [Buy/use a platform when:](#buyuse-a-platform-when)
  - [7. Feature Flags + Trunk-Based Development (Connection)](#7-feature-flags--trunk-based-development-connection)
  - [8. Senior-Level Mental Model](#8-senior-level-mental-model)
  - [Videos](#videos)
  - [References](#references)

---

## 1. What are Feature Flags?

**Feature Flags (aka Feature Toggles)** are a technique that allows you to **change system behavior at runtime without redeploying code**.

Feature flags, or feature toggles, are conditional statements in a codebase that allow developers to control the visibility and behavior of functionality at runtime without deploying new code. They decouple the deployment of code from its release to users, enabling continuous integration and safer, faster delivery.

Feature flags are a software development concept that allow you to enable or disable a feature without modifying the source code or requiring a redeploy. They are commonly referred to as feature toggles, release toggles, or feature flippers. [[1]](https://launchdarkly.com/blog/what-are-feature-flags/)

### How They Work

At its core, a feature flag is a simple if-else logic statement in your code. In its simplest form:

```java
if (featureFlag.isEnabled("new-checkout")) {
    newCheckout();
} else {
    oldCheckout();
}

// Basic example
if (isNewFeatureEnabledForUser(user)) {
  // Code path for the new feature
} else {
  // Code path for the old or disabled behavior
}
```

The "magic" happens in how the condition is evaluated:

1. **Flag Definition**: The flag's state (on or off) and associated rules (e.g., enable for 5% of users, or only for internal testers) are managed externally, typically in a centralized feature management system, configuration file, or via environment variables.
2. **Runtime Evaluation**: When a user accesses a part of the application, the code checks the current status of the relevant flag via a lightweight Software Development Kit (SDK) or API call.
3. **Dynamic Behavior**: Based on the result, the application dynamically chooses which code path to execute. A product manager, for example, could turn a feature on or off from a dashboard without needing engineering intervention or a redeployment.

But that’s only the *entry level* understanding.

At scale, feature flags are about:

- **Decoupling deployment from release**
- **Reducing risk**
- **Enabling experimentation**
- **Supporting trunk-based development**
- **Operational control in production**

### How They Relate to Commits

Feature flags fundamentally change how developers manage their commit workflow, particularly in a trunk-based development environment:

- **Continuous Integration**: Developers can commit incomplete or in-progress code to the main branch (trunk) daily because the feature flag ensures the new code remains dormant or "off" for end-users. This prevents the long-running feature branches that often lead to complex and painful merge conflicts.
- **Safe Deployment**: The code is deployed to production with the flag disabled. This allows for testing the new code in the actual production environment with internal users (a "dark launch") before exposing it to all customers.
- **Gradual Release**: When ready, the flag is gradually enabled for a small percentage of users (e.g., 1%, then 5%, then 100%).
- **Instant Rollback**: If a bug is detected, the feature can be instantly disabled by flipping the flag off, without requiring an emergency code rollback or hotfix deployment, significantly reducing downtime (Mean Time to Recovery).
- **Cleanup**: Once a feature is fully stable and universally available, the flag and the old code path are removed from the codebase to prevent technical debt. The removal commit makes the new functionality the standard behavior.

### Pros vs Cons

- Pros
   1. Kill Switch
   2. Beta Testing
   3. A/B Testing
   4. Safer Refactoring
   5. Easier Deploys
- Cons
  1. Increased Complexity
  2. Mode Code
  3. Require Maintenance
  4. New Failure Points

---

## 2. Feature Flags vs Feature Toggles (Are they different?)

Short answer:
👉 **No real difference in practice**

* **Feature Toggle** → term popularized by *Martin Fowler*
* **Feature Flag** → industry/common term (LaunchDarkly, Unleash, etc.)

Some teams use:

* **Toggle** → internal, technical switches
* **Flag** → product/business-facing switches

But conceptually: **same thing**.

---

## 3. Are Feature Flags more than just toggles?

**Yes. Much more.**

A *junior* view:

> “A boolean that turns something on or off.”

A *senior* view:

> “A controlled decision point that affects behavior, exposure, risk, and learning.”

Feature flags can be:

* Boolean
* Percentage-based
* User-segment based
* Environment-based
* Time-based
* Context-aware (region, plan, device, tenant)

Example:

```java
if (flag.isEnabled("new-pricing", userId, region, plan)) {
    applyNewPricing();
}
```

---

## 4. Types of Feature Flags (Senior-Level Classification)

### 1️⃣ **Release Flags**

**Purpose:** Control rollout of incomplete or risky features.

* Short-lived
* Removed after full rollout
* Common in Trunk-Based Development

Example:

```text
"enable_new_order_flow"
```

⚠️ Smell: flags that live forever.

---

### 2️⃣ **Experiment Flags (A/B Testing)**

**Purpose:** Learn, not just release.

* Split users (e.g. 10% vs 90%)
* Measure metrics (conversion, latency, churn)

Example:

```text
"checkout_variant_A" → 50%
"checkout_variant_B" → 50%
```

---

### 3️⃣ **Operational Flags**

**Purpose:** Control behavior during incidents.

* Kill switches
* Throttling
* Fallback control

Example:

```java
if (flag.isEnabled("disable_external_payment_gateway")) {
    useInternalFallback();
}
```

💡 This is where flags save outages.

---

### 4️⃣ **Permission / Entitlement Flags**

**Purpose:** Control access by user, role, tenant, or plan.

Example:

* Free vs Premium
* Internal users only
* Canary customers

```java
flag.isEnabled("advanced_reporting", tenantId)
```

---

### 5️⃣ **Configuration Flags**

**Purpose:** Runtime tuning without redeploy.

Example:

* Timeout values
* Batch size
* Retry strategy

```java
int retryLimit = flag.getInt("payment_retry_limit", 3);
```

---

## 5. How to Build Feature Flags Like a Senior Dev

### 🔹 1. Separate Decision from Behavior

❌ Bad:

```java
if (flag.isEnabled("x")) {
    doX();
}
```

✅ Better:

```java
Strategy strategy = flag.isEnabled("x")
    ? new NewStrategy()
    : new OldStrategy();

strategy.execute();
```

This:

* Improves testability
* Reduces flag scattering
* Makes cleanup easier

---

### 🔹 2. Flags Must Be Observable

Every serious flag system includes:

* Metrics
* Logs
* Traces

Example questions:

* Who is seeing the feature?
* Is error rate higher when enabled?
* What % of traffic is affected?

If you can’t answer → **you’re flying blind**.

---

### 🔹 3. Flags Must Be Killable

A senior engineer asks:

> “Can I turn this off in 30 seconds at 2am?”

If the answer is “no” → it’s not a real feature flag.

---

### 🔹 4. Flags Have a Lifecycle

Feature flags are **not permanent**.

Typical lifecycle:

1. Created (off)
2. Enabled for internal users
3. Enabled for canary (5%)
4. Ramp up (25% → 50% → 100%)
5. **Code cleanup**
6. Flag deleted

Senior teams track:

* Creation date
* Owner
* Expiration date

---

### 🔹 5. Avoid Flag Debt (Very Senior Concern)

**Flag debt** is like technical debt but worse:

* Nested flags
* Flags depending on flags
* Flags inside flags inside flags 😵

Example of pain:

```java
if (flagA) {
   if (flagB) {
      if (!flagC) {
         ...
      }
   }
}
```

Rule of thumb:

> If you need to explain the logic in a diagram, refactor.

---

## 6. Build vs Buy (Senior Trade-off)

### Build your own when:

* You need simple environment-based flags
* Low scale
* Internal tooling

### Buy/use a platform when:

- You need:

  - Percentage rollout
  - User targeting
  - Auditing
  - SLA-backed availability

Popular tools:

- [LaunchDarkly](https://launchdarkly.com/)
- [Unleash (open-source)](https://www.getunleash.io/)
- [Split](https://www.split.io/)
- [ConfigCat](https://configcat.com/)
- [Flagsmith (open-source)](https://www.flagsmith.com/)
- [CloudBees](https://www.cloudbees.com/)
- [Datadog feature-flag-tracking](https://www.datadoghq.com/dg/real-user-monitoring/feature-flag-tracking/)

---

## 7. Feature Flags + Trunk-Based Development (Connection)

Feature flags **enable**:

- Small commits
- Incomplete code in trunk
- Continuous deployment
- Safe rollbacks

Without flags:

- Long-lived branches
- Risky merges
- Big-bang releases

This is why modern CD pipelines **assume** feature flags exist.

---

## 8. Senior-Level Mental Model

Think of feature flags as:

> **“Runtime decision points that let us control risk, learning, and delivery independently of deployment.”**

Not toggles.
Not hacks.
Not if-statements.

---

If you want, next we can:

* Design a **feature flag architecture** (Spring Boot / Node / cloud-native)
* Show **anti-patterns from real systems**
* Tie flags to **incident response**
* Explain **how Netflix, Meta, or Uber use them**

Just tell me where you want to go deeper.

---

## Videos

- [What is a Feature Flags?](https://www.youtube.com/watch?v=eBT9bCRIHWQ)
	> [<img src="https://img.youtube.com/vi/eBT9bCRIHWQ/0.jpg" width="200">](https://www.youtube.com/watch?v=eBT9bCRIHWQ "What is a Feature Flag and why is everyone using them? Feature Flags are areas in your code that have been fenced off, and their execution is controlled in some way. In LaunchDarkly, we allow you to manage feature flags across more than 20 different SDKs and across many different teams by LaunchDarkly 18,070 views 2 minutes, 20 seconds")

- [What are Feature Flags?](https://www.youtube.com/watch?v=AJa2B-twtG4)
	> [<img src="https://img.youtube.com/vi/AJa2B-twtG4/0.jpg" width="200">](https://www.youtube.com/watch?v=AJa2B-twtG4 "What if you could release a feature to different groups of users without deployment? Is there a way to effectively test features in production, and immediately roll them back if needed? by IBM Technology 67,070 views 6 minutes, 39 seconds")

- [Feature Flags (É gambiarra?) // Dicionário do Programador](https://www.youtube.com/watch?v=dml7nKi9WI0)
	> [<img src="https://img.youtube.com/vi/dml7nKi9WI0/0.jpg" width="200">](https://www.youtube.com/watch?v=dml7nKi9WI0 "Será que Feature Flag é sinônimo de Gambiarra? Usar esse recurso em projetos em produção é uma prática extremamente comum. Entenda como, quando e porque implementar as Feature Flags. O vídeo está repleto de exemplos de código e ferramentas especializadas em gerenciamento delas. by Código Fonte TV 19,541 views 12 minutes, 29 seconds")

- [Feature Flags are more than just Toggles](https://www.youtube.com/watch?v=2lAF3_vd0k0)
	> [<img src="https://img.youtube.com/vi/2lAF3_vd0k0/0.jpg" width="200">](https://www.youtube.com/watch?v=2lAF3_vd0k0 "Feature Flags are just conditional statements but can be much more powerful. Use them so you can integrate features before they are ready to be used in production. But they have a lot more utility than just being simple toggles. Here are different ways of thinking and using feature flags. by CodeOpinion 16,868 views 9 minutes, 11 seconds")

- [Feature Flags | Feature Toggles | What are Feature Flags | TTT | Cuelogic](https://www.youtube.com/watch?v=YGDEkh36MqU)
	> [<img src="https://img.youtube.com/vi/YGDEkh36MqU/0.jpg" width="200">](https://www.youtube.com/watch?v=YGDEkh36MqU "In this episode of TTT, we talk about Feature flags (or feature toggles) which is one of the hottest topics in Software Development. It lets you incrementally roll out functionality in a more controlled way. by Cuelogic Technologies | An LTIMindtree Company 13,868 views 8 minutes, 45 seconds")

- [How To Build Feature Flags Like A Senior Dev In 20 Minutes](https://www.youtube.com/watch?v=VBCYqp8l3Lc)
	> [<img src="https://img.youtube.com/vi/VBCYqp8l3Lc/0.jpg" width="200">](https://www.youtube.com/watch?v=VBCYqp8l3Lc "Feature flags are something you have probably never included in any of your apps, but they are an incredible feature that pretty much every app should include. Most people only think of feature flags as a toggle for new features, but they can be used for A/B testing, kill switches, and so much more. They are relatively easy to implement and provide tons of value. by Web Dev Simplified 163,868 views 20 minutes, 32 seconds")

- [Feature Flags configuration, instrumentation and use](https://www.youtube.com/watch?v=ViA6suScxkE)
	> [<img src="https://img.youtube.com/vi/ViA6suScxkE/0.jpg" width="200">](https://www.youtube.com/watch?v=ViA6suScxkE "Feature Flags enable you to choose what to deploy and who to deploy to in production. It allows you to define the audience for your application updates as well as the fashion in which they will be served. Feature flags can help reduce risk, allowing you to do controlled testing, and separate feature delivery from customer launch. by GitLab 14,331 views 8 minutes, 2 seconds")

---

## References

1. https://github.com/uber/piranha
2. https://www.datadoghq.com/dg/real-user-monitoring/feature-flag-tracking/
3. https://www.split.io/
4. https://launchdarkly.com/blog/what-are-feature-flags/
5. https://x.com/ph1/status/1263186197297283072
6. https://manu.sridharan.net/files/ICSE20-SEIP-Piranha.pdf
7. https://www.bugsnag.com/
8. https://github.com/WebDevSimplified/feature-flags-sample-code
9. 