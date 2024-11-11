# Welcome to Flights Service

## Project Setup

- clone the project on your local
- Execute `npm install` on the same path as of your root directory of teh downloaded project
- Create a `.env` file in the root directory and add the following environment variable
  - `PORT=3000`
- Inside the `src/config` folder create a new file `config.json` and then add the following piece of json

```
{
  "development": {
    "username": <YOUR_DB_LOGIN_NAME>,
    "password": <YOUR_DB_PASSWORD>,
    "database": "Flights_Search_DB_DEV",
    "host": "127.0.0.1",
    "dialect": "mysql"
  }
}
```

- Once you've added your db config as listed above, go to the src folder from your terminal and execute `npx sequelize db:create`
  and then execute

`npx sequelize db:migrate`

## DB Design

- Airplane Table
- Flight
- Airport
- City

- A flight belongs to an airplane but one airplane can be used in multiple flights
- A city has many airports but one airport belongs to a city
- One airport can have many flights, but a flight belongs to one airport

# For create city model

`npx sequelize model:generate --name City --attributes name:String`

# For migration or sync with database

`npx sequelize db:migrate`

# Undo in migration file

`npx sequelize db:migrate:undo`

## Tables

### City -> id, name, created_at, updated_at

### Airport -> id, name, address, city_id, created_at, updated_at

    Relationship -> City has many airports and Airport belongs to a city (one to many)

## Create airplane model

`npx sequelize model:generate --name Airport --attributes name:String,cityId:integer`

## For Seeder file of airport

`npx sequelize seed:generate --name add-airport`

## For seed the airport data

`npx sequelize db:seed:all`

## For join city and airport data

`select * from Airports Join Cities on Airports.cityId = Cities.id where Cities.id = 2;`

## DB Sync

`db.sequelize.sync({alter : true});`

## TODO:

- Expose an api that can add multiple cities in one go(maybe pass an array in request body. no loops at all)
- Write a crud for airports
- Add an api in City resource for getting all the airports of a city

## Airplane Model

`npx sequelize model:generate --name Airplane --attributes modelNumber:String,capacity:integer`

## Seed Airplane

`npx sequelize seed:generate --name add-airplanes`

## For seed the Airplane data

`npx sequelize db:seed:all`

## For Flights model

`npx sequelize model:generate --name Flights --attributes flightNumber:String,airplaneId:integer,departureAirportId:integer,arrivalAirportId:integer,arrivalTime:Date,departureTime:Date,price:integer,boardingGate:String,totalSeats:integer`

## TODO:

- Make a general crud repository and crud service then extend it to airplane/airport/flight where it can be possible
