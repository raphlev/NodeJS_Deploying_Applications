# MEAN STACK application

Angular: used to generate client content
Mongo: used to store data in document collection
Express: used to serve client and to manage http request
Node

Express will serve all static files for Angular as well. Angular is also capable of serving content but it is less flexible. Also with Express no need to setup a reverse proxy. So angular is used only as content generator only

# setup Cloud server database using MongoDB

https://cloud.mongodb.com/
Using gmail account (rlptc)
Create a free cluster available for < 500MB
server created = mongodb+srv://learning:learning@nodedeploy-ehxpw.mongodb.net

From new cluster created in https://cloud.mongodb.com/, check Connect page: it is possible to connect using

- MongoDB Shell (linux)
- Application Driver like Node.js
- Compass

Using MongoDB Compass :

- connect using connection SRV: mongodb+srv://learning:learning@nodedeploy-ehxpw.mongodb.net
- create database: "nodejsdeploy" + collection: "games"
- go to "games" collection
- from games.tsv (provided), use online converter to convert into json
- from json file, copy each document and insert to compass>nodejsdeploy>games
- export collection from compass into csv or json files (here provided)
- then using compass, display the nodejsdeploy database: take note of the url displayed at header:

nodedeploy-ehxpw.mongodb.net/nodejsdeploy

This is used by application URI.

# Set Env Variables

Instead of using resource json file, add variables to system

set in system variable settings (better approach for CI/CD process rather using config file: depending on target cloud server, apps will be a dev or prod server, then possible to CI/CD in 2 seperate env)
Windows System Variable:
NG_CMD=prod
MONGO_URL=mongodb+srv://learning:learning@nodedeploy-ehxpw.mongodb.net/nodejsdeploy

Linux: using 'export NG_CMD=prod' ..

# Install

yarn or npm ??

Yarn stores every package in a global cache in your user directory on the file system. "yarn cache list" will print out every cached package. Running "yarn cache dir" will print out the path where yarn’s global cache is currently stored. "yarn cache clean [<module_name...>]" will clear the global cache. It will be populated again the next time yarn or yarn install is run. Additionally, you can specify one or more packages that you want to clean.

- Fast: Yarn caches every package it has downloaded, so it never needs to download the same package again. It also does almost everything concurrently to maximize resource utilization. This means even faster installs.
- Reliable: Using a detailed but concise lockfile format and a deterministic algorithm for install operations, Yarn is able to guarantee that any installation that works on one system will work exactly the same on another system.
- Secure: Yarn uses checksums to verify the integrity of every installed package before its code is executed.

yarn install

or

npm install

Both commands should execute automatically "node build.js" because of postinstall script in package.json otherwise execute it

build.js is used to build angular app to public folder (see build config file .angular-cli.json)

- it generates angular client app content
  Angular is not used to serve static page, this is performed by app.js (see start section)

# protractor can be used for testing angular client app

The test are not correct
See ./angular/e2e/app.e2e-spec.ts + ./angular/e2e/app.po.ts + tsconfig.json

see ./angular/protractor.conf.js file
referenced also in ./angular-cli.json

# testing server side

./test.js is implemented

using tape and request:
npm test

# start

node .\app.js

.\app.js is the entry point. It serves static public folder that contains client angular generated components from previous "node build.js" commands

.\app.js contains also dynamic routes defined in ./app/routes.js and using mongoose model from ./app/models/game.js

./app/routes.js contains GET + POST + PUT + DELETE methods for game object

Note : angular app does not manage anyting else than GET, so in order to test other routes postman can be used using raw body

mongoDB // mongoose connection is managed in ./app/models/game.js which uses the games collection

# See tutorial for deploying options to different cloud servers : https://www.linkedin.com/learning/node-js-deploying-applications

Heroku
AWS
Azure

# See tutorial for Continuous Deployment CI/CD process with different tools : https://www.linkedin.com/learning/node-js-deploying-applications

Jenkins Server
Travis CI
CircleCI

# This is the README file for testing changes to the repository.I'm deploying to staging

Another change
Another change
Testing the CircleCI Install
Checking on the local remote
Another new line for testing
One final github test
Adding a line for heroku push test.

##################################################################################################
################ content of ./angular/README.md created by angular cli############################
##################################################################################################

# Gametable

This project was generated with [angular-cli](https://github.com/angular/angular-cli) version 1.0.0-beta.28.3.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive/pipe/service/class/module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).
Before running the tests make sure you are serving the app via `ng serve`.

## Deploying to GitHub Pages

Run `ng github-pages:deploy` to deploy to GitHub Pages.

## Further help

To get more help on the `angular-cli` use `ng help` or go check out the [Angular-CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
