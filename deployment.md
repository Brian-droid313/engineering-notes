# Firebase Deployment (Hosting)

Deploying to Firebase can be a relatively easy process. Documentation is **great** and honestly, I probably do not need to write this up. However, I want to share my own experience and hopefully be able to automate such process in the future!


## What is Firebase and What Hosting Features/Plans does it Offer?
---
Firebase is an app development platform that allows you to build, release, and monitor your apps. It can also provide analytics to see how your users are engaging with your application

For the purpose of this documentation, we will be focusing on how you can deploy (host) your application to Firebase.

### **Plans**

Firebase offer two plans: Spark and Blaze. You can see the different options/features available for both plans, but I am using the free (Spark) version since I mostly am building projects as side hobbies.

Plans: https://firebase.google.com/pricing

## How to Setup a Firebase Project
---

### **Setup a Firebase Project**: https://firebase.google.com/docs/guides

### **Install Firebase Tools: MacOS**

- Documentation: https://firebase.google.com/docs/cli#install-cli-mac-linux
1. Install Node.js and NVM (Node Version Manager)
2. Install firebase via command line
<pre>
npm install -g firebase-tools
</pre>

### **Log in and Test Firebase**

1. Log into Firebase
<pre>
firebase login
</pre>

2. Obtain list of firebase projects that you own
<pre>
firebase projects:list
</pre>

## Initialize project with Firebase
---
1. Enable web frameworks preview
<pre>
firebase experiments:enable webframeworks
</pre>

2. Run initialization command
<pre>
firebase init hosting
</pre>

## Deploy

1. To deploy your project, run the following command. Please note, the only function that is being ran is to host your project.

<pre>
firebase deploy --only hosting
</pre>

2. When your deployment is completed, you will see something like this:

<pre>
✔  Deploy complete!

Project Console: https://console.firebase.google.com/project/sample_project/overview
Hosting URL: https://sample-project.web.app
</pre>

## Problems that You may Encounter
---

A problem that I faced with the initial deployment was that Cloud Functions were being created by default. For example, for image optimization.

<pre>
Building a Cloud Function to run this application. This is needed due to:
 • Image Optimization
</pre>

This would cause the deployment to fail because I did not opt into the Blaze plan.

<pre>
Error: Your project must be on the Blaze (pay-as-you-go) plan to complete this command. Required API artifactregistry.googleapis.com can't be enabled until the upgrade is complete. To upgrade, visit the following URL
</pre>

What I recommend is to either disable such features or opt into the plan. In my case, all I had to do was to remove the photos I was using.

## Thanks for Reading!
---

Thank you for reading this! I know there are tons of info on the internet, but I hope this would be less bulky/overwhelming!.


## References
---
- https://firebase.google.com/pricing
- https://firebase.google.com/docs/guides
- https://firebase.google.com/docs/cli#install_the_firebase_cli
- https://firebase.google.com/docs/cli#install-cli-mac-linux
- https://firebase.google.com/docs/hosting/frameworks/nextjs