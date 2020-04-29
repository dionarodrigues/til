# TypeORM is an ORM that can run in NodeJS

**Working on NodeJS applications I've found [TypeORM](https://typeorm.io/), an advanced object-relational mapping. **

> TypeORM is definitely the most mature Object Relational Mapper (ORM) available in the node.js world. Since it's written in TypeScript, it works pretty well with the Nest framework.
- https://docs.nestjs.com/recipes/sql-typeorm

I'm creating a project using NodeJS API that is powered by a PostgreSQL database (docker image) for data storage and using TypeORM to make my life easier as a developer. :)

To start the adventure with this library I had to run the following command to install all necessary dependencies:

`yarn add typeorm pg -D`

Next I need to create a new connection from the configuration file as you can see in this [documentation](https://github.com/typeorm/typeorm/blob/master/docs/using-ormconfig.md).

## Working with migrations

To work with migrations I needed to apply the following settings to my `ormconfig.json` file:

```
{
  "migrations": [
    "./src/database/migrations/*.ts"
  ],
  "cli": {
    "migrationsDir": "./src/database/migrations"
  }
}
```

And add the following command to my `package.json file`:

`"typeorm": "ts-node-dev ./node_modules/typeorm/cli.js"`

Then we'll able to run the following commands to create and run migrations:

`yarn typeorm migration:create -n CreateAppointments`
`yarn typeorm migration:run`

More information on migrations can be found [here](https://github.com/typeorm/typeorm/blob/master/docs/migrations.md).

Cheers




