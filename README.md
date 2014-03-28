simple-css
==========

Simple.css is my attempt at the least amount of CSS (in addition to the browser default styles) needed to maximize the readability (clarity and economy of display) of English language web documents on both desktop and mobile devices.

HTML Requirements
-----------------

This should be in the head section:

    <meta name="viewport" content="initial-scale=1.0, user-scalable=no">

The body content of the page should be in a div with class "article."

    <div class="article"></div>

If you have a different content element, the CSS selectors should be changed appropriately.

Reasoning</h2>
--------------

Te thoughts behind this CSS are based on actual research, my first-hand experience, and some as yet unproven personal preferences. I am certain there are mistakes to be fixed and improvements to be added, but I am happy calling the above CSS "version 1.0."

ere is my reasoning for each style rule.

### Maximum Width

    body {max-width: 580px; }

Setting a maximum width may be the most important improvement to readability over default browser styles alone. Choose a random book from your shelf and open to any page. Count the words of a single line of paragraph text. Your measurement should fall in between 10 and 15 (or about 72 characters per line). This was not chosen randomly &mdash; the longer a line of text becomes, the easier it is to lose vertical eye position while reading a paragraph. <a href="http://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast-visual-presentation">The W3C Web Content Accessibility Guidelines recommend a maximum of 80 characters per line</a>.

When the Web was being invented, most screens were much smaller and lower resolution than today. Web documents that were easily readable full-screen then are now unacceptable maximized on a 24-inch, 1,920 pixel wide monitor, rendering many paragraphs as a single long line. A body width of 580 pixels is room for about 72 characters in my browser's default paragraph sans-serif font.

Today we have have gargantuan monitors on our desktops and wide screen televisions in our living rooms, but we also want to view content on the minuscule screens of our smart phones. One step to presenting content so that it is also readable on the smallest screens is the <code>&lt;meta&gt;</code> viewport HTML element mentioned above. This, plus using the <var>max-width</var> CSS property instead of <var>width</var> means that smaller devices should always make use of the entire screen width when displaying your content.

### Font Face

    html {font-family: droid sans, sans-serif; }

Traditional serif (extra little lines on the ends of letters) fonts were developed for printed text. Unfortunately, low-resolution monitors cannot render the fine detail needed to display the serifs. Even though screen resolution is high enough today to handle serif font faces, sans-serif fonts are still considered superior for screen readability, if only to support low-resolution devices.

Using the generic font-family <var>sans-serif</var> instead of a specific font face in the CSS declaration allows the target device to choose the preferred font (typically Arial for Microsoft products and Helvetica for Apple.) Droid Sans is a very nice sans-serif screen font developed for the Android operating system. Unfortunately it is not the default sans-serif font in their mobile browser so I included it in the CSS declaration.

### Floating Center

    body {margin: 0 auto; }

When a short-width document is displayed maximized in a very large monitor, by default it is flush against the left side. By centering the document content, we are positioning it directly in front of where the user's eyes will probably be. In my opinion, dividing the extra space between both sides of the content also feels more balanced compared to a massive blank area on the right side.

### Minimum Margins

    html {padding: 10px 10px 200px; }

For screen resolutions smaller than 580 pixels, we need to make sure there is a little space around the content so it is not smashed up against the top and sides of the browser window. It is also nice to add some extra white space after the end so the last of the content is not stuck to the bottom of the browser. This gives the user the freedom to scroll the final bits to a more natural reading position.

### Remove Top Margin from First Element

    div.article &gt; *:first-child {margin-top: 0; }

This CSS rule will make your content begin immediately after the 10px html top padding, instead of after a useless gaping blank spot caused by the browser's default margins applied to the first content element.

### Paragraph Line Height

    div.article p {line-height: 1.4em; }

Browsers' default line spacing of 1.2em is a little cramped. <a href="http://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast-visual-presentation">The W3C recommends at least 1.5 times the line height</a> which I agree looks better so I increased it slightly.

