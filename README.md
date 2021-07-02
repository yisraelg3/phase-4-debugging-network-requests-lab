# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```sh
bundle install
rails db:migrate db:seed
rails s
```

Then, in a new terminal, run the frontend:

```sh
npm install --prefix client
npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged: 
  1) First I checked the routes/models/controllers and everything seems ok. 
  2) Next step is to try it in the frontend and see what happens. 
  3) I get a 500 error (internal server), so first i need to check what is being passed to the server from the frontend. It seems to be sending to the correct path and the correct column names. I realized that I first should have checked what kind of 500 error it was. It was an "uninitialized constant error" so I first need to check my variable names in my controller. 
  4) I changed Toys to Toy and now it works!

- Update the number of likes for a toy

  - How I debugged:
  1) I decided this time first to try it in the frontend end. I get a unexpected end of json input. This means I'm not rendering any json from the backend. let's fix that.

  2) I added a render into the update method and now it works!

- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged:
  1) I decided n the same approach as from the update, as that was quicker. i tried donating in the frontend and I got a 404 error that means I'm not finding the correct toy. Let's go see why.

  2) It's not obvious what is is broken so I'm putting a byebug in the destroy action to see what's going on.

  3) I didn't even hit the byebug, that tells me that I don't have a route for my destroy action let's fix that. 
  
  4) I added in a destroy action route, and now it works!
