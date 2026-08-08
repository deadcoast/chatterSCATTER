<div align="center">

# chatter**SCATTER**

<img src="https://cdn.7tv.app/emote/01J17WK010000DX4MZBQSYH8ZA/2x.gif" height="56" alt="oda">

*A proprietary interaction format.*

`->` Streamer starts a Call to Action(*CTA*); *"Can I get a...(Emote)"*

`<-` Chat answers (*Emote*) in the *CTA* time frame, earning defense against potential snipers.

[**► LIVE PAGE**](https://deadcoast.github.io/chatterSCATTER/) · [Repository](https://github.com/deadcoast/chatterSCATTER)

[![live](https://img.shields.io/badge/LIVE-deadcoast.github.io%2FchatterSCATTER-2ea44f?style=flat-square&labelColor=12161b)](https://deadcoast.github.io/chatterSCATTER/)
[![single file](https://img.shields.io/badge/SINGLE%20FILE-index.html-232c36?style=flat-square&labelColor=12161b)](https://github.com/deadcoast/chatterSCATTER/blob/main/index.html)

</div>

---

## TODO

> [!WARNING]
> ```jsonc
> // No Audio SFX included. Users must upload their own.
> { "audio":"NOT_INCLUDED" }
> ```
> for
> ```jsonc
> { 
> "sniper":[
>    "SHOT",
>    "HIT",
>    "MISS",
>    "CRITICAL",
>    "DEF-HIT"
>    ]
> }
> // DEPENDENCY_GRAPH
> ```

> [!tip]
> ```jsonc
> // Users may upload their own audio SFX for ONLY the MAIN silencer sniper shot; TODO[001]
> { "audio_upload":"SUPPORTED" }
> // DEPENDENCY_GRAPH
> ```
> for
>> ```jsonc
>> { "sniper":"SHOT" }
>> // DEPENDENCY_GRAPH
>> ```

---

> [!NOTE]
> ```jsonc
> // Develop and integrate the rest of the Audio Upload and SFX functions so the users can upload all of the sniper output sounds they wish.
> { "task":"TODO[001]" }
> { "TODO[001]":"sniper" }
> ```
>> ```jsonc
>> { "sniper":["SHOT","HIT","CRITICAL","DEF-HIT"] }
>> // DEPENDENCY_GRAPH
>> ```

## QUICK START

| Step | Action |
|---|---|
| `1` | Open the [live page](https://deadcoast.github.io/chatterSCATTER/) |
| `2` | Type your Twitch channel name → **CONNECT** |
| `3` | **OPEN OVERLAY WINDOW** → OBS → *Window Capture* → `chatterSCATTER OVERLAY` |

NON-INTRUSIVE:

- Standalone Read-only guest connection to public chat. *No Auth, login, API calls or keys.* No bloating chat with bot updates.

---

## SIMPLE FORMAT

| Mechanic | Rule |
|---|---|
| **HP** | Every chatter spawns at `100 HP` the moment they talk |
| **CTA** | You demand an emote. Chat has `30–120s` to type it |
| **DEF** | Typing the emote earns `+25 DEF` (configurable). **Stacks.** Absorbs damage before HP |
| **OPEN** | Failing the CTA flags a chatter exposed ; critical fire unlocked on them |
| **XP / PTS** | Earned by chatting, securing CTAs, surviving shots. Persists between streams, per channel |

## STREAMER ACTIONS

Click a chatter anywhere (chat window, top-list name, shot-log name) for the shot menu.

> DEP_GRAPH
> ```jsonc
> // DEPENDENCY_GRAPH
> { "chatter":["card", "top-list-name", "shot-log-name"] }
> ```


| Call | Effect |
|---|---|
| `MISS` | 0 damage, dodge animation |
| `HIT` | `-25`, absorbed by DEF first |
| `CRITICAL` | `-50`, only on **OPEN** targets |
| `WASTED` | Fatal. Silencer sound synced to the name animation |
| `GRANT DEF` | Manual `+25 DEF` |
| `REDEPLOY` | Revive at `100 HP` |

## PIN LIST: BIG IRON

> A self-curated list at the top of the chat window

| Behavior | Detail |
|---|---|
| Auto-pin | Anyone you shoot at is pinned ; engagement only, viewing never pins |
| Full detail | Pinned cards never shrink, regardless of crowd density |
| Manual | Pin / release from any chatter's menu |

## FILTERS AND LISTS

| Control | What it does |
|---|---|
| `TOP N` filter | Show only the top `5–500` of the roster, or `ALL` |
| `BY` metric | Rank by `CHATTERS` (messages), `EMOTES` (uses), or `BIG IRON` (pins) |
| `HIT ALL` | `-25` to the entire current filter (confirms on 100+) |
| `HEAL ALL` | Filter back to `100 HP`, alive |
| `PIN ALL` / `UNPIN ALL` | Big Iron the whole filter, or clear it |
| `UNDO ×2` / `REDO ×2` | Revert group actions ; trimmed to 1 step on 400+ targets, with notice |

## SIMPLE METRICS

| Readout | Source |
|---|---|
| **TOP CHATTERS** | Messages this stream ; rigid 5-column row, names clickable |
| **TOP EMOTES** | Twitch-native emotes **+ your channel's 7TV / BTTV / FFZ lists**, fetched automatically on connect ; zero keys, zero input |
| Custom words | `Also track emotes` ; comma-separated additions for anything off-platform |

## POP-OUT OVERLAY WINDOW

> `CHROMA GREEN + MAGENTA` options for `GreenScreen`

| Overlay element | Detail |
|---|---|
| CTA banner | Demand, countdown, secured count ; live for chat to see |
| Center stage | Shot moment: name in Twitch color, stamped `MISS / HIT / WASTED` |
| Kill feed | Last five events |
| Backdrops | Dark panel, chroma green, chroma magenta ; key it out, float it over gameplay |
| Sound | Built-in synthesized silencer, or load your own clip |

## CROWD-PROOF

| Roster | Density |
|---|---|
| `≤ 40` | Full cards ; HP segments, LVL, XP, PTS |
| `41–160` | Name + HP bar |
| `161–600` | Compact, hover-only HP underline |
| `600+` | Name chips, maximum targets per screen |

Click always opens full detail. Single-card refresh keeps shots instant at `1500` chatters.

## REHEARSAL

| Tool | Purpose |
|---|---|
| Demo chat | Fake chatters, offline ; full format rehearsal |
| Crowd `10–1500` | Simulate any chat size, live density preview |
| Hover manual | Built-in tooltip zone explains every control in plain words ; foldable |

---

<div align="center">

chatterSCATTER

[demo-chatterSCATTER](https://deadcoast.github.io/chatterSCATTER/) · [repo-chatterSCATTER](https://github.com/deadcoast/chatterSCATTER)

</div>
