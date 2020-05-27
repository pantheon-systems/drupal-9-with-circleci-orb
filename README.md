# Drupal 9 with Pantheon's Build Tools and CircleCI Orb

This repository is a stripped down version of the fuller [pantheon-systems/example-drops-8-composer](https://github.com/pantheon-systems/example-drops-8-composer) which shows how Drupal 8 can be run on Pantheon with various git hosts and CI services using [Pantheon's Build Tools](https://pantheon.io/docs/guides/build-tools). This repo shows only Drupal 9 + GitHub + Pantheon and uses Build Tools wrapped in [Pantheon CircleCI Orb](https://github.com/pantheon-systems/circleci-orb).


_Warning: Drupal 9 sets a higher required version for MariaDB than is currently available on Pantheon. [This repository uses patches to circumvent installation errors related to the database version](https://github.com/pantheon-systems/drupal-9-with-circleci-orb/blob/e86429c338ec3064965bc7a6bc7bd47ec0f03b81/composer.json#L44)_. Pantheon engineering is working to make a higher version available in the coming months. Until the higher version is available, we do not recommend switching your production websites to Drupal 9.

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
