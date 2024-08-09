# Lithe

Lithe is a PHP framework inspired by Express.js, known for its lightweight and flexible nature. It offers simplicity, flexibility, and expressiveness for developers, enabling the creation of everything from small applications to complex web platforms efficiently and effectively.

## Installation

To start using Lithe in your project, you can install it via Composer. Run the following command at the root of your project:

```bash
composer require lithecore/framework
```

## Configuration

After installation, you can begin using Lithe in your project. Here is a basic example of configuration and usage:

1. **Create an `index.php` file** at the root of your project:

    ```php
    <?php

    // Define PROJECT_ROOT
    define('PROJECT_ROOT', __DIR__);

    require 'vendor/autoload.php';

    \Lithe\Support\Env::load();

    // Create a new instance of the Lithe app
    $app = new Lithe\App();

    // Define a sample route
    $app->get('/users/:name', function ($req, $res) {
        $name = $req->params->name;

        $res->json(['message' => "Hello, $name!"]);
    });

    // Start the app
    $app->listen();
    ```

2. **Configure the `.htaccess` file**:

    Add the following content to your `.htaccess` file at the root of your project to ensure that all requests are handled by `index.php`:

    ```apache
    # Disable MultiViews
    Options -MultiViews

    # Enable URL rewriting
    RewriteEngine On

    # Disable directory listing
    Options -Indexes

    # Custom error document for 403 errors
    ErrorDocument 403 /403

    # Rewrite rules
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-l
    RewriteRule ^(.+)$ index.php?url=$1 [QSA,L]
    ```

3. **Create a `line` file** at the root of your project:

    This file is used to register and start the Lithe command-line application. The content of the file should be:

    ```php
    <?php
    // Register the Composer autoloader...
    require __DIR__ . '/vendor/autoload.php';

    define('PROJECT_ROOT', __DIR__);

    \Lithe\Support\Env::load();

    // Load the database configuration required for database operations in the console commands.
    define('DB_CONNECTION', include __DIR__ . '/src/database/config/database.php');

    // Start the console application by listening to the command-line arguments passed to the script.
    \Lithe\Console\Line::listen($argv);
    ```

4. **Create the `src/database/config/database.php` file** with the following content:

    ```php
    <?php

    /**
     * Initialize and return the configured database connection.
     *
     * This script initializes the database connection by invoking the `initialize`
     * method from the `\Lithe\Database\Manager` class. The method sets up the connection
     * based on the environment configuration and returns the configured database connection.
     *
     * @return mixed The configured database connection.
     * @throws \RuntimeException If there is an error setting up the connection.
     * @throws \Exception If the specified database configuration is not found.
     */

    use Lithe\Database\Manager as DB;

    // DATABASE
    return DB::initialize();
    ```

5. **Create and configure the `.env` file** at the root of your project:

    The `.env` file is used to configure environment variables required for your project. Create a `.env` file with the following content:

    ```
    APP_NAME=Lithe
    APP_KEY=
    APP_PRODUCTION_MODE=false

    DB_CONNECTION_METHOD=pdo
    DB_CONNECTION=mysql
    DB_HOST=localhost
    DB_NAME=lithe
    DB_USERNAME=root
    DB_PASSWORD=
    DB_SHOULD_INITIATE=false

    MAIL_HOST=
    MAIL_PORT=
    MAIL_USERNAME=
    MAIL_PASSWORD=
    MAIL_ENCRYPTION=
    MAIL_FROM_ADDRESS=
    MAIL_FROM_NAME="${APP_NAME}"
    ```

    Adjust the environment variables according to your project's needs.

## What is Lithe?

Lithe is a PHP framework known for its simplicity, flexibility, and efficiency. Inspired by Express.js, Lithe is designed to help developers build web applications quickly and effectively. The name "Lithe" reflects the core characteristics of the framework: flexible and agile.

## Simple and Flexible Routing

In Lithe, defining routes is very simple. You can use methods like `get()`, `post()`, and others to create routes that respond to different types of HTTP requests:

```php
$app->get('/hello/:name', function ($req, $res) {
    $res->send('Hello, ' . $req->params->name);
});
```

Discover how [routing in Lithe](https://lithecore.vercel.app/docs/the-basics/routing) can simplify your development and offer complete control over your application's routes.

## Powerful Middleware

In Lithe, middleware is your line of defense, allowing you to inspect, filter, and manipulate HTTP requests before they reach the final routes. Imagine adding functionalities like authentication and logging in a modular and reusable way!

Here’s how easy it is to define and use middleware:

```php
// Middleware to check if the token is valid
$EnsureTokenIsValid = function ($req, $res, $next) {
    $token = $req->params->token;

    if ($token !== 'my-secret-token') {
        $res->send('Invalid token.');
    }

    $next();
};

// Protected route using the middleware
$app->get('/protected/:token', $EnsureTokenIsValid, function ($req, $res) {
    $res->send('Protected content accessed successfully!');
});
```

Learn more about [middlewares in Lithe](https://lithecore.vercel.app/docs/the-basics/middleware) and see how they can transform the way you develop and maintain your applications.

## View Engine Choice

Lithe offers flexibility by allowing you to choose from various template engines, such as pure PHP, Blade, and Twig. In addition to the standard engines, you can configure others to optimize the creation and rendering of dynamic interfaces.

```php
$app->set('view engine', 'blade');
```

Explore the possibilities of [view engines](https://lithecore.vercel.app/docs/the-basics/template-engines) and learn how to integrate them into your project efficiently.

## Database Integration

Connecting to databases is straightforward with Lithe. The framework supports popular ORMs like Eloquent and native PHP drivers such as MySQLi and PDO. Configure your connections in the `.env` file and manage schema migrations easily.

```
DB_CONNECTION_METHOD=eloquent
DB_CONNECTION=mysql
DB_HOST=localhost
DB_NAME=lithe
DB_USERNAME=root
DB_PASSWORD=
DB_SHOULD_INITIATE=true
```

Learn more about [database integration in Lithe](https://lithecore.vercel.app/docs/database/integration) and see how easy it is to manage your data.

## Database Migrations

Maintain consistency and integrity of data in your applications with automated migrations. With Lithe, you can create and apply migrations quickly and easily using any ORM interface or database driver.

```bash
php line make:migration CreateUsersTable --template=eloquent
php line migrate
```

Learn more about [migrations in Lithe](https://lithecore.vercel.app/docs/database/migrations) and make the most of this feature to build robust and scalable applications.

## Contributing

Contributions are welcome! If you find an issue or have a suggestion, feel free to open an [issue](https://github.com/lithecore/framework/issues) or submit a [pull request](https://github.com/lithecore/framework/pulls).

## License

Lithe is licensed under the [MIT License](https://opensource.org/licenses/MIT). See the [LICENSE](LICENSE) file for more details.

## Contact

If you have any questions or need support, get in touch:

- **Instagram**: [@lithe.php](https://instagram.com/lithe.php)