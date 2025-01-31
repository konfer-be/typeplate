![Typescript / Express / Typeorm REST API boilerplate](https://i.ibb.co/dM2bhNJ/cover-typeplate.png)

[![Node](https://img.shields.io/badge/Node-20.18.0-informational?logo=node.js&color=43853D)](https://nodejs.org/docs/latest-v20.x/api/index.html)
[![TypeScript](https://img.shields.io/badge/Typescript-5.7.2-informational?logo=typescript&color=2F74C0)](https://www.typescriptlang.org/)
[![Express](https://img.shields.io/badge/Express-4.21.2-informational?logo=express&color=B1B1B1)](https://expressjs.com/)
[![Typeorm](https://img.shields.io/badge/Typeorm-0.3.20-informational?logo=typeorm&color=FFAB00)](https://typeorm.io/#/)
[![Mocha](https://img.shields.io/badge/Mocha-10.3.0-informational?logo=mocha&color=8A6343)](https://mochajs.org)

![Github action workflow status](https://github.com/steve-lebleu/typeplate/actions/workflows/build.yml/badge.svg?branch=master)
[![Coverage Status](https://coveralls.io/repos/github/steve-lebleu/typeplate/badge.svg?branch=master)](https://coveralls.io/github/steve-lebleu/typeplate?branch=master)
[![CodeFactor](https://www.codefactor.io/repository/github/steve-lebleu/typeplate/badge)](https://www.codefactor.io/repository/github/steve-lebleu/typeplate)
![GitHub Release](https://img.shields.io/github/v/release/steve-lebleu/typeplate?logo=Github)
![GitHub License](https://img.shields.io/github/license/steve-lebleu/typeplate?color=%230A7BBC)

Ready to use RESTful API boilerplate builded with [Express.js](http://expressjs.com/en/4x/api.html), [Typescript](https://github.com/Microsoft/TypeScript), [TypeORM](https://github.com/typeorm/typeorm) and [Mocha](https://mochajs.org/). 🤘

Thanks to Daniel F. Sousa for inspiration with his [ExpressREST API boilerplate](https://github.com/danielfsousa/express-rest-boilerplate) :beer:

## > Features

- **Containerization**
  - **Docker** with [Dockerfile](https://docs.docker.com/get-started/).
  - **Docker compose** with [docker-compose.yml](https://docs.docker.com/compose/) with mariadb and phpmyadmin.
- **Basics**
  - **Clear & clean code architecture** with classic layers such controllers, services, repositories, models, ...
  - **Object Relational Mapping** with [typeorm](https://typeorm.io/#/).
  - **Entity generation** with [rsgen](https://github.com/steve-lebleu/rsgen).
  - **Business validation** with self designed business members.
  - **Logs management** with [morgan](https://github.com/expressjs/morgan) and [winston](https://github.com/winstonjs/winston).
  - **Changelog completion** with [auto-changelog](https://www.npmjs.com/package/auto-changelog).
  - **Testing** with included unit and integration test sets builded with [mocha](https://mochajs.org/), [chai](https://www.chaijs.com/), [sinon](https://sinonjs.org/) and [supertest](https://github.com/visionmedia/supertest).
  - **Documentation** with [api-doc](https://apidocjs.com/).
- **Security**
  - **SSL secure connection** with native [HTTPS node module](https://nodejs.org/docs/latest-v14.x/api/https.html).
  - **Cross Origin Resource Sharing** with [CORS](https://expressjs.com/en/resources/middleware/cors.html).
  - **Securized HTTP headers** with [helmet](https://helmetjs.github.io/).
  - **HTTP header pollution** preventing with [hpp](https://www.npmjs.com/package/hpp).
  - **API request rate limit** with [express-rate-limit](https://www.npmjs.com/package/express-rate-limit).
  - **Route validation** with [joi](https://github.com/hapijs/joi).
  - **HTTP friendly errors** with [boom](https://github.com/hapijs/boom) and [http-status](https://www.npmjs.com/package/http-status).
- **Authentication**
  - **JWT authentication process** with [passport.js](http://www.passportjs.org/).
  - **oAuth authentication process** with [passport.js](http://www.passportjs.org/). 
  - **Sending transactional emails** with [cliam](https://github.com/steve-lebleu/cliam).
- **Performances**
  - **HTTP request cache** with [memory-cache](https://www.npmjs.com/package/memory-cache).
  - **Database query cache** with [typeorm caching](https://github.com/typeorm/typeorm/blob/master/docs/caching.md).
- **Assets management**
  - **Customizable file upload** with [multer](https://www.npmjs.com/package/multer).
  - **Customizable image resizing** with [jimp](https://www.npmjs.com/package/jimp).

## > Table of contents

- [Getting started](#getting-started)
- [Entity generation](#entity-generation)
- [Documentation](#documentation)
- [Tests](#tests)
- [Continuous integration](#continuous-integration)
- [Deployment](#deployment)
- [License](#license)

## Getting started

### Prerequisites

- Git
- Node.js >= 20.18.0
- NPM >= 10.2.3
- A database engine with a dedicated database (MariaDB, MySQL, PostgreSQL, ...) or Docker

### Step 1: install

#### Local

```bash
git clone https://github.com/steve-lebleu/typeplate.git path-to/your-project-name/
cd path-to/your-project-name/
npm run init
```

#### Docker

```bash
docker compose build
```

### Step 2: setup package.json

Open the *./package.json* file and edit it with your own values.

### Step 3: setup environment

Open *./dist/env/development.env* and fill the required env variables (uncommented in the file).

See wiki [env variables list](https://github.com/steve-lebleu/typeplate/wiki/Environment-variables) for more informations.

```bash
# Access token Secret passphrase
ACCESS_TOKEN_SECRET = "your-secret"

# CORS authorized domains
AUTHORIZED = "http://localhost:4200"

# API domain
DOMAIN = "localhost"

# Application port.
PORT = 8101

# Refresh token Secret passphrase
REFRESH_TOKEN_SECRET = "your-secret"

# Database engine
TYPEORM_TYPE = "mysql"

# Database server host. Use "db" with docker-compose, "localhost" otherwise.
TYPEORM_HOST = "localhost"

# Database name. Keep it different from your developement database.
TYPEORM_DB = "your-database"

# Database user
TYPEORM_USER = "root"

# Database password
TYPEORM_PWD = ""

# Database port
TYPEORM_PORT = "3306"
```

### Step 4: setup cliamrc.js

Transactional emails are send with [cliam](https://github.com/steve-lebleu/cliam). Open the *.cliamrc.js* and fill the [required configuration](https://github.com/steve-lebleu/cliam/wiki/Configuration-with-cliamrc.js) according your sending mode. See Cliam official [documentation](https://github.com/steve-lebleu/cliam/wiki) for more information.

Sandbox is set to true by default.

### Step 5: run

#### Local run

```bash
nodemon
```

#### Docker run

```bash
docker compose up -d
```

## Entity generation

Some repetitive tasks such as creating resources can be done quickly with [rsgen](https://github.com/steve-lebleu/rsgen).

See [entity generation](https://github.com/steve-lebleu/typeplate/wiki/Entity-generation) wiki section to learn more about generated elements and how to use.

## Documentation

```bash
npm run doc
```

Generate API documentation website into *./docs/apidoc/*.

See [apidoc](http://apidocjs.com/) for more informations about customization.

## Tests

```bash
npm run test
```

:warning: Because there are integration tests, you need a dedicated database to run the tests suites. It's already managed in CI/CD using Github actions, You need to mount it yourself in your local environment.

HTML coverage report is generated by [Istanbul](https://github.com/gotwarlost/istanbul) in *./reports/nyc-coverage*.

Bonus with *./insomnia.workspace.json* if you wish run manual e2e tests without create the config.

## Continuous integration

Basic Github actions configuration is provided in *./.github/workkflows.yml* files.

## Deployment

Project implements a basic [PM2](https://github.com/Unitech/PM2/) configuration to allow deployment.

Install PM2 globaly :

```bash
npm i pm2 -g
```

### Configuration

Configure the *./ecosystem.config.js* file with your env informations.

```javascript
{
  deploy : {
    staging : {
        user : 'node',
        host : '212.83.163.1',
        ref  : 'origin/master',
        repo : 'git@github.com:repo.git',
        ssh_options: ['StrictHostKeyChecking=no', 'PasswordAuthentication=yes', 'ForwardAgent=yes'],
        path : '/var/www/staging',
          'post-setup' : 'npm run kickstart:staging && pm2 reload ecosystem.config.js --env staging',
          'post-deploy' : 'npm i && tsc && pm2 reload ecosystem.config.js --env staging'
      }
  }
}
```

More info about PM2 [ecosystem.config.js](https://pm2.io/doc/en/runtime/reference/ecosystem-file/) file.

### Deploy

Pm 2 must be installed on the target server and your SSH public key granted.

```bash
# Setup deployment at remote location
pm2 deploy production setup

# Update remote version
pm2 deploy production update
```

More info about [PM2](http://pm2.keymetrics.io/docs/usage/quick-start/) and [PM2 deploy](https://pm2.io/doc/en/runtime/guide/easy-deploy-with-ssh/).

## License

[MIT](/LICENSE)
