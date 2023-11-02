# Messenger

A one-to-one realtime chat app.

## Working inside a Cloud Environment

## Local Setup

**Note:** these setup steps are not necessary when running the code on GitPod. They are only necessary when running the project on your local machine.

Create the PostgreSQL database (these instructions may need to be adapted for your operating system):

```
psql
CREATE DATABASE messenger;
\q
```

Alternatively, if you have docker installed, you can use it to spawn a postgres instance on your machine:

```
docker run -it -p 5432:5432 -e POSTGRES_DB=<database-name> -e POSTGRES_USER=<database-username> -e POSTGRES_PASSWORD=<database-password> postgres -c log_statement=all
```

Update db.js to connect with your local PostgreSQL set up. The [Sequelize documentation](https://sequelize.org/master/manual/getting-started.html) can help with this.

Create a .env file in the server directory and add your session secret (this can be any string):

```
SESSION_SECRET = "your session secret"
```

In the server folder, install dependencies and then seed the database:

```
cd server
npm install
npm run seed
```

In the client folder, install dependencies:

```
cd client
npm install
```

### Running the Application Locally

In one terminal, start the front end:

```
cd client
npm start
```

In a separate terminal, start the back end:

```
cd server
npm run dev
```

## How to Run E2E Tests

1. Seed the database with `npm run seed` in `server` directory.
1. Start the backend server with `npm run dev` in `server` directory.
1. Start the frontend server with `npm start` in `client` directory.
1. Open Cypress dashboard with `npx cypress open` in `client` directory.
1. Click on the test suite to run (e.g. `auth.spec.js`).

#### Notes

- You need to seed the database before each run. Because E2E test cases writes data to
  the actual database, re-seeding is necessary to assure consistent test results.
- The E2E tests are not comprehensive.
  There is a test for the authentication pages that should pass with the starting code,
  and some tests for some of the functionality for some of the tickets you will be assigned.
- When you push your changes to GitHub, E2E tests are automatically executed on GitHub Actions.
  You can find test results under Pull request > Checks > test > Cypress (see screenshots below).


### Task 1: Fix bug

Our starting code has some bugs that need to be investigated and resolved. 
One issue is that new messages do not appear immediately on the screen. 
We want new messages to show up instantly in the chat UI for both existing and new conversations. 
Additionally, messages are shown in the wrong order when the page loads. 
They should be displayed in chronological order, with the oldest messages at the top and newest messages at the bottom.

Cypress tests are included in the starter code for this ticket (bug-fix-ticket.spec.js).  
These tests should pass once both bugs are addressed.

Create a new markdown file at the root of the repository called bug-fix.md. 
Please share in this file the steps you followed to debug this issue. What tools did you use?


### Task 3: Feature: Implement a read status for messages

We want to keep track of whether the recipient has read each message, and update the front-end UI accordingly. 
This includes showing the number of unread messages in a conversation. 
To see the different updates required to show unread messages, refer to this [Figma file](https://www.figma.com/file/LnznWRFvyfWO5Mzztz5TzQ/translate-messenger?type=design&node-id=0-1&mode=design) 
(Note: The Figma file contains other specs not relevant to this feature).

Create a new markdown file at the root of the repository called read-messages.md. 
In this file, please explain a couple different ways we could have stored the read status in the database for this feature. 
What are the benefits and drawbacks of each?

