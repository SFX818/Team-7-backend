# Project Overview
This repo is the backend for Billy, Nivedh, Ross, and Vanessa's group 3 project, Chirper. When thinking about what type of app we wanted to build, we quickly identified social media as an area of opportunity due to the general lack of trust with existing social media platforms.

This repo includes the models included in our app, the authentication our app uses, and the endpoints our app hits on the database we have set up.

# Link to Frontend Repo
The frontend of our app can be found [here](https://github.com/SFX818/Team-7-frontend)

# Link to Deployed API

# Installation Instructions
- Fork & clone this repo
- cd into local directory and `npm install` to install dependencies
- You will need to have mongoDB installed on your computer

# Approach and ERD
The core functionality of our app involves a user making a post, so we began by defining how we wanted to associate posts and models. [Here](https://lucid.app/lucidchart/invitations/accept/8a5ee3bc-9af1-4987-b8d1-c4cc620a7719) is a link to our ERD.

# Tech Stack
## Security and Authentication
- bcrypt: securely stores user passwords
- JSON Web Tokens: used to authorize users

## Framework
- Express: allows us to write routes that send/retrieve information from our database

## Database
- MongoDB: we used a non-relational database for our app because it provided us with more flexibility than a SQL database
- Mongoose: allows our backend to communicate with our Mongo database

# Routes
Methods | URLs | Actions
--------|------|---------
POST  | /api/auth/signup | register new users
POST  | /api/auth/signin | log in existing users
GET   | /api/test/all    | retrieve public content
GET   | /api/test/user   | access user's content
GET   | /api/test/admin  | access admin's content
POST  | api/posts/post   | publish a new post
PUT   | api/posts/post   | edit an existing post
DELETE| api/posts/post   | delete a tweet
POST  | api/posts/retweet| re-post an existing post
POST  | api/posts/reply  | reply to a post
GET   | api/posts/feed   | view all posts
GET   | api/posts/feed/follow | view all posts from users a user follows
POST  | api/users/follow | follow a user
PUT   | api/users/unfollow | un-follow a user
POST  | /api/posts/favorite | favorite a post 


# Challenges
- We haven't worked with Mongo before, so there was a lot of learning as we went. We addressed this by focusing on incremental coding and regular peer reviews so that we could brainstorm solutions to challenges we ran into and refactor if we found a more efficient way to write a piece of code.
- Another Mongo-related challenge was defining associations between models. We spent a fair amount of time discussing, for instance, if a reply should be embedded or referenced on a post. Embedding presented the benefit of a more consolidated database, but referencing allowed for more flexibility when it came to performing CRUD operations on a reply. Ultimately, we decided to include an isReply Boolean on the Post model which, in conjunction with a reference to the parent post the reply originated from, gave us the ability to distinguish between different types of posts while also being able to track relationships between posts.
