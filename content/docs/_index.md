---
title: "Draupnir4all Docs"
weight: 1
---

## What is Draupnir4all?

Draupnir4all is a service that provisions [Draupnir](https://github.com/gnuxie/Draupnir)
instances for communities and moderators.
Providing all the features of a normal Draupnir instance without needing to host Draupnir yourself.

## What is Draupnir?

Draupnir allows moderators to manage user and server bans across a community,
subscribe to community curated spam lists, and organize their community.
It works for both small and large communities. Read more at "[Using Draupnir](/docs/how_to_use_draupnir)".
Draupnir is a continuation of the [Mjolnir](https://github.com/matrix-org/mjolnir) project.
Both bots are moderation bots for managing rooms in sync.

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

## Is this free?

Yes as of now this is completely free. However please make sure to be on fair use terms.
This means dont try to crash it or cause disruption actively. This will cause you to be banned.

Additionally if you want to support me the best way is to go via <https://en.liberapay.com/MTRNord>
