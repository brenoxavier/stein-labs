# Stein Labs

Public data that the **Stein Loader** reads on startup, in `stein.json`. Editing it here applies to everyone the
next time they start the game — no new Loader release and no new installer.

```json
{
  "discord": "https://discord.gg/xxxxxxx",
  "servers": [
    { "name": "Stein Labs", "ip": "play.example.com" }
  ],
  "news": {
    "id": "2026-09-lens",
    "title": "What's new in Stein Lens",
    "text": "Entity shadows and moonlight are in Video settings now.",
    "url": "https://discord.gg/xxxxxxx"
  }
}
```

- **`discord`** — the invite to the Stein Labs Discord. It is what the button on the main menu and the one on the
  About tab of the Stein Loader menu open. Only `https://discord.gg/...` or `https://discord.com/invite/...` is
  accepted: the Loader refuses any other address, so a mistake here can never turn into a link to somewhere else.
- **`servers`** — servers added to the multiplayer list of everyone running the Loader. The first one here ends up
  first in the player's list, under a "Recommended servers" divider. **Nothing is ever deleted**: servers the
  player already had stay where they are, and one that is already in the list (same address) is only moved to the
  top and renamed to the name given here.
- **`news`** — a small balloon in the corner of the main menu. `id` is what tells one message from the next: once a
  player closes a message, that `id` never comes back, so give every new message a new `id`. `title` and `text`
  are shown (the text is cut after three lines), and `url` is optional — with it, clicking the balloon opens the
  browser. Only `https` links to Discord or GitHub are accepted.

Empty values (`""`, `[]`, or no `news` at all) mean "there is nothing": the Loader carries on with no Discord
button, without touching the multiplayer list and with no balloon.

The file is read from `https://raw.githubusercontent.com/brenoxavier/stein-labs/main/stein.json`, once per startup,
on its own thread and with a short timeout — the game starts the same way without a connection, using the last copy
it kept.
