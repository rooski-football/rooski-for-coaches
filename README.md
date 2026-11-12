# Rooski for Coaches

Rooski's plugin for football coaches. It teaches your AI two things: how to build scouting reports, self-scouts and tendency studies from your program's play-by-play data, and how to set up and keep your **Rooski Drive**, your football folders in Google Drive.

The plugin holds instructions only. Your data and every number come from the **Rooski connector**, which you add with your program's private link. Without the connector, the plugin has nothing to read.

## Install in Claude (web or desktop app)

1. **Settings > Capabilities:** turn on **Code execution and file creation**.
2. **Customize > Plugins > Add > Add marketplace:** enter `rooski-football/rooski-for-coaches`, then add **Rooski**.
3. On the Rooski marketplace, turn on **Sync automatically** so updates reach you.
4. **Customize > Connectors:** add the Rooski connector with your program's link, if it isn't added yet. For the Rooski Drive, add Google Drive there too.

Then just ask: "scout Kansas's offense", "self-scout our 3rd downs", "how often do they run on 2nd and long?", "set up my Rooski Drive", "where do I put my call sheet?"

## Claude Code

```
/plugin marketplace add rooski-football/rooski-for-coaches
/plugin install rooski@rooski
```

## What's new

See [CHANGELOG.md](CHANGELOG.md).

Questions: your Rooski contact, or https://rooski.com
