# Create apps in 2 days (No complete yet! :))

How I am able to build projects in 2 days or less.

I build my apps using Amazon (AWS), Amplify, Serverless, Reacts.js, Bootstrap, and npm.

If you need any help, do not hesitate to contact me. 

## Projects built in 2 days
* <a href="https://www.yebana.com"> www.yebana.com </a>

* <a href="https://www.bozindo.com"> www.bozindo.com </a>

## How to set up your project

All you need is a :

* Backend folder 

* Frontend folder

## Setting up your Backend project folder

To set up your backend follow the steps listed below to the "T." Do not skip steps!!! 

- `Note` : You will need : 

  - A <a href="https://aws.amazon.com/"> AWS account </a>. Create a Root User.
  
  - All codes need to be pasted in a `command prompt` or `Windows Powershell`.
  
  - A <a href="https://github.com/"> Github account </a>.
  
  - Visual Studio (Latest Version)
  
  - <a href="https://seed.run/"> Seed account </a> for your Backend CI/CD

`Step 0` : Create IAM user on AWS (preferably done in `step 8`)

`Step 1` : Create a git repo : `xyz-app-api` 

  * ( `"xyz"` is the name of your project. For example, if your project name is facebook. You will name it `facebook-app-api` )

`Step 2` : If not already done, install serverless globaly with : `npm install serverless -g`

- `REF: https://serverless-stack.com/chapters/setup-the-serverless-framework.html`

`Step 3` : Create a project using serverless NodeJS starter with : `serverless install --url https://github.com/AnomalyInnovations/serverless-nodejs-starter --name xyz-app-api`

 * ( `"xyz"` is the name of your project. For example, if your project name is facebook. You will name it `facebook-app-api` )

`Step 4` : Move to your project in the command prompt :  `cd xyz-app-api`

`Step 5` : Find your project file and open it in a text editor (e.x. Visual Studio)

- `Note` : The directory should contain a `handler.js` and `serverless.yml`. 

  - handler.js : contains code to deploy to AWS Lambda.

  - serverless.yml : contains configuration for AWS server such as Congito, Lambda, DynamoDB, S3 bucket.

`Step 6` : In your project directory (command prompt) install npm package with : `npm install`

`Step 7` : Install uuid and aws-sdk with : `npm install aws-sdk --save-dev` and `npm install uuid --save` if you are developing a payement app, add `npm install --save stripe`

- `Note` : on aws-sdk and uuid

  - aws-sdk : allows to talk to the various AWS services.

  - uuid :  generates unique ids for DynamoDB.

`Step 8` : Install amplify and configure it with : `npm install  -g @aws-amplify/cli` and `amplify configure`

### Configure amplify

  - `regrion`: us-east-2 / press Enter (choose the region of your choice)

  - `user name` : IAM name (that you have created) / press Enter

  - `accessKeyId` : IAM Access Key / press Enter

  - `secretAccessKey` : IAM secret access Key / press Enter

  - `Profile Name` : (default) / press Enter

`Step 9` : Edit `serverless.yml` with structured data from `note-app`

- `Note` : Do not change the `service: name`! copy and paste starting below it!

`Step 10` : Copy and Paste resources folder from `note-app` use `s3-bucket.yml` if needed to store pictures, files, or documents downloaded by users using your application

- `Note` : `tests` folders (in resources folder, and in root) are needed to set up payment only (Delete if not needed)

- `Note` : also delete `billing-lib.js` from `libs` folder when you delete `tests` folders

  - Delete `stripeSecretKey` from environment in `serverless.yml`

  - Delete `billing` from `functions` in `serverless.yml`

`Step 11` : Copy and Paste `libs` folder 

- `Note` : `mock` folder is not needed as it is for `tests` file only

`Step 12` : Include the following files to the root folder: `get.js`, `list.js`, `delete.js`, `update.js`, `create.js`

### Make sure to edit: 

* `Table Names` ( `vwx` is the name you choose if it's a products, services, posts, emails, ...] and `xyz` is the name of your project )

- `Note` : if your project is about emails then vwx is "emails", if it's about products then vwx is "products", ... etc

   * `tableName` in `custom : tableName` in `serverless.yml` ( ex. ${self:custom.stage}-`xyz`-`vwx`; ex. ${self:custom.stage}-`facebook`-`posts` )

* line 2 after `Resources` in `resources folder`, `dynamobd-table.yml` ( ex. `Xyz`Table )
   
* use the name above ( ex. `Xyz` ) in `serverless.yml` in `provider` -> `Resourse` -> `"Fn:GetAtt":[ XyzTable, Arn ]` 

* `User Pool Name`

  * `UserPoolName` in `Resources` -> `Properties` in `cognito-user-pool.yml` ( ex. -`xyz`-user-pool -> where `xyz` is your project name; ex. -facebook-user-pool )
  
  * `ClientName`  in `Resources` -> `CognitoUserPoolClient` -> `Properites` in `cognito-user-pool.yml` ( ex. -`xyz`-user-pool-client -> where `xyz` is your project name )
  
* `Identity Pool Name` 

  * `IdentityPoolName` in `Resources` -> `Properties` in `cognito-identity-pool.yml` ( ex. XyzIdentityPool -> where xyz is your project name )

`Step 13` : Deploy project with, use `-v` to display data: `serverless deploy -v`

* `Note` : use the following for a precise deployment : `serverless deploy --stage $STAGE_NAME`

* `Note` : When using Stripe, `env:STRIP_SECRET_KEY` will give you an error. Make sure you have `billings.js` file in your root

`Step 14` : Run tests with console provided identifications ( dev and prod ).

* `Note` : see BACKEND TESTS bellow for this step, do not skip!

`Step 15` : Initialize with Github repo ( go to github and copy and paste the code for initializing )

`Step 16` : commit your changes to the repo with : `git add .` then `git commit -am "my commit"` then `git push`

`Step 17`: Set up backend with `seed`

* `Optional` : Add Stripe variable to the the `.env` file

`Step 18` : Run version control with : `npm version patch` then `git push` repeat for every deployment to sync with seed

* `P.S.` Run test with seed identifications ( dev and prod ) 

* ::::: `NOTE` : console provided identifications has been overrided ( do not use it anymore replace all creditential with Seed's )

## Setting up your Frontend project folder

- `Note` : You will need : 

  - A <a href="https://netlify.com/"> Netlify account </a>. Create a Root User.
  
  - All codes need to be pasted in a `command prompt` or `Windows Powershell`.
  
  - A <a href="https://github.com/"> Github account </a>.
  
  - Visual Studio (Latest Version)

`Step 0` : Create a git repo `xyz-app-client`

  * ( `"xyz"` is the name of your project. For example, if your project name is facebook. You will name it `facebook-app-client` )

`Step 1` :  Create react app with : `npx create-react-app xyz-app-client`

`Step 2` : Switch to project with : `cd name-app-client` then `npm start`

`Step 3` : Change App `title` in `public` folder -> `index.html`

* :::: `Note` : to ignore Visual studio add `.vs` to `gitignore` file (this is important before pushing to Github)

`Step 4` : Initialize with Github repo

`Step 5` : Install Boostrap with : `npm install react-bootstrap bootstrap --save`

`Step 6` : Place stylesheet in `public` folder -> `index.html` with : `<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">`

`Step 7` : Install react-router-dom with : `npm install react-router-dom --save`

`Step 8` : Install react router bootstrap with : `npm install react-router-bootstrap --save`

`Step 9` : Install aws amplify with : `npm install aws-amplify --save`

`Step 10` : (if needed) Intall react stripe element with : `npm install --save react-stripe-elements`

`Step 11` : (if needed) Include stripe script with : `<script src="https://js.stripe.com/v3/"></script>`  

`Step 12` : Copy and paste all the skeleton code `components`, `containers`, `libs`, `app.js`, `config.js`, `index.js` and `Routes.js` do not delete and paste the `src` file itself) template `notes-app-client`

`Step 13` : Change all data in `config.js`

`Step 14` : Remove `BillingForm.js`, `Setting.js` and `BillingForm.css`, `Setting.css` and from components in :root folder `Route.js` remove import `Setting` and corresponding Routes

`Step 14` : Initialize with git 

`Step 15` : Commit

