# joplin-tweaks

Style customizations for [Joplin](https://joplinapp.org/), a secure
open-source, notebook application.

Included in this repository are snippets of CSS that customize the look and
feel of the Joplin UI, its markdown previewer, and how documents are presented
in Joplin Cloud.

&ZeroWidthSpace;

&ZeroWidthSpace;

> ### Table of Tweaks
> 
> #### [Tweaks for the Markdown Previewer & Joplin Cloud](#tweaks-renderer-md)
> 
> - Render Jopin note preview as a [virtual page](#jvirtpagecss) - jvirtpage.css
> - snippet (exported note): exported notes [should not include scrollbars](#noscrollbars)
> - snippet (exported note): [remove excess spaced framing](#noframe) of exported content
> - snippet (exported note): [remove automated note titles](#notitle) from exported note
> - snippet (rendered and exported note): [toggle the embedded display of linked-to PDF](#embeddedpdf)
> - snippet (rendered and exported note): [disable links](#disablelinks)
> 
> #### [Tweaks for the Joplin UI](#tweaks-ui)
> 
> - snippet (UI): [remove the markdown vs. rich text editor switch (button)](#noeditorswitch)
> - snippet (UI): [remove the tags widget](#notagswidget)
> - snippet (UI): [make the tags widget smaller](#smallertagswidget)

&ZeroWidthSpace;

&ZeroWidthSpace;

&ZeroWidthSpace;





# <span id="tweaks-renderer-md"></span>Tweaks for the Markdown Previewer & Joplin Cloud & Exported Notes

The snippets below are added to the `userstyle.css` style configuration file.
`jvirtpage.css` is expected to be imported into a document directly. See the
associated documentation.

&ZeroWidthSpace;

## <span id="jvirtpagecss">—</span> Render Jopin note preview as an attractive virtual page

Stylesheet: [jvirtpage.css](./jvirtpage.css)  
Documentation: [jvirtpage.md](docs/jvirtpage.md)

- Preview your document as an aesthetically pleasing virtual page that
  matches international standard dimensions for US Letter, US Half-letter, A4,
  A5, A6 pages. Themeable: default (white page), dim, and dark views.
- Render the document to those dimensions when you export to PDF.
- For more detail, please read the documentation:
  https://github.com/taw00/joplin-tweaks/docs/jvirtpage.md

### Quickstart guide to `jvirtpage.css`

1. Download this repository …

`git clone https://github.com/taw00/joplin-tweaks`

2. Install Joplin's "Import Local CSS" plugin and restart

3. Create note in Joplin and add these three lines to the top …

```html
<style>
    @import url("/path/to/joplin-tweaks/jvirtpage.css");
</style>
```

4. Save, and you should see a pretty, virtualized page in the preview pane in
   the Joplin application.

5. Want an A5 landscape virtual page with a dark themed? Add this fourth line
   to your note …

```html
<div id="jvp" class="A5 landscape dark"></div>
```

### Example 1: no customization

![jvirtpage-default-us-letter](docs/images/jvirtpage-default-us-letter.png)

### Example 2: dark theme and A6 in a landscape orientation
![jvirtpage-dark-a6-landscape](docs/images/jvirtpage-dark-a6-landscape.png)

> ### [IMPORTANT NOTE: Joplin PDF Rendering Bug](https://github.com/laurent22/joplin/issues/13096)
> 
> Joplin 3.4.12 and older disallow exporting to PDF with a different page size
> than what you have set in the joplin settings. That limitation is a bug that
> should be fixed in the next major release. (Ref.
> https://github.com/laurent22/joplin/issues/13096)
>
> **The workaround** is to export to HTML, open that in a browser, then print
> to file (PDF). In a few months—as of this writing (20250916)—this will
> no longer be an issue.

&ZeroWidthSpace;

## <span id="noscrollbars">—</span> snippet (exported note): exported notes should not include scrollbars

[userstyle-snippet-exports-no-pre-scrollbars.css](./userstyle-snippet-exports-no-pre-scrollbars.css)

Joplin exports that include things like programming code will include
scrollbars in the PDF that are, of course, just visual clutter. Instead we
trim any code that extends beyond the visual window and remove any scrollbars.
It is up to the document creator to reformat those code blocks so that they
appear on the page completely.

&ZeroWidthSpace;

## <span id="noframe">—</span> snippet (exported note): remove excess spaced framing of exported content

[userstyle-snippet-exports-remove-padded-frame.css](./userstyle-snippet-exports-remove-padded-frame.css)

When exporting a raw note, Joplin will frame it and add margin space around the
note. We remove that when this snippet of CSS.

&ZeroWidthSpace;

## <span id="notitle">—</span> snippet (exported note): remove automated note titles from exported note

[userstyle-snippet-exports-remove-title.css](./userstyle-snippet-exports-remove-title.css)

Most of the time, I simply do not want Joplin adding a note title to my
exported content. If I want a title, I will add it to the note myself. This
snippet removes that inserted/automated title.

&ZeroWidthSpace;

## <span id="embeddedpdf">—</span> (#jtweaks switches) toggle behavior of linked-to PDF

[userstyle-snippet-toggle-embedded-pdf.css](./userstyle-snippet-toggle-embedded-pdf.css)

Joplin, by default, will expand a PDF within a functional viewport within a
note.  An embedded PDF, if you will. This feature is very convenient, but I
also don't have a need for it most of the time. This CSS snippet adds a toggle
of sorts. Add this snippet to your `userstyle.css` configuration and add
`<div id="jtweaks no-pdf"></div>` anywhere within your note to turn this
behavior off. And if you configured the CSS to turn off the display of PDFs by
default (like I do), do the same, but add
`<div id="jtweaks show-pdf"></div>` when you want to show that PDF.

*Note: This switch is also built into `jvirtpage.css`, and so, if you use both
there may be a conflict. Or not. Experiment. :)*

&ZeroWidthSpace;

## <span id="disablelinks">—</span> (#jtweaks switches) disable links for a note and/or exported PDF

[userstyle-snippet-disable-links.css](./userstyle-snippet-disable-links.css)

Sometimes you just wanna disable links in a note. Or, as if often the case,
in it's exported PDF. The `jweaks` switches are: `no-links` and
`no-links-export`

&ZeroWidthSpace;

&ZeroWidthSpace;

&ZeroWidthSpace;





# <span id="#tweaks-ui"></span>Tweaks to the Joplin UI

These are added to the `userchrome.css` styling configuration file.

&ZeroWidthSpace;

## <span id="#noeditorswitch">—</span> snippet (UI): remove the markdown vs. rich text editor switch (button)

[userchrome-snippet-remove-editor-switching-button.css](./userchrome-snippet-remove-editor-switching-button.css)

Do you only use the markdown editor and not the "rich text editor" then get rid
of that button that lets you toggle between the two.

&ZeroWidthSpace;

## <span id="notagswidget">—</span> snippet (UI): remove the tags widget

[userchrome-snippet-remove-click-to-add-tags.css](./userchrome-snippet-remove-click-to-add-tags.css)

Some folks don't use Joplin's tagging system at all. If so, maybe just remove
that bit of UI and give yourself some extra space.

&ZeroWidthSpace;

## <span id="smallertagswidget">—</span> snippet (UI): make the tags widget smaller

[userchrome-snippet-shrink-click-to-add-tags.css](./userchrome-snippet-shrink-click-to-add-tags.css)

Do you use tags, but wished the tags widget that sits below your note in the UI
was a bit smaller? This does exactly that.

&ZeroWidthSpace;

&ZeroWidthSpace;

&ZeroWidthSpace;





--- 

Joplin is Copyright (c) Laurent Cozic  

This readme, the documentation, and another additional work is …

Copyright (c) Todd Warner <t0dd [at] protonmail [dot] com>  
This work is licensed under Attribution 4.0 International. To view a copy of
this license, visit http://creativecommons.org/licenses/by/4.0/

If you have any questions or concerns, open an issue in Github or email me at
t0dd [at] protonmail [dot] com.

---

#### Thanking me?

Several people have asked how they could thank me for work that I have done
that they found valueable. Well, one easy way to thank me is to "buy me a cup
of coffee": <https://buymeacoff.ee/toddwarner> Or just send me an email (see
above) and express your appreciation. Or star this on Github. Or whatever.

Cheers!
