# Python Workflow Replay — experiment

Replay a small chain of trusted Python `handler(pd)` functions against saved JSON fixtures and compare the full step trace with an independently established expected result.

**[Read the synthetic example and give feedback](https://github.com/brodyga45/python-workflow-replay/issues/1)** — input, two original handlers, observed output and exact limits are shown there.

This is an early product experiment. This repository contains an illustrative example and evaluation notes; there is no installable product release or checkout yet. No customer migration has been performed or accepted.

## What has been checked

The local prototype supports previous-step return values, named exports, explicit per-step inputs, and synchronous/asynchronous handlers. Ten synthetic contract tests, a clean-archive example run and rejection of an intentionally wrong expected trace passed from the same review archive on macOS with Python 3.11.12 and 3.12.14, and Linux ARM64 with Python 3.11.17. Windows and Linux x86-64 have not been validated.

The JSON trace check distinguishes booleans from numbers and compares the representation actually emitted by the JSON encoder: Python tuples become JSON arrays. Object key order is ignored; JSON numbers `1` and `1.0` compare equal. A mismatch exits with status 1 without printing an accepted trace. These are local contract checks, not evidence of a customer's workflow equivalence.

A separate local check used the unchanged public handler from [Mopius Mobile's office-fitness-bot](https://github.com/mopius/office-fitness-bot), licensed under MIT (Copyright 2024 Mopius Mobile GmbH). For seven dates fixed by the test harness, its result matched a separate ordinary Python invocation. No original-platform execution or customer acceptance was available. The third-party code is not included in this repository.

## Limits

This is ordinary Python execution with the process's permissions, **not a sandbox**. Imports and handlers can read/write files and use the network; only reviewed, trusted code is appropriate.

No Pipedream export importer, managed OAuth, app triggers, HTTP listener, scheduler, datastore migration, automatic dependency installation, retries or branching is implemented.

Saved event data alone does not make execution deterministic: handlers can read the clock, randomness or external state. The runner does not freeze time or stub these dependencies. The linked office-fitness-bot handler chooses different messages for the same event on different weekdays; its compatibility check controlled the clock outside the product.

Preserving Python alone is not unique: free alternatives such as [MigrateFlows](https://github.com/davobene/migrateflows) already preserve Python inside n8n. The question here is whether running as ordinary Python and comparing agreed traces provides useful additional value.

## Evaluate one workflow case

The proposed product is a reusable downloadable Python source kit with the runner, CLI, synthetic fixtures, tests and setup/acceptance documentation. The price hypothesis is **$39 once** for a versioned source package, not a hosted service or a migration engagement. The tested package remains an unpublished review candidate; nothing is for sale and no payment is requested.

To check whether it fits a task you actually have, reply in [the example issue](https://github.com/brodyga45/python-workflow-replay/issues/1) with:

- The Python version and OS you need to run on.
- A made-up input and the expected per-step JSON result, established independently of this runner.
- Whether the relevant steps use only their explicit inputs, or also need a clock, network service, datastore or connected account. Describe dependencies without providing access.

The next step is to agree one supported, non-secret case and its pass/fail rule before any paid delivery. If the task needs unsupported platform services, that gap must be resolved before offering the package. A passing local fixture alone does not establish a complete migration.

Do not post customer events, private code, credentials, account exports or personal data. A synthetic example is enough for this first check.

Independent experiment by brodyga45. Not affiliated with Pipedream, Workday or n8n.
