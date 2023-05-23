Challenges
Routes, Views, Controllers

As a user, I can visit a custom landing page at localhost:3000. DONE

Rails.application.routes.draw do
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  get '/home_page' => 'home#home_page'

  # Defines the root path route ("/")
  # root "articles#index"
end


class HomeController < ApplicationController

    def home_page 
        render html: 'Hello, welcome to Scott and Justins page'
    end 
end


As a user, I can see the names of my team members as hyperlinks on the landing page. DONE

My Teammates  <%= link_to 'Justin', '/team_mates' %>
<%= link_to 'Scott', '/team_mates' %>
<%= link_to 'Cherry', '/team_mates' %>
<%= link_to 'Ernesto', '/team_mates' %>

class HomeController < ApplicationController

    def home_page 
        render html: 'Hello, welcome to Scott and Justins page'
    end 
    def team_mates
        @team_mates = 'list of team mates'
        render 'team_mates'
    end 
end


As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)
Params

As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.

As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.

As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).

As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.
