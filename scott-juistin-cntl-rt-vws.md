Challenges
Routes, Views, Controllers

As a user, I can visit a custom landing page at localhost:3000.


As a user, I can see the names of my team members as hyperlinks on the landing page.


As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)

routes.rb  <----- file name 

Rails.application.routes.draw do
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  get '/home_page' => 'home#home_page'
  get '/team_mates' => 'home#team_mates'
  get '/scott' => 'home#scott' 
  # root "articles#index"
end

team_mates.html.erb <---- file name


<h2><%=@team_mates%></h2>
<%= link_to 'scott', '/scott' %>
<%= link_to 'Cherry', '/team_mates' %>
<%= link_to 'Ernesto', '/team_mates' %>
link_to 'Justin', '/team_mates' 
<%= link_to 'scott', '/scott' %>

home_controllers.rb  <---- file name


class HomeController < ApplicationController

    def home_page 
        render html: 'Hello, welcome to Scott and Justins page'
    end 
    def team_mates
        # @Scott = ['call of duty', 'music', 'my dog']
        @team_mates = 'Here is a list of my team mates'
       
    end 
    def scott 
        @scott = ['call of duty', 'music', 'my dog']
    end
end









## Params

### As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed. ✅
-   Bash: http://localhost:3000/cubed?number=5

-   main_controller:
def cubed
        @number = params[:number].to_i ** 3
    end

-   cubed.html.erb
<h2> <%= @number %> </h2>

-   routes.rb
 get '/cubed' => 'main#cubed'

### As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.✅
-   Bash: http://localhost:3000/evenly?number1=24&number2=6

-   main_controller:
 def evenly
        @number1 = params[:number1].to_i
        @number2 = params[:number2].to_i
    
        if @number2.zero?
          @result_string = "Cannot divide by zero"
        elsif (@number1 % @number2).zero?
          @result_string = "#{@number1} is evenly divisible by #{@number2}"
        else
          @result_string = "#{@number1} is not evenly divisible by #{@number2}"
        end
      end

-   evenly.html.erb:
<%= @result_string %>

-   routes.rb:
get '/evenly', to: 'main#evenly'

### As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).✅
-   Bash: http://localhost:3000/palindrome?string=racecar

-   main_controller:
def palindrome
        @string = params[:string]

        if @string == @string.reverse
            @palindrome_string = "#{@string} is a palindrome"
        else
            @palindrome_string = "#{@string} is not a palindrome"
        end
    end

-   palindrome.html.erb:
<h1> <%= @palindrome_string %> </h1>

-   routes.rb:
get '/palindrome', to: 'main#palindrome'

### As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.