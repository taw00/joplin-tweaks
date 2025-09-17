# jvirtpage.css - Render a virtual page view in Joplin's previewer

jvirtpage.css is a stylesheet that will enable any note within the Joplin
application to render as an aesthetically pleasing virtual page in the Joplin
markdown viewer (the previewer).

> ### TL;DR
>
> After downloading this repository, add this to the top of your notes …
> ```html
> <style>
>     @import url("/path/to/joplin-tweaks/jvirtpage.css");
> </style>
> ```

By default, the page will be …
- US Letter and 1in margins
  - 8.5in x 11in (though the length is infinite in the previewer.
    But we do add a 1st-page marker so that you have an idea as to the length
    of a page.
  - In the previewer, the page will shrink if need be when the viewport shrinks
- Black text
- White paper
- Darkened "desktop"

> All of these are are adjustable. See "switches" below.

Exported to PDF or Print will … do what you expect preserve the page dimensions
and margins. Except in the case of …

> ### [IMPORTANT NOTE: Joplin PDF Rendering Bug](https://github.com/laurent22/joplin/issues/13096)
> 
> Joplin 3.4.12 and older disallow exporting to PDF with a different page size
> than what you have set in the joplin settings. That limitation is a bug that
> should be fixed in the next major release.
> https://github.com/laurent22/joplin/issues/13096
>
> **The workaround** is to export to HTML, open that in a browser, then print
> to file (PDF). In a few months—as of this writing (20250916)—this will
> no longer be an issue.


## Methods of Usage

There are four ways to use this stylesheet. Either (1) import it into your note
from the filesystem, or (2) from the web, (3) import it from another note that
is only this stylesheet content, or (4) copy this file into your
`userstyle.css`.

1. If you are importing this into your note from the filesystem …

- Install the "Import local CSS" Joplin plugin (and restart).
- Then do this at the top of your note …
```html
<style>
    @import url("/path/to/jvirtpage.css");
</style>
```

- If you want to change the default behavior, add this line anywhere in your
  note …
`<div id="jvp" class="SWITCH"></div>`

SWITCH can be one of:
- US, A4, A5, A6, or USh
  Page dimension switches (USh means US Half-letter). US is the default.
- landscape
  Switch that flips the width x height. Default is portrait.
- dim or dark
  Theme switches. Black text on a white page on a gray backound is the
  default.

2. If you are importing this into your note from the web …

- Stick the `jvirtpage.css` somewhere on the web where it is accessible to
  your system
- Change the `@import` example above to look something like:
  `@import url("https://mywebserver.com/pub/jvirtpage.css";`

3. If you want to import from a "CSS note" …

- Create note. Name it something like `jvirtpage.css`
- Copy this stylesheet into the note
- Wrap the whole thing in a ``\`css and ``\` code block
- Delete all these preliminary comments (they break the plugin)
- Right click on the css note and "Copy Markdown Link"
- Use only the :/HASHVALUE part of it and, for example …
  `@import url(":/7d66d959fa974468b4670db7228943a1");`

4. Add to your `userstyle.css` - makes the virtpage persistent for all of
    your notes; no import needed! …
- copy the contents of this stylesheet into your Joplin user styles. Either,
- edit the styles in Tools > Options > General > Appearance >
  Show Advanced Settings > Custom stylsheet for rendered Markdown
- edit directly the userstyles.css file that can be found (if you created
  it previously) in the joplin-desktop folder on your computer. That's
  `~/.config/joplin-desktop/` on a linux system, for example.


If you want the virtual page to be rendered ONLY when <div id="jvp"></div>
exists, ucomment the `:has( div#jvp) {` block that wraps the `@media screen`
and `@media print` blocks.

JOPLIN CLOUD
If you want to use this with Joplin Cloud, you will have to import it from a
web url (option 2) or stick the styles in your userstyle.css (option 4).


Copyright (c) Todd Warner <t0dd@protonmail.com>
This work is licensed under Attribution 4.0 International. To view a copy
of this license, visit http://creativecommons.org/licenses/by/4.0/

