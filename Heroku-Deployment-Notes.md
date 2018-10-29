# Heroku Deployment & CI/CD

## Intro

- [x] Pre-reading
  - There's a nice shortcut that's (as far as I know) built-in to **VSCode**: type `html` into a blank HTML and it gives you a blank HTML5 boilerplate.
- [x] Goal
  - Understood
- [x] Starting Point
  - Installed
  - Created both DBs
  - Test check - **ALL PASSING**
  - Ran seed file - gave `seeded` message
  - Ran `start-dev`
  - Visited localhost:3000 - 5 people present
  - Examined app structure

## Heroku

- [x] What is Heroku?
  - Pre-readings were useful here.
- [x] The 12-factor app
  - Again, useful readings
- [x] Install the Heroku CLI
  - Signed up on site
  - Went through CLI instructions
  - Can see help menu on `heroku` command
- [x] create
  - logged in from before
  - bikeshedding is a very interesting term for a common issue
  - settled on `some-cool-app`
  - works; created in root directory and not in the clone repo - whoops
  - created new (`some-other-app`) in create repo folder; works - shows heroku
- [x] deploy
  - Returned notification that app is deployed
  - React app is **not** running - site error
    - Something about its type being HTML and not JS...
      <details>
      <summary>CLICK FOR Browser Console error messsage</summary>
  
      ```
      some-other-app.herokuapp.com/:1 Refused to execute script from 'https://some-other-app.herokuapp.com/bundle.js' because its MIME type ('text/html') is not executable, and strict MIME type checking is enabled.
      ```
      </details>
  - Gave me an awesome log with no errors:
    <details>
    <summary>CLICK FOR Heroku Deployment Log</summary>
  
    ```
    0:50 -> Colombo -> ~/Google Drive/FS/Review-Week/PairExercise.Deployment.Solution ->  master -> git push heroku master
    Enumerating objects: 115, done.
    Counting objects: 100% (115/115), done.
    Delta compression using up to 4 threads
    Compressing objects: 100% (70/70), done.
    Writing objects: 100% (115/115), 733.89 KiB | 52.42 MiB/s, done.
    Total 115 (delta 41), reused 115 (delta 41)
    remote: Compressing source files... done.
    remote: Building source:
    remote:
    remote: -----> Node.js app detected
    remote:
    remote: -----> Creating runtime environment
    remote:
    remote:        NPM_CONFIG_LOGLEVEL=error
    remote:        NODE_ENV=production
    remote:        NODE_MODULES_CACHE=true
    remote:        NODE_VERBOSE=false
    remote:
    remote: -----> Installing binaries
    remote:        engines.node (package.json):  unspecified
    remote:        engines.npm (package.json):   unspecified (use default)
    remote:
    remote:        Resolving node version 8.x...
    remote:        Downloading and installing node 8.12.0...
    remote:        Using default npm version: 6.4.1
    remote:
    remote: -----> Building dependencies
    remote:        Installing node modules (package.json + package-lock)
    remote:
    remote:        > nodemon@1.18.4 postinstall /tmp/build_5f1e1bf7e9d8fc99fa2bbb05ccd12c17/node_modules/nodemon
    remote:        > node bin/postinstall || exit 0
    remote:
    remote:        Love nodemon? You can now support the project via the open collective:
    remote:         > https://opencollective.com/nodemon/donate
    remote:
    remote:        added 756 packages from 931 contributors and audited 8718 packages in 18.94s
    remote:        found 0 vulnerabilities
    remote:
    remote:
    remote: -----> Caching build
    remote:        - node_modules
    remote:
    remote: -----> Pruning devDependencies
    remote:        removed 430 packages and audited 2441 packages in 8.553s
    remote:        found 0 vulnerabilities
    remote:
    remote:
    remote: -----> Build succeeded!
    remote: -----> Discovering process types
    remote:        Procfile declares types     -> (none)
    remote:        Default types for buildpack -> web
    remote:
    remote: -----> Compressing...
    remote:        Done: 21.6M
    remote: -----> Launching...
    remote:        Released v3
    remote:        https://some-other-app.herokuapp.com/ deployed to Heroku
    remote:
    remote: Verifying deploy... done.
    To https://git.heroku.com/some-other-app.git
    * [new branch]      master -> master
    ```
    </details>
- [x] logs
  - I can see myself using bash pipelining, **specifically** the highlighted StackOverflow best answer A LOT.
    - Super useful shell command: `heroku logs -t | grep 'error'`
  - Tried `heroku logs --tail`
    <details>
    <summary>CLICK FOR Heroku logs</summary>
  
    ```
    2018-10-27T04:50:26.735976+00:00 app[api]: Enable Logplex by user chrismejia10@gmail.com
    2018-10-27T04:50:26.625398+00:00 app[api]: Release v1 created by user chrismejia10@gmail.com
    2018-10-27T04:50:26.735976+00:00 app[api]: Release v2 created by user chrismejia10@gmail.com
    2018-10-27T04:50:26.625398+00:00 app[api]: Initial release by user chrismejia10@gmail.com
    2018-10-27T04:52:27.000000+00:00 app[api]: Build started by user chrismejia10@gmail.com
    2018-10-27T04:53:03.378730+00:00 app[api]: Release v3 created by user chrismejia10@gmail.com
    2018-10-27T04:53:03.402033+00:00 app[api]: Scaled to web@1:Free by user chrismejia10@gmail.com
    2018-10-27T04:53:03.378730+00:00 app[api]: Deploy c4cac35a by user chrismejia10@gmail.com
    2018-10-27T04:53:06.000000+00:00 app[api]: Build succeeded
    2018-10-27T04:53:09.443815+00:00 heroku[web.1]: Starting process with command `npm start`
    2018-10-27T04:53:13.393231+00:00 app[web.1]:
    2018-10-27T04:53:13.393253+00:00 app[web.1]: > deployment-exercise@1.0.0 start /app
    2018-10-27T04:53:13.393255+00:00 app[web.1]: > node server/index.js
    2018-10-27T04:53:13.393256+00:00 app[web.1]:
    2018-10-27T04:53:14.955541+00:00 app[web.1]: listening on port 48597
    2018-10-27T04:53:15.192343+00:00 heroku[web.1]: State changed from starting to up
    2018-10-27T04:55:40.100463+00:00 heroku[router]: at=info method=GET path="/" host=some-other-app.herokuapp.com request_id=c4e15e87-9596-43b9-891c-8a26fbf8a663 fwd="69.123.21.101" dyno=web.1 connect=1ms service=40ms status=200 bytes=1052 protocol=https
    2018-10-27T04:55:40.192426+00:00 heroku[router]: at=info method=GET path="/bundle.js" host=some-other-app.herokuapp.com request_id=b428dd1b-e6f0-46e9-aa2b-aecc98b19969 fwd="69.123.21.101" dyno=web.1 connect=1ms service=13ms status=404 bytes=392 protocol=https
    2018-10-27T04:55:42.214050+00:00 heroku[router]: at=info method=GET path="/favicon.ico" host=some-other-app.herokuapp.com request_id=4dc3ce36-f06a-4e73-8197-1a87a823fcb0 fwd="69.123.21.101" dyno=web.1 connect=1ms service=4ms status=404 bytes=394 protocol=https
    ```
    </details>
  - `heroku logs -t | grep 'error'` gave me nothing
- [x] Deploying build artifacts
  - Ran `npm run deploy`
  - Browser gave a `500 Internal Server Error`
    - `Network` tab examination reveals the 500 comes from a broken `/users` route

## Heroku Add-ons

- [x] Add the Heroku postgres add-on
  - Located and added
- [x] Heroku run bash
  - Ran bash and the seed file
  - Live project now runs without issues.

## Continuous Integration and Continuous Deployment (CI/CD)

- [x] What is Continuous Integration and Continuous Deployment (CI/CD)?

  - From the StackOverflow answer:

  ```
  What's the difference between these three terms? My university provides the following definitions:

  Continuous Integration basically just means that the developer's working copies are synchronized with a shared mainline several times a day.

  Continuous Delivery is described as the logical evolution of continuous integration: Always be able to put a product into production!

  Continuous Deployment is described as the logical next step after continuous delivery: Automatically deploy the product into production whenever it passes QA!

  They also provide a warning: Sometimes the term "Continuous Deployment" is also used if you are able to continuously deploy to the test system.

  All this leaves me confused. Any explaination that is a little more detailed (or comes with an example) is appreciated!
  ```

  - [ ] Should make flashcards for all three...

- [x] Travis and .travis.yml
  - No issues; triggered a build and it passed; as expected
- [x] Encrypting your Heroku auth token
  - ran `heroku-token`
  - got the key
  - pushed; errored - WRONG APP NAME
  - fixed app name and it worked!

## DONE
