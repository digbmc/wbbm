# Who Built Bryn Mawr?

- A bootstrap jekyll theme based on work by Aaron Frey

## To do:
- [ ] Create nice display for images and metadata 
- [ ] Maybe:
  - [ ] Make compatible with GH Pages


## Editing instructions

### To add a blog post

To add a blog post, create a new file in the _posts directory with the name YYYY-MM-DD-name.md, replacing “YYYY-MM-DD” with the date of the post’s creation and “name” with something relevant to the post itself, such as part of its title. Be sure to replace any spaces with a dash (-), as the filename cannot contain whitespace. Then, copy the following YAML header into your new file: 
```yaml
---
layout: post
phase: P4 # P4 is the indicator for the 2023-2026 phase
title:
author:
description:
key_image: # do not write anything in this line
    url: 
    alt: 
    caption: 
---

```
After you have copied this code into your new file, fill out all of the missing information in the header, including the title, author, and description of the blog post. If you would like an image to appear at the top of the blog post and as its thumbnail in the list of blog posts, add the url, alt text (for image accessibility), and a caption in the corresponding lines in the header. If you do not want to add an image, you can leave those lines as they are or delete them (including the “key_image” line).

Once you have filled out the information in the header, add the text content of your blog post after the three dashes (---) that close the header. You can format the text using Markdown syntax. Feel free to reference this [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/).

### To add a page

To create a new page, you will have to create a new file in the site repository. For a page associated with the main WBBM site, create the new file in the site's root directory. For a page associated with a specific phase, create a new file in the corresponding folder. For now, the the folder for the current phase is called "2023-2026".

The file should have YAML front matter similar to the following, which is from the current phase's "About" page:
```yaml
---
title: About
layout: page
phase: P4
---
```
You can copy this front matter into your new file and update the values as needed. The `layout` must be set to `page`. The identifier for the current phase (2023-2026) is `P4`. All pages and posts associated with the current phase should have `phase: P4` in their YAML front matter.

The permalink for the new page will depend on the location of its file in the site repository. If the file is in the root directory, the page's permalink will be `/filename/`, where "filename" is the name of the file minus its file extension. If the file is in another folder, the permalink will be `/folder/filename/`, where "folder" is the name of the folder that houses the file. For example, the permalink for the current phase's "About" page, which is generated from the about.md file in the "2023-2026" folder, is `/2023-2026/about/`.

You will need the permalink to add the new page to the site's navigation bar and to create other links to the page. Instructions for editing the nav bar can be found below.

In some cases, you may need to override the permalink automatically generated for a page. To do this, you must add a line to the page's YAML front matter beginning with `permalink: `. To see an example of this, you can look at the landing.md file in the "2023-2026" folder. The automatically generated permalink for this page would be `/2023-2026/landing/`, but the front matter sets the permalink as `/2023-2026/`.

### To add media to the site's collection

To add media items, such as images, to the site’s media collection, you will have to edit the media.yml file found in the site’s _data directory. To add an item to the list of media in this file, you can copy the following code and paste it at the bottom of the media.yml file: 
```yaml
- item_id: 
  item_type: image
  item_location: # path or src/url
  title:
  creator:
  date:
  description:
  source:
```
Then, you will need to fill out the missing attributes for your new media item.

The `item_id` should be a unique identifier for the item, as it will be used to “call” this item and its metadata when you add it to a blog post or another page on the site. 

If the media item you are adding is an image, be sure that `item_type` is set to `image`. (Other types of media items, such as videos, are not currently supported, but the `item_type` attribute will allow future support for other media formats, if needed.)

The `item_location` should be the path or url for the media item, depending on where the file is stored. If the media item is from an online source, use the file’s url. If your image is stored in the images folder (located in the assets folder) in the site repository, then you will need to add the path to the image, which should look like this `/wbbm/assets/images/filename.jpg`, where “filename.jpg” is the name of your media file.

The title, creator, date, description, and source attributes store the metadata for your media item. Be sure to fill them out with the corresponding information for your item, if available.

### To add media items to a blog post or other page

To add a media item to a blog post, you will need to call the item from the collection. To do this, you will need the media item's `item_id` from the media.yml file in the site's _data directory.

In your blog post, add the following code to the text content of the post wherever you would like the media item to appear: 
```
{% include media.html item_id="media_001" align="right" %}
```
Be sure to change the `item_id` to the id associated with the media item you wish to call. You can also adjust the alignment of the item by changing `align="right"` to `align="left"` or `align="center"`.

### To change the menu/navigation items

The site is set up to allow for unique navigation bars for each phase of the project. Nav bars are automatically added to the header of pages with the `page` or `post` layout. The data used to generate these nav bars is stored in the menu.yml file in the site's _data directory.

To create a nav bar for a new phase or to change the items listed in a nav bar, you must edit the menu.yml file. 

The menu.yml file is written in YAML and consists of a list that looks something like this:
```yaml
- phase: P4
  navigation:
    - title: About
      url: /2023-2026/about/
    - title: Blog
      url: /2023-2026/blog/
    - title: Team
      url: /2023-2026/team/
```
Each item in this list has two keys: `phase` and `navigation`. The value of the `phase` key should be set to the identifier for the phase that the nav bar will be used for. The value of the `navigation` key is the list of items you want to appear in the nav bar. Each of these list items has two keys: `title` and `url`.

The value for `title` should be the name of the target page as you want it to appear in the menu bar. The `url` should match the target page's permalink. For example, the url for the current phase's Blog page is `/2023-2026/blog/`, which matches the permalink set in the front matter of the p4-blog.md file. Similarly, the url for the current phase's About page is `/2023-2026/about/`, because that the permalink set in the front matter of the p4-about.md file.

To create a nav bar for a new phase, copy the code block above and update the values.

To add an item to a phase's nav bar, add an item its `navigation` list. Here is the format for a new list item:
```yaml
- title: 
  url: 
```
Be careful with your indentation, as it is significant in YAML. Use spaces instead of tabs to replicate the list structure pictured above.

To remove an item from the menu, delete the corresponding `navigation` list item in menu.yml.