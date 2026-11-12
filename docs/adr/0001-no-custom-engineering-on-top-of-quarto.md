# No custom engineering on top of Quarto

The site's look is changed only through SCSS, the brand extension (see ADR 0002) and Quarto's built-in options (listing types, about templates, theme layers). Custom EJS listing templates, Lua filters and JavaScript are out. During the 2026 "Engineer's notebook" redesign, a custom EJS listing template was built and then removed again: it looked slightly better, but the site would have had to be maintained alongside Quarto upgrades, and the time is better spent writing Posts. If something can't be done with built-in features plus SCSS, it isn't done.
