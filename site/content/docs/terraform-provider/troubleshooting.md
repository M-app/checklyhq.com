---
title: Common issues
weight: 100
menu:
  docs:
    parent: "Terraform provider"
---

## Troubleshooting common issues

This page covers common issues users have run into while using the Checkly Terraform provider, together with their likely root cause.

### Error: 402 payment required
You might have reached the maximum number of checks you can create on your account. Contact Checkly Support via our chat widget to talk about options. 

### Alert channel has 0 out of 0 subscribers
You might have forgotten to [subscribe checks and groups](/docs/monitoring-as-code/alerting#alert-channel-subscriptions) to your alert channel.

### Check seems to run from the wrong location(s)
Different things might be happening:
* If the check is part of a group, group-level settings will decide which location set is actually used to run all the checks in that group. Check again whether your check is part of a group by checking if its resource contains the `group_id` parameter.
* If the check is has "double check" enabled, and only one location configured, it will be retried from a random location chosen among all the ones available on Checkly.