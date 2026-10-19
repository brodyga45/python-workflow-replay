# Python Workflow Replay — experiment

Replay a small chain of trusted Python `handler(pd)` functions against saved JSON fixtures and compare the full step trace with an independently established expected result.

**[Read the synthetic example and give feedback](https://github.com/brodyga45/python-workflow-replay/issues/1)** — input, two original handlers, observed output and exact limits are shown there.

This is an early product experiment. This repository contains an illustrative example and evaluation notes; there is no installable product release or checkout yet. No customer migration has been performed or accepted.

## What has been checked

The local prototype supports previous-step return values, named exports, explicit per-step inputs, and synchronous/asynchronous handlers. Eight synthetic contract tests, a clean-archive example run and rejection of an intentionally wrong expected trace passed on macOS with Python 3.11.12. Linux and Windows have not been validated.

## Limits

This is ordinary Python execution with the process's permissions, **not a sandbox**. Imports and handlers can read/write files and use the network; only reviewed, trusted code is appropriate.

No Pipedream export importer, managed OAuth, app triggers, HTTP listener, scheduler, datastore migration, automatic dependency installation, retries or branching is implemented.

Preserving Python alone is not unique: free alternatives such as [MigrateFlows](https://github.com/davobene/migrateflows) already preserve Python inside n8n. The question here is whether running as ordinary Python and comparing agreed traces provides useful additional value.

## Feedback sought

Would a finished, documented downloadable source kit for this narrow task be useful at around **$39 once**, or do pytest and your existing scripts already cover it? Nothing is for sale and no payment is requested.

Reply in [the example issue](https://github.com/brodyga45/python-workflow-replay/issues/1). Please use synthetic data only; do not post customer events, credentials or account exports.

Independent experiment by brodyga45. Not affiliated with Pipedream, Workday or n8n.
