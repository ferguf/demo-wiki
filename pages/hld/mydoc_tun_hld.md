---
title: Authoring a Lumen Doc
tags: [getting_started, formatting, content_types]
keywords: pages, authoring, exclusion, frontmatter
last_updated: July 16, 2016
summary: This theme primarily uses pages. You need to make sure your pages have the appropriate frontmatter.
sidebar: mydoc_sidebar
permalink: mydoc_tun_hld.html
folder: hld
---

## Where to author content
Use a text editor such as atom, Sublime Text, WebStorm, IntelliJ or Visual Studio Code to create pages. Atom is recommended because it's created by Github, which is driving some of the Jekyll development through Github Pages.

## Git hub account
you should signup and get a Github account, you can then download this repo and start editing 

## Where to save pages on Lumen Doc
You *MUST* store your pages in the \_hld folders and in the appropriate subdirectory that is based on product or technology, Jeykll supports any level of folder nesting.

TUNs are stored in:

- \_posts\AS3356
- \_posts\AS3549
- \_posts\AS209
- \_posts\Metro
- \_posts\Transport
- \_posts\Access

HLDs are stored in:

- \_hld\AS3356
- \_hld\AS3549
- \_hld\AS209
- \_hld\Metro
- \_hld\Transport
- \_hld\Access

The site output will pull all of those pages out of their folders and put them into the root directory. Check out the \_site folder, which is where Jekyll is generated, to see the difference between your project's structure and the resulting site output.

The listing of all pages in the root directory (which happens when you add a permalink property to the pages) is what allows the relative linking and offline viewing of the site to work.

## Frontmatter

Make sure each page has **frontmatter** at the top like this:

```yaml
---
title: TUN - Metro - sample configuration
tags: tun , metro  
keywords: Cisco , ECN , colorless, Metro 3.0
last_updated: July 3, 2021
summary: "You can insert notes, tips, warnings, and important alerts in your content."
layout: hld_layout.html
sidebar: TUN_sidebar
published: true
permalink: TUN_Metro_"XXX".html
---
```

Frontmatter is always formatted with three hyphens at the top and bottom.
Your frontmatter must have a `title` and `permalink` value.
[*tags*][Icons](mydoc_tags.html) are used to group and organize documents.
 All the other values are optional.

Note that you cannot use variables in frontmatter.

The following table describes each of the frontmatter that you can use with this theme:

| Frontmatter | Required? | Description |
|-------------|-------------|-------------|
| **title** | Required | The title for the page |
| **tags** | Optional | Tags for the page. Make all tags single words, with underscores if needed (rather than spaces). Separate them with commas. Enclose the whole list within brackets. Also, note that tags must be added to \_data/tags_doc.yml to be allowed entrance into the page. This prevents tags from becoming somewhat random and unstructured. You must create a tag page for each one of your tags following the pattern shown in the tags folder. (Tag pages aren't automatically created.)  |
| **keywords** | Optional | Synonyms and other keywords for the page. This information gets stuffed into the page's metadata to increase SEO. The user won't see the keywords, but if you search for one of the keywords, it will be picked up by the search engine.  |
| **last_updated**  | Optional | The date the page was last updated. This information could helpful for readers trying to evaluate how current and authoritative information is. If included, the last_updated date appears in the footer of the page in small font.|
| **sidebar** | Required | Refers to the sidebar data file for this page. Don't include the ".yml" file extension for the sidebar &mdash; just provide the file name. If no sidebar is specified, this value will inherit the `default` property set in your \_config.yml file for the page's frontmatter. |
| **summary** | Optional | A 1-2 word sentence summarizing the content on the page. This gets formatted into the summary section in the page layout. Adding summaries is a key way to make your content more scannable by users (check out [Jakob Nielsen's site](http://www.nngroup.com/articles/corporate-blogs-front-page-structure/) for a great example of page summaries.) The only drawback with summaries is that you can't use variables in them. |
| **permalink**| Required | The permalink *MUST* match the *filename* in order for automated links to work. Additionally, you must include the ".html" in the filename. Do not put forward slashes around the permalink (this makes Jekyll put the file inside a folder in the output). When Jekyll builds the site, it will put the page into the root directory rather than leaving it in a subdirectory or putting it inside a folder and naming the file index.html. Having all files flattened in the root directory is essential for relative linking to work and for all paths to JS and CSS files to be valid. |
| **datatable** | Optional | 'true'. If you add `datatable: true` in the frontmatter, scripts for the [jQuery Datatables plugin](https://www.datatables.net/) get included on the page. You can see the scripts that conditionally appear by looking in the \_layouts/default.html page. |
| **toc** | Optional | If you specify `toc: false` in the frontmatter, the page won't have the table of contents that appears below the title. The toc refers to the list of jump links below the page title, not the sidebar navigation. You probably want to hide the TOC on the homepage and product landing pages.|

what is this

## Including the Links and Page Content

The last line of the file MUST include the follow config which pulls in the *Content and the links* of the current page, without this the page content will NOT display:

{% raw %}
{% include links.html %}
{% endraw %}


{% include warning.html content="Every document needs the to add this statement to create linkage to get sidebars menus working correctly" %}

Adding text here

## Dynamically updating Pages and links

Here is the **frontmatter** for a HLD with

* tags: - used for dynamic Page creation
* keywords: - used for search in the nav panel
* date: - (year-month-day) used for sorting in the liquid template
* layout: - hld is used to present the page with a specific layout
* sidebar: - loads the HLD_sidebar when the page is loaded   

```yaml
---  
title: HLD transport Sample HLD#2
sidebar: HLD_sidebar
permalink: HLD_transport_002.html
layout: hld
date: 2021-02-01
tags: [hld, transport]
keywords: ciena, adva, infineria
summary: This HLD specifies the transport Architecture.
---
```

The following **liquid template** can be used to create a page with URL links to all TUN (  TUNs/posts are stored in the _posts directory) that are associated with transport.

 **Liquid template** creates a list of the TUNs and stored them in the sorted variable and sorted them based on the 'date:' field in the page's **frontmatter**; reverse get the dates ordered newest to oldest posts.
it then iterates over these pages and matches on all TUN that have a tag = transport

{% raw %}
```liquid
{% assign sorted = site.pages | sort: 'date' |reverse %}
{% for page in sorted %}
{% for tag in page.tags %}
{% if tag == "transport" %}
  <li><a href="{{page.url | remove: '/'}}">{{page.title}}</a></li>
{% endif %}
{% endfor %}
{% endfor %}
```
{% endraw %}

 **Liquid template** creates a list of the HLDs (collection) and stored them in the sorted variable and sorted them based on the 'date:' field in the page's **frontmatter**; reverse get the dates ordered newest to oldest posts.
it iterates over these pages and matches on all HLDs that have a tag = AS3356


{% raw %}
```liquid
{% assign sorted = site.hld | sort: 'date' |reverse %}
{% for page in sorted %}
{% for tag in page.tags %}
{% if tag == "AS3356" %}
  <li><a href="{{page.url | remove: '/'}}">{{page.title}}</a></li>
{% endif %}
{% endfor %}
{% endfor %}
```
{% endraw %}


## Saving pages as drafts

If you add `published: false` in the frontmatter, your page won't be published. You can also move draft pages into the \_drafts folder to exclude them from the build. With posts, you can also keep them as drafts by omitting the date in the title.

## Adding and internal Link

How to add an [*Internal Links*](mydoc_hyperlinks.html) or [*External Links*](mydoc_hyperlinks.html)

## Markdown or HTML format

Pages can be either Markdown or HTML format (specified through either an .md or .html file extension).

If you use Markdown, you can also include HTML formatting where needed. But if your format is HTML, you must add a `markdown="1"` attribute to the element in order to use Markdown inside that HTML element:

```
HTML
<div markdown="1">This is a [link](http://google.com).</div>


Markdown for addinng a link
[*Internal Links*](mydoc_hyperlinks.html)
[*google*](http://google.com)
```

For your Markdown files, note that a space or two indent will set text off as code or blocks, so avoid spacing indents unless intentional.

If you have a lot of HTML, as long as the top and bottom tags of the HTML are flush left in a Markdown file, all the tags inside those bookend HTML tags will render as HTML, regardless of their indentation. (This can be especially useful for tables.)

## TUN names

I recommend prefixing your page names with the product, such as *"tun_AS3356_tun#20"* or *"hld_Metro_hld#1"* instead of just "pages." This way if you have other products that also have topics with generic names such as "pages," there won't be naming conflicts.

Additionally, consider adding the product name in parentheses after the title, such as "Pages (Mydoc)" so that users can clearly navigate different topics for each product.

## Kramdown Markdown

Kramdown is the Markdown flavor used in the theme but you are free to move to [CommonMark](https://jekyllrb.com/docs/configuration/markdown/#commonmark) or [Redcarpet](https://jekyllrb.com/docs/configuration/markdown/#redcarpet). This mostly aligns with Github-flavored Markdown, but with some differences in the indentation allowed within lists. Basically, Kramdown requires you to line up the indent between list items with the first starting character after the space in your list item numbering. See this [blog post on Kramdown and Rouge](http://idratherbewriting.com/2016/02/21/bug-with-kramdown-and-rouge-with-github-pages/) for more details.

You can use standard Multimarkdown syntax for tables. You can also use fenced code blocks with lexers specifying the type of code. The configuration file shows the Markdown processor and extension:

```yaml
highlighter: rouge
markdown: kramdown
kramdown:
 input: GFM
 auto_ids: true
 hard_wrap: false
 syntax_highlighter: rouge
```

## Automatic mini-TOCs

By default, a TOC appears at the top of your pages and posts. If you don't want the TOC to appear for a specific page, such as for a landing page or other homepage, add `toc: false` in the frontmatter of the page.

The mini-TOC requires you to use the `##` Markdown syntax for headings. If you use `<h2>` elements, you must add an ID attribute for the heading element in order for it to appear in the mini-TOC (for example, `<h2 id="mysampleid">Heading</h2>`.

## Headings

Use pound signs before the heading title to designate the level. Note that kramdown requires headings to have one space before and after the heading. Without this space above and below, the heading won't render into HTML.

```
## Second-level heading
```

**Result:**

## Second-level heading

-----

```
### Third-level heading
```
**Result:**

### Third-level heading

------

```
#### Fourth-level heading
```

**Result:**

#### Fourth-level heading

## Headings with ID Tags {#someIdTag}

If you want to use a specific ID tag with your heading, add it like this:

```
## Headings with ID Tags {#someIdTag}
```

Then you can reference it with a link like this on the same page:

```
[Some link](#someIdTag)
```

**Result:**

[Some link](#someIdTag)

For details about linking to headings on different pages, see [Automated links to headings on pages][mydoc_hyperlinks.html#bookmarklinks].

## Specify a particular page layout

The configuration file sets the default layout for pages as the "page" layout.

You can create other layouts inside the layouts folder. If you create a new layout, you can specify that your page use your new layout by adding `layout: my_layout.html` in the page's frontmatter. Whatever layout you specify in the frontmatter of a page will override the layout default set in the configuration file.

## Comments

Disqus, a commenting system, is integrated into the theme. In the configuration file, specify the Disqus code for the universal code, and Disqus will appear. If you don't add a Disqus value, the Disqus form isn't included.

{% include links.html %}