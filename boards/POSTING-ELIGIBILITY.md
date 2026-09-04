# How a Japanese player actually gets to MLB

Most English coverage treats this as a single mechanism called "posting." It is four different mechanisms, and they have almost nothing in common. This page is the reference behind [`posting-board.csv`](posting-board.csv).

---

## The four routes

### 1. Posting

The club agrees to make the player available. MLB clubs then negotiate with him directly, and the club that signs him pays a release fee to the NPB club on top of the contract.

**There is no service time requirement.** This is the single most common misunderstanding in English coverage.

Roki Sasaki was posted in his fifth professional season. Yoshinobu Yamamoto in his seventh. Players with more service than either have asked and been refused. **What governs posting is whether the club says yes.**

Clubs say yes when a player has given them most of a career, when refusing would damage their reputation with future draft picks, or when the release fee is worth more to them than one more season of the player. Clubs say no when the player is young, cheap and central to the roster.

That last case is not only sentiment. It is arithmetic, and the release fee schedule below explains it.

### 2. International free agency

**Nine seasons of first-team service.** At that point the player can sign anywhere in the world with no club consent and no release fee.

Service is counted in days on the top-team roster. **145 days in a season counts as one season.** Seasons shorter than that are not lost: the leftover days accumulate, and every 145 days banked converts to one more season. A player who spends half of several years in the farm system still gets there, just later than his debut year suggests. This is why the arithmetic often surprises people, and why a player in his eleventh professional season can still be short.

There is also a **domestic** free agency threshold that arrives earlier:

| Route into NPB | Domestic FA |
|---|---|
| High school | 8 seasons |
| University or corporate league | **7 seasons** (drafted autumn 2007 onward) |
| Drafted autumn 2006 or earlier | 8 seasons regardless of route |

**Domestic free agency does not permit a move to MLB.** It matters here only because it is frequently rendered in English as "free agency" without qualification, which makes players look available years before they are.

### 3. Release

A club can release a player outright. He is then free to sign anywhere, including MLB, with no fee and no waiting period. This is how fringe and veteran players occasionally appear on MLB minor league deals with no posting story attached.

### 4. Never signing with NPB

A Japanese amateur can sign directly with an MLB organization instead of entering the NPB draft. It is rare and socially discouraged, and the player forfeits the NPB path. It becomes a live question roughly once a decade, when a high school player is good enough that MLB clubs pursue him before the NPB draft.

---

## The calendar

| | |
|---|---|
| **Posting window** | **November 1 to December 15**, US Eastern Time. The NPB club files during this window |
| **Negotiation period** | **45 days**, starting the day after the commissioner's office notifies all MLB clubs |

If the 45 days lapse without a contract, the posting fails and the player returns to his NPB club for the following season.

**The news cycle for this board is November and December.** Speculation builds through the NPB postseason in October and resolves around the MLB winter meetings.

---

## The release fee

The fee is **marginal, not flat.** Each band of the contract is charged at its own rate, the way a progressive tax works. English coverage routinely reports it as a flat 20 percent, which overstates it on every large contract.

### Major league contract, on total guaranteed value

| Band of the contract | Rate | Fee from this band |
|---|---|---|
| Up to $25M | 20.0% | up to $5.0M |
| $25M to $50M | 17.5% | up to $4.375M |
| Above $50M | 15.0% | no cap |

**Worked example, $60M guaranteed:**

```
first  $25M  x 20.0%  =  $5.000M
next   $25M  x 17.5%  =  $4.375M
last   $10M  x 15.0%  =  $1.500M
                         --------
                         $10.875M   (18.1% effective)
```

### Minor league contract

**25% of the signing bonus, flat.** This applies to players who cannot sign a major league deal, which in practice means players under 25 or with fewer than six professional seasons.

### Later additions

If incentives are earned or options are exercised, **15% of the additional money** goes to the NPB club when it is paid to the player.

### One detail that matters to MLB clubs

**The release fee does not count against the Competitive Balance Tax.** A club paying it is not adding to its taxed payroll, which is why the fee is a weaker deterrent than its size suggests.

---

## Why the fee schedule explains club behaviour

Read the two schedules together and the reluctance to post young stars stops looking sentimental.

| | Player under 25 | Player 25 or older |
|---|---|---|
| Contract available to him | Minor league deal, bonus capped by the international signing pools | Major league deal, no cap |
| What the NPB club receives | **25% of a bonus measured in single-digit millions** | **A marginal-rate fee on the full guarantee** |

**The same player is worth an order of magnitude more to his NPB club at 25 than at 23.** A club refusing to post a 22-year-old ace is not only protecting its roster. It is declining to sell its most valuable asset at the worst possible moment.

This is the most useful thing on this page for predicting the `likelihood` column, and it is almost never stated in English coverage.

---

## How to fill in the board

| Column | How to determine it |
|---|---|
| `draft_year` / `draft_route` | NPB draft records. Route is `high_school`, `university`, `corporate`, `independent` or `foreign`. **Route sets the domestic FA threshold, not the international one** |
| `service_years` | Days on the top-team roster, 145 days to a season, leftover days carried forward. Published by NPB, and Japanese media report it every autumn as players approach free agency |
| `intl_fa_earliest` | The offseason after the player banks nine seasons. Leave empty when the player has already moved |
| `route` | `posted`, `intl_fa`, `released`, `direct`, or `unresolved` |
| `likelihood` | `completed`, `high`, `medium`, `low`, `speculative`. See below |
| `basis` | **The reason, in one sentence.** This column is the entire value of the board. A likelihood with no stated basis is a guess |
| `key_metric_1` / `key_metric_2` | Two numbers that define the player. Raw NPB figures, not translated |
| `last_verified` | Date the row was last checked. Rows go stale fast in November |

### The likelihood scale

| Value | Means |
|---|---|
| `completed` | Already moved. Kept as a reference point for the scale |
| `high` | Club has signalled willingness, or the player has international free agency in hand |
| `medium` | Player has publicly expressed intent and has enough service that a refusal would be costly for the club |
| `low` | Player has expressed intent but the club has no reason to agree yet |
| `speculative` | Performance suggests MLB interest. No stated intent from either side |

**`medium` and `low` are where this board earns its keep.** Japanese media report player intent constantly, in interviews and off-day columns that are never translated. That reporting is the input English readers cannot get for themselves.

**Check the player's age against the fee schedule before assigning either.** A 23-year-old with stated intent belongs in `low` far more often than his performance suggests, because his club loses money by agreeing.

---

## What this board does not do

**It does not translate NPB statistics into MLB equivalents.** Conversion factors circulate, but no rigorous, published, current translation exists that this project is willing to stand behind. The board carries raw NPB numbers, and league context is provided separately so readers can calibrate for themselves.

Publishing a conversion we cannot defend would undermine the one thing this project is for.

---

Corrections welcome. Open an issue with a source.
