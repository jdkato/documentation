---
title: Using the Jet CLI
description: Technical documentation for Codeship Pro's CLI (Jet) that allows to debug and run builds locally on the development machine
menus:
  pro/jet:
    title: Using the Jet CLI
    weight: 2
tags:
  - docker
  - jet
  - introduction
  - installation
  - running locally
  - debug
  - setup
  - troubleshooting
  - cli
categories:
  - CLI
redirect_from:
  - /docker/installation/
  - /pro/installation/
  - /pro/getting-started/installation/
  - /docker/cli/
  - /pro/cli/
  - /jet/
  - /docker/getting-started/installation/
  - /pro/builds-and-configuration/cli/
---

{% csnote info %}
If you are unfamiliar with Codeship Pro, we recommend our [getting started guide]({{ site.baseurl }}{% link _pro/quickstart/quickstart-examples.md %}) or [the features overview page](https://codeship.com/features/pro).
Note that if you are using Codeship Basic, you will not be able to use the local CLI.
{% endcsnote %}

* include a table of contents
{:toc}

## Using The Jet CLI

To list available commands, run `jet` with no parameters, `jet -h` or `jet --help`:

```shell
$ jet

Usage:
  jet [command]

Available Commands:
  cleanup     Remove docker resources left behind by jet
  decrypt     Decrypt a file using an AES key
  encrypt     Encrypt a file using an AES key
  generate    Generate an AES key for encrypting files
  help        Help about any command
  load        Pull or build service images
  run         Run a command inside a service container
  steps       Run steps
  update      Download and install the latest version of Jet
  validate    Validate codeship-services.yml and codeship-steps.yml files
  version     Display the jet version

Flags:
  -h, --help   help for jet

Use "jet [command] --help" for more information about a command.
```
## Troubleshooting With Jet

Because the Jet CLI accurately reproduces your CI/CD build pipeline locally, you can use it to quickly solve difficult problems.

For instance, if a test or command fails on a build in Codeship, you can try to reproduce the error with `jet steps`. When you want to test a change, `jet steps` will let you verify the change is working prior to committing so that you don't have to wait for the full build to run remotely to get feedback.

We recommend that developers using Codeship make use of the Jet CLI to improve productivity and solve build-related issues.

{% csnote info %}
The results of a `jet steps` run can differ from the corresponding CodeShip Pro build. We've [listed a number of reasons for why that may be the case]({{ site.baseurl }}{% link _pro/common-issues/jet-pro-disjoint.md %}).
{% endcsnote %}

## Examples

### Display help text
To list the help for any command, execute the command followed by the `-h` or `--help` flag.

```shell
$ jet steps -h
Run steps

Usage:
  jet steps [flags]

Flags:
      --ci-branch string                  The name of the branch being built
      --ci-build-id string                The id of the build being run
...
```

### Option types

#### Multi
Some flags like -e=[ ] may be used multiple times in a single command line, for example:

```shell
$ jet steps -e foo=bar -e baz=qux
```

#### String and Integers
Some flags require a string like `--ci-branch` and can only be specified once.

```shell
$ jet steps --ci-branch master
```
