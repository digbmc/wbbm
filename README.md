# Who Built Bryn Mawr?

- A bootstrap jekyll theme based on work by Aaron Frey

## To do:
- [ ] Create nice display for images and metadata 
- [ ] Maybe:
  - [ ] Make compatible with GH Pages


## Editing instructions

### To add a blog post

To add a blog post, create a new file in the _posts directory with the name YYYY-MM-DD-name.md, replacing “YYYY-MM-DD” with the date of the post’s creation and “name” with something relevant to the post itself, such as part of its title. Be sure to replace any spaces with a dash (-), as the filename cannot contain whitespace. Then, copy the following YAML header into your new file: 
```
---
title:
layout: post
author:
description:
key_image: #do not write anything in this line
    url: 
    alt: 
    caption: 
---

```
After you have copied this code into your new file, fill out all of the missing information in the header, including the title, author, and description of the blog post. If you would like an image to appear at the top of the blog post and as its thumbnail in the list of blog posts, add the url, alt text (for image accessibility), and a caption in the corresponding lines in the header. If you do not want to add an image, you can leave those lines as they are or delete them (including the “key_image” line).

Once you have filled out the information in the header, add the text content of your blog post after the three dashes (---) that close the header. You can format the text using Markdown syntax. Feel free to reference this [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/).

### To add media to the site's collection

To add media items, such as images, to the site’s media collection, you will have to edit the media.yml file found in the site’s _data directory. To add an item to the list of media in this file, you can copy the following code and paste it at the bottom of the media.yml file: 
```
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

### To change the menu items

To change the pages listed in the menu or navigation bar, edit the menu.yml file in the site's _data directory. 

To add an item to the menu, add an item to the list in this file. Here is the format for a new list item:
```
- title: 
  url: 
```
The `title` should be the name of the target page as you want it to appear in the menu bar. The `url` should match the target page's permalink. For example, the url for the Blog page is `/blog/`, which matches the permalink set in the front matter of the blog.md file. Similarly, the url for the About page is `/about/`, because that the permalink set in the front matter of the about.md file.

To remove an item from the menu, delete the corresponding list item in menu.yml.