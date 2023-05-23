<!-- class MainController < ApplicationController

    def members
        @our_members = ['tucker', 'yuehan']
    end

    def tucker
        @fav_movies = ['Office Space', 'Dazed and Confused', 'Dodgeball']
    end

    def yuehan
        @favorite_movies = ['prestige', 'train to busan', 'princess mononaki']
    end

end -->


<!--<h1> Here is a list of tuckers top three favorite movies </h1>

<ol>

<% @fav_movies.each do |movie| %>
    
    <li> <%= movie %> </li>

<% end %>

</ol>

 -->


 <!-- <h1> Here is a list of yuehans top three favorite movies </h1>

<ol>

<% @favorite_movies.each do |movie| %>
    
    <li> <%= movie %> </li>

<% end %> -->


<!-- Rails.application.routes.draw do
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"
  root 'main#members'
  get'/members' => 'main#members'
  get'/tucker' => 'main#tucker'
  get'/yuehan' => 'main#yuehan'


end -->
