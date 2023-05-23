app/controllers/main_controller.rb
class MainController < ApplicationController
        
    def cubed
        @cubed = params[:Integer].to_i**3
    end 
end
app/views/main/cubed.html.erb
<h3> number is <%= @cubed %> </h3>
/Users/learnacademy/Desktop/rails-challenges/routes_controllers_views_params/config/routes.rb
Rails.application.routes.draw do
  # get 'team_memebers/:username/:logged_in' => 'team_members_account#github_user'
  get '/cubed/:Integer' => 'main#cubed'

end
http://localhost:3000/cubed/3
number is 27