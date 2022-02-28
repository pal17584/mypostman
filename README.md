### HOW TO RUN AND INTEGRATE TEST SCRIPT WITH CI/CD TOOLS


## Table of contents

1. [Installation](#installation)
2. [Usage](#usage)
    1. [Run Test Scripts](#run-test-scripts)
    2. [Reporters](#reporters)
3. [Integrate with Jenkin](#integrate-with-jenkin)


### Installation
Step 1: install Node.js >= v10
Step 2: Install Newman is using NPM
```console
  $ npm install -g newman
```
Step 3: Install Reporter package
```console
$ npm install -g newman-reporter-htmlextra
```

## Usage

### Run Test Scripts

#### Run on your location:
The `newman run` command allows you to specify a collection to be run. Go to the forder: API_Collection and run following command using Newman:

```console
$ newman run API_Collection/NAB_AUTO_API_TEST.json -e NAB_TEST_ENV.json
```
#### Run via your Postman desktop:
Step 1: Create a collection
Step 2: Import the file: NAB_AUTO_API_TEST.json
Step 3: Import the test environment file: NAB_TEST_ENV.json
Step 4: Run the script.
  
### Reporters
Use the installed reporter, either via the CLI, or programmatic usage.<br/>

```console
$ newman run API_Collection/NAB_AUTO_API_TEST.json -e NAB_TEST_ENV.json -r htmlextra
```

## Integrate with Jenkin

### Step 1: Install Node.js and Newman in Jenkins server:
Step 1: install Node.js >= v10
Step 2: Install Newman is using NPM
```console
  $ npm install -g newman
```
Step 3: Install Reporter package
```console
$ npm install -g newman-reporter-htmlextra
```
Step 4: Install HTML publisher Jenkin plugin to link HTML report to the build

### Step 2: Integrate with Postman scripts
 1. Create a new job with Freestyle project
 2. In 'Build' tab, add a build step in the project and choose Execute Shell
 3. Add a shell command as:

```console
$ newman run API_Collection/NAB_AUTO_API_TEST.json -e NAB_TEST_ENV.json -r htmlextra
```
4. In 'Source Code Management' tab, click on Git and paste Github reposity URL in 'Repository URL' field

### Step 3: Public HTML report
 1. In Post-build Actions, input HTML directory, index pages, report title
 2. Save the job

 Additional, you can config in Build section to send email with HTML report after the jenkins job is finished to your team.

[back to top](#table-of-contents)


