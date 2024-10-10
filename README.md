# JobVerse
This project is a web application built using Laravel and Tailwind CSS. 

Follow the steps below to set up and run the application on your local machine.

## Prerequisites
Before you begin, ensure you have the following installed on your system:

- PHP >= 8.0
- Composer
- Node.js & npm
- Docker & Docker Compose

## Installation
Clone the repository:
```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

Install PHP dependencies:
```bash
composer install
```

Install Node.js dependencies:
```bash
npm install
```

Set up environment variables: Copy the .env.example file to .env and update the necessary environment variables.
```bash
cp .env.example .env
```

Generate application key:
```
php artisan key:generate
```

Run database migrations:
```
php artisan migrate
```

## Docker Setup
Create a docker-compose.yml file: Add the following content to set up MySQL and Adminer services:
```
version: "3.9"
services:
  mysql:
    image: mariadb:10.8.3
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: # some password
    ports:
      - 3306:3306
  adminer:
    image: adminer
    restart: always
    ports:
      - 8080:8080
```
Start Docker services:
```
docker-compose up -d
```
## Setting Up Tailwind CSS
Install Tailwind CSS and its dependencies:
```
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```
Configure Tailwind CSS: Update the tailwind.config.js file to include the paths to your template files:
```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./resources/**/*.blade.php",
    "./resources/**/*.js",
    "./resources/**/*.vue",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```
Add Tailwind directives to your CSS: In your ./resources/css/app.css file, add the following lines:
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```
Build your CSS: Run the following command to compile your CSS:
```
npm run dev
```
## Vite Configuration
Install Vite and Laravel Vite Plugin:
```
npm install --save-dev vite laravel-vite-plugin
```
Create Vite configuration file: Create a vite.config.js file in the root of your project and add the following configuration:
```
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';

export default defineConfig({
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
});
```
## Running the Application
Start the development server:
```
php artisan serve
```
Access the application: Open your browser and navigate to http://localhost:8000.


## Usage
You can now start building your application using Laravel and Tailwind CSS. Use Tailwind’s utility classes to style your components and pages.

## Contributing
If you wish to contribute to this project, please fork the repository and create a pull request with your changes.

License
This project is licensed under the MIT License.

This rearrangement places the Docker setup before the Tailwind CSS setup, which might be more logical since Docker is part of the initial environment setup. Let me know if you have any other preferences or changes in mind!
