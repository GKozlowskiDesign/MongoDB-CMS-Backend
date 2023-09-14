# MongoDB NodeJS CMS BackEnd
The motivation for this project was to help me write code more efficiently and to understand foundational concepts and standardized processes of using MongoDB in connection to ExpressJS and NodeJs.

# Table of Contents
<ol>
  <li>Featured</li>
  <li>Technologies</li>
  <li>Architecture</li>
  <li>Authentication</li>
  <li>Categories</li>
  <li>Posts</li>
  <li>Users</li>
  <li>Release Checklist</li>
  <li>General Considerations</li>
  <li>Contributions</li>
  <li>License</li>
  <li>Acknowledgments</li>
</ol>


# Featured
<ul>
  <li>I learned how to set up different types of Models such as Posts, Users, and Authentication</li>
  <li>I learned more of the standardized processes of using MongoDB or NoSQL databases tools</li>
  <li>I learned more about use of ExpressJS and NodeJS with a NoSQL database</li>
</ul>

# Technologies

- <b>JavaScript: </b>The primary programming language for implementing dynamic and interactive elements of the website.
- <b>ExpressJS: </b>Express.js is a minimalistic and flexible Node.js web application framework. It simplifies building robust APIs and web applications by providing a set of features for routing, middleware, and handling HTTP requests and responses.
- <b>AWS MongoDB Cluster: </b> An AWS MongoDB Cluster refers to a managed MongoDB database service offered by Amazon Web Services (AWS). It provides scalable, high-performance MongoDB databases in a cloud environment, allowing users to offload the operational aspects of database management while focusing on application development.
- <b>Mongoose: </b>Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js. It provides a convenient way to interact with MongoDB databases, defining schemas, models, and perform operations on data using a higher-level abstraction.
- <b>Nodemon: </b>Nodemon is a tool used during Node.js development. It monitors for changes in your source code and automatically restarts your server, saving you from manually stopping and restarting the server after each code modification.
- <b>Bcrypt: </b>A library to help you hash passwords. You can read about bcrypt in Wikipedia as well as in the following article: How To Safely Store A Password.
- <b>Multer:</b> Multer is a node.js middleware for handling multipart/form-data, which is primarily used for uploading files. It is written on top of busboy for maximum efficiency.
- <b>Path:</b> This is an exact copy of the NodeJS ’path’ module published to the NPM registry.
</ul>

# Architecture
The Model-Controller-Route (MCR) architecture is a design pattern commonly used in web applications, including those built with Node.js, Express.js, and NoSQL databases like MongoDB. 

> This architecture separates the concerns of your application into three main components:

<b>Model:</b> The model represents the data structures and the business logic of your application. In the context of MongoDB, the model typically corresponds to the schema that defines the structure of the documents you'll store in the database. In Node.js, you can use libraries like Mongoose to define and work with models. The model interacts directly with the database, handling data validation, retrieval, insertion, and updates.

<b>Controller:</b> The controller acts as an intermediary between the routes and the model. It contains the application's logic for processing requests, making decisions, and invoking methods on the model to interact with the database. Controllers handle tasks like data validation, authentication, and responding to client requests. Controllers are typically organized based on the routes they handle.

<b>Routes:</b> Routes define the endpoints and routes requests to the appropriate controller methods. In Express.js, you create routes using the Router object. Each route is associated with one or more HTTP methods (GET, POST, PUT, DELETE, etc.) and specifies a URL path. When a request matches a defined route, the corresponding controller method is executed.

![mvc_express](https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/ee6163cc-fbab-4687-8690-17a30c903e88)

# Authentication
<h3>Description</h3>

> This code is for a Node.js application using the Express.js framework to create two API routes for user registration and user login. It appears to be related to user authentication and is likely part of an authentication system for a web application.

<p><b>User Registration Endpoint (/register):</b></p>

<ul>
  <li>When a POST request is made to /register, the code attempts to create a new user record in the database.</li>
  <li>It generates a salt using bcrypt.genSalt and then hashes the user's password with the generated salt using bcrypt.hash.</li>
  <li>It creates a new User instance with the provided username, email, and the hashed password.</li>
  <li>It saves the new user to the database using newUser.save() and responds with a JSON representation of the newly created user if successful.</li>
  <li>If there's an error during registration, it responds with a 500 internal server error and sends the error message.</li>
</ul>


<p><b>User Login Endpoint (/login):</b></p>

<ul>
  <li>When a POST request is made to /login, the code attempts to authenticate a user.</li>
  <li>It searches the database for a user with the given username using User.findOne.</li>
</ul>
<div align="center" background-color="#000000" >
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/e715f5b6-a8f1-4cd1-9218-22d9c0106c4e" align="center" height="300" width="400">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/70273f07-8d59-4d7a-b665-3ae58147dbb7" align="center" height="300" width="400">

</div>
<br>

# Categories
<h3>Description</h3>

> This code defines an Express.js API route for managing categories.

<p><b>Category Creation (POST):</b> When a POST request is made with JSON data containing a category name, it creates a new category using the provided data and saves it     to the database. If successful, it responds with the saved category. If there's an error, it returns a 500 internal server error.</p>
<p><b>Fetching All Categories (GET):</b>  When a GET request is made to this route, it retrieves all categories from the database and responds with a JSON array containing the categories. If there's an error, it returns a 500 internal server error.</p>
<div align="center">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/43a900ad-8804-4e30-8076-35ad04b1655f" align="center" height="250" width="400">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/8434d348-b835-4aec-80ed-579e554f4406" align="center" height="250" width="400">
</div>
<br>

# Post
<h3>Description</h3>

> This code defines two API routes for managing posts within a Node.js application using Express.js

<p><b>Create Post (POST):</b> This route allows users to create a new post. When a POST request is made to the root URL ("/"), it creates a new Post object based on the data provided in the     request's body. It then attempts to save this post to the database. If successful, it responds with the saved post data (HTTP 200). If there's an error, it responds with a 500 internal server   error.</p>
<p><b>Update Post (PUT):</b> This route is used to update an existing post identified by its ID. It first checks if the post's username matches the one provided in the request body, ensuring    that only the original author can update the post. If it's the correct user, the route updates the post's data with the new content provided in the request body using Post.findByIdAndUpdate.    It then responds with the updated post data (HTTP 200). If there's an error during either the authorization or the update process, it responds with a 500 internal server error or a 401          unauthorized error if the user is not authorized to update the post.</p>
<div align="center">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/7f563e0b-7484-46d6-bcbf-23219c8fa9f4" align="center" height="300" width="400">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/856bae67-eff8-4202-bafa-e293553885b7" align="center" height="300" width="400">
</div>

<h3>Description</h3>

> This code defines two API routes for managing posts within a Node.js application using Express.js 

<p><b>Delete Post (DELETE):</b> When a DELETE request is made to /id, the code first attempts to find the post by its ID using Post.findById. If the post is found, it checks if the username     associated with the post matches the username provided in the request body for authorization. If authorized, it proceeds to delete the post using post.delete() and responds with a success       message ("Post has been deleted!") and an HTTP status code of 200. If not authorized, it responds with a 401 unauthorized error. If there's an error during the deletion process, it responds     with a 500 internal server error.</p>
<p><b>Get Post (GET):</b> When a GET request is made to /id, the code attempts to find the post by its ID using Post.findById. If the post is found, it responds with the post data in JSON       format and an HTTP status code of 200. If the post is not found, it responds with a 404 not found error.</p>
<p>These two routes allow users to delete their own posts (if authorized) and retrieve posts by their unique IDs.</p>
<div align="center">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/c1066e76-758d-441e-b275-c19a5d29a65d" align="center" height="300" width="400">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/6ee0316c-94a1-40a1-b268-c9a82eaf167a" align="center" height="300" width="400">
</div>

<h3>Description</h3>

> This code defines an API route for managing posts within a Node.js application using Express.js

<p>
<b>GET All Posts ("/"):</b> When a GET request is made to this route, it retrieves posts from the database. It can filter posts by two query parameters:
username: If username is provided as a query parameter, it retrieves posts created by that specific user.
catName: If catName is provided as a query parameter, it retrieves posts that belong to the specified category.
</p>
<div align="center">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/c9124d49-4169-4369-8458-661755e72548" align="center" height="400" width="400">
</div>
<br>

# User
<h3>Description</h3>

> This code defines an API route for managing a user account within a Node.js application using Express.js. These routes are used for user registration and authentication, ensuring secure password storage and authentication before granting access to user data.

<p><b>User Registration ("/register"):</b> This route handles user registration. When a POST request is made with user registration data (including username, email, and password), it does the following:</p>
<p><ul>
<li>It generates a salt using bcrypt.genSalt(10) for password hashing security.It hashes the provided password with the generated salt using bcrypt.hash.</li>
<li>It creates a new User object with the provided username, email, and the hashed password.</li>
<li>It saves the new user to a database and responds with the user data (excluding the password) if successful (HTTP 200). If there's an error, it responds with a 500 internal server error</li> 
</ul></p>
<p><b>User Login ("/login"):</b> This route handles user login. When a POST request is made with login data (username and password), it does the following:</p>
<p>
<ul>
<li>It attempts to find a user in the database with the provided username using User.findOne.</li>
<li>If no user is found, it responds with a 400 bad request and an error message ("Wrong Credentials!").</li>
<li>If a user is found, it compares the provided password with the stored hashed password using bcrypt.compare.</li>
<li>If the passwords do not match, it responds with a 400 bad request and an error message ("Wrong Credentials!").</li>
<li>If the passwords match, it constructs a response object containing all user properties except the password (using destructuring and _doc) and responds with this user data (HTTP 200).</li>
<li>If there's an error during the login process, it responds with a 500 internal server error.</li>
</ul>
</p>
<div align="center">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/470dffbc-f5af-4bba-82a9-9721536818b4" align="center" height="300" width="400">
<img src="https://github.com/GKozlowskiDesign/Project_CMSBackendMongoDB/assets/82541715/39d8a0ce-4b04-4c43-b590-584807c0c34a" align="center" height="300" width="400">
</div>

# Release Checklist

- [x] Deploying is consistent across all environments.
- [x] Environments have distinct, defined names for reference.
- [x] Uniform software stack across all environments.
- [x] Configuration is version-controlled (web, CI, etc.).
- [x] Tested on target networks and devices.
- [x] Simplicity in tracking code across environments.
- [x] A clear versioning scheme was established.
- [x] Versions easily linked to code state.
- [x] Feasible rollback after deployment.
- [x] Functional backups in operation.
- [x] Tested restoration from backups.
- [x] No secrets in version control.
- [x] Active logging is in place.
- [x] Defined process for log access/search.
- [x] Logs include exceptions and traces.
- [x] Errors mapped to stack traces.
- [x] Comprehensive release notes were written.
- [x] Current server environments are maintained.
- [x] Updates plan for server environments.
- [x] The product was subjected to load testing.
- [x] Replicating environments via a method.
- [x] Automation for repeating releases.

# General Considerations
<ol>
  <li>What is the expected/required lifespan of the project?</li>
  <li>Is the project one-off, or will there be continuous development?</li>
  <li>What is the release cycle for a version of the service?</li>
  <li>What environments (dev, test, staging, prod, ...) are going to be set up?</li>
  <li>How will downtime of the production service impact the value of the service?</li>
  <li>How mature is the technology?</li>
  <li>Are major changes that break backward compatibility to be expected?</li>
</ol>

# Contributing
<p>Contributions to the Website are welcome! If you find any issues or have suggestions for improvements, please feel free to open an issue or submit a pull request.</p>

# License
<p>This project is licensed under the <a href="LICENSE">MIT License</a>.</p>

# Acknowledgments
<p>The Website was developed by Gary Kozlowski.</p>
