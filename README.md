# CS Sensitivity Converter

Free mouse sensitivity converter for **CS 1.6, CS2 and Call of Duty** (Warzone, Black Ops 6, Modern Warfare III). Get the same cm/360 and the same muscle memory in every game, with eDPI and DPI math, plus a **PUBG calibrator**. It runs in your browser with no install.

**Live site:** https://YOUR-SITE-ADDRESS (replace this after you deploy)

## What it does

- Converts your sensitivity between games so a full 360° turn takes the same mouse distance.
- Shows your cm/360, inches/360 and eDPI.
- Has a page for each game pair, with a reference table at 400, 800 and 1600 DPI and setup tips.
- Includes a PUBG calibrator that matches PUBG to another game by measurement.

## Supported games

| Game | Yaw (degrees per count) | Pages |
|---|---|---|
| CS 1.6 | 0.022 | converter, CS2, Call of Duty |
| CS2 | 0.022 | converter, CS 1.6, Call of Duty |
| Call of Duty (Warzone, BO6, MW3) | 0.0066 | converter, CS 1.6, CS2 |
| Valorant, Apex Legends | 0.07, 0.022 | main converter |
| PUBG | not a verified linear scale | calibrator page |

## How the conversion works

Every game turns mouse movement into rotation using a yaw value. To keep your turn distance the same:

```
new sensitivity = old sensitivity × (old yaw ÷ new yaw)
cm per 360° = 360 ÷ (yaw × sensitivity × DPI) × 2.54
eDPI = sensitivity × DPI
```

Example: CS 1.6 sensitivity 2.5 becomes 8.333 in Call of Duty at the same DPI.

## About PUBG

PUBG’s sensitivity slider does not have a single verified linear formula, and published yaw values for it disagree. Instead of showing a number that may be wrong, the calibrator finds the cm/360 you want from another game, then helps you adjust PUBG’s slider by measuring one turn in the training ground until the distances match.

## Limits to know about

- Only general mouse sensitivity is converted. Scoped and ADS sensitivities are separate settings in each game.
- Turn off mouse acceleration and Windows pointer precision. In CS 1.6, use `m_rawinput 1`.
- Always test one full turn in-game after converting.

## Project structure

```
index.html                              main converter
cs-1-6-to-cs2-sensitivity.html
cs-1-6-to-call-of-duty-sensitivity.html
call-of-duty-to-cs-1-6-sensitivity.html
cs2-to-call-of-duty-sensitivity.html
call-of-duty-to-cs2-sensitivity.html
pubg-sensitivity-calibrator.html
```

Each page is a single static HTML file with its own styles and script. There is no build step and no dependencies.

## Run it locally

Download the files and open `index.html` in any browser.

## Deploy

Upload the files to the root of a GitHub repository, then connect it to Cloudflare Pages or Netlify. Leave the build command empty and the output directory empty (or `/`). Every change you commit to GitHub is then published automatically.

## Contributing

Found a wrong yaw value or want another game added? Open an issue with a link to a source for the value.

## Disclaimer

Not affiliated with Valve, Krafton or Activision. Game names are trademarks of their owners.
