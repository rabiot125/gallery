# Jenkins Pipeline Automation Project

This project focuses on automating Jenkins pipeline tasks.

## Jenkins Setup

1. Install Jenkins on your server or local machine.
2. Install the necessary plugins, including those for Git integration, Pipeline, and Slack integration.
3. Configure Slack integration in Jenkins to receive build notifications.
4. Configure Jenkins pipeline jobs with the appropriate stages and steps.
5. Save and run the pipeline jobs to automate the build, test, and deployment processes.

## Setting up Atlas MongoDB

To set up MongoDB using Atlas, visit [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and follow the instructions to create and configure your MongoDB cluster.

## Project Setup

1. Clone the project repository:
2. git clone https://github.com/rabiot125/gallery.git

2. Install dependencies:
npm install

3. Start the server:
node server

## Branch Merging

To merge the `test` branch into `master`, use the following Git command:
git checkout master
git merge test

## Testing

To run tests, execute:
npm test

## Integrating Slack

To integrate Slack with Jenkins:

1. In your Jenkins project configuration, navigate to the "Post-build Actions" section.
2. Click "Add post-build action" and select "Slack Notifications".
3. Enter the Slack webhook URL obtained from your Slack workspace.
4. Configure additional settings as desired, such as channel, message format, and notifications for build results.

## Deployment

Deploy the project to Render to access the live site.

