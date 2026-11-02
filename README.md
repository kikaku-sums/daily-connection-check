# Daily connection check

A small, dependency-free daily HTTPS monitor. It runs at 00:00 UTC (09:00 Japan time); GitHub may delay scheduled delivery.

Uses a standard GitHub-hosted Ubuntu runner in this public repository. Standard runners for public repositories are free independently of private-repository allowances. No AI services, paid runners, artifacts, caches, or paid plans are used.

Target addresses, authentication headers and response expectations are stored together in the encrypted Actions Secret `MONITOR_TARGETS`. Logs show only target/check numbers and results. The monitor sends GET requests, refuses redirects and never prints response bodies. No private application code or target configuration is published here.

The workflow continues through all targets if one fails. It does not automatically restore suspended services. Check Actions for results; GitHub notifications follow the account's existing notification preferences.

Public scheduled workflows may be disabled after 60 days of repository inactivity. A separate step maintains a harmless monthly marker, even if a target is unavailable. Its short-lived repository token can update repository contents; no external actions or repository code are executed. Scheduling availability is still subject to GitHub policy and service availability.

To stop checks, disable the workflow in Actions. To change credentials, replace `MONITOR_TARGETS`. Do not make the repository private or change the standard runner if zero execution charges are required.

References:
- https://docs.github.com/en/billing/concepts/product-billing/github-actions
- https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#schedule
