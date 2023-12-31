# Bookmarks API

Welcome to the Bookmarks API project! This is a NestJS-based API project that allows you to manage bookmarks and users.

## Database Design Diagram

![Database Diagram](https://raw.githubusercontent.com/mr-meselmani/bookmarks-api/3165d8488a35cf0a11382746f46afe170a0a76ff/db-diagram/Bookmarks%20API.svg)

## Table of Contents

- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Testing](#testing)
- [License](#license)

## Project Structure

The project follows the following structure:

- `prisma/`: Directory containing Prisma-related files.

  - `schema.prisma`: Prisma schema definition file for defining your data model.

- `src/`: Application source code.

  - `auth/`: Authentication-related components.
  - `bookmark/`: Bookmark-related components.
  - `prisma/`: Prisma service and configurations.
  - `user/`: User-related components.
  - `app.module.ts`: Main application module where components are imported and configured.
  - `main.ts`: Entry point for the application.

- `test/`: Test files and suites.

- `.env`: Environment variables for development.
- `.env.test`: Environment variables for testing.
- `.eslintrc.js`: ESLint configuration for linting your code.
- `.gitignore`: Specifies intentionally untracked files to ignore.
- `.prettierrc`: Configuration file for Prettier code formatter.
- `docker-compose.yml`: Docker Compose configuration for containerized development.
- `nest-cli.json`: Nest CLI configuration file.
- `package-lock.json` and `package.json`: Dependency management files.
- `README.md`: This file, containing project information and instructions.
- `tsconfig.build.json` and `tsconfig.json`: TypeScript configuration files.

## Getting Started

To get started with the Bookmarks API, follow these steps:

1. Clone this repository.
2. Install dependencies using `npm install`.
3. Configure your environment variables (see [Environment Variables](#environment-variables)).
4. Run the application (see [Running the Application](#running-the-application)).

## Environment Variables

The following environment variables are used in the project:

- `DATABASE_URL`: Connection URL for the database.
- `JWT_SECRET`: A secret key to let our server know that this token coming in the request to our api is generated from our server `e.g: secret-key`.

## Running the Application

1. Use docker to clone the postgres image, make sure your docker desktop is running then open your terminal and use the following command for e.g:

```bash
docker pull postgres:13
```

2. Now CD into your project directory and run the following command specified in `package.json` scripts to automate your work environment after that you will have a postgres container running:

```bash
npm run db:dev:restart
```

3. To run the application locally, use the following command:

```bash
npm run start:dev
```

## API Endpoints

### Base Url

`http://localhost:3333` try endpoint in postman or thunderclient(vscode) or whatever HTTP client you want e.g: `http://localhost:3333/auth/signup`

### 1. Sign Up

**Endpoint:** `POST /auth/signup`

**Description:** This endpoint is used for user registration.

**Request Body:**

```json
{
  "email": "asm@dev.com",
  "password": "asm123"
}
```

### 2. Sign In

**Endpoint:** `POST /auth/signin`

**Description:** This endpoint is used for user authorization.

**Request Body:**

```json
{
  "email": "asm@dev.com",
  "password": "asm123"
}
```

### 3. Get Me

**Endpoint:** `GET /users/me`

**Description:** This endpoint is used getting current user.

**Headers:** Authorization: Bearer `jwt token`.


### 4. Edit User

**Endpoint:** `PATCH /users`

**Description:** This endpoint is used for user authorization.

**Headers:** Authorization: Bearer `jwt token`.

**Request Body:** all optional

```json
{
  "email": "asm@engineer.com",
  "firstName": "ASM",
  "lastName": "Engineer"
}
```

### 5. Get Bookmarks

**Endpoint:** `GET /bookmarks`

**Description:** This endpoint is used to get all bookmarks.

**Headers:** Authorization: Bearer `jwt token`.


### 6. Create Bookmark

**Endpoint:** `POST /bookmarks`

**Description:** This endpoint is used to create bookmark.

**Headers:** Authorization: Bearer `jwt token`.

**Request Body:** description is optional

```json
{
  "title": "Bookmark Title",
  "description": "",
  "link": "https://twitter.com/mr_meselmani"
}
```

### 7. Get Bookmark By ID

**Endpoint:** `GET /bookmarks/{id}`

**Description:** This endpoint is used to get bookmark by id.

**Headers:** Authorization: Bearer `jwt token`.


### 8. Edit Bookmark

**Endpoint:** `PATCH /bookmarks/{id}`

**Description:** This endpoint is used to edit bookmark.

**Headers:** Authorization: Bearer `jwt token`.

**Request Body:** description is optional

```json
{
  "title": "Bookmark Two",
  "description": "Supercalifragilisticexpialidocious",
  "link": "https://twitter.com/mr_meselmani"
}
```

### 9. Delete Bookmark

**Endpoint:** `DELETE /bookmarks/{id}`

**Description:** This endpoint is used to edit bookmark.

**Headers:** Authorization: Bearer `jwt token`.



## Testing

I added a test db in `docker-compose.yml` to run the test again & again just run in the Terminal this command and it will create a test-db container from the postgres image & it will start the tests directly:

```bash
npm run test:e2e
```

## License

Bookmarks API is [MIT licensed](https://github.com/mr-meselmani/bookmarks-api/blob/master/LICENSE)