### Migration ```bash   ```
Resources: guides.rubyonrails.org/

### How to drop rails database
 - $ rails db:drop
 - $ cd .. 
 - $ rm -rf <name of the rails app>

- Generate a model 
  - model: Ruby class that is used to represent data
  - naming convention: singular, PascalCase
    -  $ rails generate model PartyAgenda title:string role:string name:string
      - command creates a model and migration
    - $ rails db:migrate (every time you make a change)
      - command makes schema appear, in the migrate tab
      - table will be in snake_case and plural (created by rails)

- Preform a migration
  - migration: used to alter the structure of the database (AKA - schema)

- CRUD actions on data entries
  - $ rails console (active record queries)
  - create entries (instance of class PartyAgenda)
  > PartyAgenda.create(role:'hula_dancer', name:'Elmer')
  > PartyAgenda.create(role:'hula_dancer', name:'Dre')
  > PartyAgenda.create(role:'hula_dancer', name:'Felix')

 - READ
 > PartyAgenda.all

 - UPDATE - two ways to perform 
  - store the active record query in a variable
    > fire = PartyAgenda.find_by(name: 'Felix') -- instance you want to update
    > fire.update(role: 'fire_twirler') -- what needs to be changed
 ## Adding a column ## snake_case or PascalCase
 - Generate a migration -
   - $ rails generate migration AddConfirmedColumnToPartyAgenda
     - $ rails g... also works
 - Add a change definition to the change method in migration file
   - structure - add_column :table_name, :column_name, :datatype
     - add_column :party_agendas, :confirmed, :string (in our change method)

- Update schema with the migrations
  - $ rails db:migrate (to update the change)
  - to change the value of confirmed column
    - confirm = PartyAgenda.find (1)
    - confirm.update(confirmed:'yes')

   