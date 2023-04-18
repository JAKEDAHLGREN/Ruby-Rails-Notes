# Active Recod 4/13/2023

- Full Stack - Model, View, controller
- MVC - philosophy


### Active Record

Active Record - gem, ORM
 - PostgreSQL (flacor of SQL) <-> Rails (written in Ruby)
  - ORM - Object Relational Mapper (translator between languages)

### Terminal Commands

- create a new app: $ rails new active-record -d postrgresql -T
- ActiveRecord::NoDatabaseError
- create a new database: $ rails db:create
- start the server: $ rails s
- go to localhost:3000

### Databases

db live only on your server/computer they were created on
Rails app and files can be shared

### Generate Model

- $ rails generate model Schedule day:string date:date event:string
- migration file, model file
- never modify a db directly, always done through migration
- $ rails db:migrate
- migration creates the schema

### Rails Console

- $ rail c
- Schedule.all
- => Schedule Load (0.5ms) SELECT "schedules".\* FROM "schedules"

- Schedule.creat(day: 'Wednesday', date: '2023-04-12', event: 'Office Hours')

- Schedule.first -> returns the first index 
- Schedule.last -> returns the last index 
- Schedule.find(1) -> returns the specified primary key instance

### The types supported by Active Record are :primary_key, :string, :text, :integer, :float, :decimal, :datetime, :timestamp, :time, :date, :binary, :boolean ###

- Schedule.find(2) - read action (CRUD)
- Schedule.where(day: 'Wednesday') - where=read action - takes in a key and return every instances that is true

### Update
- create new variable
  - office = Schedule.first
    - update variable
      - office.update(event: 'Really Awesome Office Hours')

### Delete
- find instance
  - Schedule.find 3
   - Destroy

