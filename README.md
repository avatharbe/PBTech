## PBTech Style for phpBB

PBTech is a tech-themed style for phpBB 3.3, inspired by the Blizzard Battle.net forums of 2015: a dark header, a light content area, and blue accent colours throughout.

![PBTech screenshot](contrib/screenshot.png)

The style is built as a child of **prosilver**. It keeps phpBB's standard markup, template events and responsive layout, and it picks up prosilver fixes automatically.

- **Version:** 3.0.29 (04-10-2026)
- **Authors:** PayBas (2015) and [@Sajaki](https://www.phpbb.com/customise/db/author/sajaki/) (since 2016)
- **Design reference:** [the Battle.net forums as they were in 2014](http://web.archive.org/web/20141207163104/http://us.battle.net/en/forum/topic/10423582376)

## Requirements
- phpBB 3.3.18 or higher
- prosilver (parent style)

## Features
- Dark-to-light gradient design with a tech-inspired header and logo.
- A complete custom icon set for forum, topic, sticky and announcement states.
- Online users marked by a glowing green dot before their name, shown consistently in posts and on the full profile.
- Collapsible forum categories. Each visitor's browser remembers which are open or closed.
- The last poster shown in the forum list.
- Styled breadcrumb tooltips.
- Restyled polls, quotes and code boxes.
- Font Awesome icons throughout, using phpBB's built-in Font Awesome.
- Styling for the Recent Topics extension, and compatibility with pbwowExt.
- Responsive layout for tablets and phones, plus a print view.
- Right-to-left (RTL) language support.

## Installation
1. Copy the `pbtech` folder into your forum's `styles` folder.
2. In the Administration Control Panel (ACP), go to **Customise → Styles → Install Styles** and install **PBTech**.

### Upgrading
1. Replace the `pbtech` folder with the new version.
2. Purge the board cache in the ACP.

## Designer resources
The `contrib` folder contains a Photoshop PSD with an alternative icon set.

## Support
- https://www.avathar.be/forum/viewforum.php?f=100

## Changes
See [contrib/CHANGELOG.md](contrib/CHANGELOG.md) for the full version history.

## Development
The repository includes lint tooling, With Node.js 24:

- `npm ci`, then `npm run lint` checks the theme CSS with stylelint and the templates with a phpBB-specific checker (legacy syntax, `DEFINE`, extension-owned variables). GitHub Actions runs the same on every pull request.
- `npm run validate` checks rendered pages of a running board with the W3C Nu HTML Checker. Set `BOARD_URL` to the board root, and `STYLE_ID` to force the style while *Override user style* is off.


## License
[GNU General Public License v2](https://opensource.org/licenses/GPL-2.0)

## Credits
- **Original author:** PayBas (2015)
- **Contributions:** Galixte, nfsmaniac
- **Maintainer:** [@Sajaki](https://www.phpbb.com/customise/db/author/sajaki/) ([avathar.be](https://www.avathar.be))

© PayBas, 2015

---

*Battle.net is a trademark of Blizzard Entertainment, Inc. PBTech is a fan-made style and is not affiliated with or endorsed by Blizzard Entertainment.*
