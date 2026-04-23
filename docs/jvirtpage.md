# jvirtpage.css - Render a virtual page view in Joplin's previewer

jvirtpage.css is a stylesheet that will enable any note within the Joplin
application to render as an aesthetically pleasing virtual page in the Joplin
markdown viewer (the previewer).

### TL;DR

1. Install Joplin's "Import Local CSS" plugin and restart
2. Create note in Jopin and add these three lines to the top …

```html
<style>
    @import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
</style>
```

Alternatively, to enable this CSS for all of your notes by default …

1. Install Joplin's "Import Local CSS" plugin and restart
2. Created a note that will be imported by other notes …

~~~html
```css
@import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
```
~~~

 3. right-click on the new CSS note and "Copy markdown link"
 4. Tools >  Options > Local CSS > Global CSS > insert link you just copied

> LIMITATION: The "Global CSS" option only extends to the rendered view. If you
> want the CSS to be applied to the exported note, you have to use the first
> method listed above method shown above.

By default, the page will be …

- US Letter with 1in margins
- Black text
- White paper
- Darkened "desktop"

All of these are are adjustable with switches (see all switches below). For
example, if I wanted to make the note in the dimensions of A4, and use a dark
theme instead of a light them …

```html
<style>
    @import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
</style>
<div id="jvp" class="A4 dark"></div>

Here is my note, with the page-dimensions aligning with A4.
```

BUT. If you wish, for example, A4 as your default for all imports of
jvirtpage.css. Create a `jvirtpageA4.css` stylesheet with this content and
import it instead:

```css
/* jvirtpageA4.css */
@import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
:root {
    --jvp-page-width:  var(--jvp-page-widthA4);
    --jvp-page-height: var(--jvp-page-heightA4);
    --jvp-page-margin: var(--jvp-page-marginA4);
}
```

Since I commonly turn off syntax highlighting on code blocks, PDF display, and
titles and dates when I export, I could do this on every note …

```html
<style>
    @import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
</style>
<div id="jvp" class="no-syntax no-pdf no-title no-date"></div>

Here is my note. It will appear on a US-letter-dimensioned page, no Joplin
PDF expansion will occur, there will be no syntax highlighting if I have
fenced code blocks. And if I export to a PDF, no title nor update date will be
shared.
```

But I use that often enough that I created my own stylesheet where those are
the defaults …

```css
/* jvirtpage-mydefaults.css */
@import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
:root {
    #rendered-md pre * { color: var(--jvp-text-color); } /* no-syntax */
    --jvp-pdf-display: none;   /* no-pdf */
    --jvp-title-display: none; /* no-title */
    --jvp-date-display: none;  /* no-date */
}
```

Finally, sometimes I want to turn off the virtual page for a bit. Maybe I am
testing some other layout of something. I don't have to comment out the
`@import`. I just add `off` to the set of classes …

```html
<style>
    @import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
</style>
<div id="jvp" class="off no-syntax no-pdf no-title no-date"></div>

Here is my note. I added the off switch to the set of classes and so, this
note will be temperarily not styled to look like a virtual page. All I have to
do is remove off from the list of classes and the view will switch right back.
```

&ZeroWidthSpace;

That's the TL;DR and should get you 90% of the way to where you want to go
with this.

&ZeroWidthSpace;

&ZeroWidthSpace;



# More detail …

## Methods of Enabling the Stylesheet

There are five ways to enable this stylesheet for a note. Either … (1) import
it into your note from the filesystem, or (2) import it into your note from the
web, (3) import it from a dedicated stylesheet note, (4) configure the "Import
Local CSS" plugin to set the stylesheet as the default for all notes, or (5)
add the stylesheet to `userstyle.css`.

> Do this first before doing anything else:  
> In Joplin, install the "Import local CSS" Joplin plugin (and restart).

Four ways to import the stylesheet:

```html
<style>
    @import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
    @import "/path/to/joplin-tweaks/jvirtpage.css";
    @import "https://mywebserver.example.com/pub/jvirtpage.css";
    @import ":/7d66d959fa974468b4670db7228943a1";
</style>
```

1. Using the stylesheet directly from the repository

Note, I do break the upstream stylesheet from time to time, so … if it flakes
out on you, that may be what happened.

```html
<style>
    @import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
</style>
```

2. Importing the stylesheet from the filesystem …

- Download the whole repository from https://github.com/taw00/joplin-tweaks
  using `git clone https://github.com/taw00/joplin-tweaks` or just a manual
  download. Or just download `jvirtpage.css` (it has no dependencies).
- Add this to the top of your note …

```html
<style>
    @import "/path/to/joplin-tweaks/jvirtpage.css";
</style>
```

3. Importing the stylesheet from the web …

- Grab the style sheet similarly to step 2. But on your own webserver.
- Make sure it has the right permissions so that your webserver can serve it.

```html
<style>
    @import "https://mywebserver.example.com/pub/jvirtpage.css";
</style>
```

4. Import from a Joplin note …

- Create note. Name it something like `jvirtpage.css-note`
- Copy this stylesheet into the note (or @import the github link)
- Wrap the whole thing in a ``\`css and ``\` fenced code block
- Right click on the css note and "Copy Markdown Link"
- Use only the `:/HASHVALUE` part of it (the one in the example is just an
  example)

~~~html
```css
/* jvirtpage.css-note */
@import "https://taw00.github.io/joplin-tweaks/jvirtpage.css";
:root {
    /* if I want to turn off PDF expansion by default */
    --jvp-pdf-display: block;
}
```
~~~

- in your notes, import that note …

```html
<style>
    @import ":/7d66d959fa974468b4670db7228943a1";
</style>
```

4. If you want this formattting available by default for ALL of your notes …

- Perform step 3 above.
- Add the copied link to Tools > Options > Import CSS > Global CSS:
  `[jvirtpage.css](:/7d66d959fa974468b4670db7228943a1)`
- This configuration must be repeated on each device.

5. If you want this formattting available by default for ALL of your notes
   (desktop Joplin only) …

Copying the entire stylesheet into your `userstyle.css` configuration file.
That can be found

- On linux and macOS: `~/.config/joplin-desktop/userstyle.css`
- One windows: `C:\users\<username>\.config\joplin-desktop\userstyle.css`

Steps …

- Download `jvirtpage.css`
- Open `jvirtpage.css` and `userstyle.css` in an editor.
- Cut and paste all of `jvirtpage.css` into `userstyle.css`
- If you already have some things configured in `userstyle.css` I leave it to
  you to merge to the concepts.

For both options (4) and (5), if you want to modify the behavior of the
rendering to a virtual page, you simply insert the line
`<div id="jvp" class=""></div>` anywhere in your note. Some you will likely add
a `<div id="jvp" class="off"></div>` because you want to turn it off for that
note.

Good luck. —t

&ZeroWidthSpace;

&ZeroWidthSpace;

&ZeroWidthSpace;

## Usage Notes

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

If you want to change the default behavior for a single note, add this line
anywhere in your note …

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
  Dim theme or dark theme. A more white-paper-like them with black text is the
  default.
- `no-syntax`\
  Eliminate all fenced code block syntax coloration.
- `native-code`\
  All code—inline or fenced—will be themed according to native Joplin, even if
  it conflicts with the theme of jvirtpage.css.
- `no-1st-page-marker`  
  Turns off the marker that notes the page length of the current configuration.
- `no-pdfs`  
  Turns off rendering of PDFs in the note.
- `show-pdfs`  
  Turns on rendering of PDFs in the note. (Only useful if you turn it off by
  default by editing the initial constant value within the CSS.)
- `no-notes`  
  Turns off rendering of jvp notes within the document.
- `show-notes`  
  Turns on rendering of jvp notes within the document. (Only useful if you turn
  it off by default by editing the initial constant value within the CSS.)
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

—

Enjoy!

Copyright (c) Todd Warner  
This work is licensed under Attribution 4.0 International. To view a copy
of this license, visit http://creativecommons.org/licenses/by/4.0/
