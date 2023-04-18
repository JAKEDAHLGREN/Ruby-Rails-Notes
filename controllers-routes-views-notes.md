## Rails Notes 4-18-2023 ##

Create branch
  $ git checkout -b routes-controllers
Create app
  $ rails new routes_controllers_views -d postgresql -T
    - cd into app
Create Database
  $ rails db:create
Start server and open new terminal tab
  $ rails s
Create a Controller (PascalCase) - in app under controllers
$ rails g controller Home 
$ rm app/helpers/home_helper.rb (not neccessary for now)



## Controllers, Routes, and Views

- View: what the user sees

- Controller: grabs data and coordinates the interaction between the user, the views, and the model

- Route: the path to seeing something

# Method Example: in home_controller.rb
```bash
class HomeController < ApplicationController
 # first method
  def greeter
    render html: 'Hey there Movie Lovers!'
  end
# second method
  def movie
    render html: 'Slept on movie of the day: High Tension'
  end
# third method
  def movie_recommendations # go to apps/views/home to create html.erb file, name your view file the same as your method (movie_recommendations.erb)
    @recommendations = 'These are movies that I promise you will like' # instance variable(call in .erb file)
    @movies = ['Kingdom Come', 'Anything Produced by A24', 'John Wick 4'] # instance variable to replace the <ul> of movies in the erb file
  end
# fourth method
  def landing 
  end
end

```
- Config folder
 - routes.rb
```bash
    Rails.application.routes.draw do
    # Defines the root path route ("/")
    # root "articles#index"
    # HTTP verb / route(url) / hash rocket / controller#controller_method
      get '/greeter' => 'home#greeter' # first route
      
      get '/movie' => 'home#movie' # second route
      
      get '/recommendations' => 'home#movie_recommendations' # third route
      
      get '/landing' => 'home#landing' # fourth route
      root to: 'home#landing' # landing page/ root page
    end
    # can be see in the server terminal and live server when you enter in/route_name
``` 

## View file (movie_recommendations.erb) - embedded ruby file
  - use <%= to embed ruby

```js
<h1>Need a movie to watch?</h1>
  <h2>Here are some movie recommendations to checkout </h2>
  <p> <%= @recommendations </p> // this calls embed a ruby instance variable

  // line 68-70 replaces 72-74 with an instance variable from home_controller.rb
  <ul> 
    <% @movies.each do |value| %>
      <li> <%= value %></li>
      <% end %>

    // <li>Kingdom Come</li> // remove list Items and replace with @movie instance variable array
    // <li>Anything Produced by A24</li>
    // <li>John Wick 4</li>
  </ul>

```

## views/home add file landing.html.erb

```bash

<h1> Welcome to your Favorite Movie site </h1> #landing page title
# Creating clickable links to all of your routes
<%= link_to 'Greeter', '/greeter' %>
<br/> 
<%= link_to 'Movie of the Day', '/movie' %>
<br/> 
<%= link_to 'Movie Recommendations', '/recommendations' %>


```