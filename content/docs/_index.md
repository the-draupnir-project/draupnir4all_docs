---
title: "Draupnir4all Docs"
weight: 1
---

## What is Draupnir4all?

Draupnir4all describes a provisioned [Draupnir](https://github.com/gnuxie/Draupnir) instance.
It comes with all the features of the normal bot without needing to host it yourself.

## What is Draupnir?

Draupnir is a hard fork based on [Mjolnir](https://github.com/matrix-org/mjolnir).
Both bots are moderation bots for managing rooms in sync. Additionally the bot allows
to follow room lists across communities and at large scale.
It works for both small and large communities. Read more at "[Using Draupnir](/docs/how_to_use_draupnir)"

## Who hosts this?

Currently this is hosted by MTRNord on the draupnir.midnightthoughts.space server which is a
dedicated synapse instance for the draupnir instances. It is running on a Kubernetes cluster and
the infrastructure files can be found here:

- <https://git.nordgedanken.dev/kubernetes/gitops/src/branch/main/apps/base/matrix/draupnir-synapse>
- <https://git.nordgedanken.dev/kubernetes/gitops/src/branch/main/apps/base/matrix/draupnir4all>
- <https://git.nordgedanken.dev/kubernetes/gitops/src/branch/main/apps/production/synapse-draupnir.yaml>
- <https://git.nordgedanken.dev/kubernetes/dns/src/branch/main/midnightthoughts.js#L41-L42>
- <https://git.nordgedanken.dev/kubernetes/grafana/src/branch/main/draupnir4all.json>

## How do I register?

To get started please follow the "[Getting Started](/docs/getting_started)" section.
