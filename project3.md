### STEP ONE – BACKEND CONFIGURATION
> *Make sure you have a functioning AWS account (Free tier or Paid account)*

> For this demostration, I am using a free tier account which is connected remotely to my windows computer.

1. Let's install the packages needed for the backend.

```bash
sudo apt update
```
![alt text](./images/1.png)
```bash
sudo apt upgrade
```
![alt text](./images/2.png)
Lets get the location of Node.js software from Ubuntu repositories.

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```
![alt text](./images/3.png)

Install Node.js on the server and npm(node package manager).
```bash
sudo apt-get install -y nodejs
```
![alt text](./images/4.png)

Verify node and node package manager are installed.
package manager).
```bash
node -v
```
```bash
npm -v
```
![alt text](./images/5.png)

Let's create the directory/domain to store our todo application files.
```bash
npm -v
```
![alt text](./images/6.png)

Change directory to the project directory ***todo***.
```bash
cd todo
```
![alt text](./images/7.png)

Initialise the project, that creates the package.json file that holds the mta data to manage the application and it's dependancies.
```bash
npm init
```
![alt text](./images/8.png)

Notice the newly created ***package.json file***
```bash
ls
```
![alt text](./images/9.png)

Next, Install ExpressJs and create the Routes directory.

Install ExpressJS
```bash
npm install express
```
![alt text](./images/10.png)

Create the index page for the todo application
```bash
touch index.js
```
![alt text](./images/11.png)
Install the dotenv module - environment variables
```bash
npm install dotenv
```
![alt text](./images/12.png)

Open the index.js file and type this codes
```bash
nano index.js
```
![alt text](./images/13.png)
![alt text](./images/14.png)

Start the server
```bash
node index.js
```
![alt text](./images/15.png)

Remember port 5000 was specified in the index.js file create. we would need to open this port under the security group fiie AWS EC2 instance.

![alt text](./images/16.png)

Verify in the broswer - use your public ip or public dns.
```bash
http://44.203.110.111:5000/
```
![alt text](./images/17.png)
![alt text](./images/18.png)

Create ROUTES.
The ***Todo application*** is created to perform (3) actions namely, create, display and delete. These actions would be associated with endpoints using HTTP standards - POST, GET and DELETE.

Create Routes directory and change to it's directory
```bash
mkdir routes
```
![alt text](./images/19.png)

Create API file, open and type the codes as shown in the image below.
```bash
touch api.js
```
```bash
nano api.js
```
![alt text](./images/20.png)
![alt text](./images/21.png)

MODELS
Create models neccessary for the database schema.
```bash
npm install mongoose
```
![alt text](./images/22.png)

Create a directory for models, change to the directory and create a new file called *todo.js*
```bash
mkdir models
```
```bash
cd models
```
```bash
touch todo.js
```
![alt text](./images/23.png)
Create schema - write the following codes in the image below. save and exit
```bash
nano todo.js
```
![alt text](./images/24.png)

Update **routes** in the ***api.js*** file.
```bash
nano api.js
```
![alt text](./images/25.png)
![alt text](./images/26.png)

MONGODB - Let's setup the database.
Sign up for a free ***mlab account***.

Create user name password, allow ip (0.0.0.0) from anywhere for this test purpose. 
![alt text](./images/35.png)
Copy the connection string
![alt text](./images/34.png)

Create a .env file to add the connection to the database in the todo directory.
```bash
touch .env
```
```bash
nano .env
```
```bash
DB = 'mongodb+srv://todo_user:PassWord.1@cluster0.9braz2z.mongodb.net/?retryWrites=true&w=majority'
```
*save and exit*
![alt text](./images/31.png)
![alt text](./images/30.png)

Let's Update the index.js file use .env to enable database connection.
![alt text](./images/37.png)

Check Node Connection
```bash
node index.js
```
![alt text](./images/41.png)

It is successful - Backend Done!!

Let's test the api endpoint using postman.
Download postman [Here](https://www.postman.com/)

Test GET request
![alt text](./images/52.png)

Test POST request
![alt text](./images/51.png)

Test DELETE request by adding the id to the URL
![alt text](./images/54.png)

### STEP 2 -  FRONTEND

In the todo directory, run the code below which would create a folder *client* and some dependencies where the frontend react code would be stored.

```bash
npx create-react-app client
```
![alt text](./images/55.png)

Install more dependenies concurrently
```bash
npm install concurrently --save-dev
```
![alt text](./images/56.png)

Install nodemon to monitor the server and automatic restart when needed.
```bash
npm install nodemon --save-dev
```
![alt text](./images/57.png)

Now, Open edit the packahe.json file in the todo directory.

![alt text](./images/58.png)

Configure Proxy in package.json in the client folder.
```bash
cd client && nano package.json
```
![alt text](./images/60.png)

![alt text](./images/59.png)

In the todo directory run 
```bash
npm run dev
```


In the client directory go the src directory, create a directory, create some files.
```bash
mkdir components
```
```bash
cd components
```
```bash
touch Input.js ListTodo.js Todo.js
```
![alt text](./images/61.png)

In the Input.js file, add these codes.
![alt text](./images/62.png)

In the client, Axios packages needs to be installed.
```bash
npm install axios
```
![alt text](./images/63.png)

### Finally Steps 

Open the ListTodo.js In the components directory.
```bash
nano ../client/src/components/ListTodo.js
```
![alt text](./images/64.png)

Open the Todo.js in the components directory.
```bash
nano ../client/src/components/ListTodo.js
```
![alt text](./images/65.png)

In the src directory, open the App.js file and type the following codes.
![alt text](./images/66.png)
In the same directory, open the App.css file and type the following codes.
![alt text](./images/67.png)
In the same directory, open the index.css file and type the following codes.
![alt text](./images/68.png)
Now go to the todo directory and run
```bash
npm run dev
```
![alt text](./images/69.png)
View from the browser using your public ip or public dns at port 3000.
![alt text](./images/699.png)