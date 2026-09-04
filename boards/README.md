# Boards

Ranked boards covering both ends of the Japanese pipeline: players entering NPB, and players leaving it for MLB.

## 2026 NPB Draft (October 22, 2026)

**[`2026-npb-draft-board.csv`](2026-npb-draft-board.csv)** — 18 ranked prospects across high school, university and the corporate leagues.

Written version, with scouting notes on every player: **[Japan's Draft Is October 22. Here Are the 18 Players Who Matter.](https://japanprospects.substack.com/p/japans-draft-is-october-22-here-are)**

### Columns

| Column | Notes |
|---|---|
| `rank` | Japan Prospect Lab's own ranking. Not a consensus, and no Japanese outlet publishes one in this form |
| `name` / `name_jp` / `reading` | Romanized name, the Japanese original, and the kana reading. Readings are taken from club or school official sources where available, because aggregator sites get them wrong |
| `position` | Two-way players carry both, e.g. `RHP/1B` |
| `school` / `school_jp` / `school_type` | `High school`, `University`, or `Corporate league` |
| `height_in` / `height_cm`, `weight_lb` / `weight_kg` | Both unit systems. Imperial values are rounded from the published metric figure |
| `peak_velo_mph` / `peak_velo_kph` | Published career-high velocity. Empty for position players |
| `key_metric` | The single number that defines the player |
| `notes` | Context, and any caveat that belongs with the row |

### Caveats specific to this board

- **Velocities are as published in Japan.** Japanese stadium guns are generally believed to read optimistic against TrackMan. No correction is applied here, because no rigorous offset has been published.
- **High school home run totals include practice games.** That is the standard convention in Japan. They are labelled "HS home runs" and are not an official statistic.
- **Empty cells are empty, not zero.** Several fields are simply not published in Japan. Caught-stealing rate for catchers is the clearest example.
- **Eligibility is not final until the filing deadline.** High school and college players must file a *shibou-todoke* declaring their intent to turn pro, roughly two weeks before the draft. A player on this board can decline to file and drop out of the class entirely.

Corrections welcome. Open an issue with a source.

---

## NPB to MLB Posting Board

**[`posting-board.csv`](posting-board.csv)** — NPB players tracked by how and when they could reach MLB.

Read **[How a Japanese player actually gets to MLB](POSTING-ELIGIBILITY.md)** first. It explains the four routes, why service time does not govern posting, and how each column is determined.

### Columns

| Column | Notes |
|---|---|
| `draft_year` / `draft_route` | Route is `high_school`, `university`, `corporate`, `independent` or `foreign`. It sets the domestic free agency threshold, not the international one |
| `service_years` | Days on the top-team roster, 145 days to a year. A player in his eleventh professional season may still be short of nine years of service |
| `intl_fa_earliest` | The offseason the player banks nine years. Empty once he has moved |
| `route` | `posted`, `intl_fa`, `released`, `direct`, `unresolved` |
| `likelihood` | `completed`, `high`, `medium`, `low`, `speculative` |
| `basis` | **The reason, in one sentence.** A likelihood with no stated basis is a guess |
| `key_metric_1` / `key_metric_2` | Raw NPB figures. Not translated to MLB equivalents |
| `last_verified` | Rows go stale fast in November |

### Caveats specific to this board

- **Posting requires club consent and has no service time requirement.** Sasaki was posted at five years; players with more have been refused. Any row implying otherwise is wrong.
- **Player intent is reported in Japanese and rarely translated.** The `basis` column is where that reporting lands, and it is the reason this file exists.
- **No MLB equivalency is applied.** No current, rigorous, published conversion exists that this project will stand behind. Raw NPB numbers only.
- **The board is seasonal.** It resolves every December. Rows carry `last_verified` because a November row is stale in a week.

Corrections welcome. Open an issue with a source.
