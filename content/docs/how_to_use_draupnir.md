+++
description = "How to get started with Draupnir"
title = "Using Draupnir"
weight = 2
+++

## Setting up Draupnir

After following the registration you will be invited to a Managment room for your draupnir.
This room will be the most important room for using Draupnir. Most actions will happen within this room.

{{< tip "warning" >}}
Do not leave or part from the management room.

Losing access to the management room means that you will lose access to your bot.
{{< /tip >}}

### Inviting the bot to rooms

{{< tip >}}
Commands are run in the management room by sending a message into the room.
{{< /tip >}}

Before we can get started you will need to invite the bot into your rooms, so that
the bot can protect them.

In order for Draupnir to protect rooms, you will need to run the following command for
each room that you want to protect:

```
!draupnir rooms add <room id or room alias>
```

{{< tip >}}
You can only protect rooms you have admin access to. Abusing the bot for spam will
also result in a ban from the service.
{{< /tip >}}

After you have protected your rooms, you will need to give your Draupnir bot the role of Admin.
As Matrix uses a [power level model](https://spec.matrix.org/v1.8/client-server-api/#mroompower_levels),
the simplist way to give Draupnir the required privileges is by providing the bot the Admin role.
This is necessary because Draupnir requires the privilege to ban servers.

To do this we suggest running the following command in each room you invited the bot into:

```
/op @yourMjolnirBot:example.com 100
```

Make sure to use the userid of the bot that invited
you to the managment room and not the user id you used from the email.

Alternatively you can find the bot in the user's section of your client and provide
it with the Admin role there.

{{< tip >}}
For more advanced set-ups, read the [spec covering power levels](https://spec.matrix.org/v1.5/client-server-api/#mroompower_levels).

Our recommendation for advanced use cases is to keep the power level of the bot above 50 (moderators)
and below 100 (admins), since admins cannot be demoted by a user of the same power level.
This can, as an example, be done using the "Change server ACLs" permission option in
Element-Web's room settings.
{{< /tip >}}

### Setting up policy lists

The core feature of Draupnir is the use policy lists. Policy lists allow moderators to share or
subscribe to moderation actions.
In the most basic setup, policy lists can be thought of as a database of all your bans for your bot.
However in a more advanced setup, policy lists allow you
to share moderation decisions with other communities.
This includes watching the lists from other communities in Matrix or
collaborating with them on the same lists.

First of all you should define a default policy list. This is where all your actions go to.

{{/* FIXME: why are we doing this? doesn't d4all create them a list called `list`? */}}

To set this up you run:

```
!draupnir list create <shortcode> <alias localpart>
```

- `shortcode` is a short name given to this list. It should be short and easy to type.
  However contrary to mjolnir you are likely not going to type it often.
- `alias localpart` is the local part of the address draupnir is going to create for this list.
  This is useful if you ever want to share your policy list with other communities.

For example, the following command will create a policy list with the short code `spam` and the
address `#my-community-spam-policy-list:draupnir.midnightthoughts.space`:

```
!draupnir list create spam my-community-spam-ban-list
```

You only need to create a policy list once, and you can then add as many users and servers
as you want to that policy list. You can also create as many policy lists as you want.

It is also possible to configure a default policy list draupnir will use for bans if
no short code is specified.
For example, to use the policy list with short code `spam` by default, issue the following command:

```
!draupnir default spam
```

#### Subscribing to policy lists

Policy lists are a clever mechanism that allows moderation teams to ban users for different motives
(e.g. one list for `spam` and one for `coc`).
Such a distinction can be useful when several communities want to collaborate together.

Not all communities will share a similar Code of Conduct,
but a lot of them will agree on what is spam.
Being able to subscribe to another community's spam list means your own community
will be protected from spammers that the other community has already met,
all while observing different code of conducts.

To subscribe to a public policy list, you need to retrieve the address of this list.
That list being technically nothing more than a Matrix room,
its address follows the usual `#room_name:server.tld` format.

Then to make draupnir follow this list, you need to issue the following command in its control room

```
!draupnir watch <room alias/ID>
```

For example to subscribe to the `#matrix-org-coc-bl:matrix.org` ban list maintained
by the Matrix Foundation, you would issue the following command

```
!draupnir watch #matrix-org-coc-bl:matrix.org
```

{{< tip >}}
An alternative list we suggest is the CME (Community Moderation Effort) list which is being
managed by a group of active community members and has proven itself over time to be effective,
fast and objective with their decissions. Their list has the alias `#community-moderation-effort-bl:neko.dev`.
{{< /tip >}}

## Moderating with Draupnir

If you are coming from a Mjolnir instance, you may just use the same commands as before.
However draupnir in most cases has simpler ways of running commands which will be explained in
the following sections.

### Banning users

### Kicking users

### Redacting users
