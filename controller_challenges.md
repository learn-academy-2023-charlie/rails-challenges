<!-- Routes -->
Rails.application.routes.draw do
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"
  get '/greeter'=>'home#greeter'
  get '/landing'=> 'home#landing'
  root 'home#landing'
  get '/henri'=>'home#henri'
  get '/ernesto'=>'home#ernesto'
  get '/cubed/:Integer'=>'home#cubed'
  get '/evenly/:num1/:num2'=>'home#evenly'
end


<!-- Controller -->
class HomeController < ApplicationController
    def greeter
        render html: 'Hiya Stranger! Come on in!'
    end
    def landing
    end
    def henri
    end
    def ernesto
    end
    def cubed
        @cubed = params[:Integer].to_i
    end
    def evenly
        @num1 = params[:num1].to_i
        @num2 = params[:num2].to_i
        if @num1 % @num2 == 0
            is_even = "#{@num1} is divisible by #{@num2}"
        else 
            is_not = "#{@num1} is not divisible by #{@num2}"
        end
    end
end


<!-- landing -->
<h1>Welcome to the Bearded Boys</h1>
<%= link_to 'Greeter', '/greeter' %>
<br/>
<%= link_to 'Henri', '/henri' %>
<br/>
<%= link_to 'Ernesto', '/ernesto' %>
<br/>
<%= link_to 'Cubed', '/cubed' %>
<br/>
<%= link_to 'Evenly', '/evenly' %>



