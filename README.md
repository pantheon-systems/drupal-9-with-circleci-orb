# Experimental Repo For Running Drupal 9 with Pantheon's Build Tools and CircleCI Orb

This repository is a stripped down version of the fuller [pantheon-systems/example-drops-8-composer](https://github.com/pantheon-systems/example-drops-8-composer) which shows how Drupal 8 can be run on Pantheon with various git hosts and CI services using [Pantheon's Build Tools](https://pantheon.io/docs/guides/build-tools). This repo shows only Drupal 9 + GitHub + Pantheon and uses Build Tools wrapped in [Pantheon CircleCI Orb](https://github.com/pantheon-systems/circleci-orb).

At this point this repository is meant for experimentation only.

To create a copy of this repository including a separate GitHub repo, a CircleCI configuration, and a Pantheon sandbox, run this command. Be sure to replace `machine-name-for-new-site` with a machine name of your choice.

```
terminus build:project:create "pantheon-systems/drupal-9-with-circleci-orb:dev-master" machine-name-for-new-site --stability=dev --team='optional-pantheon-organization-name' 
```

After that command completes, verify that Drupal 9 has been installed in the Pantheon Dev environment by visiting it in your browser. this command will get you a one-time log in link that that environment. Be sure to replace `machine-name-for-new-site` with the machine name you chose above.

```
terminus drush machine-name-for-new-site.dev -- user-login
```

Next, deploy to the Pantheon Test and Live environments. When pull requests are created on your GitHub repo they will generate Multidev environments on Pantheon that clone the database and files from the Live environment. Be sure to replace `machine-name-for-new-site` with the machine name you chose above.


```
terminus env:deploy machine-name-for-new-site.test
terminus env:deploy machine-name-for-new-site.live
```
