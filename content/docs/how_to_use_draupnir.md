+++
description = "How to get started with Draupnir"
title = "Using Draupnir"
weight = 2
+++

## Setting up Draupnir

After following the registration you will be invited to a Managment room for your draupnir.
This room will be the most important room for this. Most actions will happen within this room.

{{< tip "warning" >}}
Make sure to stay in the room. Loosing access to the room means that you will loose
access to your bot.
{{< /tip >}}

### Inviting the bot to rooms

Before we can get started you will need to also invite the room into your rooms.
These are the rooms it will be watching over.

To do this inside of your Management room run this command for each room you want
to protect:

```
!draupnir rooms add <room id or room alias>
```

{{< tip >}}
You can only protect rooms you have admin access to. Abusing the bot for spam will
also result in a ban from the service.
{{< /tip >}}

After you did that you will need the bot admin rights. This is required since banning
servers in Matrix requires Admin rights currently.

To do this we suggest you run:

```
/op @yourMjolnirBot:example.com 100
```

in each room you invited the bot into. Make sure to use the userid of the bot that invited
you to the managment room and not the user id you used from the email.

{{< tip >}}
For more advanced set-ups, read the [spec covering power levels](https://spec.matrix.org/v1.5/client-server-api/#mroompower_levels).

A recommendation is to keep it above 50 (moderators) and below 100 (admins) since admins cannot be demoted by the same level.
This can for example be done using the "Change server ACLs" permission option in Element-Web's room settings.
{{< /tip >}}

### Setting up policy lists

The core feature of Draupnir is to use policy lists. These allow you to share or subscribe to moderation actions.
In the most basic setup it just is used as a database for your bot. However in a more advanced setup this allows you
to share the policies with others or allows you to subscribe to common lists used in the community.

First of all you should define a default policy list. This is where all your actions go to.

To set this up you run:

```
!draupnir list create <shortcode> <alias localpart>
```

- `shortcode` is a short name given to this list. It should be short and easy to type. However contrary to mjolnir you are likely not going to type it often.
- `alias localpart` is the local part of the address draupnir is going to create for this list.
This is useful if you ever want to share your policy list with other communities.

For example, the following command will create a policy list with the short code `spam` and the address `#my-community-spam-policy-list:draupnir.midnightthoughts.space`

```
!draupnir list create spam my-community-spam-ban-list
```

You only need to create a policy list once, and can then add as many users and servers
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
will be protected from spammers the other community has already met,
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
fast and objective with their decissions. You can subscribe to `#community-moderation-effort-bl:neko.dev`
for it.
{{< /tip >}}

## Moderating with Draupnir

If you are coming from a Mjolnir instance you may just use the same commands as before.
However draupnir in most cases has simpler ways of running commands which will be explained in
the following sections.

### Banning users

Users can be banned from your community by adding them to a policy list.
When you ban a user from a room, a prompt will be shown in the management room for Draupnir asking
if the ban should be added to a list. Selecting a list from this prompt will publish a policy,
and the ban will be synchronised with all of your protected rooms.

Alternatively, the ban command can be used within the management room to ban users directly.

```
!draupnir ban entity list [...reason]
```

- `entity` A Matrix user ID, a reference to a room (either an alias, room ID, or a matrix.to URL),
  or a server name.
- `list` A reference to a room (either an alias, room ID, or a matrix.to URL) or a list shortcode.
- `reason` A reason for the ban to be shown in the list (and potentially to other communities that
  are watching the list).

So to ban a user with the username `@spam:example.com` we would write the following:

```
!draupnir ban @spam:example.com list spam
```

### Kicking users

### Redacting users
