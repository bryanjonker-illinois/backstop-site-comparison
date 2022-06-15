# Backstop comparison project

## Introduction

Backstop is a great project, but it is intended to compare the same project across time. This makes things a bit difficult to understand in a training session where you only have an hour to learn something that requires a whole process to have. 

This training is a bit different. By using the power of mustache and scripting, this project allows you to test two sites and see the difference between them. This can be a production site and a development site, two different versions of the same site, or two sites where you expect content has changed.

## Requirements

* Two sites that are similar, or one site that you can change in between two runs. 
* NPM installed on your machine. See [NPM Install Instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
* Basic knowledge of NPM and JSON.
* (Optional) An IDE like Visual Studio Code. 

## Steps

1. Clone the repository to your local machine and run "npm install" in a command-line prompt to install everything.
2. Update the "pages/urls.json" to reflect your information. Things you can change:
    * The "testname" (currently "Toolkit Information"). This can be anything and is the title of your project. 
    * The "dev" (currently "https://cdn.toolkit.illinois.edu/2.8/"). This is your development URL. If you don't have a development site, you can use your production site. Make sure you include the final "/".
    * The "prod" (currently "https://cdn.toolkit.illinois.edu/2.7/"). This is your production URL. Again, make sure you include the final "/".
    * The individual items inside "urls". Note that the last one cannot have a comma at the end and needs the "last" value set to true. 
3. Run "npm run backstop_create_prod_screenshots" in a command-line prompt or through your IDE. This is generating the initial reference screenshots from your production site. 
4. If you are using a single site, make changes to this site.
5. Run "npm run backstop_test" in a command-line prompt or through your IDE. This will generate a comparison report between the two sites. 

## If you have problems

Make sure your "pages/urls.json" file is proper JSON. You can use an online validator like [JSONLint](https://jsonlint.com/) or use an IDE like Visual Studio to validate your JSON. 

If files are not generated, make sure you aren't adding a double slash (like adding "/" at the end of the "prod" or "dev" and "/" at the beginning of the "url" field.

## Advanced Options
 
You can look at the /backstop_files folder to see the backstop configuration files set up. These files are generated by the /pages/urls.json file plus the mustache files in /templates folder. You could probably get away with generating a single backstop configuration file (using the referenceUrl), but this allows you to see the difference between the two runs.

The /pages/urls.json also has information about the viewport. You can add or remove the viewport sizes you want to check by changing this. Again, note that the last viewport cannot have a comma at the end and needs the "last" value set to true. 

Right now, the configuration options for all the pages are the same except for the label and URL. You can change this by adding additional fields in the /pages/urls.json file and extracting them in the templates using the mustache syntax. Remember that you need ``{{{ }}}`` instead of ``{{ }}`` so the infomration is not HTML encoded. Some things you may want to vary by page are the _hideSelectors_ and _misMatchThreshold_ values.

The package.json has the actual backstop commands. We are not using the "backstop approve" command, which you normally would use to move your test files to approval. Instead, we are using the "backstop reference" command. 

## Links

* [Backstop](https://github.com/garris/BackstopJS)
* [NPM Documentation](https://docs.npmjs.com/)
* [JSON Cheatsheet](https://quickref.me/json)
* [JSONLint](https://jsonlint.com/)
* [Gulp](https://gulpjs.com/)
* [Mustache](https://mustache.github.io/mustache.5.html)
