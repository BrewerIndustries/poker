# Jarvis Poker

An old-school casino bar-top **video poker** machine in your browser — IGT "Game King"
style, with **five classic variants** (Jacks or Better, Bonus, Double Bonus, Double Double
Bonus, Deuces Wild), hold and draw, lit paytables, a denomination badge with cash value, the
iconic **Double-Up** gamble, a jackpot coin shower, and a glowing CRT cabinet.

Play it: **[poker.dabrewer.dev](https://poker.dabrewer.dev/)** · dev build at
[poker.dabrewer.dev/dev/](https://poker.dabrewer.dev/dev/)

## How to play

1. Set your wager with **BET ONE** (cycles 1→5) or **MAX BET** (5 coins, deals at once).
2. Press **DEAL** for five cards.
3. Click any cards to **HOLD** them (a gold lamp lights above each held card).
4. Press **DRAW** to replace the rest. Make a paying hand and you win.
5. On a win, **TAKE WIN** to bank it — or **DOUBLE UP** to gamble: pick a card
   higher than the dealer's to double your winnings (tie pushes, lower loses it all).
   Repeat as far as your nerve holds.
6. **CASH OUT** banks your credits.

Keyboard: `1`–`5` hold a card · `Enter`/`Space` deal / draw / take · `D` double up · `M` mute.

## Paytable (9/6 Jacks or Better)

| Hand | Per coin |
| --- | --- |
| Royal Flush | 250 ( **4000** at max bet ) |
| Straight Flush | 50 |
| Four of a Kind | 25 |
| Full House | 9 |
| Flush | 6 |
| Straight | 4 |
| Three of a Kind | 3 |
| Two Pair | 2 |
| Jacks or Better | 1 |

## Tech

- Single-file `index.html` — vanilla JS + CSS, **no framework, no build step**. Open it and it runs.
- Web Audio API for synthesized SFX (no asset files); `localStorage` for credits + stats.
- Deployed via **GitHub Pages** with a dev→prod pipeline: `main` → `/`, `dev` → `/dev/`
  (see `.github/workflows/pages.yml`).
- Registered in the Jarvis **Launcher** and **Dashboard** via the committed `.jarvis.json`.

## Develop

```bash
python3 -m http.server 3000   # then open http://localhost:3000
```

`dev` is the working branch (auto-deploys to `/dev/`); `main` is production and is
updated only via an approved PR.

## Changelog

### v0.4 — *Game King Lineup*
- **Five selectable games** (OPTIONS → Game): Jacks or Better, Bonus Poker, Double Bonus,
  **Double Double Bonus** (four-of-a-kind kicker tiers), and **Deuces Wild** (every 2 is wild)
- Per-game paytables + correct evaluation — bonus quad-by-rank tiers, DDB kicker logic, and a
  full wild-card evaluator (natural/wild royal, five of a kind, four deuces). Pay tables match
  [Wizard of Odds](https://wizardofodds.com/games/video-poker/) (9/6 JoB, 8/5 Bonus, 10/7 Double
  Bonus, 9/6 DDB, full-pay Deuces)
- **Denomination-aware WIN meter** — WIN now shows its cash value alongside CREDITS
- Deuces render as gold **WILD** cards; the marquee ribbon shows the active game

### v0.3 — *Max Theming*
- Crowned marquee + gold cabinet with corner screws and a chrome screen frame
- **Denomination badge** (1¢ – $5) with a live **cash-value** readout under credits
- **MENU** (rules) and **OPTIONS** (sound · speed · denomination · reset bankroll / clear
  stats) overlays; **SPEED** control (Slow → Turbo) that scales every animation
- Jackpot celebration — screen flash + gold **coin shower**, animated win/credit count-ups,
  and a special Royal Flush jackpot banner

### v0.2 — *Game King*
- Reskinned to the classic IGT **Game King** look: royal-blue field, gold cabinet
  bezel + button rail, and a marquee topper
- Paytable now uses dotted leaders with the **active bet column lit red** (the max-bet
  Royal Flush jackpot stays at 4000)
- Authentic card faces: real pip layouts for 2–10, framed **court cards** (J/Q/K) with a
  crown emblem, and a big-pip Ace — with corner indices (rank over suit)
- **WIN · BET-oval · CREDITS** status bar (replaces the 7-segment meters); gold buttons
  (Bet Up / Bet Max / Cash Out) with a red Deal/Draw

### v0.1 — *Cold Open*
- Jacks or Better video poker: shuffle, deal, hold, draw, 9/6 paytable + hand evaluator
- Bet 1–5 with the classic max-bet Royal Flush jackpot (4000)
- Double-Up bonus (beat the dealer's card to double; tie pushes)
- CRT cabinet: neon marquee, lit paytable with the active bet column highlighted,
  card-back/flip animation, 7-segment CREDITS / BET / WIN meters, blinking messages
- Synthesized Web Audio SFX (coin, deal, hold, draw, win jingle, double-up) + mute
- `localStorage` save (credits, hands played, biggest win); responsive / mobile layout

## Backlog

- More variants (Deuces Wild, Bonus Poker, Double Double Bonus) via a game-select menu
- Multi-hand (Triple / Five Play) draw
- "Optimal hold" hint / trainer mode
- Payout history + session stats panel
- Coin-drop and cabinet ambience audio polish
