# 5-Point Plan dashboard galleries

As part of the 5PP program implementation an R script is used to produce a dashboard image at regular interval, so this project lets you load a folder with images with chronological filenames (i.e. `2020-01-02.jpg`) and then view the series in a gallery on a simple webpage. 

## Adding images to a gallery

- [Create an account on GitHub](https://github.com/join?source=header-home) if you don't already have one.
- Give your user name to the Red Cross point of contact for the project and request to be given edit access to the project.
- You should get an email notification, or you can go the [organization page on GitHub](https://github.com/AmericanRedCross/) and you should see an alert.  
![screen grab of invitation alert](https://raw.githubusercontent.com/AmericanRedCross/5PP/gh-pages/img/contributing/invitation-1.png)  
- View and then accept the invitation.  
![screen grab of invitation join screen](https://raw.githubusercontent.com/AmericanRedCross/5PP/gh-pages/img/contributing/invitation-2.png)  
- From the [main page](https://github.com/AmericanRedCross/5PP) for the 5PP project on GitHub, click into the `images` folder.  
![screen grab of root folder](https://raw.githubusercontent.com/AmericanRedCross/5PP/gh-pages/img/contributing/folders-1.png)  
- Click into the folder for the 5PP campaign for which you would like to add dashboard images.  
![screen grab of images folder](https://raw.githubusercontent.com/AmericanRedCross/5PP/gh-pages/img/contributing/folders-2.png)  
- Click the **Upload files** button.  
![screen grab of images folder for a campaign](https://raw.githubusercontent.com/AmericanRedCross/5PP/gh-pages/img/contributing/folders-3.png)  
- The images need to sort alpha-numerically to display in the correct order in the gallery. The best way to ensure this is to create filenames using [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standards for date and time. Use a four digit year, followed by a 2 digit month, followed by a 2 digit day. For submissions morning and evening, you may append "AM" and "PM" as seen in the screen grab above. Or for multiple submission each day you can append a "T" followed by a zero-padded hour of day. For example, `2020-05-01-T09.png` and `2020-05-01-T18.png`.
- Drag the image(s) to the window where requested or use the **choose your files** link. Optionally, you can add a short description of the changes in the first text box under **Commit changes** and you can also add an extended description to provide more details if necessary. More details may be desired if replacing an image or conducting some other more extensive edit.  
![screen grab of the upload files screen](https://raw.githubusercontent.com/AmericanRedCross/5PP/gh-pages/img/contributing/upload-files.png)  
- If you're ready for the images to go to the live website, you can leave **Commit directly to the `gh-pages` branch.** selected and then click the green **Commit changes** button.
- The changes should take effect almost immediately. You will need to refresh any webpages that are already open.

## Deleting an image from a gallery

- Follow the above instructions to get into a 5PP campaign folder showing a list of images with the one you want to delete.
- Click the image you want to delete to open the page for the file.
- Click the trash can delete icon.  
![screen grab showing the delete icon](https://raw.githubusercontent.com/AmericanRedCross/5PP/gh-pages/img/contributing/delete-file-1.png)  
- Optionally, you can add a short description of the changes in the first text box under **Commit changes** and you can also add an extended description to provide more details if necessary.    
![screen grab showing the delete icon](https://raw.githubusercontent.com/AmericanRedCross/5PP/gh-pages/img/contributing/delete-file-2.png)  
- If you're ready for the images to be removed from the live website, you can leave **Commit directly to the `gh-pages` branch.** selected and then click the green **Commit changes** button.
- The changes should take effect almost immediately. You will need to refresh any webpages that are already open.

## Adding a new gallery page

- Create a new folder in `./images` with the name you want to be included in your URL.
  - GitHub ignores empty folders when evaluating changes, so create a `README.md` file inside the folder if you're going to skip the next step and wait until later to add images. Placing  a file into the folder will make the folder available to users in the web interface. The `.md` extension is important, the gallery page will ignore that extension when placing files into the image carousel. 
- Add images to the folder. The image file names should sort in the order you want them to appear in the gallery. Using [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standards for representing dates and times is a good option. 
- Add the folder name as a list item under `collections:` in the `_config.yml` file.
- Create a new `.html` file in the main `5PP` project folder and give it the same name as your new images folder.
- Add the below text into the new `.html` file.
  - Update the title and description.
  - Update the order number.
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
