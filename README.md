simple-css
==========

Simple.css is my attempt at the least amount of CSS (in addition to the browser default styles) needed to maximize the readability (clarity and economy of display) of English language web documents on both desktop and mobile web browsers.

    <!doctype html>
    <html>
    <head>
    <meta charset="utf-8">
    <meta name="viewport" content="initial-scale=1.0, user-scalable=no">
    <title></title>

    <style type="text/css">
    * {box-sizing: border-box; }
    html {padding: 10px 10px 200px; font-family: droid sans, sans-serif; }
    body {margin: 0 auto; max-width: 580px; }
    article > *:first-child {margin-top: 0; }
    li {margin-bottom: 0.3em; line-height: 1.4em; font-size: 16px; }
    h1 {font-size: 36px; }
    h2 {padding-bottom: 0.2em; border-bottom: 1px solid #bbb; font-size: 28px; }
    h3 {font-size: 24px; }
    h4 {padding: 0.2em; background: #eee; font-size: 20px; }
    p, h5 {line-height: 1.4em; font-size: 17px; }
    pre {padding: 1em; background: #eee; overflow: auto; }
    blockquote {margin: 16px 0; padding: 0 15px; color: #777; border-left: 4px solid #ddd; }
    table {border-collapse: collapse; }
    table td {border: 1px solid #ddd; padding: 6px 13px; }
    </style>

    <body>
    <article>
    <h1></h1>
    <p>
    </article>

HTML Requirements
-----------------

Other than the basic HTML5 document requirements, you will need two additional elements.

To more gracefully handle display on mobile devices, put this meta tag in the head section:

    <meta name="viewport" content="initial-scale=1.0, user-scalable=no">

The body content of the page should be in an `article` HTML element. There are some good reasons for this, but the most practical is that it is required to enable the "reader mode" feature in mobile Safari.

    <article></article>

If you use a different content element, the CSS selectors should be changed appropriately.

CSS Rules
---------

The reasoning behind the CSS is based on actual research, my first-hand experience, and some as yet unproven personal preferences. I am certain there are mistakes to be fixed and improvements to be added.

Here is my reasoning for each style rule.

### Box Sizing

    * {box-sizing: border-box; }

When setting height and width in CSS, it will now take into account the padding and borders in the final size.

### Maximum Width

    body {max-width: 580px; }

Setting a maximum width may be the most important improvement to readability over default browser styles alone. Take a random book off of the nearest shelf and open it to any page. Count the words of a single line of paragraph text. Your measurement should fall in between 10 and 15 (or about 72 characters per line). This was not chosen arbitrarily&mdash;the longer a line of text becomes, the easier it is to lose vertical eye position while reading. <a href="http://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast-visual-presentation">The W3C Web Content Accessibility Guidelines recommend a maximum of 80 characters per line</a>.

When the Web was young, most screens were much smaller and lower resolution than today. Web documents that were easily readable full-screen then are now unacceptable maximized on a 24-inch, 1,920 pixel wide monitor that render many paragraphs as a single, wide line. A body width of 580 pixels is room for about 72 characters in a 17px sans-serif font.

Today we have have gargantuan monitors on our desktops and wide screen televisions in our living rooms, but we also want to view the same content on the minuscule screens of our smart phones. How is this possible? One technique is the <code>&lt;meta&gt;</code> viewport HTML element mentioned above. This, plus using the <var>max-width</var> CSS property instead of <var>width</var> means that smaller devices should always make use of the full screen width when displaying your content.

### Font Face

    html {font-family: droid sans, sans-serif; }

Traditional serif (extra little lines on the ends of letters) fonts were developed for printed text. Unfortunately, low-resolution monitors cannot render the fine detail needed to display the serifs. Even though screen resolution is high enough today to handle serif font faces, sans-serif fonts are still considered superior for screen readability, if only to support low-resolution devices.

Using the generic font-family <var>sans-serif</var> instead of a specific font face in the CSS declaration allows the target device to choose the preferred font (typically Arial for Microsoft products and Helvetica for Apple.) Droid Sans is a very nice sans-serif screen font developed for the Android operating system. Unfortunately it is not the default sans-serif font in their mobile browser so I added it to the CSS declaration.

### Floating Center

    body {margin: 0 auto; }

When a short-width document is displayed maximized in a very large monitor, by default it is flush against the left side. By centering the document content, we are positioning it directly in front of where the user's eyes will probably be. In my opinion, dividing the extra space between both sides of the content also feels more balanced compared to a massive blank gap on the right side.

### Minimum Margins

    html {padding: 10px 10px 200px; }

For screen resolutions smaller than 580 pixels, we need to make sure there is a little space around the content so it is not smashed up against the top and sides of the browser window. It is also nice to add some extra white space after the end so the last of the content is not stuck to the bottom of the browser. This gives the user the freedom to scroll the final bits to a more natural reading position.

### Remove Top Margin from First Element

    article > *:first-child {margin-top: 0; }

This CSS rule will make your content begin immediately after the 10px html top padding, instead of after a useless gaping blank spot caused by the browser's default margins applied to the top of the first element.

### Paragraph Line Height

    p {line-height: 1.4em; }

Browsers' default line spacing of 1.2em is a little cramped. <a href="http://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast-visual-presentation">The W3C recommends at least 1.5 times the line height</a> which I agree looks better so I increased it slightly.

    p {font-size: 17px; }

I increased the paragraph font a little, but not so much that it looks bold.

    li {margin-bottom: 0.3em; line-height: 1.4em; font-size: 16px; }

I also included slightly different styles for list items. Document content should almost always be contained in an `h1`-`h6`, `p`, or `li` element, so the CSS should handle most pages.

### Header Styles

    h2 {padding-bottom: 0.2em; border-bottom: 1px solid #bbb; }
    h4 {padding: 0.2em; background: #eee; }

Headers of adjacent level are different to distinguish between, so I added a unique style to h2 and h4.

    h1 {font-size: 36px; }
    h2 {font-size: 28px; }
    h3 {font-size: 24px; }
    h4 {font-size: 20px; }
    h5 {font-size: 17px; }

Since the paragraph font is 17px, I adjusted the header font size to make relative sense.

Here is how they should look:

# H1 Header

## H2 Header

### H3 Header

#### H4 Header

##### H5 Header

###### H6 Header

### Prerendered Text

    pre {padding: 1em; background: #eee; overflow: auto; }

To display blocks of code, I add a background and a scrollable container.

### Block Quote

    blockquote {margin: 16px 0; padding: 0 15px; color: #777; border-left: 4px solid #ddd; }

Quotes are indented with a left side border.

### Tables

    table {border-collapse: collapse; }
    table td {border: 1px solid #ddd; padding: 6px 13px; }

Collapse space between cells and lighten default borders.

Don't Be Afraid to Add More
---------------------------

This CSS and HTML is a good starting point, but most page content will need more. I will revisit this if I find common content that requires additional styling. If you have suggestions, please submit an issue.
