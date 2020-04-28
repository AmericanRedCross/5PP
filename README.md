# 5-Point Plan dashboard galleries

As part of the 5PP program implementation an R script is used to produce a dashboard image at regular interval, so this project lets you load a folder with images with chronological filenames (i.e. `2020-01-02.jpg`) and then view the series in a gallery on a simple webpage. 

## Adding a new gallery page

- Create a new folder in `./images` with the name you want to be included in your URL.
- Add images to the folder. The image file names should sort in the order you want them to appear in the gallery. Using [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standards for representing dates and times is a good option. 
- Add the folder name as a list item under `collections:` in the `_config.yml` file.
- Create a new `.html` file in the main `5PP` project folder and give it the same name as your new images folder.
- Add the below text into the new `.html` file.
  - Update the title and description.
  - Change `my-folder-name` to the name of your new folder.

```
---
layout: default
title: "This is my title"
description: "This is my description."
order: 1
---
{% assign images = site.static_files | where_exp: "item", "item.path contains 'images/my-folder-name'" %}
{% assign imageCount = images | size  %}
{% include images.html %}
{% include footer.html %}
```

## Development environment

- Install ruby. Suggested to use [Ruby Version Manager (RVM)](https://rvm.io/).
- `gem install bundler` to get [Bundler](https://bundler.io/). 
- `bundle install` to get [Jekyll](https://jekyllrb.com/).
- To run a test server: `bundle exec jekyll serve --baseurl ""`.
- https://learn.cloudcannon.com/jekyll-cheat-sheet/
