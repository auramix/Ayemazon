
## Table of Contents
1. [Overview](#overview)
2. [Environment Setup](#environment)
3. [API Usage](#api)


## Overview
> This project consisted of 3 parts:
> 1. Adopt legacy code, make application functional and write CRUD functions.
> 2. Seed database with 10M primary records and do local stress testing w/artillery.io & New Relic ahead of deployment to AWS.
> 3. Deploy to AWS and scale server response to handle as much load as possible. Loader.io used to stress test deployed service.

## Environment

*Install MySQL*
```console
brew install mysql@5.7
```

*Install dependencies*
```console
npm install
```

*Run MySQL from command line*
```console
mysql -u root -p
```

*Create Database*
```
source ./database-mysql/schema.sql
```

*Create setup.js*
- Copy temp_setup.js to setup.js
- Update environment information in setup.js file


*Seed database*
```console
node ./database-mysql/seeds/loadFakeData.js
```

*Compile react app for Production*
```
npm run react-prod
```

*Run server*
```
npm run server
```

## API

**`GET`** path **`/product/:id`**
- Fetches product info for the given id, including product availability

## Local server routes - internal, not exposed

**`POST`** path **`/`**
- Creates record in database table of choice
- Provide request body with a table name and data to insert e.g. `{ table: 'your_table_name', data: { col_1: 'someValue' } }`

**`PUT`** path **`/`**
- Updates record in database table of choice
- Provide request body with a table name, data to update, and id e.g. `{ table: 'your_table_name', data: { col_1: 'someValue' }, id: 45 }`

**`DELETE`** path **`/`**
- Deletes record in database table of choice
- Provide request body with a table name and id e.g. `{ table: 'your_table_name', id: 86 }`
