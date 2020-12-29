# The Sandbox #

## Installation ##

### Installation Requirements ###

* Install and configure Git
* Install and configure Node.js

### Installation Suggestions ###

* Git UI for managing files and branches, eg: SourceTree, GitKrackin
* Code editing software: eg: Microsoft Visual Studio Code, Atom

## Start Development ##

  1. Using your git ui or terminal clone the sandbox repository: `git clone git@github.com:bayfielddesign/sandbox.git`
  2. Create a feature branch from master and label it with your last name: `feature/name`
  3. Navigate to ./app `cd app`
  4. Install packages `npm install`
  5. Start local development server: `npm run serve`
  6. Open your local server at: http://localhost:8080/

## Instructions ##

Using vue's data-driven approach to building user interfaces you will construct a basic registration form.

### Requirements ###

  1. The form can be setup using test data created by you
  2. Required fields: first name, last-name, email, password, confirm password
  3. Required buttons: clear/reset and submit
  4. Basic form validation should be setup for each field
  5. The form will only submit if all fields are populated and pass validation
  6. The form should be styled and polished using scss
  7. The form must maintain an accessibility standard of AA as laid out in the Web Content Accessibility Guidelines (WCAG).
  8. After a successful registration the user should receive a message confirming success and a receipt of the information they provided

Other than the requirements above, get creative and structure/build your project and any way you'd like.

## Submitting ##

  1. Commit all of your changes to your local branch
  2. Push your branch to the remote and submit a pull request
