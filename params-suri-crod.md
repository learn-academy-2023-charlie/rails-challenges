<!-- homecontroller.rb -->
class HomeController < ApplicationController
    def landing

    end  

    def suri
        @variable = ['Rick and Morty', 'Solar Opposites', 'Parks and Rec']
    end

    def crod
        @tvshow = ['Rick and Morty', 'Solar Opposites', 'American Dad']
    end

    def cubed  
        @cubed= params[:cubed].to_i
    end
    def evenly
        @num1= params[:num1].to_i
        @num2= params[:num2].to_i
       if  @num1 % @num2  == 0
        @result_string= 'Even'
       else
        @result_string= 'Odd'
       end

    end
end

<!-- routes.rb -->

Rails.application.routes.draw do
  root 'home#landing'
  get '/landing' => 'home#landing'
  get 'cubed/:cubed' => 'home#cubed'
  get 'evenly/:evenly' => 'home#evenly'
  get 'evenly/:num1/:num2', to: 'home#evenly'


end






<!-- evenly.html.erb -->
<% @evenly %>




<h2> <%= @result_string %> </h2>