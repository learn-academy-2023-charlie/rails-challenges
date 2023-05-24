Challenges
Routes, Views, Controllers

As a user, I can visit a custom landing page at localhost:3000.
As a user, I can see the names of my team members as hyperlinks on the landing page.
As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)
Params

As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.
As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.
As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).
As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.


class HomeController < ApplicationController
    def landing
    end

    def vance
        @vance = 'Vance'
    end

    def aubrey
        @aubrey = 'Aubrey'
    end

    def vance_likes
        @vance_likes = ['rollerskating', 'in-n-out', 'water']
    end

    def aubrey_likes
        @aubrey_likes = ['cats', 'coffee', 'mountains']
    end

    def cubed
        @cubed = params[:integer].to_i**3
    end

    def even
        if @even = params[:integer].to_i % params[:integer2].to_i == 0
           @even = 'first number is evenly divisible by second'
        else
           @even = 'first number is not evenly divisible by second'
        end
    end

    def palindrome_checka
        if @palindrome_checka = params[:string].reverse == params[:string]
           @palindrome_checka = 'its a palindrome!!!'
        else
           @palindrome_checka = 'not a palindrome ;P'
        end
    end
end




Rails.application.routes.draw do
  get '/landing' => 'home#landing'
  root 'home#landing'
  get 'vance' => 'home#vance'
  get 'aubrey' => 'home#aubrey'
  get 'vance_likes' => 'home#vance_likes'
  get 'aubrey_likes' => 'home#aubrey_likes'
  get 'cubed/:integer' => 'home#cubed'
  get 'even/:integer/:integer2' => 'home#even'
  get 'palindrome_checka/:string' => 'home#palindrome_checka'
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"
end


html.erb page-------
<%= @palindrome_checka %>





<h1> Welcome to our landing pageeeeeeee </h1>

<h2> Our Team </h2>

<ul>
<li><%= link_to 'Aubrey', '/aubrey_likes' %></li>
<li><%= link_to 'Vance', '/vance_likes' %></li>
</ul>