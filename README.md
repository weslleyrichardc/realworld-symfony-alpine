# ![RealWorld Example App](logo.png)

> ### Codebase with the **Symfony + Alpine.js** implementation of the [RealWorld](https://github.com/gothinkster/realworld) spec and API.

This codebase was created to demonstrate a fully fledged fullstack application built with **Symfony + Alpine.js** including CRUD operations, authentication, routing, pagination, and more.

This implementation showcases a **progressive enhancement** approach: server-side rendering with Symfony and Twig provides a solid, accessible foundation, while Alpine.js adds modern interactivity without the complexity of a full frontend framework.

For more information on how to this works with other frontends/backends, head over to the [RealWorld](https://github.com/gothinkster/realworld) repo.

# Technology Stack

### Backend
- **Symfony 8** - Modern PHP framework with robust architecture
- **Doctrine ORM** - Database abstraction layer and object mapping
- **PostgreSQL** - Powerful relational database
- **Pest** - Comprehensive testing framework

### Frontend
- **Twig** - Server-side templating engine with inheritance and components
- **Alpine.js** - Lightweight reactive framework for UI interactions

### Development Tools
- **Docker** - Containerized development environment
- **PHP-CS-Fixer** - Automatic code formatting
- **Composer** - PHP dependency management
- **npm** - Node.js dependency management

# Getting started

## Prerequisites

- **PHP 8.1+** with required extensions (pdo_pgsql, tokenizer, curl, xml, mbstring)
- **Node.js 18+** and npm/yarn
- **PostgreSQL 13+** 
- **Composer** for PHP dependencies
- **Docker** (optional, for development environment)

## Installation

### 1. Clone and Install Dependencies

```bash
# Clone the repository
git clone https://github.com/weslleyrichardc/realworld-symfony-alpine.git
cd realworld-symfony-alpine

# Install PHP dependencies
composer install

# Install Node.js dependencies
npm install
```

### 2. Environment Configuration

```bash
# Copy environment template
cp .env.example .env

# Configure your database connection and other variables
# Edit .env file with your settings
```

### 3. Database Setup

```bash
# Create the database
php bin/console doctrine:database:create

# Run database migrations
php bin/console doctrine:migrations:migrate

# Load demo data (optional)
php bin/console doctrine:fixtures:load
```

### 4. Asset Compilation

```bash
# Compile frontend assets
npm run build

# For development with hot reloading
npm run dev
```

### 5. Start Development Server

```bash
# Start Symfony development server
php bin/console server:start

# Or use Docker Compose (if configured)
docker-compose up -d
```

Your application should now be available at `http://localhost:8000`

## Development Commands

```bash
# Run tests
php bin/pest

# Fix code style
php vendor/bin/php-cs-fixer fix
```

## RealWorld API Compliance

This implementation fully complies with the [RealWorld API specification](https://github.com/gothinkster/realworld/tree/main/api), implementing all required endpoints:

### Authentication & User Management
- `POST /api/users/login` - User login with JWT token response
- `POST /api/users` - User registration
- `GET /api/user` - Get current user profile
- `PUT /api/user` - Update current user profile

### Profiles
- `GET /api/profiles/{username}` - Get user profile
- `POST /api/profiles/{username}/follow` - Follow a user
- `DELETE /api/profiles/{username}/follow` - Unfollow a user

### Articles
- `GET /api/articles` - Get articles (with filters: tag, author, favorited)
- `GET /api/articles/feed` - Get articles from followed users
- `POST /api/articles` - Create new article
- `GET /api/articles/{slug}` - Get single article
- `PUT /api/articles/{slug}` - Update article
- `DELETE /api/articles/{slug}` - Delete article

### Comments
- `GET /api/articles/{slug}/comments` - Get article comments
- `POST /api/articles/{slug}/comments` - Create comment
- `DELETE /api/articles/{slug}/comments/{id}` - Delete comment

### Favorites
- `POST /api/articles/{slug}/favorite` - Favorite an article
- `DELETE /api/articles/{slug}/favorite` - Unfavorite an article

### Tags
- `GET /api/tags` - Get all tags

## Contributing

When contributing to this project:

1. **Follow PSR standards** for PHP code style
2. **Write tests** for new features and bug fixes
3. **Update documentation** for any API or frontend changes
4. **Run the full test suite** before submitting pull requests
5. **Check code quality** with PHPStan and PHP-CS-Fixer

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [RealWorld](https://github.com/gothinkster/realworld) for the API specification
- [Symfony](https://symfony.com/) for the excellent PHP framework
- [Alpine.js](https://alpinejs.dev/) for the lightweight reactive framework
- [Twig](https://twig.symfony.com/) for the powerful templating engine
