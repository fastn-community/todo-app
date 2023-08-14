# Fastn Todo-App

This is a full-stack todo-app project built using the Fastn language and utilizing Supabase for the PostgreSQL database. The app allows users to create, update, and delete tasks.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Installation](#installation)
3. [Project Structure](#project-structure)
4. [Configuration](#configuration)
5. [Usage](#usage)
6. [Deployment to Heroku (Web)](#deployment-to-heroku-web)
7. [Deployment to Heroku (CLI)](#deployment-to-heroku-cli)

## Prerequisites

Before you begin, ensure you have the following software and tools installed:

- `fastn`
- `heroku` CLI (for deployment) (optional)

## Installation

Clone the repository to your local machine:

```bash
git clone https://github.com/fastn-community/todo-app.git
cd todo-app
```

## Project structure

```bash
.
├── FASTN.ftd
├── images
│   ├── checkbox-dark.svg
│   ├── github.svg
│   ├── delete-bin-dark.svg
│   ├── github-dark.svg
│   ├── delete-bin.svg
│   ├── checkbox-fill-dark.svg
│   ├── checkbox.svg
│   └── checkbox-fill.svg
├── index.ftd
├── components
│   ├── todo.ftd           # UI components for todo functionality
│   ├── switch.ftd         # UI components for switches
│   └── layout.ftd         # Layout components
├── repository.ftd         # `fscript` functions for making API requests
├── theme
│   └── colors.ftd         # Color scheme for the project
├── utils.ftd              # Utility functions
├── api
│   ├── models.ftd         # Model definition for todo (fastn record)
│   ├── update-todo.ftd    # CRUD API for updating todos
│   ├── delete-todo.ftd    # CRUD API for deleting todos
│   └── add-todo.ftd       # CRUD API for adding todos
└── Procfile               # Heroku configuration for serving the project
```

## Configuration

Follow these steps to set up your Supabase PostgreSQL database and obtain the database URL for your Fastn Todo-App:

1. **Sign Up/Login on Supabase**:

- Visit the Supabase website at [https://supabase.io](https://supabase.io).
- Sign up for a new account or log in to your existing account.

2. **Create a New Project**:

- Once you're logged in, click on the "New Project" button.
- Give your project a name, and you can choose an existing organization or create a new one.
- Click the "Create Project" button to proceed.

3. **Access Visual Table Creator**:

- In your project dashboard, navigate to the "Database" section by clicking on "Database" (icon) in the left sidebar.
- Click on the "Tables" tab, and you'll be directed to the "Tables" page.

4. **Create a New Table**:

- Click the "New Table" button to open the Visual Table Creator.
- Design your "todos" table:
    - Add a "todo" column with the data type "VARCHAR".
    - Add a "complete" column with the data type "Boolean".
- Click the "Create Table" button to create the "todos" table.

5. **Access Database Settings**:

- On the "Tables" page, locate the "Settings" icon (represented by three vertical dots) for your newly created "todos" table.
- Click on the "Settings" icon and select "Edit table".
- Under the "Connection Pooling Custom Configuration" section, you'll find the connection string under the "Connection strings" section. It will look something like this:
    
    ```plaintext
    postgres://username:password@hostname:port/database
    ```

6. **Replace the Database Password**:

- Replace `[YOUR-PASSWORD]` in the connection string with the password you entered during the creation of the project. If you've forgotten the password, you can reset it:
    - Under the "Database password" section on the same page, click on the "Reset database password" button.
    - Follow the instructions to reset the password.

7. Set the Path variable for database url: 

```bash
export FASTN_PG_URL=postgres://username:password@hostname:port/database
```

## Usage

1. Run the app locally:

   ```bash
   fastn serve --edition=2023
   ```

   Your app should be live at `http://localhost:8000`.

2. Access the app in your web browser and start managing your todos.

---

## Deployment to Heroku (Web)

Follow these steps to deploy your `fastn` Todo-App to Heroku using the Heroku web interface:

1. **Create a Heroku App**:

   - Log in to your Heroku account at [https://dashboard.heroku.com](https://dashboard.heroku.com).
   - Click on the "New" button and select "Create new app."
   - Provide a unique name for your app, and choose the region.
   - Click the "Create App" button to create your Heroku app.

2. **Configure Environment Variables**:

   - In your Heroku app dashboard, navigate to the "Settings" tab.
   - Under the "Config Vars" section, click the "Reveal Config Vars" button.
   - Add a new variable named `FASTN_PG_URL` and set its value to your Supabase PostgreSQL database URL.

3. **Add the `fastn` Buildpack**:

   - In the "Settings" tab of your Heroku app dashboard, scroll down to the "Buildpacks" section.
   - Click the "Add buildpack" button.
   - In the "Add buildpack" dialog, enter the following URL for the `fastn` buildpack: `https://github.com/fastn-stack/heroku-buildpack.git`
   - Click the "Save Changes" button.

4. **Deploy Your App**:

   - In the "Deploy" tab of your Heroku app dashboard, you can connect your GitHub repository by linking it to your Heroku app.
   - Choose the branch you want to deploy, typically the `main` branch.
   - Enable automatic deployments or manually trigger deployments as needed.
   - Click the "Deploy Branch" button to deploy your app.

5. **Access Your Live App**:

   - Once the deployment is successful, your app will be live on Heroku.
   - Access your app by navigating to `https://your-app-name.herokuapp.com` in your web browser.

Your `fastn` Todo-App is now deployed and accessible on the Heroku platform.

---

## Deployment to Heroku (CLI)

1. Create a Heroku app using the Heroku CLI:

   ```bash
   heroku create your-app-name
   ```

2. Set environment variables:

   ```bash
   heroku config:set FASTN_PG_URL=your-database-url
   ```

3. Add the `fastn` buildpack:

   ```bash
   heroku config:set BUILDPACK_URL=https://github.com/fastn-stack/heroku-buildpack.git
   ```

4. Deploy your app:

   ```bash
   git push heroku master
   ```

Your app should be live at `https://your-app-name.herokuapp.com`.

---

Feel free to tailor this README to fit your specific project details, add additional sections, or make any other modifications you see fit. Once you're satisfied with the content, you can include it in your GitHub repository's `README.md` file to provide clear instructions for setting up, using, and deploying your `fastn` todo-app project.
