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

