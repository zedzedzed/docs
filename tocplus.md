---
layout: default
title: Table of Contents Plus
---

# Table of Contents Plus
{: .no_toc }

A powerful yet user friendly WordPress plugin that automatically creates a context specific index or table of contents (TOC) for long pages (and custom post types). More than just a table of contents plugin, this plugin can also output a sitemap listing pages and/or categories across your entire site.

1. Table of contents
{:toc}

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

### My site has 100 pages but I only want the table of contents to appear on 10 of them

You could put `[no_toc]` on the 90 pages but that wouldn’t be fun... so try the following:

1. Go to Settings > TOC+ and disable the auto insertion option for pages (or the content type you’re working with).
2. Add `[toc]` onto the 10 pages that need them. Note that the table of contents will appear where you placed the shortcode.

Alternatively, you could also experiment with the restrict path option if the pages you want to include the index on all fall within a certain section of your site (eg /doc/).

### I want to ignore certain headings

Use the ‘exclude headings’ option if you would like to ignore certain headings. Separate multiple headings with a pipe `|`. Use an asterisk `*` as a wildcard to match other text. Note that this is not case sensitive. Some examples include:

* `Fruit*` ignore headings starting with *Fruit*
* `*Fruit Diet*` ignore headings with `Fruit Diet` somewhere in the heading
* `Apple Tree|Oranges|Yellow Bananas` ignore headings that are exactly *Apple Tree*, *Oranges* or *Yellow Bananas*

### Can I have the table of contents in the sidebar?

Use the TOC+ widget and drag it into your desired position. If you want the table of contents to only be displayed in the sidebar, then make sure you tick that option in the widget.

### Unlike Wikipedia, I want all my anchors to be lowercase and use hyphens rather than underscores

There are two options that allow you to adjust the casing and use of hyphens. If you still require more, you can massage it a little more by attaching into the `toc_url_anchor_target` filter. See the [developers](#For_developers) section for an example.

### I would like to incorporate a sitemap

1. Create a page for your sitemap (if you have an existing one, use that instead).
2. Add `[sitemap]` into your page and save.

The above is the simplest example of integrating a sitemap listing all pages and categories. You can customise the sitemap options under Settings > TOC+ or check out some of the more advanced uses with the sitemap related shortcodes below.

You could also incorporate a sitemap using a text widget and pasting any of the sitemap shortcodes.

### The sitemap uses a strange font dissimilar to the rest of the site

No extra styles are created for the sitemap, instead it inherits any styles you used when adding the shortcode. If you copy and pasted, you probably also copied the ‘code’ tags surrounding it so remove them if this is the case.

In most cases, try to have the shortcode on its own line with nothing before or after the square brackets.

## Shortcodes

The plugin was designed to be as seamless and painfree as possible and did not require you to insert a shortcode for operation. However, using the shortcode allows you to fully control the position of the table of contents within your page. The following shortcodes are available with this plugin.

When parameters are left out for the shortcodes below, they will fallback to the settings you defined under Settings > TOC+.

### [toc]

Lets you generate the table of contents at the preferred position. Also useful for sites that only require a TOC on a small handful of pages.

Attributes:

* `label`: text, title of the table of contents
* `no_label`: true/false, shows or hides the title
* `wrapping`: text, either “left” or “right”
* `heading_levels`: numbers, this lets you select the heading levels you want included in the table of contents. Separate multiple levels with a comma. Example: include headings 3, 4 and 5 but exclude the others with `heading_levels="3,4,5"`
* `exclude`: text, enter headings to be excluded. Separate multiple headings with a pipe `|`. Use an asterisk `*` as a wildcard to match other text. You could also use regular expressions for more advanced matching.
* `class`: text, enter CSS classes to be added to the container. Separate multiple classes with a space.

### [no_toc]

Allows you to disable the table of contents for the current post, page, or custom post type.

### [sitemap]

Produces a listing of all pages and categories for your site. You can use this on any post, page or even in a text widget.

### [sitemap_pages]

Lets you print out a listing of only pages.

Attributes:

* `heading`: number between 1 and 6, defines which html heading to use
* `label`: text, title of the list
* `no_label`: true/false, shows or hides the list heading
* `exclude`: IDs of the pages or categories you wish to exclude
* `exclude_tree`: ID of the page or category you wish to exclude including its all descendants

### [sitemap_categories]

Similar to `[sitemap_pages]` but for categories.

### [sitemap_posts]

This lets you print out an index of all published posts on your site. By default, posts are listed in alphabetical order grouped by their first letters. There are CSS classes for each section, letter and list allowing you to customise the appearance.

Attributes:

* `order`: text, either ASC or DESC
* `orderby`: text, popular options include “title”, “date”, “ID”, and “rand”. See WP_Query for a list.
* `separate`: true/false (defaults to true), does not separate the lists by first letter when set to false.

## For developers

### How do I customise my anchors?

If you’re still not happy with the anchors, you can modify them to suit your needs through a custom function hooked into the `toc_url_anchor_target` filter. As an example, place the below code snippet into your functions.php file to convert all anchors to uppercase.

```php
function my_custom_anchor( $anchor ) {
	return strtoupper( $anchor );
}
add_filter( 'toc_url_anchor_target', 'my_custom_anchor' );
```

### toc_get_index( $content = ”, $prefix_url = ” )

Returns a HTML formatted string of the table of contents without the surrounding UL or OL tags to allow the theme editor to supply their own ID and/or classes to the outer list.

Both parameters are optional:

* `$content` is the entire content with headings. If blank, will default to the current content found in `$post` (eg within “the loop”).
* `$prefix_url` is the URL to prefix the anchor with. If a string was provided, it will be used as is. If set to `true` then will try to obtain the permalink from the `$post` object.

These examples assume you are within “the loop”:

1. Obtain the index for the current page
```php
echo '<ul id="my_toc">' . toc_get_index() . '</ul>';
```

2. Create a listing of all children and their headings
```php
$children = new WP_Query(array(
  'post_parent' => get_the_ID(),
  'posts_per_page' => -1	// get all children
));
while ( $children->have_posts() ) {
  $children->the_post();
  echo 
    '<h3>' . get_the_title() . '</h3>' .
    '<ul>' . toc_get_index( get_the_content(), get_permalink( $children->post->ID ) ) . '</ul>'
  ;
}
wp_reset_postdata();
```

### Versioning scheme

I have adopted the same Ubuntu versioning scheme so the first release is 1107.

Other releases in the same month will be dot releases, eg the second release in July 2011 is 1107.1.

## I love it, how can I show my appreciation?

If you have been impressed with this plugin and would like to somehow show some appreciation, rather than send a donation my way, please donate to your charity of choice. Feel free to leave a short note here if you’d like.

I will never ask for any form of reward or compensation. Helping others achieve their goals is satisfying enough 🙂
