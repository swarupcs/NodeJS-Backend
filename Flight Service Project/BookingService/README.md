## Create migration, models, seeders and config folder
`npx sequelize init`

## Create database
`npx sequelize db:create`

## Create the booking model
    `npx sequelize model:generate --name Booking --attributes flightId:integer,userId:integer,status:enum`


## Migrate DB
`npx sequelize db:migrate`

## Normal Migration
`npx sequelize migration:create --name modify_bookings_add_new_fields`

## TODO

    - Update booking feature
    - Read about winston
    - Complete error handling in other services