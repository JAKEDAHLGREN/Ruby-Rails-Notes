### Active Record Association 4-14-2023 ##

- Foreign Key - ("match maker of the data world")
  - setting up relationship between parent table(primary key) and child table(foreign key)
    - a cohort has many students: HAS_MANY
      - In cohort.rb - has_many:students
    - a student belongs to a cohort: BELONGS_TO
      - In student.rb - belongs_to:cohort

  # Core Concepts
    - Relationships between tables
    - HAS_MANY, BELONGS_TO
    - Every table has a primary key - id:number
    - Foreign key - referenve to another tables's primary key

  # Setup
  - rails new associations -d postgresql -T
  - rails db:create

  # Databases
  - rails g model Cohort name:string year:string
  - rails g model Student name:string cohort_id:iteger
    - $$ must run rails db:migrate to update the model $$

  # Model Classes
  - app/models/cohort.rb
    - class cohort < ApplicationRecord

