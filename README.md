# DART github pages site

## Requirements: Hugo

To install Hugo on your mac you can download a binary from the [hugo release page](https://github.com/gohugoio/hugo/releases).

The version I have been using to build the site is Hugo Static Site Generator v0.80.0-792EF0F4/extended darwin/amd64 BuildDate: 2020-12-31T13:44:15Z

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

#### Adding a new team member

Edit `data/team.yml` to add a new team member

````
  - image       : images/team/profile-pic.jpg
    name        : MARGARET HAMILTON
    designation : Scientist
    ncarpage    : https://staff.ucar.edu/users/mhamilton
    github      : https://github.com/mhamilton
````

#### Adding a new reseach project

You can use Hugo to create a new project.md file with the hugo front matter. In the top level dircetcory run the command:

````
hugo new research/my-cool-project.md
````

This creates `content/research/my-cool-project.md`

#### Adding a new tutorial page

You can use Hugo to create a new tutorial.md file with the hugo front matter. In the top level dircetcory run the command:

````
hugo new tutorials/my-cool-tutorial.md
````

#### Adding a regular static page

You can create a 

## Publishing the website at dart.ucar.edu

The dart webiste is hosted on the `gh-pages` branch on  https://github.com/NCAR/DART.git

You can clone the single branch gh-pages into a DART-gh-pages directory with:

````
git clone -b gh-pages --single-branch https://github.com/NCAR/DART.git DART-gh-pages
````

You will notice that the gh-pages branch only has the dart website.  This is where you should put your updated website.

````
cd dart-web 
hugo -d ../DART-gh-pages
````

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


By the magic of gitpages, this becomes the workshop website at:

````
https://dart.ucar.edu/
```` 
