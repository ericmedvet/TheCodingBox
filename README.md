![Jekyll](https://img.shields.io/badge/Built%20with-Jekyll-blueviolet?logo=jekyll)
![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![Github Pages](https://img.shields.io/badge/github%20pages-121013?style=for-the-badge&logo=github&logoColor=white)

# TheCodingBox

This repository contains the source code for the website [thecodingbox.org](https://thecodingbox.org/). It is build with [Jekyll](https://jekyllrb.com/) based on a modified version of [Clean Blog Jekyll](https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll) theme and deployed on GitHub Pages using GitHub Actions.

## Project structure

-   `_includes`: overloaded core _HTML_ theme files, in particular
    -   `head.html` correspondes to `<head>` _HTML_ tag; it has been overloaded to add custom CSS ([`assets/css/style.css`](assets/css/style.css)), the favicon and [Lightbox](https://lokeshdhakar.com/projects/lightbox2/) for slideshows
    -   `scritps.html` same as previous point (e.g., to use Lightbox) and to add _js_ listeners for handle resizing and click on navabr item while in Desktop view
    -   `navbar.html` define the navigation menu at the top of the page. The modification applied consists in the addition of dropdown menu
    -   `footer.html` to use custom footer with social icons
-   `_layouts`: overloaded _HTML_ theme files used to define home, pages, and events
    -   `home.html` is used for the homepage (here [`pages/index.md`](pages/index.md)). The overload consists in remove the dynamic part inserting posts
    -   `page.html` is the template to publish a page. Since Jekyll allows [Liquid](https://shopify.github.io/liquid/) language, you can use variables that will be considered when rendering. Now, by overloading, you can decide if the page will render the title using `show_title: True` in the [Front Matter](https://jekyllrb.com/docs/front-matter/).
    -   `event.html` is the template for creating a new event (~post in the context of this blog). The Front Matter of the _md_ file will have the vast majority of information to create the event, and its body will only has the actual content (check [`_posts`](_posts) for examples)
-   `_posts`: folder for events, with Jekyll naming convention (e.g., `YYYY-MM-DD-post-title.md`)
-   `assets`: folder containing all the assets. Every folder inside it will be recognized
-   `pages`: folder with all pages of the website
-   `posts`: folder for events
-   `_config.yml`: used to define the Jekyll project as well as the paths of you website used to generate the navigation bar (order matters). Please note that even if they are defined, children of children will not be rendered in the menu.

## Usage

### New event

To create a new event, you have to add a _md_ file in [`_posts`](_posts) folder, and the file should following the Jekyll naming convention (e.g., `YYYY-MM-DD-post-title.md`). At the top insert the following Front Matter

```
---
layout: event
title:
category:
day:
duration:
image:
background:
permalink:
facebook:
twitter:
linkedin:
mail:
---
```

-   `layout: event` specify the [`layout`](_layouts/event.html) that will be used to render the page event
-   `title` is a string for the title that will be displayed inside the event page as well as in the events list page
-   `category` is needed to distinguish for past events ("eventi-passati") and future events ("eventi-in-programma"). At the moment only these two categories exists. Please note that if you need to add more, you have to modify the [page listing all events](posts/index.html) (e.g., [`thecodingbox.org/i-nostri-eventi`](thecodingbox.org/i-nostri-eventi)) accordingly, otherwise they will not be shown
-   `day` is a string (so no specific format) for the day of the event. Currently, only the "dd-mm-yy" and "dd-mm-yy to dd-mm-yy" formats are in use
-   `duration` allows you to specify the event duration. Currently, only the "All day" and "hh:mm - hh:mm" formats are in use
-   `image` is the image that will be displayed in the body of the event and in the events list page. Insert it in [`assets/images`](assets/images/) folder
-   `background` is the image shown in the header of the page (typically [`/assets/images/DSC_1507.jpg`](/assets/images/DSC_1507.jpg))
-   `permalink` is the output path of the event; typically it is something like `/i-nostri-eventi/evento1`
-   `facebook`, `twitter`, `linkedin` and `mail` are the links that can be used to share the event on the various platforms. They require the full URL of the post on the relative platform (for the mail you have to insert `mailto:?subject=` and so on); if you do not want to include a link, just remove the relative variable

After the definition of the Front Matter, just write the body of the event. You can also insert videos or other images using markup or _HTML_ syntax.

### New page

A similar argument holds true for creating a new page; again you have to create a _md_ file in [`pages`](pages) folder. At the top insert the following Front Matter

```
---
layout: page
title:
background:
permalink:
---
```

The meaning of the variables are the same as for events. Additionally, here you can set `show_title: True` if you want to show the title in the header of the page (i.e., on the background image).

> [!IMPORTANT]
> If the added page is to appear in the navigation menu, the `navigation` variable of [`config.yml`](_config.yml) should also be modified

### Pushing changes

The simplest way to add and modify files is to act directly from the repository. On the main page or repository, you can add files using the "Add file" button. This allows you to choose whether to create or upload files. Once you have added the file, GitHub Actions will take care of the rest. Instead, to modify current ones, you have to position on the file you want to change and click on the pencil button (i.e., "Edit this file").

You can also clone the repository with `git clone https://github.com/dravalico/TheCodingBox`, go to the cloned folder (`cd TheCodingBox`) and applying the changes/adding content. Once you have finished, push the changes and GitHub Actions will do the reamining.

> [!NOTE]
> Jekyll is needed only if you want to locally run the website with `bundle exec jekyll serve` for faster development or other needs.
