WILD LIFE TRACKER

## Process ##
- Desktop
 $ rails new wildlife_tracker -d postgresql -T
 $ cd wildlife_tracker
 $ rails db:create
- Connect app to repo
 $ git remote add origin "http"
 $ ls -a (check for .git)
 $ git branch (none yet)
 $ git checkout -b main
 $ git status
 $ git add . (adds all file)
 $ git commit -m "initial commit"
 $ git push origin main

 $ bundle add rspec-rails
 $ rails g rspec:install
 $ rails s (to check if the server is running)
- Open localhost in browser

Create a resource
 $ rails generate resource Animal common_name:string scientifi_binomial:string
 $ rails db:migrate
 $ code .

- Look at routes file
 - check all your routes
   $ rails routes || $ rails routes -Expand

Now we have routes, controllers, database, 

$ rails c
$Animal.all (no instances yet)
- Create an instance
$ Animal.create(common_name:'', scientific_binomial:'')

- In animal_controller
```bash
class AnimalController < ApplicationController
  def index
    animals = Animal.all
    render json: animals
  end
end

```
- Open postman
- Create new
- Enter your request type and then the Localhost:3000/
- Check to make sure JSON is selected


- In animal_controller
```bash
class AnimalController < ApplicationController
  def index
    animals = Animal.all
    render json: animals
  end
  def show
    animal = Animal.find(params[:id])
    render json: animal
  end

  def create
    animal = Animal.create(animal_params)
    if animal.valid?
      render json: animal
    else
      render json: animal.errors
  end

  def update
    animal = Animal.find(params[:id])
    animal.update(animal_params)
    if animal.valid?
      render json: animal.update
    else
      render json: animal.errors
    end
  end

  def destroy
    animal = Animal.find(params[:id])
    if animal.destroy
      render json: animal
    else
      render json: animal.errors
    end
  end

  private
  % Strong params
  def animal_params
    params.require(:animal).permit(:common_name, :scientific_binomial)
  end
end
```
- Check in Postman for create using a POST , body, raw, JSON

{
  "common_name": "  "
  "scientific_binomila": "  "
}
- Look at the Preview, Look at syllabus "Rails API" for Disable Authenticity Token - copy code and post it in the application_controller.rb 