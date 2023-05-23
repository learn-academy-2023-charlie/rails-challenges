Challenges
Routes, Views, Controllers

As a user, I can visit a custom landing page at localhost:3000.
As a user, I can see the names of my team members as hyperlinks on the landing page.
As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)


class MainController < ApplicationController
    def landing
        render 'landing'
    end
    def halie
        render 'halie'
    end
    def jessica
        render 'jessica'
    end
end

Rails.application.routes.draw do
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"
  get '/landing' => 'main#landing'
  root 'main#landing'
  get '/halie' => 'main#halie'
  get 'jessica' =>'main#jessica'
end

Halie HTML
<h1> Halie's Top 3 Drinks </h1>
<h3>
    <ul>
        <li>One</li>
        <li>Two</li>
        <li>Three</li>
    </ul>
</h3>

<%= link_to 'Back to Home', '/landing' %>

Jessica HTML
<h1> Jessica's Top 3 Movies </h1>
<h3>
    <ul>
        <li>One</li>
        <li>Two</li>
        <li>Three</li>
    </ul>
</h3>

<%= link_to 'Back to Home', '/landing' %>

Landing HTML
<h2> Want to See Our Top 3? </h2>
<%= link_to "Halie's Top 3 Drinks", '/halie' %>
<div>
<%= link_to "Jessica's Top 3 Movies", '/jessica' %>
</div>
