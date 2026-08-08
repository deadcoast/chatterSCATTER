<div align="center">

# chatter**SCATTER**

<img src="https://cdn.7tv.app/emote/01J17WK010000DX4MZBQSYH8ZA/2x.gif" height="56" alt="oda">

*A standalone chat interaction format.*

`->` Streamer starts a Call to Action(*CTA*); *"Can I get a...(Emote)"*

`<-` Chat answers (*Emote*) in the *CTA* time frame, earning XP + DEF(defense) against streamer's sniper overwatch.

[**► LIVE PAGE**](https://deadcoast.github.io/chatterSCATTER/) · [Repository](https://github.com/deadcoast/chatterSCATTER)

[![live](https://img.shields.io/badge/LIVE-deadcoast.github.io%2FchatterSCATTER-2ea44f?style=flat-square&labelColor=12161b)](https://deadcoast.github.io/chatterSCATTER/)
[![single file](https://img.shields.io/badge/SINGLE%20FILE-index.html-232c36?style=flat-square&labelColor=12161b)](https://github.com/deadcoast/chatterSCATTER/blob/main/index.html)

</div>

---

## QUICK START

| Step | Action                                                                      |
|------|-----------------------------------------------------------------------------|
| `1`  | Open the [live page](https://deadcoast.github.io/chatterSCATTER/)           |
| `2`  | Type your Twitch channel name → **CONNECT**                                 |
| `3`  | **OPEN OVERLAY WINDOW** → OBS → *Window Capture* → `chatterSCATTER OVERLAY` |

NON-INTRUSIVE:

- Standalone Read-only guest connection to public chat. *No Auth, login, API calls or keys.* No bloating chat with bot updates.

---

## SIMPLE FORMAT

| Mechanic     | Rule                                                                                                  |
|--------------|-------------------------------------------------------------------------------------------------------|
| **HP**       | Every chatter spawns at `100 HP` the moment they talk                                                 |
| **CTA**      | You demand an emote **or keyword**. Chat has `30–120s` to type it                                     |
| **DEF**      | Typing it earns `+25 DEF` (configurable). **Stacks.** Absorbs damage before HP                        |
| **OPEN**     | Failing the CTA renders the chatter without armor incase of sniper fire                               |
| **STREAK**   | Consecutive CTAs secured. `×N` chip on cards; wasting a `×10+` streak stamps it broken on the overlay |
| **XP / PTS** | Earned by chatting, securing CTAs, surviving shots. Persists between streams, per channel             |

## CTA MODES

> One dropdown beside `Start CTA`

| Mode                | Rule                                                           |
|---------------------|----------------------------------------------------------------|
| `STANDARD`          | The base format                                                |
| `FIRST 10`          | Only the fastest ten earn DEF; late typers are safe but unpaid |
| `DOUBLE OR NOTHING` | Double DEF on success; failures lose their entire DEF stack    |
| `SUDDEN DEATH`      | Everyone starts OPEN; typing it is the only way out            |

## DEV NOTES + TODO

APP_STATE:

- The game format in the application is operational, tested live for smaller audiences.
- The demo stress tests the application up to 1500 viewers, and all runs smooth. Any issues moving forward from **validated** functions would be from bugs that arise during live testing.
- THERE IS STILL SCAFFOLDING that requires further development such as integrating ALL `"sniper":"audio_upload"` SFX integrations.
- Padding needs to be fixed on the Larger chat cards.
- Would benefit from revisiting the condensed chat users window view; once chats get around 800 it might get hairy on the eyes.

> [!NOTE]
> ```jsonc
> // ONLY main silencer Audio SFX included. Users must upload their own for changes or additional uses.
> { "audio":"main_only" }
> for
>> { "sniper":["SHOT","HIT","MISS","CRITICAL","DEF-HIT"] }
> // DEPENDENCY_GRAPH
> ```

> [!tip]
> ```jsonc
> // Users may upload/change the audio SFX for ONLY the MAIN silencer sniper shot;(TODO[001])
> { "audio_upload":"SUPPORTED" }
> for
>> { "sniper":"SHOT" }
> // DEPENDENCY_GRAPH
> ```

### TODO

> [!NOTE]
> ```jsonc
> // Develop and integrate the rest of the Audio Upload and SFX functions so the users can upload all of the sniper output sounds they wish.
> { "task":"TODO[001]" }
> { "TODO[001]":"DEVELOP" }
> for
>> { "sniper":["SHOT","HIT","CRITICAL","DEF-HIT"] }
> // DEPENDENCY_GRAPH
> ```

## STREAMER ACTIONS

Click a chatter anywhere (chat window, top-list name, shot-log name) for the shot menu. The menu opens folded into two parents; `ATTACK OPTIONS` and `PINNED LISTS`.

> ```jsonc
> { "chatter":["card", "top-list-name", "shot-log-name"] }
> { "menu":["ATTACK OPTIONS", "PINNED LISTS"] }
> // DEPENDENCY_GRAPH
> ```

| Call       | Effect                                                    |
|------------|-----------------------------------------------------------|
| `MISS`     | 0 damage, dodge animation                                 |
| `HIT`      | `-25`, absorbed by DEF first                              |
| `CRITICAL` | `-50`, only on **OPEN** targets                           |
| `WASTE'EM` | Fatal. Silencer sound synced to the name animation        |
| `+DEF`     | Manual `+25 DEF`                                          |
| `REDEPLOY` | Revive at `100 HP` (off in HARDCORE; restore via RECORDS) |

## PIN LIST

> A self-curated list at the top of the chat window. Manual placements only; `#D14568`

## BOUNTIES

> Marked chatters; sits between PIN and BIG IRON; `#5EC26E`

| Mark    | Hand-pick from the menu, or `TOP 5–20` / `LAST CTA` / `NEXT CTA` (armed) from the dropdown |
|---------|--------------------------------------------------------------------------------------------|
| Resolve | Securing the next CTA cashes out `+100 XP`. Failing leaves them OPEN; their fate is yours  |

## BIG IRON

> Automated list of all chatters that have had a shot operated on them

| Behavior    | Detail                                                              |
|-------------|---------------------------------------------------------------------|
| Auto-pin    | Anyone you shoot at is pinned ; engagement only, viewing never pins |
| Full detail | Pinned cards never shrink, regardless of crowd density              |
| Release     | `RELEASE IRON` from the chatter's menu                              |

## HARDCORE + CHONKID

> One life. `CHONKID` is the character genome ; the username is the account, the CHONK is the life.

| Event   | Detail                                                                        |
|---------|-------------------------------------------------------------------------------|
| Death   | Permanent. The fallen CHONK is logged with its stats and genome               |
| Rebirth | The username returns as a fresh CHONK ; zero XP, zero PTS, life counter ticks |
| Restore | `RECORDS` → `THE FALLEN` ; the exact character returns, alive at `100 HP`     |

## FILTERS AND LISTS

| Control                 | What it does                                                                         |
|-------------------------|--------------------------------------------------------------------------------------|
| `TOP N` filter          | Show only the top `5–500` of chat, or `ALL`                                          |
| `BY` metric             | Rank by `CHATTERS` (messages), `EMOTES` (uses), or `BIG IRON` (PIN + Big Iron lists) |
| `LIST`                  | Target of the ALL actions ; `PIN`, `BOUNTIES`, or `BIG IRON`. Never the whole chat   |
| `HIT ALL`               | `-25` to every chatter on the selected list (confirms on 100+)                       |
| `HEAL ALL`              | Selected list back to `100 HP`, alive                                                |
| `PIN ALL` / `UNPIN ALL` | Add / remove the selected list's members on `PIN`                                    |
| `UNDO` / `REDO`         | Revert group actions ; 2 steps, trimmed to 1 on 400+ targets, with notice            |
| `RANDOM`                | Marks a random living chatter from the filter ; the overlay spins the barrel         |
| `BOUNTY` + `MARK`       | Apply the selected bounty group                                                      |

## SIMPLE METRICS

| Readout          | Source                                                                                                                         |
|------------------|--------------------------------------------------------------------------------------------------------------------------------|
| **TOP CHATTERS** | Messages this stream ; rigid 5-column row, names clickable                                                                     |
| **TOP EMOTES**   | Twitch-native emotes **+ your channel's 7TV / BTTV / FFZ lists**, fetched automatically on connect ; zero keys, zero input     |
| Custom words     | `Also track emotes` ; comma-separated additions for anything off-platform                                                      |
| **RECORDS**      | All-time per-channel tallies ; shots by type, kills, CTAs, secured/exposed, bounties claimed, best streak, top XP + THE FALLEN |

## DATA

| Action | Detail                                                                |
|--------|-----------------------------------------------------------------------|
| Export | Downloads the channel's full save as `<channel>.scatter.json`         |
| Import | Replaces the current save ; validated, warns on cross-channel imports |

## POP-OUT OVERLAY WINDOW

> `CHROMA GREEN + MAGENTA` options for `GreenScreen`

| Overlay element | Detail                                                                                                 |
|-----------------|--------------------------------------------------------------------------------------------------------|
| CTA banner      | Demand, countdown, secured count ; live for chat to see                                                |
| Urgency         | Final `10s` ; soft red fade, one pulse per `5s`                                                        |
| Center stage    | Shot moment: name in Twitch color, stamped `MISS / HIT / WASTED`                                       |
| Roulette        | `RANDOM` spins names on stream before the mark lands                                                   |
| Kill feed       | Last five events ; group receipts fold/unfold in sync with the shot log (capped at 12 lines on stream) |
| Idle records    | Rotates `TOP XP` / `LONGEST STREAK` / `MOST WASTED` between actions                                    |
| Backdrops       | Dark panel, chroma green, chroma magenta ; key it out, float it over gameplay                          |
| Sound           | Shipped silencer clip built in, or load your own                                                       |

## CROWD-PROOF

| Chatters  | Density                                |
|-----------|----------------------------------------|
| `≤ 40`    | Full cards ; HP segments, LVL, XP, PTS |
| `41–160`  | Name + HP bar                          |
| `161–600` | Compact, hover-only HP underline       |
| `600+`    | Name chips, maximum targets per screen |

Click always opens full detail. Single-card refresh keeps shots instant at `1500` chatters.

## DEMO: TRY IT

| Tool            | Purpose                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------|
| Demo chat       | Fake chatters, offline ; full format rehearsal                                                                   |
| Crowd `10–1500` | Simulate any chat size, live density preview                                                                     |
| Hover manual    | Built-in tooltip zone (top right below button `CHANGE CHANNEL`) explains every control in plain words ; foldable |

---

<div align="center">

chatterSCATTER

[demo-chatterSCATTER](https://deadcoast.github.io/chatterSCATTER/) · [repo-chatterSCATTER](https://github.com/deadcoast/chatterSCATTER)

</div>