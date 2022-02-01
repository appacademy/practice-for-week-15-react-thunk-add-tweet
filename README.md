# Add A Post to Twitter Thunk App

In the videos, you learned how to create a _thunk_ as well as how to create a
`GET` route that goes from the Express backend through the `thunk`
middleware all the way to the component. Now it's your turn to create a `POST`
route for the tweets.

## Setup

Clone the starter repo accessible from the `Download Project` button at the
bottom of this page.

## Backend

Take a moment to look through all of the backend code. Then do the following:

1. `cd` into the __backend__ directory
2. Install dependencies with `npm install`
3. Create a __.env__ file based on the __.env.example__ with proper settings for
   your local environment:
   - The server should be listening for requests on port 5000.
   - The database owner should have a username of your choice which you can
     create and a password of "password".
   - The name of the database should be "twitter_lite"
   - The host of the database should be "localhost"
4. Create a database user with the same name and password as found in your
   __.env__ file with CREATEDB privileges
5. Run

   - `npx dotenv sequelize db:create`
   - `npx dotenv sequelize db:migrate`
   - `npx dotenv sequelize db:seed:all`
   - `npm start`

6. Create a POST route to add a tweet with no validation. Refer to the GET route
   that is in your __routes/api/tweets.js__ file and make the changes based on a
   POST route

## Frontend

In the __frontend__ folder, you are going to add all the pieces to `POST` a
fetch call to the backend, which will subsequently add a tweet to the database.
If successful, the browser should automatically update the page based on the
`useSelector` that was already created in the videos.

Without giving you the explicit steps this time, here is a barebones checklist
of what you need to do:

### Store

- Add a _thunk action creator_ to add a post to the database using the `POST`
  route you created. Make sure you export it.
  Remember a post will need:

  - a `method` key
  - a `headers` key with the `'Content-Type'` of `'application/json'`
  - a `body` key that uses `JSON.stringify` to send the information

- Add a regular _action creator_ which should receive the information from the
  thunk action creator and use it as the payload.

- Create a constant to use in the action creator.

- Add a case in the reducer for adding a tweet and add a tweet using
  normalization. Do not mutate state!

### Component

- Create a form in the __CreateTweet.js__ file's `CreateTweet` component.
- Use local state for the tweet information.
- Use a `handleSubmit` function to check if the tweet is empty. If it isn't,
  dispatch the tweet using the thunk action creator.
- Don't forget to instantiate your component on the page!