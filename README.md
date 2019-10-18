# amplify-s3-cognito
This is the guide to create S3 bucket and Cognito Userpool.

## 1. Preparation

### 1-1. Install Amplify CLI
```
$ npm install -g @aws-amplify/cli
```

## 2. Setup with Amplify CLI
### 2-1. Initialization
```
$ mkdir amplify-s3-cognito
$ cd amplify-s3-cognito
$ amplify init
? Enter a name for the project amplify-s3-cognito
? Enter a name for the environment dev
? Choose your default editor: Sublime Text
? Choose the type of app that you're building javascript
Please tell us about your project
? What javascript framework are you using none
? Source Directory Path:  src
? Distribution Directory Path: dist
? Build Command:  npm run-script build
? Start Command: npm run-script start
Using default provider  awscloudformation
```

### 2-2. Add Cognito AuthN/AuthZ feature
This will be used to add cognito userpool/identitypool to the project.

```
$ amplify auth add 
Using service: Cognito, provided by: awscloudformation
 
 The current configured provider is Amazon Cognito. 
 Do you want to use the default authentication and security configuration? Default configuration
 Warning: you will not be able to edit these selections. 
 How do you want users to be able to sign in when using your Cognito User Pool? Username
 Warning: you will not be able to edit these selections. 
 What attributes are required for signing up? (Press <space> to select, <a> to toggle all, <i> to invert selection)Email
Successfully added resource amplifys3cognito366c9ceb locally

$ amplify push
```

### 2-3. Add S3 Storage feature
This will be used to put files (objects) to S3 bucket, which will be created automatically by the following commands.

```
$ amplify storage add
? Please select from one of the below mentioned services Content (Images, audio, video, etc.)
? Please provide a friendly name for your resource that will be used to label this category in the project: s3b66e80d4
? Please provide bucket name: s3-cognito-access
? Who should have access: Auth users only
? What kind of access do you want for Authenticated users? create/update, read, delete
Successfully added resource s3b66e80d4 locally

$ amplify push
```
## 3. Generate aws-exports.js
### Edit src/aws-exports.js and create aws-exports.json