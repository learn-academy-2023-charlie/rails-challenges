Params

    * create new rails application:
    rails new params_challenges -d postgresql -T

    * create database
    rails db:create

    * start server
    rails s

    * create controller
    rails g controller Main


As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.



As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.

As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).

As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.

in main_controller.rb

    class MainController < ApplicationController
        def cube
            @num = params[:num].to_i
        end

        def even
            @num1 = params[:num1].to_i
            @num2 = params[:num2].to_i
        end

        def palindrome
            @str = params[:str]
        end

        def madlib
            @num = params[:num].to_i
        end
        

        def landing

        end

    end

in routes.rb

    Rails.application.routes.draw do
    root 'main#landing'
    get '/cube' => 'main#cube'
    get '/cube/:num' => 'main#cube'
    get '/even' => 'main#even'
    get '/even/:num1' => 'main#even'
    get '/even/:num1/:num2' => 'main#even'
    get '/palindrome' => 'main#palindrome'
    get '/palindrome/:str' => 'main#palindrome'
    get '/madli' => 'main#,madli'
    get '/landing' => 'main#landing'
    end

in landing.html.erb

    <h1>This is the landing page.</h1>

    <p> 
        <%= link_to 'Click me to the cube page', "/cube" %>
    </p>
    </br>
    <p> 
        <%= link_to 'Click me to the even page', "/even/" %>
    </p>
    </br>
    <p> 
        <%= link_to 'Click me to the palindrome page', "/palindrome/" %>
    </p>
    </br>
    <p> 
        <%= link_to 'Click me to the madlib page', "/madlib/" %>
    </p>

in cube.html.erb

    <h3> Cubed </h3>
    <% if @num == 0 %>
        <p>
        You need a params number.
        </p>
    <% else %>
        <p>
        The cube of <%= @num %> is <%= @num **3 %>
        </p>
    <%end%>

    <p> 
        <%= link_to 'Click me to the landing page', "/" %>
    </p>

in even.html.erb

    <h3> Evenly </h3>

    <% if @num1.zero? || @num2.zero? %>
        <p>
        2 params numbers is required.
        </p>
    <% elsif @num1 % @num2 == 0 %>
        <p>
        <%= @num1 %> is evenly divisble by <%= @num2 %>!
        </p>
    <% else %>
        <p>
        <%= @num1 %> is not evenly divisble by <%= @num2 %>!
        </p>
    <%end%>

    <p> 
        <%= link_to 'Click me to the landing page', "/" %>
    </p>


    in palindrome.html.erb

    <h3> Palindrome </h3>

    <% if params[@str].downcase == params[@str].downcase.reverse? %>
        <p>
        <%= @str %> is a palindrome word. 
        </p>
    <% else %>
        <p>
        <%= @str %> is not a palindrome word.    
        </p>
    <%end%>

    <p> 
        <%= link_to 'Click me to the landing page', "/" %>
    </p>