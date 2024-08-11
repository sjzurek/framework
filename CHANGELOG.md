# Changelog

## [1.0.1] - 2024-08-11

- **Description**: This release includes significant improvements in code modularization and organization.

- **Changelog**:
  - **Middleware Management**:
    - Removed integrated middlewares from the core framework.
    - Middlewares are now part of the `lithe_modules` directory, allowing greater flexibility and customization in middleware integration and usage.
  - **Autoloading**:
    - Adjusted autoloading to ensure specific files from the `Utilities` folder are loaded correctly.
  - **Code Cleanup**:
    - Removed automatic import of the `Utilities` directory to improve organization and file loading.

## [1.0.0] - Initial Release

- **Description**: Lithe is a PHP framework inspired by Express.js, renowned for its lightweight and flexible nature. It offers a minimalist approach to web development, integrating various components, ORMs, and databases while maintaining agile and efficient performance.

- **Key Features**:
  - **Routing**: Simple and expressive route management with methods like `get()`, `post()`, among others.
  - **Middleware**: Robust support for middleware to handle requests, responses, and add functionalities such as authentication and logging.
  - **Templates**: Support for multiple template engines, including PHP Pure, Blade, and Twig, with easy configuration.
  - **CSRF Protection**: Middleware for CSRF protection, including token generation and validation.
  - **Session Management**: Flexible session management with support for variables and customizable configurations.
  - **Database Integration**: Integrated support for various ORMs and database drivers, including Eloquent, MySQLi, and PDO. Simple configuration through `.env` file and support for automated migrations.
  - **Migration Flexibility**: Ability to perform migrations with any database approach, including custom SQL queries or ORM-based migrations.
  - **Component Support**: Integration with various PHP components and libraries for enhanced functionality.
  - **Package Manager**: Lithe includes an integrated package manager to simplify the addition and management of modules and packages within your application.

- **Achievements**:
  - **Agile Development**: Implementation of a lightweight framework that promotes rapid and intuitive development.
  - **Flexibility**: Seamless integration of various components and libraries, offering high flexibility for developers.
  - **Documentation**: Provision of clear and comprehensive documentation to facilitate effective use of the framework.
  - **Testing**: Support for testing with PHPUnit and Mockery to ensure code quality and reliability.
  - **Ease of Use**: User-friendly interfaces and abstractions designed to simplify the creation and maintenance of web applications.
  - **Module Management**: Effective management of modules with commands to create, list, and update modules using Lithe’s package manager.
  - **Database Integration**: Ease of configuration and management of connections to different databases, making integration with data management systems more efficient and flexible.
  - **Migration Capabilities**: Support for a variety of migration approaches, allowing developers to manage schema changes flexibly with either ORM tools or custom SQL scripts.