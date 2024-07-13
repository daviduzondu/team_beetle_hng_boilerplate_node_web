
### Table of Contents
<!-- TOC start -->
- [TEAM BEETLE HNG BOILERPLATE Integration Documentation](#team-beetle-hng-boilerplate-integration-documentation)
  - [Overview](#overview)
  - [Description](#description)
  - [Folder Structure](#folder-structure)
  - [Dependencies (Dev)](#dependencies-dev)
  - [API Endpoints](#api-endpoints)
  - [Database Schema Documentation](#database-schema-documentation)
  - [Database Entity Relationship Diagram](#database-entity-relationship-diagram)
  - [Tables and Relationships](#tables-and-relationships)
    - [1. Users (`users`)](#1-users-users)
    - [2. Organizations (`organizations`)](#2-organizations-organizations)
    - [3. User Organizations (`user_organization`)](#3-user-organizations-user_organization)
    - [4. Messages (`messages`)](#4-messages-messages)
    - [5. User Settings (`user_settings`)](#5-user-settings-user_settings)
    - [6. Contact Submissions (`contact_submission`)](#6-contact-submissions-contact_submission)
    - [7. Notifications (`notifications`)](#7-notifications-notifications)
    - [8. Payments (`payments`)](#8-payments-payments)
    - [9. Widgets (`widgets`)](#9-widgets-widgets)
    - [10. Content (`content`)](#10-content-content)
    - [11. Activity Log (`activity_log`)](#11-activity-log-activity_log)
    - [12. Email Templates (`email_templates`)](#12-email-templates-email_templates)
    - [13. Invite Links (`invite_links`)](#13-invite-links-invite_links)
    - [14. Waitlist (`waitlist`)](#14-waitlist-waitlist)
    - [15. Blog Posts (`blog_posts`)](#15-blog-posts-blog_posts)
  - [Getting Started](#getting-started)
  - [Contribution Guide](#contribution-guide)
  - [Getting Started](#getting-started-1)
      - [If you don't have git on your machine, install it.](#if-you-dont-have-git-on-your-machine-install-it)
  - [Fork this repository](#fork-this-repository)
  - [Clone the repository](#clone-the-repository)
  - [Create a branch](#create-a-branch)
    - [Make Changes](#make-changes)
    - [Run Tests](#run-tests)
  - [commit those changes](#commit-those-changes)
  - [Push changes to GitHub](#push-changes-to-github)
  - [Submit your changes for review into Staging](#submit-your-changes-for-review-into-staging)
  - [Setup Instructions](#setup-instructions)
    - [1. Clone the Repository](#1-clone-the-repository)
    - [2. Install Dependencies](#2-install-dependencies)
    - [3. Configure Environment Variables](#3-configure-environment-variables)
    - [4. Compile TypeScript](#4-compile-typescript)
    - [5. Run the Development Server](#5-run-the-development-server)
    - [6. Run the Production Server](#6-run-the-production-server)
    - [7. Verify the Setup](#7-verify-the-setup)
  - [Folder Structure](#folder-structure-1)
  - [Scripts](#scripts)
  - [Additional Resources](#additional-resources)
  - [Versioning](#versioning)

<!-- TOC end -->

# TEAM BEETLE HNG BOILERPLATE Integration Documentation

## Overview

This is a README file containing the detailed API and DATABASE design of TEAM BEETLE's HNG BOILERPLATE 

## Description
For stage 3 in the Backend Track, we were asked to come up with an architectural design for an API and database based on the requirements found [here](https://github.com/hngprojects/hng_boilerplate_instructions).


## Folder Structure

```
.
├── API_REFERENCE.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTORS_GUIDE.md
├── docs
│   ├── index.html
│   ├── public
│   └── swagger.yaml
├── LICENSE
├── package.json
├── package-lock.json
├── README.md
├── src
│   ├── controllers
│   ├── interfaces
│   ├── services
│   └── utils
├── team-beetle-erd-diagram.png
├── tests
└── tsconfig.json
```
## Dependencies (Dev)

- Node.js
- TypeScript
- Express
- ts-node-dev
- axios
- bcrypt
- cloudinary
- cookie-parser
- cors
- dotenv
- express-rate-limit
- flutterwave-node
- jsonwebtoken
- mjml
- morgan
- multer
- nodemailer
- passport
- passport-jwt
- pg
- sequelize
- seuqelize-cli
- socket.io
- stripe
- uuid

## API Endpoints

All API endpoints can be referenced at https://team-beetle-api-docs.netlify.app/#/ 

## Database Schema Documentation

## Database Entity Relationship Diagram

![Database Entity Relationship Diagram](https://raw.githubusercontent.com/daviduzondu/team_beetle_hng_boilerplate_node_web/main/team-beetle-erd-diagram.png)

## Tables and Relationships

### 1. Users (`users`)

- **Description:** Stores information about users.
- **Columns:**
  - `id`: Primary key
  - `email`: User's email
  - `password_hash`: Hashed password
  - `name`: User's name
  - `role`: User's role in the organisation
  - `created_at`: Timestamp of creation
  - `updated_at`: Timestamp of last update

### 2. Organizations (`organizations`)

- **Description:** Stores information about organizations.
- **Columns:**
  - `id`: Primary key
  - `name`: Organization name
  - `created_at`: Timestamp of creation
  - `updated_at`: Timestamp of last update


### 3. User Organizations (`user_organization`)

- **Description:** Associates users with organizations.
- **Columns:**
  - `id`: Primary key
  - `user_id`: Foreign key referencing `users`
  - `organization_id`: Foreign key referencing `organizations`
  - `role`: Role of the user in the organization
  - `created_at`: Timestamp of creation

### 4. Messages (`messages`)

- **Description:** Stores messages sent between users.
- **Columns:**
  - `id`: Primary key
  - `sender_id`: Foreign key referencing `users` (sender)
  - `recipient_id`: Foreign key referencing `users` (recipient)
  - `subject`: Message subject
  - `body`: Message Body
  - `status`: Message status
  - `created_at`: Timestamp of creation

### 5. User Settings (`user_settings`)

- **Description:** Stores settings for each user.
- **Columns:**
  - `id`: Primary key
  - `user_id`: Foreign key referencing `users`
  - `language`: User's language
  - `region`: User's region
  - `push_notification`: Boolean indicating if push notifications are enabled
  - `email_notification`: Boolean indicating if email notifications are enabled
  - `updated_at`: Timestamp of creation

### 6. Contact Submissions (`contact_submission`)

- **Description:** Stores contact form submissions.
- **Columns:**
  - `id`: Primary key
  - `name`: Name of the person submitting the contact form
  - `email`: Email of the person submitting the contact form
  - `message`: Message content
  - `created_at`: Timestamp of creation

### 7. Notifications (`notifications`)

- **Description:** Stores notifications for users.
- **Columns:**
  - `id`: Primary key
  - `user_id`: Foreign key referencing `users`
  - `type`: Notification type
  - `message`: Notification message
  - `is_read`: Boolean indicating if the notification has been read
  - `created_at`: Timestamp of creation

### 8. Payments (`payments`)

- **Description:** Stores payment information.
- **Columns:**
  - `id`: Primary key
  - `user_id`: Foreign key referencing `users`
  - `amount`: Payment amount
  - `currency`: Payment currency
  - `status`: Payment status
  - `provider`: Payment provider
  - `provider_payment_id`: ID of payment provider
  - `created_at`: Timestamp of creation
  - `updated_at`: Timestamp of last update

### 9. Widgets (`widgets`)

- **Description:** Stores widget information.
- **Columns:**
  - `id`: Primary key
  - `user_id`: Foreign key referencing `users`
  - `name`: Widget name
  - `type`: Widget type
  - `data`: Widget data (JSON)
  - `created_at`: Timestamp of creation
  - `updated_at`: Timestamp of last update

### 10. Content (`content`)

- **Description:** Stores content information.
- **Columns:**
  - `id`: Primary key
  - `type`: Content type
  - `content`: Content data
  - `created_at`: Timestamp of creation
  - `updated_at`: Timestamp of last update

### 11. Activity Log (`activity_log`)

- **Description:** Stores user activity logs.
- **Columns:**
  - `id`: Primary key
  - `user_id`: Foreign key referencing `users`
  - `action`: Action performed by the user
  - `details`: Additional details (JSON)
  - `created_at`: Timestamp of creation

### 12. Email Templates (`email_templates`)

- **Description:** Stores email templates.
- **Columns:**
  - `id`: Primary key
  - `name`: Template name
  - `subject`: Email subject
  - `body`: Email body
  - `created_at`: Timestamp of creation
  - `updated_at`: Timestamp of last update

### 13. Invite Links (`invite_links`)

- **Description:** Stores invite links.
- **Columns:**
  - `id`: Primary key
  - `email`: Email associated with the invite
  - `role`: Role to be assigned
  - `token`: Token
  - `expires_at`: Timestamp of creation
  - `updated_at`: Timestamp of last update

### 14. Waitlist (`waitlist`)

- **Description:** Stores waitlist entries.
- **Columns:**
  - `id`: Primary key
  - `email`: Email of the person on the waitlist
  - `created_at`: Timestamp of creation

### 15. Blog Posts (`blog_posts`)

- **Description:** Stores blog posts.
- **Columns:**
  - `id`: Primary key
  - `title`: Blog post title
  - `content`: Blog post content
  - `author_id`: Foreign key referencing `users`
  - `created_at`: Timestamp of creation
  - `updated_at`: Timestamp of last update

****
## Getting Started

Before you begin, ensure you have the following installed on your machine:

- [Node.js](https://nodejs.org/) (v14 or later)
- [npm](https://www.npmjs.com/) (Node Package Manager, included with Node.js)
- [Git](https://git-scm.com/)

## Contribution Guide

## Getting Started

#### If you don't have git on your machine, [install it](https://docs.github.com/en/get-started/quickstart/set-up-git).

## Fork this repository

Fork this repository by clicking on the fork button on the top of this page.
This will create a copy of this repository in your account.

## Clone the repository

<img align="right" width="300" src="https://firstcontributions.github.io/assets/Readme/clone.png" alt="clone this repository" />

Now clone the forked repository to your machine. Go to your GitHub account, open the forked repository, click on the code button and then click the _copy to clipboard_ icon.

Open a terminal and run the following git command:

```bash
git clone "url you just copied"
```

where "url you just copied" (without the quotation marks) is the url to this repository (your fork of this project). See the previous steps to obtain the url.

<img align="right" width="300" src="https://firstcontributions.github.io/assets/Readme/copy-to-clipboard.png" alt="copy URL to clipboard" />

For example:

```bash
git clone git@github.com:this-is-you/first-contributions.git
```

where `this-is-you` is your GitHub username. Here you're copying the contents of the first-contributions repository on GitHub to your computer.

## Create a branch

Change to the repository directory on your computer (if you are not already there):

```bash
cd first-contributions
```

Now create a branch using the `git switch` command:

```bash
git switch -c your-new-branch-name
```

For example:

```bash
git switch -c add-alonzo-church
```

### Make Changes

Make your changes to the codebase. Ensure your code follows the project's coding standards and guidelines.

### Run Tests

Run the existing tests to ensure your changes do not break anything. If you added new functionality, write corresponding tests.

```sh
npm run test
```

## commit those changes

Now open `Contributors.md` file in a text editor, add your name to it. Don't add it at the beginning or end of the file. Put it anywhere in between. Now, save the file.

<img align="right" width="450" src="https://firstcontributions.github.io/assets/Readme/git-status.png" alt="git status" />

If you go to the project directory and execute the command `git status`, you'll see there are changes.

Add those changes to the branch you just created using the `git add` command:

## Push changes to GitHub

Push your changes using the command `git push`:

```bash
git push -u origin your-branch-name
```

replacing `your-branch-name` with the name of the branch you created earlier.

<details>
<summary> <strong>If you get any errors while pushing, click here:</strong> </summary>

- ### Authentication Error
     <pre>remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
  remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
  fatal: Authentication failed for 'https://github.com/<your-username>/first-contributions.git/'</pre>
  Go to [GitHub's tutorial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) on generating and configuring an SSH key to your account.

</details>

## Submit your changes for review into Staging

If you go to your repository on GitHub, you'll see a `Compare & pull request` button. Click on that button.

<img style="float: right;" src="https://firstcontributions.github.io/assets/Readme/compare-and-pull.png" alt="create a pull request" />

Now submit the pull request.

<img style="float: right;" src="https://firstcontributions.github.io/assets/Readme/submit-pull-request.png" alt="submit pull request" />

Soon your changes will be merged into the staging branch of this project. You will get a notification email once the changes have been merged.

## Setup Instructions

### 1. Clone the Repository

First, clone the repository to your local machine using Git.

```sh
git clone https://github.com/your-username/[app-name].git
cd [app-name]
```

### 2. Install Dependencies

Navigate to the project directory and install the required dependencies.

```sh
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the root directory of the project and add your environment-specific variables. You can use the provided `.env.example` file as a reference.

```sh
cp .env.example .env
```

Edit the `.env` file to match your environment configuration.

### 4. Compile TypeScript

Compile the TypeScript code to JavaScript.

```sh
npm run build
```

### 5. Run the Development Server

Start the development server with the following command. This will also watch for any changes in your code and automatically restart the server.

```sh
npm run start:dev
```

### 6. Run the Production Server

To run the application in a production environment, use the following command:

```sh
npm run start
```

### 7. Verify the Setup

Open your browser and navigate to `http://localhost:3000/api/v1/` to verify that the application is running correctly.

## Folder Structure

Here's an overview of the project's folder structure:

```
.
├── API_REFERENCE.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTORS_GUIDE.md
├── docs
│   ├── index.html
│   ├── public
│   └── swagger.yaml
├── LICENSE
├── package.json
├── package-lock.json
├── README.md
├── src
│   ├── controllers
│   ├── interfaces
│   ├── services
│   └── utils
├── team-beetle-erd-diagram.png
├── tests
└── tsconfig.json
```

## Scripts

Here are some useful npm scripts that you can use during development and production:

- `npm run build`: Compiles the TypeScript code to JavaScript.
- `npm run start:dev`: Starts the development server with live reloading.
- `npm run start`: Starts the production server.
- `npm run test`: Runs the test suite (if available).
- `npm run lint`: Runs the linter to check for code style issues.

## Additional Resources

- [Node.js Documentation](https://nodejs.org/en/docs/)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [Express Documentation](https://expressjs.com/)

By following these steps, you should have your Node.js and TypeScript application up and running. If you encounter any issues, please refer to the documentation of the respective tools or seek help from the community.

## Versioning

This project is versioned to ensure backward compatibility and easy maintenance. The current version is v1.
