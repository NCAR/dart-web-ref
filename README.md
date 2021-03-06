
:bangbang: | For reference, here is a copy of the code used to generate the DART website with hugo.  
:---: | :---



# DART github pages site


## Requirements: Hugo

To install Hugo on your mac you can download a binary from the [hugo release page](https://github.com/gohugoio/hugo/releases). Choose an _extended version. 

The version I have been using to build the site is Hugo Static Site Generator v0.80.0-792EF0F4/extended darwin/amd64 BuildDate: 2020-12-31T13:44:15Z
which you can download from here:
https://github.com/gohugoio/hugo/releases/tag/v0.80.0


For more details see:<br>
[hugo install instructions](https://gohugo.io/getting-started/installing/)

There are two repositories to be aware of:

[https://github.com/NCAR/dart-web.git](https://github.com/NCAR/dart-web.git) Is the repository used to build the site. 

The website is hosted via github pages on dart.ucar.edu

[https://github.com/NCAR/DART.git](https://github.com/NCAR/DART.git)

## Building the site locally
This is a static site built with hugo. Hugo has a built in webserver so you can 
test your build locally.

To build the site on your machine:

````
git clone https://github.com/NCAR/dart-web.git
cd dart-web
hugo serve
````

You will see something like this:

````
Start building sites … 

                   | EN   
-------------------+------
  Pages            |  32  
  Paginator pages  |   2  
  Non-page files   |   0  
  Static files     | 175  
  Processed images |   0  
  Aliases          |   2  
  Sitemaps         |   1  
  Cleaned          |   0  

Built in 438 ms
Watching for changes in /Users/hkershaw/DART/website/hugo-website/Fresh/hugo-dart/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /Users/hkershaw/DART/website/hugo-website/Fresh/hugo-dart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:51000/ (bind address 127.0.0.1)

````

Using your favorite browser, navigate to ` http://localhost:XXXX/`

Where XXXX is the port number given in the hugo message.  Hugo uses live reload, so as you edit your files, the site will be rebuilt. 


## Adding content

The hugo directory structure looks like this:

````
.
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
````

The following are used when adding content to the website:

`config.toml` Is site wide settings, for example, the base-url and the navigation items

`content` contains the website pages. Each directory is a section. Single pages are in the top level

`data` contains data to pull into the website, for example the team members info.

`static` contains files used in the website as-is, such as images and pdfs and the CNAME file. 



#### Adding a new team member

Edit `data/team.yml` to add a new team member

````
  - image       : images/team/profile-pic.jpg
    name        : MARGARET HAMILTON
    designation : Scientist
    ncarpage    : https://staff.ucar.edu/users/mhamilton
    github      : https://github.com/mhamilton
````

#### Adding an item to the impact list

Edit `data/counter.yml` to add an item to the impact list

````
  - title: "Models supported"
    number: "20"
````

If you want the counter to link to another page, add a url

````
  - title: "Publications"
    number: "100"
    url: "publications"
````

#### Adding a new reseach project

You can use Hugo to create a new project.md file with the Hugo front matter. In the top level directory run the command:

````
hugo new research/my-cool-project.md
````

This creates `content/research/my-cool-project.md`

#### Adding a new tutorial page

You can use Hugo to create a new tutorial.md file with the hugo front matter. In the top level dircetcory run the command:

````
hugo new tutorials/my-cool-tutorial.md
````

This creates `content/tutorials/my-cool-tutorials.md`

#### Adding a regular static page

You can create a regular page with

````
hugo new my-new-page.md
````

This creates `content/my-new-page.md`

#### Adding a redirect

You can use _aliases_ to add redirects. For example, publications used
to be on the page:

````
https://dart.ucar.edu/pages/Publications.html
````

which no longer exists on dart.ucar.edu. Rather than having `pages/Publications.html` give a 404 error, you can have `pages/Publications.html` redirect to the new publications page `https://dart.ucar.edu/publications/`. To do this, add an aliases line to the front matter of `publications.md`. 

````
---
title       : "Publications featuring DART"
layout      : "staticpage"
aliases     :
   - /pages/Publications.html
---
````

You can add multiple aliases for a page:

````
---
title       : "Publications featuring DART"
layout      : "staticpage"
aliases     :
   - /pages/Publications.html
   - /pages/More-publications.html
---

````

#### Using re-structured-text rather than markdown

To use rst, you will need to have rst2hml installed. To install rst2html in
a virtual environment:

````
python -m venv web
source web/bin/activate
pip install rst2html
````

Run hugo in this virtual environment to use `.rst`.

#### Using NCAR icons

You can use NCAR icons.  To see a demo of all the NCAR icons available, 

````
open static/icomoon/demo.html
````

To use a particular icon:

````
<span class="icon-data-assimilation"></span>
````

## Changing page layouts and appearance

The hugo directory structure looks like this:

````
.
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
````

The `layouts` directory contains .html layouts.  These override the default settings for the theme.

The `themes` directory contains the .scss files that control the look of the site. 

`themes/roxo-hugo/assets/scss/`

**Future work**   create a dart-theme rather than using roxo-hugo + many overrides. 

## Publishing the website at dart.ucar.edu

**Note, these instructions are for when the dart website has been switched to gh-pages**

The dart webiste is hosted on the `gh-pages` branch on  https://github.com/NCAR/DART.git

You can clone the single branch gh-pages into a DART-gh-pages directory with:

````
git clone -b gh-pages --single-branch https://github.com/NCAR/DART.git DART-gh-pages
````

You will notice that the gh-pages branch only has the dart website.  This is where you should put your updated website.

````
cd dart-web 
hugo --minify -d ../DART-gh-pages
````

The `--minify` option squishes the html to reduce load times.  You may want to omit `--minify` if you want to read the html more easily.


Replace `../DART-gh-pages` with wherever you checked out the DART repo. 

Add and commit your changes:

````
git add .
git commit
````

Push DART-gh-pages to the https://github.com/NCAR/DART.git

````
git push origin gh-pages
````

**Be aware** you must push your site to the gh-pages branch


You may want to do something cooler and automate push process in the future. 


By the magic of gitpages, this becomes the website at:

````
https://dart.ucar.edu/
```` 
