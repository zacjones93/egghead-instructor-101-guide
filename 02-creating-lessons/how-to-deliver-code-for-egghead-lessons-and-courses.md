# How to deliver code for egghead lessons and courses
The code that we deliver alongside the video is arguably as important as the video content itself. We want to make sure that it is concise, organized, readable, and presented to the user in a runnable embed using Plunker directly below the lesson video. Access to the code is a PRO member feature, and a huge perk.

Plunker is flexible, and allows us to embed even fairly complex apps as runnable examples. There are cases where it just won’t work, and in those cases we will simply link to a Github repository.

Please note that you should **record in a local environment, using your favorite text editor**. While it is possible to record lessons in a tool like Plunker, do so only because it is your preference. We use Plunker for the delivery of code to end users. It isn’t a requirement for recording.


# Using Plunker 

Plunker has a public UI, but we primary use its embeds. The first is the typical approach, where you use the public UI and setup your example code there. This is very functional, and will work just fine. For stand alone lessons, feel free to just do this.

Plunker also supports loading the code for your example directly into the embed via Github 😳 

This is an amazing feature as it allows us to version control the examples that are presented to the user. This means that we (egghead) can handle maintenance on your examples and keep the updated and supported for a much longer time. This is *critical* for course content!

## Link a Plunker embed to a Github repo

Linking a Github repository to plunker is fairly simple and involves configuring the plunker embed url. We start with `https://embed.plnkr.co/` , which is the base embed url.

To link to Github we configure the url by adding:


      `https://embed.plnkr.co/github/{profile-name}/{repository}/{branch}` 

`{branch}` can be replaced with `{tag|sha1}`  depending on how your repo is set up. If your repo is set up with an example in individual folders, you can add that `/path` to the embed url.

[Click here to see an example repo.](https://github.com/eggheadio-projects/nlp-in-javascript-with-natural) This is divided into a folder per lesson.


https://d2mxuefqeaa7sj.cloudfront.net/s_8105448CE6BE7B09A22ECBB05188409410D34AA6CBCE3636EE692CDF03958981_1488045591787_file.png



## Additional Plunker embed config

URL parameters can be added to affect how the embed presents itself. The most used feature is showing specific files (the default being the index and preview). Add `?show=` to the end of the url with the various filenames separated via commas. 


    https://embed.plnkr.co/github/eggheadio-projects/egghead-wikipedia-demo/angular-2-building-an-instant-search-with-angular-2-combining-observables-with-flatmap?preview=plnkr.html&show=src%2Fapp%2Fapp.component.ts,preview

An complex example of this is shown [here](https://embed.plnkr.co/github/eggheadio-projects/egghead-wikipedia-demo/angular-2-building-an-instant-search-with-angular-2-combining-observables-with-flatmap?preview=plnkr.html&show=src%2Fapp%2Fapp.component.ts,preview). There are quite a few additional parameters that can be used which are all documented in this [gist](https://ggoodman.gitbooks.io/plunker/content/embed.html).

# Build complex apps in plunker

**STOP!**

*You don’t have to do this*. **egghead will do this for you**. Hit up @zac in Slack. That said, if you are the DIY type, this is actually pretty cool…

Plunker itself does not support the node file system. *ie* import and export statements in plunker will not work. With that being said, it is possible to create an *in-browser Typescript compiler.* This is usually required for Angular lesson examples. Doing this takes a bit of set-up so hang in there.

Install jspm on local machine if it isn’t already which is an auto-configure systemjs tool:


    $ npm i -g jspm@beta

Run in whatever dir pleases you:

    $ jspm init

Select all the defaults given to you. Then run: 

    $ jspm i npm:{package_you_want_to_install}

Eg: `jspm i npm:data.task` 
This will give a *verbose* working example of the config file needed to achieve in-browser compiling. After init is done, this is the barebones .html page you will need:

    <!DOCTYPE html>
    <html lang="en">
      <head>
          <meta charset="UTF-8">
          <title>Document</title>
          <script src="./jspm_packages/system.src.js"></script>
          <script src="./jspm.config.js"></script>
      </head>
      <body>
          <script>
              System.import('app')
          </script>
      </body>
    </html>

You will then need to create an `app.js` ****file in the `src` directory `src/app.js` . This file will contain the code you want to run.
Any packages that are installed using `jspm i npm:{package_you_want_to_install}` will create a `jspm_packages/npm/{package_you_want_to_install}@1.2.3.json` file.
 
**Copy those contents.** 

The content will be placed in your `SystemJS.config` ****under the `packages` property as the package you installed.
Eg:

    SystemJS.config({
      map: {
          "data.task": "npm:data.task@3.1.1",
          "process": "npm:jspm-nodelibs-process@0.2.0"
      },
      packages: {               
          "data.task": {
              "main": "lib/index.js",
              "format": "cjs",
              "meta": {
                  "*": {
                      "globals": {
                          "process": "process"
                      }
                  },
                  "*.json": {
                      "format": "json"
                  }
              },
              "map": {
                  "./lib": "./lib/index.js"
              }
          }
      }
    });

**Jspm** will also give you a ****`jspm.config.js` file that we will want to copy with some slight modifications


    SystemJS.config({
      paths: {
        "npm:": "//unpkg.com/",
        "app/": "src/"
      },
      browserConfig: {
        "baseURL": "."
      },
      devConfig: {
          "map": {
            "plugin-babel": "npm:systemjs-plugin-babel@0.0.17",
            "systemjs-babel-build": "npm:systemjs-plugin-babel/systemjs-babel-browser.js"
          }
      },
      transpiler: "plugin-babel",
      packages: {
          "app": {
            "main": "app.js",
            "meta": {
              "*.js": {
                "loader": "plugin-babel"
              }
            }
          }
      }
    });

Note that the `"baseURL":` property was changed from `/` to a `.` 
 
Also note that `"systemjs-babel-build": "npm:systemjs-plugin-babel/systemjs-babel-browser.js` **** line was added under the `map` ****property (nested in the `devConfig` property).

For plunker apps just add this script tag (in `index.html` ):
`<script src="https://unpkg.com/systemjs@0.19.41/dist/system.src.js"></script>` 
Then the two `SystemJS.config` ****objects can be added in their own script, and you should be good to go!

Shout out to @John L for the walkthrough on in-browser compiling. 🙌 

Example for further clarity: 
http://embed.plnkr.co/UxkIoIK9PEkaupwTInDE?show=script.js,preview
 

