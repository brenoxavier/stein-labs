# Stein Labs

Public data that the **Stein Loader** reads on startup, in `stein.json`. Editing it here applies to everyone the
next time they start the game — no new Loader release and no new installer.

```json
{
  "discord": "https://discord.gg/xxxxxxx",
  "servers": [
    { "name": "Stein Labs", "ip": "play.example.com" }
  ]
}
```

- **`discord`** — the invite to the Stein Labs Discord. It is what the button on the main menu and the one on the
  About tab of the Stein Loader menu open. Only `https://discord.gg/...` or `https://discord.com/invite/...` is
  accepted: the Loader refuses any other address, so a mistake here can never turn into a link to somewhere else.
- **`servers`** — servers added to the multiplayer list of everyone running the Loader. The first one here ends up
  first in the player's list. **Nothing is ever deleted**: servers the player already had stay where they are, and
  one that is already in the list (same address) is only moved to the top and renamed to the name given here.

Empty values (`""` and `[]`) mean "there is nothing": the Loader carries on with no Discord button and without
touching the multiplayer list.

The file is read from `https://raw.githubusercontent.com/brenoxavier/stein-labs/main/stein.json`, once per startup,
on its own thread and with a short timeout — the game starts the same way without a connection, using the last copy
it kept.
