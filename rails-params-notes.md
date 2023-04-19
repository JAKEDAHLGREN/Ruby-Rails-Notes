## Rails Params

Request-response cycle
 - request
  - action: http verb - post, get, put, patch delete
  - location: url
 - response
  - code: 100, 200, 300, 400, 500,
  - payload: html

- param - short for parameter - are always a string
- params are a hash that adds info to URL
  - when you define and instance (@user) instead of hard coding the user name you can set it equal to params[:username], so in your @username = params[:username] *** on the controller.rb page ***
  - Then you need to modify your routes.rb to include :username in the path  
   - ex: get '/github_user/:username' = 'github_user_account_controller#github_user'
  
Process (controller, route, view)
 - Rails g controller gitHubUserAccount

 