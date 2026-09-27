# PBTech changelog

Version history for the [PBTech style for phpBB](../README.md).

3.0.27 (27-09-2026)
- restored the underline on links inside posts: `.postlink` carried a `border-bottom` with a colour and no width or style, which is valid CSS that resets `border-style` to `none`, so prosilver's underline was removed and nothing replaced it - links were left identifiable by colour alone, at 1.00:1 against the surrounding text ([#46](https://github.com/avatharbe/PBTech/issues/46))
- removed the duplicate subforum icon: the forum list dropdown drew both a background sprite from `common.css` and `imageset.css` and the Font Awesome icon the template already renders ([#49](https://github.com/avatharbe/PBTech/issues/49))
- removed twelve colour-only `border` declarations that never had any effect, and the six rules left empty by them; prosilver draws no border on any of those elements, so nothing is lost ([#47](https://github.com/avatharbe/PBTech/issues/47))

3.0.26 (27-09-2026)
- restored the back-to-top arrow in topics: `viewtopic_body.html` had dropped the `<i class="icon fa-chevron-circle-up">` that prosilver renders, and `theme/links.css` sets `content: none` on the pseudo-element that could have stood in for it, so the link rendered nothing for sighted users ([#41](https://github.com/avatharbe/PBTech/issues/41))
- restored the chevrons on the search result arrow links - "Return to topic", "Go to advanced search" and "Jump to post" - the same dropped-icon defect in `search_results.html` and `navbar.html` ([#43](https://github.com/avatharbe/PBTech/issues/43))
- fixed the dropdown menu and profile card shadows, which rendered in the element's own text colour because the colour was given with no offsets, and deleted the dead `.dropdown-extended a.mark_read:before` rule ([#30](https://github.com/avatharbe/PBTech/issues/30))
- fixed the arrow-link hover glow, which rendered in the inherited text colour instead of blue ([#31](https://github.com/avatharbe/PBTech/issues/31))
- fixed the four button shadows, affecting every button on the board, including the blue hover glow ([#33](https://github.com/avatharbe/PBTech/issues/33))
- fixed the rank icon shadow in the post author column ([#32](https://github.com/avatharbe/PBTech/issues/32))
- fixed the post notice shadow ([#29](https://github.com/avatharbe/PBTech/issues/29))
- retargeted the poll title rule to `.topic_poll h2.poll-title`: the old `.topic_poll h2 span` selector matched no element in phpBB 3.3, so the rule had never applied ([#34](https://github.com/avatharbe/PBTech/issues/34))
- removed the forum rules box gradient rather than repairing it: making the declaration valid turned the box dark while the rest of the page stayed light, putting the text at 1.47:1 contrast ([#29](https://github.com/avatharbe/PBTech/issues/29))
- removed the author column text shadow rather than repairing it: `.postprofile` is also the search results author column, where the shadow read as a blur ([#32](https://github.com/avatharbe/PBTech/issues/32))

3.0.25 (27-09-2026)
- fixed Customisation Database validation blockers from the 3.0.21 denial ([#14](https://github.com/avatharbe/PBTech/issues/14))
- added missing `viewtopic_body_postrow_signature_before` and `viewtopic_body_postrow_signature_after` template events ([#23](https://github.com/avatharbe/PBTech/issues/23))
- fixed missing pagination arrows: removed the `template/pagination.html` override, which differed from prosilver's only by the dropped `<i class="icon fa-chevron-...">` and `fa-level-down` elements, so the parent's icons are inherited again; the orphaned RTL `:after` arrows in `theme/bidi.css` were removed with it, since they would otherwise draw a second arrow ([#24](https://github.com/avatharbe/PBTech/issues/24))
- changed the online indicator from the `«` `»` pair to a single dot before the username, and applied the same dot to the full profile, which showed no indicator at all because the `background:` shorthands on `.panel` and `.bg1, .bg2, .bg3` reset `background-image` to `none` ([#25](https://github.com/avatharbe/PBTech/issues/25))
- fixed blank search and ignore icons in the profile hover card: `theme/buttons.css` set `display: none` on `.profile-context .user-icons a:before`, cancelling the FontAwesome content defined in `theme/fontawesome.css` ([#26](https://github.com/avatharbe/PBTech/issues/26))
- replaced the hover card's ignore button with a private message button built from `postrow.U_PM` and `SEND_PRIVATE_MESSAGE`; the ignore link's URL was assembled in the template and its "Ignore user" title hardcoded, and `ADD_FOES` cannot replace it because it lives in `language/en/ucp.php`, which `viewtopic.php` never loads ([#26](https://github.com/avatharbe/PBTech/issues/26))
- fixed invalid `text-shadow` on the online indicator (a bare colour with no offsets, so the glow never rendered) ([#25](https://github.com/avatharbe/PBTech/issues/25))
- fixed white table headers on light backgrounds outside `.panel-container`: the postlove most-liked summary measured 1.52:1 contrast and the memberlist and team headers 1.19:1; `table.table1 thead th` is no longer panel-scoped ([#16](https://github.com/avatharbe/PBTech/issues/16))
- removed 92 dead CSS declarations superseded by a later declaration of the same property on an identical selector (no rendering change: 0 computed-style differences across 31,337 elements on 8 pages at 1280/700/500/430px) ([#5](https://github.com/avatharbe/PBTech/issues/5))
- removed `theme/responsive.css`: never imported or linked, and drifted out of the style - its first 39 lines sit outside any media query and set a dark `.page-body` background plus rules for the top bar removed in 3.0.22 ([#5](https://github.com/avatharbe/PBTech/issues/5))

3.0.24 (24-09-2026)
- aligned with phpBB 3.3.18 prosilver
- refreshed `theme/images/icons/icons_contact.png` from prosilver 3.3.18: the pm, skype, twitter and aol icons were redrawn, and prosilver's inherited `.phpbb_twitter-icon` position moved from `-203px` to `-202px`, so the sprite and the position have to be updated together
- inherits the new `mcp_topic_postrow_post_after` template event automatically — pbtech does not override `mcp_topic.html`

3.0.23 (24-09-2026)
- aligned with phpBB 3.3.17 prosilver
- inherits the prosilver `login_body_oauth.html` fix automatically (`oauth.REDIRECT_URL` renamed to `oauth.LOGIN_URL`) — pbtech does not override that template

3.0.22 (24-09-2026)
- fixed unclickable footer links (Privacy, Terms, the phpBB and PBWoW credits, and the ACP link): pbwowext's WebKit `z-index: auto` reset promotes its decorative `#video-background` layer into the `z-index: 0` layer, where it swallowed clicks on the static `#page-footer`; `theme/extensions.css` now sets `pointer-events: none` on that layer ([#7](https://github.com/avatharbe/PBTech/issues/7))
- removed the hardcoded top bar (`template/top_bar.html`, `theme/topbar.css` and its `@import`): demo scaffolding with a dead `href="#"` and two language keys undefined in the pack (`PHPBB`, `LINK`), which also clashed with pbwowext's own `#top-bar` id ([#9](https://github.com/avatharbe/PBTech/issues/9))

3.0.21 (30-04-2026)
- aligned with phpBB 3.3.16 prosilver ([#6](https://github.com/avatharbe/PBTech/issues/6))
- ported null-safety checks for `U_NEWEST_POST`, `U_VIEW_TOPIC`, `U_LAST_POST` in search_results.html and viewforum_body.html (avoids broken anchors when URLs are empty)
- fixed watch-forum toggle icon: `data-toggle-class` now flips to the opposite icon on click (was unchanged in 3.0.20)
- inherits prosilver `ucp_pm_viewmessage_message_content_before` event and viewtopic_topic_tools watch-icon fix automatically (pbtech does not override those templates)
- inherits prosilver `ul.topiclist dfn` accessibility cleanup automatically (pbtech does not override the rule)

3.0.20 (30-04-2026)
- fixed Customisation Database validation blockers
- fixed empty mark-forums and view-unread links: added inline FontAwesome icons and sr-only labels
- fixed mislabelled Who-is-Online link (LAST_POST_IMG → arrow icon + sr-only label)
- fixed double search icon at responsive widths (removed redundant `icon-search` class on responsive-search li)
- fixed double pagination chevrons (removed redundant li.next/previous/page-jump :after pseudo-rules)
- fixed breadcrumb tooltips clipped on hover (truncation moved onto inner [itemprop="name"] span)
- removed duplicate BootstrapCDN @font-face declaration (T_FONT_AWESOME_LINK already loads FA locally)
- simplified mark-forums template branching (dropped redundant U_SITE_HOME / S_USER_LOGGED_IN guards)
- cleaned up colours.css select rule (dead declarations + padding-inline-end)

3.0.19 (04-04-2026)
- added missing theme/print.css for print view
- added styled CSS tooltips for breadcrumb links (replaces native browser tooltips)
- fixed post background: invalid multi-gradient CSS caused fallback to wrong colour; replaced with light grey gradients
- fixed low contrast: postprofile username (#DDD on light bg) changed to #0072a3
- fixed low contrast: blockquote text (#CCCCCC on light bg) changed to #555
- fixed search results: topic status icons tiling across full row width (missing background-repeat)
- fixed search results: changed dl.icon to dl.row-item for proper column alignment and font rendering
- fixed post content text-align: changed justify to left
- fixed postprofile text-align: changed center to left, added left padding
- fixed duplicate quote sigils: removed decorative blockquote:before/:after (prosilver cite:before suffices)
- fixed duplicate arrow icons: suppressed CSS :before/:after arrows (prosilver template provides icons)
- fixed notification popup header/footer colour mismatch (#4d606d to #555)
- fixed button font-size: override prosilver 13px to 12px
- fixed forum titles and recent topics titles: dark blue (#074E79) to black
- aligned forum blocks and recent topics row backgrounds (#DCDBD9 base, #E6E6E6 hover)
- CSS lint cleanup: merged duplicate selectors and removed dead code across all theme files (87 to 49 issues)

3.0.18 (27-03-2026)
- added missing template events for phpBB 3.3.15 compliance (forumlist_body, search_results)
- added last poster username display to forum list
- removed custom quickstyle_event; use default overall_header_breadcrumbs_after location ([#3](https://github.com/avatharbe/PBTech/issues/3))
- fixed poll block dark background and thick black border
- fixed UCP message colour legend thick border
- fixed incomplete text-shadow in online user guillemets (content.css)
- fixed duplicate closing tag in navbar_footer.html
- fixed broken child-arrow-big.gif reference (now .png)
- removed dead CSS: video-background, mChat, pf_pbbnetavatar, action-bar.compact
- consolidated duplicate CSS rules (vote-submitted, postprofile avatar, poll styles)
- replaced deprecated jQuery .bind() with .on()
- fixed schema.org URL to use HTTPS
- fixed non-standard background-repeat-x/y
- added cache-bust parameter to imageset.css import

3.0.17 (22-02-2026)
- fixed hardcoded assets_version in prosilver stylesheet link
- removed unnecessary prosilver en/stylesheet.css
- removed tweaks.css IE conditional
- use T_FONT_AWESOME_LINK instead of hardcoded CDN URL
- updated webfont URL in simple_header.html
- removed dead CSS rules referencing missing images (poll icons, imageset)
- replaced missing border images with CSS borders in responsive view
- simplified quick-login panel styling (removed missing image references)

3.0.16 (08-02-2026)
- updated for phpBB 3.3.15
- updated post display links to use AJAX anchors (viewtopic)
- added viewtopic_body_postrow_content_before event
- added viewtopic_body_online_list_after event
- added forum link type detection in forumlist tooltips
- updated autocomplete attributes on login forms
- simplified search results sort condition
- merged overall_header.html from prosilver 3.3.15

3.0.15 (10/01/2020)
- updated for phpbb 3.3.2

3.0.14 (03/01/2020)
- updated for phpbb 3.2.10 ([#2](https://github.com/avatharbe/PBTech/issues/2))

3.0.13 (24-10-2020)
- updated for phpbb 3.1.11
    
3.0.12 (21-02-2017)
- stylesheet.css refactored into separate files
- pbwow.css merged to other css files

3.0.11.1 (21-02-2017)
- style validation fix.

3.0.11 (15-12-2016)
- style validation fix.

3.0.9 (05-11-2016)
- updated for phpbb 3.1.10

3.0.8.2 (05-11-2016)
- fix top margin of avatar

3.0.8.1 (26-6-2016)
- new design for Polls
- new design for Top bar
- new design for Rules
- changed colors for Bbcode code box
- updated Fontawesome to 4.6
- fix for Recent topics

3.0.8 (12-6-2016)
- updated for phpbb 3.1.9
- updated for Recent Topics v2.1

3.0.7 (05-3-2016)
- updated for phpbb 3.1.8

3.0.6 (05-3-2016)
- updated for phpbb 3.1.7

3.0.5 (05-3-2016)
- updated for phpbb 3.1.6
