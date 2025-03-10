---
title: How runtimes work
weight: 69
slug: /
menu:
  docs:
    parent: "Runtimes"
---

Checkly allows you to use JavaScript code in your [Browser checks](/docs/browser-checks) and in the optional 
[setup & teardown scripts](/docs/api-checks/setup-teardown-scripts/) you can add to your API checks.

This JavaScript code executes in a runtime environment that is managed by Checkly. This environment has access to specific 
Node.js versions and NPM packages, like the "latest Playwright version on Node 14". We call these environments **runtimes**.

## Using runtimes

It's pretty easy. You don't have to do anything most of the time.

1. View all the available runtimes on the [runtimes tab in the account section](https://app.checklyhq.com/settings/account/runtimes). See the screenshot below.
2. There is always one runtime marked as **active**. This is the runtime all checks use, unless you decide to override this at the check or group level.
4. Runtimes have a simple `YYYY.MM` name, e.g. `2021.06` Newer dates hold newer dependencies.   
3. Pick the runtime you want and click "Save settings". This runtime now applies to all of your checks and any new checks you create.

![runtimes](/docs/images/monitoring/account_runtimes@2x.png)

Note that one runtime version, e.g. `2021.6` holds all dependencies for all check types. There is no separate runtime for
different types of checks.

## Overriding runtimes for specific checks

Before updating your Checkly account to a new runtime, you can enable a newer runtime just for one check or check group.
This is a very powerful way to make sure your checks are compatible with a new runtime.

You can:

- Select a specific runtime in the **Browser check** editor.
- Select a specific runtime in the "Setup & teardown" tab for each **API check**.
- Select a specific runtime on the "Runtimes" tab for each **check group**.

> Overriding the global, account level runtime for a handful of checks is **the recommended way to check for any compatibility issues**
 before committing to a new, global runtime. Note the hierarchy: **check** runtime trumps **group** runtime trumps **global account** runtime.
 
## How we update and release new runtimes

We ship new runtimes with a regular cadence. This is what you can expect from us:

**1. Major & minor version upgrades of core packages and Node.js versions**
  
We aim to release a new runtime that holds the major and minor upgrades of Playwright, Puppeteer and Node.js **every quarter**.
This will result in a new, named runtime e.g. `2023.03` available in the Checkly webapp and in our API.

**2. Patch releases and security patches**

We reserve the right to **update an existing runtime** with critical security patches if deemed necessary. We will only do
this if there are no known backwards compatibility issues.

## Why are runtimes important?

We introduced the concept of runtimes so customers can upgrade their JavaScript enhanced checks to more recent Node package versions
in a controlled fashion; and roll back if anything breaks! Before, this was a more risky "big bang" migration.
