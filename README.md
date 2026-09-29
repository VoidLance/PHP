# PHP Learning Workspace

[![Social Media Analytics CI](https://github.com/VoidLance/PHP/actions/workflows/ci.yml/badge.svg)](https://github.com/VoidLance/PHP/actions/workflows/ci.yml)

A collection of PHP learning projects, web applications, and small standalone exercises. The
workspace ranges from beginner scripts to MVC-style applications with databases, authentication,
REST endpoints, and a React dashboard.

## Why this repository is useful

- **Learn incrementally:** Start with short PHP scripts, then move to database-backed applications.
- **Explore complete examples:** Study authentication, CRUD, sessions, CSRF protection, file
  handling, APIs, and responsive front ends in working projects.
- **Run projects independently:** Each larger application keeps its own setup notes and schema.
- **Practice full-stack development:** The Social Media Analytics Dashboard combines a PHP API,
  React/Vite frontend, Docker services, and automated checks.

## Projects

| Project | Description | Start here |
| --- | --- | --- |
| [Social Media Analytics Dashboard](SocialMediaAnalyticsDashboard/README.md) | Multi-tenant analytics platform with PHP backend, React frontend, Docker infrastructure, and API documentation. | [Quick start](SocialMediaAnalyticsDashboard/README.md#quick-start-docker) |
| [SecureFileShare](SecureFileShare/README.md) | Vanilla PHP file-sharing app with encrypted storage, expiring share links, quotas, and a small API. | [Setup](SecureFileShare/README.md#setup) |
| [E-Commerce System](e-commerce_system/README.md) | MySQL-backed catalog, cart, checkout, orders, administration, coupons, reviews, and PayPal sandbox integration. | [Setup](e-commerce_system/README.md#setup) |
| [Task Management System](TaskManagementSystem/README.md) | MVC and REST task manager with projects, roles, JWT authentication, comments, search, and a Vue interface. | [Setup](TaskManagementSystem/README.md#setup) |
| [BlogSystem](BlogSystem/README.md) | PHP/MySQL blog with posts, categories, comments, search, profiles, and administration. | [Getting started](BlogSystem/README.md#getting-started) |
| `core-exercises/` | Small exercises covering arithmetic, arrays, configuration, grades, and student data. | Open the PHP files directly |
| `data-apps/` | Inventory, library, bookstore, and shopping-cart examples using PHP data structures and JSON. | Open the PHP files directly |
| `http-playground/` | Examples for query handling, profiles, superglobals, and a small server dashboard. | Open the PHP files directly |
| `regex-tools/` | Email validation and regular-expression matching examples. | Open the PHP files directly |
| `log_analyser/` | A JSON log analysis exercise. | Open `log_analyser/log_analyser.php` |
| `Basic App/`, `Calculator/`, `PasswordChecker/` | Small introductory scripts demonstrating PHP syntax and functions. | Open the PHP files directly |

The root `index.php` is a browser-based directory launcher for the workspace. It also links to
the main applications and displays the repository file tree.

## Requirements

Install only the requirements for the project you want to run:

- PHP 8.1 or newer for SecureFileShare; PHP 8.2 or newer for the analytics backend.
- PHP extensions required by the selected application, commonly `pdo`, `pdo_mysql`, `mysqli`,
  `json`, and `openssl`.
- MySQL/MariaDB for BlogSystem, E-Commerce System, and Task Management System.
- Node.js and npm for the analytics frontend.
- Docker Compose for the complete analytics stack.

Check each project README before installing additional services. The repository does not use a
single root dependency file.

## Get started

### Browse the workspace

From the repository root, start the PHP development server:

```bash
php -S localhost:8000 router.php
```

Open <http://localhost:8000/> to use the launcher. The router keeps application public
directories as entry points and blocks direct access to SecureFileShare's private source paths.

### Run a standalone exercise

For a command-line script:

```bash
php core-exercises/arithmetic_operations.php
```

For a browser-based exercise, serve the repository and open its path, for example:

```text
http://localhost:8000/Calculator/
```

### Run a full application

Use the application-specific README for database initialization, credentials, and routes:

1. [Social Media Analytics Dashboard](SocialMediaAnalyticsDashboard/README.md)
2. [SecureFileShare](SecureFileShare/README.md)
3. [E-Commerce System](e-commerce_system/README.md)
4. [Task Management System](TaskManagementSystem/README.md)
5. [BlogSystem](BlogSystem/README.md)

Do not expose a project's private source directories as a web root. Use the `public/` entry point
where the project provides one.

## Validation

The analytics project documents its backend syntax check, integration script, and frontend build
in [its validation section](SocialMediaAnalyticsDashboard/README.md#local-validation-commands).
The same PHP syntax check can be useful while working on other applications:

```bash
find path/to/project -name "*.php" -print0 | xargs -0 -n1 php -l
```

For the analytics frontend:

```bash
cd SocialMediaAnalyticsDashboard/frontend
npm ci
npm run build
```

The repository's CI workflow is located at
`.github/workflows/ci.yml` within the Social Media Analytics Dashboard project.

## Documentation and support

- Read the README in the directory for the application you are using.
- Review the analytics [architecture](SocialMediaAnalyticsDashboard/docs/architecture.md),
  [API contract](SocialMediaAnalyticsDashboard/docs/api-v1.yaml), and
  [testing strategy](SocialMediaAnalyticsDashboard/docs/testing-strategy.md).
- Open a GitHub issue for reproducible bugs or improvement proposals.
- For PHP language reference, see the [PHP manual](https://www.php.net/manual/en/).
- For security guidance, see [OWASP](https://owasp.org/).

## Contributing

Contributions are welcome, especially improvements that make the examples clearer or safer.

1. Create a focused branch from the default branch.
2. Make changes within the relevant project and update that project's documentation when setup
   changes.
3. Run the applicable syntax checks, integration scripts, and frontend builds.
4. Open a pull request describing what changed and how it was verified.

Keep credentials, generated databases, uploaded files, and environment-specific configuration out
of commits. Replace example secrets before running any application outside a local development
environment.

## Maintainer

This workspace is maintained by [VoidLance](https://github.com/VoidLance). Please use GitHub
issues and pull requests for project support and contributions.

## License

No root license file is currently provided. Review the licensing terms of the specific project
before redistributing or deploying it.
