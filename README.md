# Who Built Bryn Mawr?
- Dev site: [https://digbmc.github.io/wbbm/](https://digbmc.github.io/wbbm/)
- Prod site: [https://wbbm.digitalprojects.brynmawr.edu/](https://wbbm.digitalprojects.brynmawr.edu/)

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
tag: # A tag for the current year/subphase (e.g. "Disoriented" for the Summer 2023 subphase)
phase: P4 # P4 is the indicator for the current phase
title:
author:
description:
key_image: # do not write anything in this line
    url: 
    alt: 
    caption:
public: true 
---

```
After you have copied this code into your new file, fill out all of the missing information in the header, including the title, author, and description of the blog post. If you would like an image to appear at the top of the blog post and as its thumbnail in the list of blog posts, add the url, alt text (for image accessibility), and a caption in the corresponding lines in the header. If you do not want to add an image, you can leave those lines as they are or delete them (including the “key_image” line). 

The "tag" line is very important. Make sure you add the tag corresponding to the post's year/subphase (e.g. "Disoriented" for the Summer 2023 subphase). If you are creating a new tag, you must add it to the tag-order.yml file in the _data folder. The order of the tags in this file determines the order in which the tag sections will appear on the blog page. If you do not add a tag to your post or you do not add the new tag to tag-order.yml, the post will not appear on the blog page.

Once you have filled out the information in the header, add the text content of your blog post after the three dashes (---) that close the header. You can format the text using Markdown syntax. Feel free to reference this [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/).

If your post is still a draft or not ready to be made public, change `public: true` to `public: false`. Once you push your changes to your remote branch, open a pull request to main in GitHub, and the pull request is merged, you will still be able to navigate to your blog post by typing its url into your browser's address bar, but the post will not appear on the list of posts on the site.

The url for a blog post consists of the site's base url (currently https://digbmc.github.io/wbbm/) plus /current/blog/YYYY/MM/DD/name/, where the date and name come from the post's file name.

### To add a page

To create a new page, you will have to create a new file in the site repository. For a page associated with the main WBBM site, create the new file in the site's root directory. For a page associated with a specific phase, create a new file in the corresponding folder. For now, the folder for the current phase is called "current".

The file should have YAML front matter similar to the following, which is from the current phase's "About" page:
```yaml
---
title: About
layout: page
phase: P4
---
```
You can copy this front matter into your new file and update the values as needed. The `layout` must be set to `page`. The identifier for the current phase (current) is `P4`. All pages and posts associated with the current phase should have `phase: P4` in their YAML front matter.

#### Permalinks

The permalink for the new page will depend on the location of its file in the site repository. If the file is in the root directory, the page's permalink will be `/filename/`, where "filename" is the name of the file minus its file extension. If the file is in another folder, the permalink will be `/folder/filename/`, where "folder" is the name of the folder that houses the file. For example, the permalink for the current phase's "About" page, which is generated from the about.md file in the "current" folder, is `/current/about/`.

You will need the permalink to add the new page to the site's navigation bar and to create other links to the page. Instructions for editing the nav bar can be found below.

In some cases, you may need to override the permalink automatically generated for a page. To do this, you must add a line to the page's YAML front matter beginning with `permalink: `. To see an example of this, you can look at the landing.md file in the "current" folder. The automatically generated permalink for this page would be `/current/landing/`, but the front matter sets the permalink as `/current/`.

### To add media to the site's collection

To add images to the site, you will either need to upload the image file to the repository or, if it is already on another website, you can use the image's url.

To upload an image to the site, you will need to add the image to the "images" folder, which is located inside the "assets" folder. You can either do this by uploading a file to your remote branch in GitHub, or by adding it to the /assets/images folder in your local branch and committing and pushing your changes to your remote branch. Make sure your new image has a unique filename that contains no spaces (use dashes or underscores instead) and ends in the file extension .jpg, .jpeg, or .png. 

Also, it is good to be mindful of the file size of your images. Images that are too large will make the site take longer to load and increase the site's carbon footprint. To avoid this, image file sizes should be around 200 KB or less. If an image you would like to use has a large file size, you can use the image compression tool [Squoosh](https://squoosh.app/) to reduce the file size by decreasing the size of the image in pixels and/or compressing the image. Often, you can reduce the file size of large images without noticeably reducing the quality of the image at the size it will be displayed on the website.

Once you have added the file to the repository or found the image's url, you should add the image and any relevant metadata to the site's media collection. To add media items, such as images, to the site’s media collection, you will have to edit the media.yml file found in the site’s _data directory. To add an item to the list of media in this file, you can copy the following code and paste it at the bottom of the media.yml file: 
```yaml
- item_id: 
  item_type: # image or yt-video
  item_location: # path or src/url
  title:
  creator:
  date:
  description:
  source:
  accession_number:
  transcription: # true or false
```
Then, you will need to fill out the missing attributes for your new media item.

#### item_id

The `item_id` should be a unique identifier for the item, as it will be used to “call” this item and its metadata when you add it to a blog post or another page on the site. Ideally, if you have added the image to the /assets/images folder, the `item_id` should be identical to the image's filename (minus the file extension).

#### item_type

If the media item you are adding is an image, be sure that `item_type` is set to `image`. If your media item is a YouTube video, set `item_type` to `yt-video`.

#### item_location

The instructions for the `item_location` are different depending on whether your new media item is an image or a YouTube video.

##### For images

The `item_location` should be the path or url for the media item, depending on where the file is stored. If the image is from an online source, use the image's url. If your image is stored in the images folder (located in the assets folder) in the site repository, then you will need to add the path to the image, which should look like this `/assets/images/filename.jpg`, where “filename.jpg” is the name of your media file.

##### For YouTube videos

If your media item is a YouTube video, the `item_location` should be the video's embed code. To get the embed code, click the share button under the video on YouTube and select "embed" (it should be the first circle). When you select embed, a pop-up will appear. Scroll down in the pop-up and make sure that the box to "Enable privacy-enhanced mode" is checked. Then, copy the embed code to your clipboard and paste it next to `item-location`. It should look something like this:
```yaml
item_location: <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/NlvRvsDUkdM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
You MUST then delete the `width="560" height="315"` part of the embed code above. It will then look like this:
```yaml
item_location: <iframe src="https://www.youtube-nocookie.com/embed/NlvRvsDUkdM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
#### transcription

If your media item is an image that contains a lot of text (more than can reasonably go in the description or alt text for the image), you will likely need to provide a transcription of the text. To do so, make sure the transcription value in media.yml is set to true for the item. Then, create a new Markdown file in the _transcriptions folder. The file name should match the `item_id` and have .md at the end (e.g. "media_008.md"). The front matter for this file should look something like this:
```yaml
---
layout: transcription
phase: P4
item_id: media_008
---
```
Feel free to copy and paste this front matter into your new file and change the information in it as necessary. The text that follows the front matter should be the transcription itself in Markdown.

#### Other attributes
The title, creator, date, description, source, and accession_number attributes store the metadata for your media item. Be sure to fill them out with the corresponding information for your item, if available. If you do not have the information for all of these attributes (for example, if you do not know the creator of the item or the item does not have an accession number), you can safely leave these attributes empty, or fill them in as "Unknown".

Note: Currently, the "description" attribute is also used to add alt text to the images on the site, so be sure to add a description that can function as alt text.

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
      url: /current/about/
    - title: Blog
      url: /current/blog/
    - title: Team
      url: /current/team/
```
Each item in this list has two keys: `phase` and `navigation`. The value of the `phase` key should be set to the identifier for the phase that the nav bar will be used for. The value of the `navigation` key is the list of items you want to appear in the nav bar. Each of these list items has two keys: `title` and `url`.

The value for `title` should be the name of the target page as you want it to appear in the menu bar. The `url` should match the target page's permalink. Instructions for figuring out what the page's permalink is can be found in the ["Permalinks"](#permalinks) section above.

To create a nav bar for a new phase, copy the code block above and update the values.

To add an item to a phase's nav bar, add an item its `navigation` list. Here is the format for a new list item:
```yaml
- title: 
  url: 
```
Be careful with your indentation, as it is significant in YAML. Use spaces instead of tabs to replicate the list structure pictured above.

To remove an item from the menu, delete the corresponding `navigation` list item in menu.yml.

*This site was built using a bootstrap jekyll theme based on work by Aaron Frey.*
