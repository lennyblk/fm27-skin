# FM Dugout skin for Football Manager 27

A dark Navy and Volt skin built from plain Unity stylesheets (USS). Shared
colours, typography and control settings live in `skin/theme.uss`; component
styles are grouped by the part of the game they affect.

The skin needs no build step, Python, BepInEx or FM Dugout application to use.
This is a work in progress, last tested against FM27 Launch Preview.

## Install

1. Download or clone this repository.
2. Copy the **contents of `skin/`** into a folder named `FM Dugout` inside your
   FM27 user-data `skins` folder. `skin.json` and `main.uss` must be directly
   inside `skins/FM Dugout/`, rather than inside another nested `skin` folder.
3. Open FM27 Preferences, choose **FM Dugout** in the skin selector and apply it.

Typical user-data locations are:

- macOS: `~/Library/Application Support/Sports Interactive/Football Manager 27/skins/`
- Windows: `Documents/Sports Interactive/Football Manager 27/skins/`

If you moved the game's user-data folder or Documents is redirected to
OneDrive, use that location instead. Back up an existing copy before replacing it.

## Edit

Edit the installed files, save, then reload or reapply the skin in FM.

| File | Edit here for |
| --- | --- |
| `theme.uss` | Shared palette, text, fonts, surfaces, control states and radii |
| `custom.uss` | Your own overrides, loaded last |
| `styles/*.uss` | Rules for navigation, controls, panels, messages, data and other game areas |
| `styles/fm-contracts.uss` | FM variable names mapped to theme roles |
| `styles/fm-defaults.uss` | Native football/data defaults |
| `main.uss` | Ordered imports; preserve their order |

The [full editing guide](skin/README.md) explains the theme's shared settings
and the component behaviour behind them:

- [Palette and global text](skin/README.md#theme-palette-and-global-text), including alpha companions and semantic colours.
- [Surfaces, borders and corners](skin/README.md#surfaces-borders-and-corners), with separate card, dialog and popup settings.
- [Buttons, fields and selection](skin/README.md#buttons-fields-and-selection), including radio, checkbox, switch and disabled states.
- [Navigation and menus](skin/README.md#navigation-bookmarks-and-menus), plus bookmarks and start-screen settings.
- [Fonts and scoreboards](skin/README.md#fonts-and-competition-scoreboards), keeping native competition fonts separate from the skin's typography.
- [Club/player headers](skin/README.md#club-and-player-headers), including colour backplates and gradient geometry.
- [Messages](skin/README.md#messages-and-news), [tables and charts](skin/README.md#tables-badges-and-data-charts), [tactics and recruitment](skin/README.md#tactics-recruitment-and-training), and [match presentation](skin/README.md#match-presentation).
- [Compact layout settings](skin/README.md#compact-layout-settings) for dense tables, training, staff, finance and other fixed native lanes.
- [Editing examples](skin/README.md#editing-examples-and-checks) and what to check after reloading.

Keep filled controls paired with their foreground through every state. Club
colours, results and player status retain separate football meanings. Personal
changes can live in `custom.uss`; broader theme palettes belong in `theme.uss`
or a token override imported immediately after it.

## Known limitations

- **Light is experimental.** Dark is the default. `theme-light.uss` is an optional
  token override, not a complete supported light skin. To preview it, add
  `@import url("theme-light.uss");` immediately after the `theme.uss` import in
  `main.uss`. Remove that import to return to Dark.
- In the tested FM27 build, some embedded club/player links receive explicit
  rich-text colours from the game. They can stay white even when the label's
  USS foreground changes. No loose-USS override has been verified for those
  spans. The experimental Light palette also leaves some chart/data text with
  insufficient contrast.
- Competition scoreboards use fonts supplied by the installed game. UEFA fonts
  are not included. Native font rendering can differ from the intended outlines;
  this public copy's native-font configuration still needs an in-game check.
- Not every screen, resolution, language or interaction state has been verified.
  Game updates can change native classes and bindings.

## Included files

This repository contains the skin, editing instructions and font notices.
It does not include the development skill, inspection tools, test saves,
runtime evidence, game bundles or development-repository history.

See [third-party notices](NOTICE.md) and the bundled Poppins font licence.
This is an independent community skin, not an official Sports Interactive,
SEGA or UEFA product.
