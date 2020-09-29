# Create apps in 2 days
I have learned programming from many great people. I want to start sharing the knowledge I have aquired over the years to speed up my work.
Here I will show you how I create real world app in only 2 days.

I build my apps using Amazon (AWS), Amplify, Serverless, Reacts.js, Bootstrap, and npm.

If you need any help, do not hesitate to contact. 

## Projects built in 2 days
* <a href="https://www.yebana.com"> www.yebana.com </a>

* <a href="https://www.bozindo.com"> www.bozindo.com </a>

## How to set up your project

what you will need to do is set up your :
* Backend project 
* Frontend project

## Setting up your Backend project 

To set up your backend follow the steps listed below to the "T." Do not skip steps!!! 

- `Note`: You will need : 

  - A <a href="https://aws.amazon.com/"> AWS account </a>. Create a Root User.
  
  - All codes need to be pasted in a `command prompt` or `Windows Powershell`.
  
  - A <a href="https://github.com/"> Github account </a>.
  
  - Visual Studio (Latest Version)

`Step 0` : Create IAM user on AWS (preferably done in step 8)

`Step 1` : Create a git repo : `xyz-app-api` 

  * ( `"xyz"` is the name of your project. For example, if your project name is facebook. You will name it `facebook-app-api` )

`Step 2` : If not already done, install serverless globaly with : `npm install serverless -g`

- `REF: https://serverless-stack.com/chapters/setup-the-serverless-framework.html`

`Step 3` : Create a project useing serverless NodeJS starter with : `serverless install --url https://github.com/AnomalyInnovations/serverless-nodejs-starter --name xyz-app-api`

 * ( `"xyz"` is the name of your project. For example, if your project name is facebook. You will name it `facebook-app-api` )

`Step 4` : Move to your project in the command prompt :  `cd xyz-app-api`

`Step 5` : Find your project file and open it in a text editor (e.x. Visual Studio)

- `Note` : the directory should contain a `handler.js` and `serverless.yml`. 

  - handler.js : contains code to deploye to AWS Lambda.

  - serverless.yml : contains configuration for AWS server such as Congito, Lambda, DynamoDB, S3 bucket.

`Step 6` : In your project directory (command prompt) install npm package with : `npm install`

`Step 7` : Install uuid and aws-sdk with : `npm install aws-sdk --save-dev` and `npm install uuid --save` if you are developing a payement app, add `npm install --save stripe`

- `Note` : on aws-sdk and uuid

  - aws-sdk : allows to talk to the various AWS services.

  - uuid :  generates unique ids for DynamoDB.

`Step 8` : Install amplify and configure it with : `npm install  -g @aws-amplify/cli` and `amplify configure`

### Configure amplify

  - `regrion`: us-east-2 ;example / press Enter

  - `user name` : IAM name (that you have created) / press Enter

  - `accessKeyId` : IAM Access Key / press Enter

  - `secretAccessKey` : IAM secret access Key / press Enter

  - `Profile Name` : (default) / press Enter

`Step 9` : Edit `serverless.yml` with structured data from `note-app`

- `Note` : Do not change the `service: name`! copy and paste starting below it!

`Step 10` : Copy and Paste resources folder from `note-app` use `s3-bucket.yml` if needed to store pictures, files, or document downloaded by users using your application

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

* `P.S.` Run test with seed identifications (dev and prod) 
* ::::: `NOTE` : console provided identifications has been overrided {do not use it anymore replace all creditential with seed's}
