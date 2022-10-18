<span id="title">

# My own inverted pendulum benchmark

</span>

[![webots.cloud - Page](https://img.shields.io/badge/webots.cloud-Page-007ACC)](https://benchmark.webots.cloud/run?version=R2022b&url=https://github.com/TotallyRandomGus/my_own-inverted.pendulum_benchmark/blob/main/worlds/inverted_pendulum.wbt&type=benchmark)

## Organizer setup

Here is a quick summary of the instructions for somebody who wants to organise a robotics simulation benchmark. The links in the rest of the setup are relative to the repository where the README is, so to be able to use them you should first [create your own repository](../../generate) from this template and go to its main page to continue reading the instructions.

Then you will need to follow those steps:

### GitHub settings
- Go to the [Settings tab](../../settings):
  - Tick the "Template repository" box so that the competitors can easily make a copy of the simulation files
  - Go to [Actions settings tab](../../settings/actions) and tick the "Allow all actions and reusable workflow" permission to enable the automation scripts and save the setting

- You will need to setup a GitHub secret to be able to fetch your competitors' controllers:

  - [Create a new Personal Access Token](../../../../settings/tokens/new). Give it a name to remember what it is for and set its "Expiration" to the end of the tournament. You can always set it to "No expiration" or recreate a token when it expires to allow the automated scripts to continue working. Tick the "repo" scope box, click "Generate token" and copy the generated code to your clipboard

  - Go to the repo's [secrets settings](../../settings/secrets/actions/new) to create a new repository secret. Name it "REPO_TOKEN", paste in the Personal Access Token you just created and finally click the "Add secret" button.

### Metadata update

- Update the fields inside [webots.yml](../../edit/main/webots.yml):
  - file: put the relative path to your world file
  - maximum-duration: the maximum duration of an evaluation in seconds. Set it not large to avoid long evaluations of broken controllers but not too short to have enough time to finish the task
  - metric: should be one of "percent", "time-speed", "time-duration" or "distance". It depends on how the perfomance is evaluated
  - dockerCompose: it is a special path used by the integrated IDE and GitHub actions to locate the default controller. Change "edit_me" to the name of your main controller
- Replace the files of the [preview folder](/preview) with an example animation of your benchmark (keep the same file names)

### README update

Update the [README file](../../edit/main/README.md):

- Change the title and the description section to fit your new scenario

- Update the different fields of the information section. They are used for the info box on webots.cloud:
  - Difficulty: an idea of the benchmark's complexity (for example: Middle School, High School, Bachelor, Master, PhD...)
  - Robot: the name of the robot used in the benchmark
  - Language: the programming language of the example controller
  - Commitment: an idea of the time required to complete the benchmark (a few minutes, a couple of hours, a couple of days...)

- Replace "ORGANIZER_NAME" in the "How to paricipate" section with your GitHub username

- You can submit your benchmark to [webots.cloud](https://benchmark.webots.cloud/benchmark) to share it with other people. Then you are on the website on the "Benchmark" tab, click on "Add a new benchmark" and enter the URL to your .wbt world file located in the [world folder](./worlds/)

- When you have submitted your benchmark to webots.cloud, change the link of the shield badge at the top of this document to the correct webots.cloud page

### Webots files

Replace/add all the files needed for your Webots simulation at the root of the repository, notably the folders "worlds", "controllers" and the folder "plugins" needed for the robot window.

Finally, when all the previous steps have been made, you can remove this "Organizer setup" section from the README file!

<!-- <details>
<summary style="font-size:1.25em">Detailed step-by-step guide</summary>

TODO: Detailed step-by-step guide if needed
 could be done in the wiki of the repo?

</details>
-->

---

## Description

<span id="description">

In this benchmark, the goal is to program an e-puck2 to balance an inverted pendulum as long as possible. A random force is applied to the tip of the pendulum and grows bigger and bigger as time goes on. An example controller is provided with a basic PID controller.

</span>

<img src="./preview/thumbnail.jpg" width="75%">

## Information

<span id="information">

- Difficulty: Bachelor
- Robot: e-puck2
- Language: Python
- Commitment: a couple of hours

</span>

---

## How to participate

### Create your own entry repository from the template

[Click here](../../generate) to create your own repository or do it manually by clicking on the green "Use this template" button.

Fill the "Repository name" field with a name for your controller.
Choose the visibility of your controller, keep it "Public" if you don't care about people looking at your controller code otherwise set it to "Private".
Finally, click on the green "Create repository from template".

### Add the organizer as collaborator if you set your repository as private

Go to your personal repository page (https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME) and go to the "Settings" tab.

Under "Access" click on the "Collaborators" section.
You will then need to confirm the access by re-entering your GitHub password.

When this is done you should see a "Manage access" box where you will see the current collaborators of the repo.
Click on the "Add people" and search for "TotallyRandomGus". When you found the organizer, add them to the repository.

### Submit your entry by using posting an issue using the provided template

After you added the organizer as a collaborator, go back to the main page of your repository and copy your full repository URL.

Come back to this page and [click here](../../issues/new?assignees=&labels=registration&template=registration_form.yml&title=Registration+to+benchmark) to start your registration. If it doesn't work, you can do it manually by going to the "Issues" tab, creating a new issue and choosing the "Registration to benchmark" template.

Paste your repository URL in the URL field and click the "Submit new issue" button.

A series of automated actions will take place. If everything went well, you should get a message saying that you are successfully registered to the benchmark.

### Modify the template controller and/or create your own one

Everything should be good to go, you can modify the files in the controllers folder.

The supervisor controller is a special controller that is used to evaluate your controller's performance.

Webots supports multiple programming languages, see the [Webots documentation](https://www.cyberbotics.com/doc/guide/language-setup) if you are interested.
Be sure to name your main controller like the default controller (except for the file extension) for it to be used in the leaderboard evaluation.
