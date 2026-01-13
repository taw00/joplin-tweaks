# jvirtpage.css - Render a virtual page view in Joplin's previewer

jvirtpage.css is a stylesheet that will enable any note within the Joplin
application to render as an aesthetically pleasing virtual page in the Joplin
markdown viewer (the previewer).

> ### TL;DR
>
> 1. download this repository
> 2. install the "Import Local CSS" plugin and restart Joplin
> 3. add this to the top of your notes
> ```html
> <style>
>     @import url("/path/to/joplin-tweaks/jvirtpage.css");
> </style>
> ```
>
> Alternatively, to enable this CSS for all of your notes by default …
> 3. cut-n-paste `jvirtpage.css` into a note, but surrounded by
> ~~~html
> ```css
> this CSS document inserted here
> ```
> ~~~
> 4. right-click on the new CSS note and "Copy markdown link"
> 5. Tools >  Options > Local CSS > Global CSS > insert link you just copied
>
> LIMITATION: The "Global CSS" option only extends to the rendered view. If you
> want the CSS to be applied to the exported note, you have to use the @import
> method shown above.

By default, the page will be …
- US Letter with 1in margins
- Black text
- White paper
- Darkened "desktop"

> All of these are are adjustable. See "switches" below.

Exported to PDF or Print will do what you expect preserve the page dimensions
and margins.

## Methods of Enabling the Stylesheet

There are five ways to enable this stylesheet for a note. Either … (1) import
it into your note from the filesystem, or (2) import it into your note from the
web, (3) import it from a dedicated stylesheet note, (4) configure the "Import
Local CSS" plugin to set the stylesheet as the default for all notes, or add
the stylesheet to `userstyle.css`.

> Do this first before doing anything else:  
> Install the "Import local CSS" Joplin plugin (and restart).

1. Importing the stylesheet from the filesystem …

- Then do this at the top of your note …
```html
<style>
    @import url("/path/to/joplin-tweaks/jvirtpage.css");
</style>
```

2. If you are importing this into your note from the web …

- Stick the `jvirtpage.css` somewhere on the web where it is accessible to
  your system
- Change the `@import` example above to look something like:
  `@import url("https://mywebserver.com/pub/jvirtpage.css";`

3. If you want to import from a "CSS note" …

- Create note. Name it something like `jvirtpage.css`
- Copy this stylesheet into the note
- Wrap the whole thing in a ``\`css and ``\` fenced code block  
  *You may have to delete all of the preliminary comments (they sometimes break the plugin)*
- Right click on the css note and "Copy Markdown Link"
- Use only the :/HASHVALUE part of it and, for example …
  `@import url(":/7d66d959fa974468b4670db7228943a1");`

4. If you want this formattting available by default for ALL of your notes …

- Perform step 3 above.
- Add the copied link to Tools > Options > Import CSS > Global CSS:
  `[jvirtpage.css](:/7d66d959fa974468b4670db7228943a1)`
- This configuration must be repeated on each device.

4.b. If you want this formatting available by default for all notes, but only
enabled with a switch …

- Perform step 4 above
- Edit the CSS note and uncomment the `:has( div#jvp ) {`  and `}` lines that
  wrap `@media screen` and `@media print`
- Add `<div id="jvp"></div>` to any note you wish to be rendered as a virtual
  page. In this case, without the `<div>` element, the page will be rendered
  according to Joplin's defaults.

5. Add stylesheet to `userstyle.css` (not recommended)

If you cut-n-paste this styles sheet into the `userstyle.css` inside the
`joplin-desktop` folder (Linux/macOS: `~/.config/joplin-desktop/` -or- Windows:
`C:\Users\%USERNAME%\.config\joplin-desktop\`) the styles will also be
persistent AND available to Joplin Cloud published notes. But, it's messy and I
don't recommend it. Instead, if you want the styles to be enabled for a
published note, I would instead directly import the stylesheet (option 2 or 3).

&ZeroWidthSpace;

## Usage

Once imported into a note or enabled for all notes, the default behavior should
be evident. The preview for the styled note should be rendered as a "virtual
page".

Again, by default, the page will be …

- US Letter with 1in margins
  - 8.5in x 11in at maximum view
    - note that the length is infinite in the preview because the preview is
      note a "page" really, but …
    - a 1st-page marker is added so that you have an idea as to the length of a
      page.
  - The virtual page will shrink if need be when the viewport shrinks.
- Black text
- White paper
- Darkened "desktop"

### Switches

If you want to change the default behavior, add this line anywhere in your
  note …
`<div id="jvp" class="SWITCH"></div>`

SWITCH can be one of …

- `off`  
  This will disable all of `jvirtpage.css`'s functionality.
  I.e., if you want to turn off these stylings for a particular note, just add
  `<div id="jvp" class="off"></div>`
  anywhere within that note.
- `US`, `A4`, `A5`, `A6`, or `USh`  
  Page dimension switches (`USh` means US Half-letter). `US` is the default.
- `landscape`  
  Switch that flips the width x height. Default is portrait.
- `dim` or `dark`  
  Theme switches. Black text on a white page on a gray backound is the
  default.
- `no-1st-page-marker`  
  Turns off the marker that notes the page length of the current configuration.
- `no-pdf`  
  Turns off rendering a PDF in the note.
- `show-pdf`  
  Turns on rendering a PDF in the note (only useful if you turn it off by
  default by editing the initial constant value within the CSS).
- `no-links`  
  This will turn off all link functionality within a note and attempt to set
  their stylings to something neutral.
- `no-links-export` —affects exported notes only
  This will turn off all link functionality within an *exported* note and
  attempt to set their stylings to something neutral.
- `show-title` —affects exported &amp; Joplin Cloud rendered notes only
  Upon export to PDF or HTML, or upon publish to Joplin Cloud, turn on view of
  the note title. (default is off)
- `show-date` —affects Joplin Cloud rendered notes only
  Upon publish to Joplin Cloud, show Last Update date.
- `help`
  Display a help summary at the top of your note.

For example, many (maybe most) of my notes are configured as such:  
`<div id="jvp" class="dark no-pdf"></div>`

-

Enjoy!

Copyright (c) Todd Warner  
This work is licensed under Attribution 4.0 International. To view a copy
of this license, visit http://creativecommons.org/licenses/by/4.0/

