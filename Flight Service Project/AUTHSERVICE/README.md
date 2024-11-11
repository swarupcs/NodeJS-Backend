

`npx sequelize init`

`npx sequelize db:create`

## For create User model
`npx sequelize model:generate --name User --attributes email:string,password:string`

## For migrate the db
`npx sequelize db:migrate`

## For create role model
    `npx sequelize model:generate --name Role --attributes name:string`

## DB migrate
    `npx sequelize db:migrate`

## Seeders for user-roles
    `npx sequelize seed:generate --name add-roles`

## Seed the roles data
    `npx sequelize db:seed --seed 20241103145113-add-roles.js`