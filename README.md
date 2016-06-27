# Setting up

This file will take you through the basic setup for watching and compiling your Sass with npm.

* Open terminal, create a project, set up your `package.json` file

(Make sure that you have installed Nodejs)

    $ mkdir project
    $ cd project
    $ npm init

* Set up your files

Create these folders:

    $ mkdir bin public scss && mkdir public/css
    $ touch scss/main.scss

Add your `.gitignore`:

    $ touch .gitignore

Add the following to your `.gitignore` file

    node_modules/
    npm-debug.log
    .DS_Store

# Create Sass compiler and watcher

Node-sass will compile our scss files into css
Nodemon will watch our scss files for changes

    $ npm install -D node-sass nodemon

Note: you may have to use the `sudo` command.

Create a `build-css` and a `watch-css` file in your `bin` folder:

    $ touch bin/build-css bin/watch-css

Within `build-css`, add this command:

    node-sass --include-path scss scss/main.scss public/css/main.css

Within `watch-css`, add this command:

    nodemon -e scss -x "npm run build-css"

Make sure both files are executable:

    chmod +x bin/build-css
    chmod +x bin/watch-css

Go to your `package.json` file and modify the scripts object to match the paths of our new commands:

    "scripts": {
      "build-css": "./bin/build-css",
      "watch-css": "./bin/watch-css"
    },

Add some test sass to your `main.scss` file and test the build/watch commands:

    $npm run build-css
    $npm run watch-css
