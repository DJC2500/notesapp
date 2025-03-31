# Full-Stack React Application with AWS Amplify and GraphQL

This project demonstrates how to build, deploy, and manage a full-stack web application using React, AWS Amplify, and GraphQL. The application includes features such as authentication, data storage, and hosting capabilities.

# Author

Created by Divine Ciroma.

# Prerequisites

Before you begin, ensure you have the following:

AWS Account: Sign up for an [AWS account](https://signin.aws.amazon.com/signup?request_type=register).

AWS CLI: Install and configure the [AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

Node.js and npm: Download and install [Node.js](https://nodejs.org/en/download).

Git: Get comfortable with git.

GitHub Account: Create a [GitHub account](https://github.com/)

# Getting Started

Follow these steps to set up and run the project:

# 1. Create and Deploy a React Application

1. Create a New React App:

   ```bash
   npx create-react-app my-app
   cd my-app
   ```
2. Initialize a Git Repository:

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```
3. Create a GitHub Repository:

   - [Create a new repository on GitHub](https://github.com/new).
   - Follow the instructions to push your local repository to GitHub.

4. Deploy with AWS Amplify:

   - Access AWS Amplify Console:
     - Navigate to the [AWS Amplify Console](https://aws.amazon.com/amplify/).
     - Click on Get Started under Deploy.

   - Connect Your Repository:
     - Select GitHub and authorize AWS Amplify to access your repositories.
     - Choose the repository you just pushed and select the branch to deploy.

   - Configure Build Settings:
     - Amplify will detect the build settings for your React app. Review and confirm the settings.

   - Deploy the App:
     - Click Save and Deploy. Amplify will build and deploy your app to a globally available content delivery network (CDN).

   - Verify Deployment:
     - Once the deployment is complete, Amplify provides a URL where your app is hosted.

# 2. Initialize the Amplify Backend

1. Install Amplify CLI:

   ```bash
   npm install -g @aws-amplify/cli
   ```
2. Configure Amplify CLI:

   ```bash
   amplify configure
   ```
   - Follow the prompts to set up your AWS profile.

3. Initialize Amplify in Your Project:

   ```bash
   amplify init
   ```
   - Provide the required information when prompted:
     - Project name: `my-app`
     - Environment name: `dev`
     - Default editor: Choose your preferred code editor.
     - App type: `javascript`
     - Framework: `react`
     - Source Directory Path: `src`
     - Distribution Directory Path: `build`
     - Build Command: `npm run build`
     - Start Command: `npm start`
     - AWS Profile: Select the profile you configured earlier.

4. Add Authentication (Optional):

   ```bash
   amplify add auth
   ```
   - Choose default configuration for authentication.

5. Add GraphQL API:

   ```bash
   amplify add api
   ```
   - When prompted:
     - API type: `GraphQL`
     - API name: `myapiname`
     - Authorization type: `API key`
     - Schema creation: Choose to create a new schema and select the Single object with fields template.

6. Add Storage (Optional):

   ```bash
   amplify add storage
   ```
   - Configure storage options as needed.

7. Deploy Backend Resources:

   ```bash
   amplify push
   ```
   - Confirm the changes and wait for the deployment to complete.

# 3. Connect the React App to the Amplify Backend

1. Install Amplify Libraries:

   ```bash
   npm install aws-amplify @aws-amplify/ui-react
   ```
2. Configure Amplify in Your App:

   - In `src/index.js`, add the following:

     ```javascript
     import { Amplify } from 'aws-amplify';
     import awsExports from './aws-exports';
     Amplify.configure(awsExports);
     ```
3. Implement Authentication UI (Optional):

   - Use Amplify's UI components to add authentication flows:

     ```javascript
     import { withAuthenticator } from '@aws-amplify/ui-react';

     function App() {
       // Your app code
     }

     export default withAuthenticator(App);
     ```
4. Interact with the GraphQL API:

   - Use Amplify's API category to interact with your GraphQL API. For example, to fetch data:

     ```javascript
     import { API, graphqlOperation } from 'aws-amplify';
     import { listItems } from './graphql/queries';

     async function fetchItems() {
       const data = await API.graphql(graphqlOperation(listItems));
       // Process data
     }
     ```

5. Manage Storage (Optional):

   - Use Amplify's Storage category to upload and retrieve files.

# Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

# License

This project is licensed under the MIT License. See the LICENSE file for details.

---
