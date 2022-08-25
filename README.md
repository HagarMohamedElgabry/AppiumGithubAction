# AppiumGithubAction
"Continuous Integration using GitHub Actions" to run our Appium scripts.

GitHub Actions
GitHub Actions help us to automate our software development workflows in the same place as the source code.

Also, you can create your custom workflows based on your tech stack.

#GitHub Actions Workflow
Workflows are custom automated processes that you can set up in your repository to build, test, package, release, or deploy any code project on GitHub.

Workflows run in Linux, macOS, and Windows and containers on GitHub-hosted machine.

You can create a workflow file configured to run on specific events, for example, every pull request or schedule, and also you can trigger it manually.

Now the branch will be the main branch - this is the default branch, and you can create different branches.

We have "Actions", but first we need to push our existing project to our GitHub repository, and then we will be able to set up our GitHub Actions project.

#Add our project to GitHub or a GitHub repository
To add our existing project to GitHub, this is documentation from GitHub that you can follow for Mac and Windows and Linux, with different operating systems.

For example, we can open the terminal and then start initializing the local directory, and then add all the files in the project and add the various commands.

Let's do it in our project.

This is a project that I created for the GitHub actions to use in our GitHub repository.

This includes our BDD and our test data, data-driven and also includes our applications.

To create our GitHub Actions YML file, we can click on "Actions".

Here we can find different templates for the GitHub Actions projects.

You can find AWS, for Azure, for NodeJS, and a lot of things.

We can select Java with Maven and click "Set up this workflow".

![image](https://user-images.githubusercontent.com/53398885/186633845-43ba1a94-933d-4f28-9fc1-b097827e46c3.png)

For the first one, we will use it for Appium and Android, so we will name the workflow appium-android.yml.

Then we can change the name in this file to "Appium Android".


Here you will see that on every push of the main branch or every pull_request, we will run this trigger.

The build will be ubuntu-latest so we need to change the machine to be MacOS so we will change this to be macos-latest version.

Then, with the steps we have a checkout, we have Java, we have Maven, and everything we will need to add our test steps for installing the Appium, or running Appium in headless mode, or to be able to use the command line with Maven.

We need to change our workflow in this section.

So what did I change here?

I changed the operating system to be macos-latest instead of ubuntu, and I added strategy and under matrix we have api-level, so I will run Android devices with api-level "25" and target will be [default].

Then this is the checkout to check out the code from our repository and then with the Java version, we are setting up NodeJS because we need to use it with installing Appium.

After we use NodeJS with version 12, we can start here with npm installing the latest version of Appium.

Then we can double-check Appium is installed with the Appium version.

After that, we need to run the Appium in headless mode, so we need to use this command:
appium &>/dev/null &

Then, in the step to "Run Appium Tests", we are using the emulator to be able to run our test case in the emulator, and for GitHub Actions, we are using a predefined step with android-emulator-runner with the api-level from the matrix, which will be 25.

These are arrays so you can use different API versions with your test case.

The target is also from the matrix, and x86_64 is the architecture of the device, and the profile is Nexus 6.

After that, in our script, because it's already including Maven and Java in this workflow, from the command line we just need to run:


mvn clean test -Pandroid

This will take the test case or the Android test case and run it on GitHub Actions

