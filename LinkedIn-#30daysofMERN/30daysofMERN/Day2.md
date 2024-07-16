### Day 2: Setting Up Your React Environment

Welcome back to Day 2 of our #30daysofMERNstack series! Today, we’re going to set up your React development environment. By the end of this article, you’ll have Node.js and npm/yarn installed, and you’ll have created a new React project using Create React App.

#### Step 1: Install Node.js and npm

Node.js is a JavaScript runtime that allows you to run JavaScript on the server side. npm (Node Package Manager) is a package manager for Node.js that allows you to install and manage dependencies for your projects.

1. **Download and Install Node.js**:
   - Go to the [official Node.js website](https://nodejs.org/).
   - Download the LTS (Long Term Support) version of Node.js for your operating system.
   - Run the installer and follow the instructions to complete the installation.

2. **Verify the Installation**:
   - Open your terminal (or Command Prompt on Windows).
   - Run the following commands to check the versions of Node.js and npm:
     ```bash
     node -v
     npm -v
     ```

   You should see the installed versions of Node.js and npm displayed in the terminal.

#### Step 2: Install Yarn (Optional)

Yarn is an alternative package manager to npm. It offers some benefits like faster installation and better dependency management. If you prefer to use Yarn, you can install it globally on your system.

1. **Install Yarn**:
   - Run the following command in your terminal:
     ```bash
     npm install -g yarn
     ```

2. **Verify the Installation**:
   - Run the following command to check the version of Yarn:
     ```bash
     yarn -v
     ```

   You should see the installed version of Yarn displayed in the terminal.

#### Step 3: Create a New React Project Using Create React App

Create React App is a command-line tool that sets up a new React project with a sensible default configuration. It includes all the necessary dependencies and boilerplate code to get you started quickly.

1. **Create a New Project**:
   - Open your terminal and run the following command:
     ```bash
     npx create-react-app my-app
     ```

   Replace `my-app` with your preferred project name. This command will download and set up a new React project in a directory named `my-app`.

2. **Navigate into Your Project Directory**:
   - Change into your project directory using the `cd` command:
     ```bash
     cd my-app
     ```

3. **Start the Development Server**:
   - Once inside your project directory, start the development server by running:
     ```bash
     npm start
     ```

   If you are using Yarn, you can start the server with:
     ```bash
     yarn start
     ```

   This command will launch a development server and open your new React application in a web browser. You should see the default React starter template rendered on the screen.

#### Exploring Your Project Structure

Take a moment to explore the project structure created by Create React App. Here are a few key directories and files:

- **`public/`**: Contains static assets like the HTML file and favicon.
- **`src/`**: Contains the source code of your React application. This is where you will be spending most of your time.
  - **`App.js`**: The main component of your application.
  - **`index.js`**: The entry point of your application. This file renders the `App` component into the DOM.
- **`package.json`**: Lists project dependencies and scripts. You can add, update, or remove dependencies here.


#### Conclusion

Today, we set up your React development environment by installing Node.js and npm/yarn, and creating a new React project using Create React App. You’ve also learned how to start the development server and make your first changes to a React component.

In the next lesson, we'll dive deeper into creating and using React Components and Props. Stay tuned and happy coding!
