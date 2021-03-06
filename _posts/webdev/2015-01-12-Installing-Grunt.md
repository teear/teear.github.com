---
layout: article
title: Installing Grunt
published: false

image:
  teaser: grunt.png
  feature: grunt.png
  credit: Grunt #name of the person or site you want to credit
  creditlink: http://gruntjs.com #url to their site or licensing
---

Installing Grunt for a project
------------------------------
-Node.js must be installed, you can find it from [http://nodejs.org/download/](http://nodejs.org/download/)

-Add a package.json file to your project folder

{% highlight javascript %}
{
  "name": "foxtrotlima",
  "version": "0.1.0",
  "devDependencies": {
    "grunt": "~0.4.5"
  }
}
{% endhighlight %}

-Run <kbd>npm install</kbd> from command line

-Install Grunt CLI (command line interface) with <kbd>npm install -g grunt-cli</kbd>

Lets install compass
--------------------
For this to work Ruby, Sass, and Compass has to be installed already.

-Run <kbd>npm install grunt-contrib-compass --save-dev</kbd> (--save-dev updates package.json automatically with the new dependency)

-Create a Gruntfile.js with the following contents

{% highlight javascript %}
module.exports = function(grunt) {

    // 1. All configuration goes here
    grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),

        concat: {
            // 2. Configuration for concatinating files goes here.
        }

    });

    // 3. Where we tell Grunt we plan to use this plug-in.
    grunt.loadNpmTasks('grunt-contrib-compass');

    // 4. Where we tell Grunt what to do when we type "grunt" into the terminal.
    grunt.registerTask('default', ['compass']);

};
{% endhighlight %}

The line which loads the compass task is:

        grunt.loadNpmTasks('grunt-contrib-compass');

We still need to add the config for compass to the Gruntfile.js file:

{% highlight javascript %}
compass: {                  // Task
    dist: {                   // Target
      options: {              // Target options
        sassDir: 'scss',
        cssDir: 'css',
        environment: 'production'
      }
    },
    dev: {                    // Another target
      options: {
        sassDir: 'scss',
        cssDir: 'css'
      }
    }
  }
{% endhighlight %}

You can find all the config options at <https://www.npmjs.org/package/grunt-contrib-compass>


## Installing Autoprefixer

npm install grunt-autoprefixer --save-dev

Gruntfile.js

{% highlight javascript %}
autoprefixer: {
        options: {
          browsers: [
            'last 2 versions',
            'Explorer >= 9',
            'Android >= 3'
          ]
        },
        dist: {
          src: 'foxtrotlima.css'
        }
      },

watch: {
            styles: {
                files: ['foxtrotlima.css'],
                tasks: ['autoprefixer']
            }
        }

grunt.loadNpmTasks('grunt-autoprefixer');
{% endhighlight %}

## Updating

### Node.js
Node.js installers: <http://nodejs.org/download/>
Or updating only npm: npm install npm -g

###Local Packages
Updating local packages: Use <kbd>npm update</kbd> in the folder where your package.json file is,
this will update the packages to the wanted versions as indicated in your package.json.

###Packages to the Latest Versions
Updating the packages to the latest versions: Use <kbd>npm install -g npm-check-updates</kbd> to install npm-check-updates (<http://www.npmjs.com/package/npm-check-updates>)

Run <kbd>npm-check-updates</kbd> and you can see what can be updated, for global packages use <kbd>npm-check-updates -g</kbd>.

The updates to package.json can be done with <kbd>npm-check-updates -u</kbd>

Finally use <kbd>npm update</kbd> to do the install.