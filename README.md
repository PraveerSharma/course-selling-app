# Course Selling App
The Course Selling App is a web application that allows users to buy and manage courses. It provides functionalities for both administrators and users to create, edit, and purchase courses.

# Features
Authentication and authorization for administrators and users.
Course management for administrators (create, edit, list).
Course purchasing for users.
List purchased courses for users.

# Technologies Used
Node.js
Express.js
JSON Web Tokens (JWT)
File system for data storage
RESTful API design principles

# Setup Instructions
1. Clone the repository:
 git clone https://github.com/your-username/course-selling-app.git
 cd course-selling-app
2. Install dependencies:
 npm install
3. Run the server:
 node index.js
4. API Endpoints
 ## Routes
 ### Admin Routes:
 - POST /admin/signup
   Description: Creates a new admin account.
   Input: { username: 'admin', password: 'pass' }
   Output: { message: 'Admin created successfully', token: 'jwt_token_here' }
 - POST /admin/login
   Description: Authenticates an admin. It requires the admin to send username and password in the headers.
   Input: Headers: { 'username': 'admin', 'password': 'pass' }
   Output: { message: 'Logged in successfully', token: 'jwt_token_here' }
 - POST /admin/courses
   Description: Creates a new course.
   Input: Headers: { 'Authorization': 'Bearer jwt_token_here' }, Body: { title: 'course title', description: 'course description', price: 100, imageLink: 'https://linktoimage.com', published: true }
   Output: { message: 'Course created successfully', courseId: 1 }
 - PUT /admin/courses/:courseId
   Description: Edits an existing course. courseId in the URL path should be replaced with the ID of the course to be edited.
   Input: Headers: { 'Authorization': 'Bearer jwt_token_here' }, Body: { title: 'updated course title', description: 'updated course description', price: 100, imageLink: 'https://updatedlinktoimage.com', published: false }
   Output: { message: 'Course updated successfully' }
 - GET /admin/courses
   Description: Returns all the courses.
   Input: Headers: { 'Authorization': 'Bearer jwt_token_here' }
   Output: { courses: [ { id: 1, title: 'course title', description: 'course description', price: 100, imageLink: 'https://linktoimage.com', published: true }, ... ] }
   User Routes:

### User routes
 - POST /users/signup
   Description: Creates a new user account.
   Input: { username: 'user', password: 'pass' }
   Output: { message: 'User created successfully', token: 'jwt_token_here' }
 - POST /users/login
   Description: Authenticates a user. It requires the user to send username and password in the headers.
   Input: Headers: { 'username': 'user', 'password': 'pass' }
   Output: { message: 'Logged in successfully', token: 'jwt_token_here' }
 - GET /users/courses
   Description: Lists all the courses.
   Input: Headers: { 'Authorization': 'Bearer jwt_token_here' }
   Output: { courses: [ { id: 1, title: 'course title', description: 'course description', price: 100, imageLink: 'https://linktoimage.com', published: true }, ... ] }
 - POST /users/courses/:courseId
   Description: Purchases a course. courseId in the URL path should be replaced with the ID of the course to be purchased.
   Input: Headers: { 'Authorization': 'Bearer jwt_token_here' }
   Output: { message: 'Course purchased successfully' }
 - GET /users/purchasedCourses
   Description: Lists all the courses purchased by the user.
   Input: Headers: { 'Authorization': 'Bearer jwt_token_here' }
   Output: { purchasedCourses: [ { id: 1, title: 'course title', description: 'course description', price: 100, imageLink: 'https://linktoimage.com', published: true }, ... ] }
