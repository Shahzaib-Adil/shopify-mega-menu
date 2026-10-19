# Dynamic Mega Menu (Shopify Dawn)

A header section with a data-driven mega menu. Top-level items come from a Shopify Navigation menu. Panel content is entered in the theme editor and linked to a menu item by title or handle.

## Files

- `sections/mega-header.liquid`: the whole feature in one file (CSS, Liquid markup, JavaScript, and the section schema). No apps, no jQuery, no libraries.

## Install

1. Copy `sections/mega-header.liquid` into the Dawn theme's `sections` folder.
2. In `layout/theme.liquid`, replace `{% sections 'header-group' %}` with `{% section 'mega-header' %}`, or add the section in the theme editor and remove Dawn's default header.
3. Open the theme editor and select **Mega header**.

## How the owner links panel data to a menu item

1. Online Store > Navigation: create or edit a menu (for example `Main menu`) and add the top-level items.
2. In the theme editor, open **Mega header** and choose that menu under **Main menu**.
3. Click **Add block > Mega panel**.
4. In **Menu item (title or handle)** type the title (for example `Features`) or handle (`features`) of the menu item. Matching is not case-sensitive.
5. Fill in the panel:
   - 6 cards: icon, title, description, link
   - Explore: small label, video (or image), title, text, link label, link
   - Footer row: round icon, text, inline link, button label, button link
6. The small gray heading at the top left of the panel is the menu item's title.

A menu item with no matching block stays a normal link: no chevron, no panel.

## Behaviour

- Desktop: hovering a menu item that has a panel opens it. The panel closes on mouse leave (120 ms delay so the pointer can cross the gap), on click outside, or on Escape. The chevron button also toggles it (touch and keyboard).
- Explore video: `autoplay loop muted playsinline`. It plays while its panel is open and pauses when closed.
- Mobile (under 990px): burger button opens the menu, and panels become an accordion. The Explore column is hidden to keep the mobile layout simple.
- Typography and colors for nav links, button, headings, cards, Explore block and footer row are editable in the section settings.

## How the matching works

For each menu link, the section loops over the Mega panel blocks and compares the block's "Menu item" text (trimmed, lowercased) with the link's lowercased title and with the link's handle. The first match is rendered as that link's panel. Filters are applied in `assign` tags before the `if`, because Liquid does not allow filters inside conditions.

## Unfinished / notes

- Colors, sizes and spacing were matched to the Figma design by eye and the section settings; small differences from Dev Mode values may remain.
- The Explore column is not shown on mobile.
- The logo area is hidden by CSS (the design shows only the nav pill), so the Logo setting has no visible effect.
- Maximum of 8 panels per section (set in the schema).
- Tested in the theme editor preview only; not tested in every browser.
