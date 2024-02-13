---
layout: default
title: Table of Contents Plus
---

A powerful yet user friendly WordPress plugin that automatically creates a context specific index or table of contents (TOC) for long pages (and custom post types). More than just a table of contents plugin, this plugin can also output a sitemap listing pages and/or categories across your entire site.

## Description

Built from the ground up and with Wikipedia in mind, the table of contents by default appears before the first heading on a page. This allows the author to insert lead-in content that may summarise or introduce the rest of the page. It also uses a unique numbering scheme that doesn't get lost through CSS differences across themes.

This plugin is a great companion for content rich sites such as content management system oriented configurations. That said, bloggers also have the same benefits when writing long structured articles.

Includes an administration options panel where you can customise settings like display position, define the minimum number of headings before an index is displayed, other appearance, and more. For power users, expand the advanced options to further tweak its behaviour, eg: 

* exclude undesired heading levels like h5 and h6 from being included;
* disable the output of the included CSS file;
* adjust the top offset and more.

Using shortcodes, you can override default behaviour such as special exclusions on a specific page or even to hide the table of contents altogether.

Prefer to include the index in the sidebar? Go to Appearance > Widgets and drag the TOC+ to your desired sidebar and position.

Custom post types are supported, however, auto insertion works only when `the_content()` has been used by the custom post type. Each post type will appear in the options panel, so enable the ones you want.

## Screenshots

## Install / upgrade

Install the plugin by searching for Table of Contents Plus from the plugin add menu, or directly from the WordPress plugins repository.

There are no special upgrade instructions (woohoo!). Overwrite your existing folder with the latest or use the streamlined approach in the plugin menu. Your options will not be lost.

## Help

### The simplest approach

For the impatient, all you have to do is enable the plugin.

The plugin will apply default settings and produce the table of contents before the first heading on pages (not posts, nor custom post types) with **four or more** headings.

No shortcodes are needed.

### Where's my table of contents?

1. In most cases, the post, page or custom post type has less than the minimum number of headings. By default, this is set to four so make sure you have at least four headings within your content. If you want to change this value, you can find it under ‘Main Options' > ‘Show when'.
2. Is auto insertion enabled for your content type? By default, only pages are enabled.
3. Have you got `[no_toc]` somewhere within the content? This will disable the index for the current post, page or custom post type.
4. If you are using the TOC+ widget, check if you have the “Show the table of contents only in the sidebar” enabled as this will limit its display to only the sidebar. You can check by going into Appearance > Widgets.
5. You may have restricted generation to a URL path match. The setting can be found in the advanced section under Main Options.

### How do I stop the table of contents from appearing on a single page?

Place the following `[no_toc]` anywhere on the page to suppress the table of contents. This is known as a shortcode and works for posts, pages and custom post types that make use of the_content()

### I've set wrapping to left or right but the headings don't wrap around the table of contents

This normally occurs when there is a CSS clear directive in or around the heading originating from the theme (Twenty Eleven and Twenty Twelve are two themes which do this). This directive tells the user agent to reset the previous wrapping specifications.

You can adjust your theme's CSS or try moving the table of contents position to the top of the page.

Try adding the following CSS to allow the wrapping to occur around the table of contents:

```css
h1, h2, h3, h4, h5, h6 { clear: none; }
```

### How do I include the name of the page in the table of contents title?

As the title of the page changes depending on the page you’re viewing, you can use the following special variable to automatically insert the title of the page into the table of contents heading:

`%PAGE_NAME%`

You can use it as is or place text either side of the variable.

As an example: if your page is named *Great Expectations* and your table of contents title is set to `Contents for %PAGE_NAME%`, the final title would read *Contents for Great Expectations*

## My site has 100 pages but I only want the table of contents to appear on 10 of them

You could put `[no_toc]` on the 90 pages but that wouldn’t be fun... so try the following:

1. Go to Settings > TOC+ and disable the auto insertion option for pages (or the content type you’re working with).
2. Add `[toc]` onto the 10 pages that need them. Note that the table of contents will appear where you placed the shortcode.

Alternatively, you could also experiment with the restrict path option if the pages you want to include the index on all fall within a certain section of your site (eg /doc/).

