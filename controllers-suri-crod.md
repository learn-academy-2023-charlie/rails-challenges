#Routes Controllers Views Suri and CRod 5/23/23

#Routes, Views, Controllers

✅As a user, I can visit a custom landing page at localhost:3000.

✅As a user, I can see the names of my team members as hyperlinks on the landing page.

✅As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)

In the home_controller.rb file the code is as follows:

```ruby

class HomeController < ApplicationController
    def landing
    end

    def suri
        @tv_shows_suri = ['Rick and Morty', 'Solar Opposites', 'Parks and Recreation']
    end

    def crod
        @tv_shows_crod = ['Rick and Morty', 'Solar Opposites', 'American Dad']
    end
end
```

Then in the routes.rb file the code is as follows:
```ruby
Rails.application.routes.draw do
 
  root 'home#landing'
  get 'landing' => 'home#landing'
  get '/suri' => 'home#suri'
  get '/crod' => 'home#crod'
end

```

Then in the landing.html.erb file the code is as follows:
```html
 <h1>Hello World</h1>

<h2>Checkout the member pages</h2>

<%= link_to 'Suri', '/suri' %>
<br />
<%= link_to 'Crod', '/crod' %>

```

Then for each member page we add the following:
suri_html.rb
```html

<h1>Suri</h1>
<ul>
<h2>Favorite TV shows</h2>
<% @tv_shows_suri.each do |value| %>
    <li> <%= value %> </li>
<% end %>
</ul>

<%= link_to 'Home', '/landing' %>
<%= link_to 'Crod', '/crod' %>

```

crod.html.rb
```html
<h1>C Rod</h1>
<ul>
<h2>Favorite TV shows</h2>
<% @tv_shows_crod.each do |value| %>
    <li> <%= value %> </li>
<% end %>
</ul>

<%= link_to 'Home', '/landing' %>
<%= link_to 'Suri', '/suri' %>
```