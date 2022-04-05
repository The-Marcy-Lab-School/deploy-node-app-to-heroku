# Tutorial on How to Deploy your Node/Express applicaton to Heroku

These instructionrs were adapted from the following sources and tweaked to fit the need of The Marcy Lab School. 
* [Deploying Node.js Apps on Heroku](https://devcenter.heroku.com/articles/deploying-nodejs)
* [Heroku Postgres](https://devcenter.heroku.com/articles/heroku-postgresql)
* [How to Deploy an Express App on Heroku with Postgres and Knex](https://blog.codeselfstudy.com/blog/deploy-node-postgres-heroku/)

## Step 1: Download the Heroku CLI
1. Run `heroku --version` in your temrinal. If you don't get an error and get a version number, you can skip to Step 2. 
2. Run `npm install -g heroku` to install the heroku cli via npm. Then run `heroku --version` to confirm the installation was successul. 
3. If you're still not able to download the Heroku CLI, see more instructions [here](https://devcenter.heroku.com/articles/heroku-cli). 

## Step 2: Deploy your App
1. Create a [Heroku](https://www.heroku.com/) account if you don't already have one. 
2. In the terminal run `heroku login` to log into your heroku account. Once you log in through the browser, your terminal will be able to create Heroku apps.  
3. Run `heroku create` to create a Heroku remote to where you can push your code. 
4. Run `git push heroku main` or whatever the name of the branch you wish to deploy. For some, it might be `git push heroku master` instead. This will take a few minutes as your app is being deployed. 
5. Run `heroku open` to open your application in the browser. 

## Step 3: Setting up you Database
0. At this point, you can make requests to your server, but you may find that you can't access any data. This is because you must set up a Heroku Database. 
1. Run `heroku addons:create heroku-postgresql:hobby-dev` to create a free Postgres database for your Heroku app. 
2. Run `heroku config:set PGSSLMODE=no-verify` to turn off SSL.
3. To run any command on the Heroku server, prefix the command with `heroku run`. Therefore, the command to run you knex migrations in Heroku is `heroku run knex migrate:latest`. 
4. Run `heroku run knex seed:run` to fun your seed files and seed the Heroku database. 

## Step 4: Verify that your Express API is working
1. If your browser does not already have it open, run `heroku open` to open a new broswer tab to make GET requests to your server. Make requests via the browser and via Postman to ensure all the routes work as expected. 
