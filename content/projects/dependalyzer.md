---
title: "dependalyzer"
description: "A program to help identify and remediate dependency based attacks, and dependency confusion."
summary: "A program to help identify and remediate dependency based attacks, and dependency confusion."
weight: 10
---

[Check it out on GitHub here!](https://github.com/lachlan-waugh/dependalyzer)

![](https://i.imgur.com/kk08mRi.png)

[![codecov](https://codecov.io/gh/cs9447-team2/money-trees/branch/main/graph/badge.svg?token=QMGZT3LLA3)](https://codecov.io/gh/cs9447-team2/money-trees)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

## What is this?

Dependalyzer provides a more secure way to interact with private and public package repositories using CodeArtifact, it also provides an enforcible process to handle code changes in private repositories and a dashboard that provides actionable intel, where the developers can focus on deploying a fix when the dashboard highlights packages that are vulnerable.

![](https://i.imgur.com/VDpD4Ky.png)

## Table of contents
- [Background](#background)
- [Demo](#demo)
- [Installation](#installation)
- [Deployment](#deployment)
- [Usage](#usage)
- [Team](#team)
- [Components](#components)

## Background

Software based dependency based attacks have been rising as one of the most damaging cyber attacks impacting business in this current time. This project created by Enron2 tries to mitigate some of the risks related to dependency based attacks by preventing basic attack vectors such as dependency confusion, and also provides a clear and visible view of how dependencies are being used.

## Demo

[![Watch the video](https://img.youtube.com/vi/dzok_QP5998/maxresdefault.jpg)](https://www.youtube.com/watch?v=dzok_QP5998)

## Installation

Install all dependencies, use node 14.18.1

```bash
$ npm install
```

## Deployment

Run the setup script [`./setup.sh`](./setup.sh) to deploy the application. Fill in the prompts when requested, for more info read the deployment documentation [here](./apps/deployment/README.md).

## Usage

- First an npmjs account has to be created and a free organisation needs to be created.
- This organisation now serves as the scope/namespace and nobody can create a public package with the name `@<chosen namespace during setup>/<package-name>` except the owner of the npmjs account.
- This project can then be setup with the created organisation.
- You then create a new GitHub repository and initiate a new package under it by running:

```bash
$ npm init --scope=<chosen namespace during setup>
```

- Once the new package is ready to be used, a `git push` or merge to main uploads the `@<chosen namespace during setup>/<package-name>` to the private repository of CodeArtifact.
- You then have to sign into CodeArtifact with the following command

```bash
$ aws codeartifact login --tool npm --domain <company> --repository base-<company> --namespace <scope>
```

- Now any `npm install @<chosen namespace during setup>/<package-name>` will consider the private repository for CodeArtifact and install that latest version.
- During the setup script there will be a link to access the dashboard for the project
- The dashboard will then display all the packages and projects associated with the orgnisation created earlier
- You can then select the report vulnerability to report a vulnerability into the database that can then be viewed in the dashboard

## Team

```
Team 2 (Enron 2)
Mentor: Brian Farnhill & Elisa Han
Tutor: Tim Thacker

Members:
Razin Idzuddin
William Tremain
Fiona O'Chee
Lachlan Waugh
Steven Phung
Andrew Xie
```

## Components

Click on the links below to learn more about each individual component and how it functions in the project

- [Deployment](https://github.com/lachlan-waugh/dependalyzer/tree/main//apps/deployment/README.md)
- [Hooks](https://github.com/lachlan-waugh/dependalyzer/tree/main//apps/hooks/README.md)
- [HTTP](https://github.com/lachlan-waugh/dependalyzer/tree/main//apps/http/README.md)
- [Parser](https://github.com/lachlan-waugh/dependalyzer/tree/main//apps/parser/README.md)
- [Dashboard](https://github.com/lachlan-waugh/dependalyzer/tree/main//apps/dashboard/README.md)
- [Scanner](https://github.com/lachlan-waugh/dependalyzer/tree/main//apps/scanner/README.md)
- [Seeder](https://github.com/lachlan-waugh/dependalyzer/tree/main//apps/seeder/README.md)
