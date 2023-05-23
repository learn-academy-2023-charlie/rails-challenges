app/controllers/main_controller.rb
class MainController < ApplicationController
        def team_members
            @logged_in = params[:logged_in]
            if @logged_in == 'true'
                @user = params[:username]
            else 
                @user = 'message here'
        end
    end
    def cubed
    end
end
app/views/main/cubed.html.erb
<p> this is coming from my view page of cubed </p>
config/routes.rb
Rails.application.routes.draw do
  # get 'team_memebers/:username/:logged_in' => 'team_members_account#github_user'
  get '/cubed' => 'main#cubed'

end
