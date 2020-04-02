# Experimental Repo For Running Drupal 9 with Pantheon's Build Tools and CircleCI Orb

This repository is a stripped down version of the fuller [pantheon-systems/example-drops-8-composer](https://github.com/pantheon-systems/example-drops-8-composer) which shows how Drupal 8 can be run on Pantheon with various git hosts and CI services using [Pantheon's Build Tools](https://pantheon.io/docs/guides/build-tools). This repo shows only GitHub + Pantheon and uses Build Tools wrapped in [Pantheon CircleCI Orb](https://github.com/pantheon-systems/circleci-orb).

At this point this repository is meant for experimentation only.

To create a copy of this repository including a separate GitHub repo, a CircleCI configuration, and a Pantheon sandbox, run:

```
terminus build:project:create stevector/drupal-9-with-pantheon-orb machine-name-for-new-site --stability=dev --team='optional-pantheon-organization-name' 
```
