![Jekyll](https://img.shields.io/badge/Built%20with-Jekyll-blueviolet?logo=jekyll)
![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![Github Pages](https://img.shields.io/badge/github%20pages-121013?style=for-the-badge&logo=github&logoColor=white)

# TheCodingBox

This repository contains the source code for the website [thecodingbox.org](https://thecodingbox.org/). It is build with [Jekyll](https://jekyllrb.com/) based on a modified version of [Clean Blog Jekyll](https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll) theme and deployed on GitHub Pages using GitHub Actions.

## Project structure

-   `_includes`: overloaded core HTML theme files, in particular
    -   `head.html` correspondes to `<head>` HTML tag; it has been overloaded to add custom CSS (`/assets/css/style.css`), the favicon and [Lightbox](https://lokeshdhakar.com/projects/lightbox2/) for slideshows
    -   `scritps.html` same as previous point (e.g., to use Lightbox)
    -   `navbar.html` define the navigation menu at the top of the page. The modification applied consists in the addition of dropdown menu
    -   `footer.html` to use custom footer with social icons
-   `_layouts`: overloaded HTML theme files used to define home, pages, and events
    -   `home.html` is used for the homepage (here `/pages/index.md`). The overload consists in remove the dynamic part inserting posts
    -   `page.html` is the template to publish a page. Since Jekyll allows [Liquid](https://shopify.github.io/liquid/) language, you can use variables that will be considered when rendering. Now, by overloading, you can decide if the page will render the title using `title: True` in the [Front Matter](https://jekyllrb.com/docs/front-matter/).
    -   `event.html` is the template for creating a new event (~post in the context of this blog). The Front Matter of the MD file will have the vast majority of information to create the event, and its body will only has the actual content (check `/_posts` for examples)
-   `_posts`: folder for events, with Jekyll name convention (e.g., `YYYY-MM-DD-post-title.md`)
-   `assets`: folder containing all the assets. Every folder inside it will be recognized
-   `pages`: folder with all pages of the website
-   `posts`: folder for events
-   `_config.yml`: used to define the Jekyll project as well as the paths of you website used to generate the navigation bar (order matters). Please note that even if they are defined, children of children will not be rendered in the menu.

## Usage

Clone the repository using `git clone https://github.com/dravalico/TheCodingBox` and move to the cloned folder `cd TheCodingBox` and apply the changes/add content. When you have finished, push changes; GitHub Actions will do the remaining.

Jekyll is needed only if you want to locally run the website with `bundle exec jekyll serve` for faster development or other needs.
