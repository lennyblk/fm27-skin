# Editing the FM Dugout skin

`skin.json` loads `main.uss`. That file imports the theme and component
stylesheets directly, followed by utility classes and `custom.uss`.
There is no generated runtime stylesheet or compilation step.

## Stylesheet ownership

| File | Purpose |
| --- | --- |
| `theme.uss` | Shared colours, text roles, font roles, feedback pairs and corner sizes |
| `theme-light.uss` | Optional, incomplete Light token experiment; disabled by default |
| `styles/navigation.uss` | Main and secondary navigation, bookmarks and header chrome |
| `styles/controls.uss` | Buttons, inputs, dropdowns, toggles and their interaction states |
| `styles/panels.uss` | Cards, panels, floating surfaces and image backplates |
| `styles/messages.uss` | Inbox/Portal rows, message details, conversations and attachments |
| `styles/typography.uss` | Heading, body and text utilities |
| `styles/data.uss` | Tables, lists, attributes, charts and radars |
| `styles/people.uss` | Clubs, players, staff, training, scouting and transfers |
| `styles/tactics.uss` | Pitches, positions, instructions and set pieces |
| `styles/match.uss` | Match, scoreboards, commentary and touchline presentation |
| `styles/screens.uss` | Calendar, preferences, setup and other game pages |
| `styles/core.uss` | Shared helpers, layout and platform rules |
| `styles/fm-defaults.uss` | Advanced native football/data defaults |
| `styles/fm-contracts.uss` | FM variable names mapped to skin roles |
| `styles/utilities.uss` | Explicit spacing, layout and text helpers |
| `custom.uss` | Optional personal overrides, imported last |

Start with `theme.uss` for broad appearance changes. Use a component stylesheet
for a particular control or page. Preserve import order: changing it can change
which equally specific rule wins.

## Common theme roles

| Tokens | Role |
| --- | --- |
| `--skin-surface-canvas`, `--skin-surface-page` | Top bar/canvas and page workspace |
| `--skin-surface-panel`, `--skin-surface-raised`, `--skin-surface-strong` | Surface layers |
| `--skin-text-primary`, `--skin-text-secondary`, `--skin-text-disabled` | Ordinary text hierarchy |
| `--skin-text-link`, `--skin-text-link-hover` | USS-controlled link text |
| `--skin-action-primary-*`, `--skin-selection-*` | Filled actions and selection, including foregrounds |
| `--skin-control-*`, `--skin-field-*` | Neutral controls and fields |
| `--skin-feedback-*` | Paired success, information, warning and danger colours |
| `--skin-card-border-*`, `--skin-dialog-*` | Report-card edges and floating-dialog chrome |
| `--skin-radius-*` | Shared corner scale |
| `--skin-font-family-*`, `--skin-font-size-*` | Font families and size scale |
| `--skin-chart-series-*`, `--skin-comparison-*` | Categorical chart and comparison colours |

FM's ordinary `--global-text-primary` contract maps to the theme's primary ink.
It does not control every embedded rich-text span; see the
[known limitations](../README.md#known-limitations).

## Editing rules

- Keep filled surfaces paired with their foreground through rest, hover, focus,
  pressed and disabled states. Volt action/selection fills use dark ink.
- Use semantic theme variables in component colour declarations. Preserve
  independent club, competition, result, tactics and player-status colours.
- USS uses explicit RGB/RGBA values. When changing an opaque colour, update its
  matching `-alpha-*` RGB channels too.
- Loose font and image URLs resolve from the skin root. For example, use
  `fonts/Poppins-Regular.ttf` from `theme.uss`.
- Poppins Regular and Bold are bundled under the SIL Open Font License.
  Competition font roles refer to FM's own resources; no UEFA font files ship.
- Native bindings and inline rich-text paint can override stylesheet values.
  Check the rendered result, including disabled controls and linked names.
- Keep rectangular control radii separate from functional circles, chart dots,
  pitch marks and portrait masks.
- Header paint-extension/overlap pairs must remain equal and opposite. Any
  paired paint/content scales must multiply to one to preserve native layout.

Save changes and reload or reapply the skin in FM. Check representative pages
and interaction states after each change; successful parsing alone does not
prove that the game renders every state correctly.
