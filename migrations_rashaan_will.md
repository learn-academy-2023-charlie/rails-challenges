Add five entries to the database via the Rails console
Movie.create(title: 'Interstellar', category: 'SciFi')
Movie.create(title: 'Arrival', category: 'SciFi')
Movie.create(title: 'BladRunner 2049', category: 'SciFi')
Movie.create(title: 'Dune', category: 'SciFi')
Movie.create(title: 'Anchorman', category: 'Comedy')

Create a migration to add a new column to the database called movie_length
rails g migration add_column_length_to_movie
Updated the db file as follows:
    add_column :movies, :length, :string

Update the values of the five existing attributes to include a movie_length value
[#<Movie:0x000000010f619620 id: 1, title: "Interstellar", category: "SciFi", created_at: Thu, 18 May 2023 22:24:35.322459000 UTC +00:00, updated_at: Thu, 18 May 2023 22:32:18.308972000 UTC +00:00, length: "2.5 hours">,
 #<Movie:0x000000010f6194e0 id: 2, title: "Arrival", category: "SciFi", created_at: Thu, 18 May 2023 22:24:48.876474000 UTC +00:00, updated_at: Thu, 18 May 2023 22:33:51.617506000 UTC +00:00, length: "2.3 hours">,
 #<Movie:0x000000010f6193a0 id: 3, title: "BladRunner 2049", category: "SciFi", created_at: Thu, 18 May 2023 22:25:04.646340000 UTC +00:00, updated_at: Thu, 18 May 2023 22:34:18.870657000 UTC +00:00, length: "2 hours">,
 #<Movie:0x000000010f619260 id: 4, title: "Dune", category: "SciFi", created_at: Thu, 18 May 2023 22:25:15.089095000 UTC +00:00, updated_at: Thu, 18 May 2023 22:34:49.904458000 UTC +00:00, length: "2.45 hours">,
 #<Movie:0x000000010f619120 id: 5, title: "Anchorman", category: "Comedy", created_at: Thu, 18 May 2023 22:25:29.755655000 UTC +00:00, updated_at: Thu, 18 May 2023 22:35:18.977916000 UTC +00:00, length: "1.95 hours">] 

Generate a migration to rename the column 'category' to 'genre'
rails g migration change_column_name_to_genre
Updated the db file as follows:
    rename_column :movies, :category, :genre
[#<Movie:0x00000001074a6cf0 id: 1, title: "Interstellar", genre: "SciFi", created_at: Thu, 18 May 2023 22:24:35.322459000 UTC +00:00, updated_at: Thu, 18 May 2023 22:32:18.308972000 UTC +00:00, length: "2.5 hours">,
 #<Movie:0x0000000107aa23c0 id: 2, title: "Arrival", genre: "SciFi", created_at: Thu, 18 May 2023 22:24:48.876474000 UTC +00:00, updated_at: Thu, 18 May 2023 22:33:51.617506000 UTC +00:00, length: "2.3 hours">,
 #<Movie:0x0000000107aa2320 id: 3, title: "BladRunner 2049", genre: "SciFi", created_at: Thu, 18 May 2023 22:25:04.646340000 UTC +00:00, updated_at: Thu, 18 May 2023 22:34:18.870657000 UTC +00:00, length: "2 hours">,
 #<Movie:0x0000000107aa2280 id: 4, title: "Dune", genre: "SciFi", created_at: Thu, 18 May 2023 22:25:15.089095000 UTC +00:00, updated_at: Thu, 18 May 2023 22:34:49.904458000 UTC +00:00, length: "2.45 hours">,
 #<Movie:0x0000000107aa21e0 id: 5, title: "Anchorman", genre: "Comedy", created_at: Thu, 18 May 2023 22:25:29.755655000 UTC +00:00, updated_at: Thu, 18 May 2023 22:35:18.977916000 UTC +00:00, length: "1.95 hours">] 