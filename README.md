# Loggin'

## Setup

### MacOS/Linux

* `npm install`
* `npm start`
* Open another terminal window; from there, `npm run seed` to seed the database

### Windows

* `npm install`
* `npm run build-watch` to start the webpack process
* Open another terminal window; from there, `npm run start-server` to start the server process
* Open another terminal window; from there, `npm run seed` to seed the database

## In either case, make sure you have a database titled "loggin" in order to move forward with this project

By the way, a signup route might look like this (see below):

```js

// A "signup" route and handler function might look like this;

router.post("/signup", async (req, res, next) => {
  try {
    const user = await User.create(req.body);
    req.login(user, err => (err ? next(err) : res.json(user)));
  }
  catch (err) {
    if (err.name === "SequelizeUniqueConstraintError") {
      res.status(401).send("User already exists");
    }
    else {
      next(err);
    }
  }
});

```
