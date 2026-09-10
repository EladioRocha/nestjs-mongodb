# NestJS and MongoDB — Users CRUD

A **NestJS 10 tutorial application using Mongoose** to create, list, update, and delete users in MongoDB. The users module demonstrates controllers, services, DTOs, schemas, and dependency injection.

## Setup

Install Node.js, npm, and a development MongoDB instance, then run:

```sh
npm ci
```

In [src/app.module.ts](src/app.module.ts), replace `<MONGODB_URI>` in `MongooseModule.forRoot()` with your local connection URI, for example `mongodb://127.0.0.1:27017/nest_users`. The current application does not load a `.env` file or read a MongoDB environment variable. Keep private credentials out of committed source.

```sh
npm run start:dev
```

The server listens on port `3000`, configured in [src/main.ts](src/main.ts).

## Users API

| Method | Path | Action |
| --- | --- | --- |
| GET | `/users` | List users. |
| GET | `/users/:id` | Find a user by MongoDB ID. |
| POST | `/users` | Create a user. |
| PUT | `/users/:id` | Update and return the updated user. |
| DELETE | `/users/:id` | Delete a user. |

Example JSON body for creation:

```json
{"name":"Example User","username":"example","email":"example@example.com","age":25}
```

The create DTO defines `name`, `username`, `email`, and optional `age`. TypeScript declarations alone do not provide runtime request validation. This tutorial does not implement authentication guards for these routes.

## Build and tests

```sh
npm run build
npm run start:prod
```

The build emits `dist`; production startup runs `dist/main`. Available checks include `npm test`, `npm run test:cov`, and `npm run test:e2e`. The generated tests may require configured providers or a test database; they were not run as part of this documentation-only update. `npm run lint` and `npm run format` modify files.

## Code map

- [src/modules/users/users.controller.ts](src/modules/users/users.controller.ts): HTTP routes.
- [src/modules/users/users.service.ts](src/modules/users/users.service.ts): Mongoose operations.
- [src/modules/users/schemas/user.schema.ts](src/modules/users/schemas/user.schema.ts): data schema.
- [src/modules/users/dto](src/modules/users/dto): request types.
- [test](test): end-to-end test configuration.

This repository accompanies the author's NestJS/MongoDB tutorial. Generic Nest framework badges and sponsorship text have been replaced with project-specific instructions. The package declares `UNLICENSED`; upstream Nest licensing does not automatically license this repository.
