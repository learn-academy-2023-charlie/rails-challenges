we had lots of trouble shooting..

➜  Desktop ls 
charlie-github-config             rolodex_challenge
charlie-github-setup              ruby-challenges
countries.sql                     text-based-game-no-name
favorite_movies                   treasure-hunt-Romoramel
git-command.md                    untitled folder
javascript-foundations-challenges week-1-assessment-Romoramel
javascript-intro-challenges       week-2-assessment-Romoramel
projects                          week-3-assessment-Romoramel
rails-challenges                  weekly-assessments
react-challenges                  whiteboard3.js
➜  Desktop cd favorite_movies/
➜  favorite_movies git:(main) ✗ rails db:create
Created database 'favorite_movies_development'
Created database 'favorite_movies_test'
➜  favorite_movies git:(main) ✗ rails server
=> Booting Puma
=> Rails 7.0.4.3 application starting in development 
=> Run `bin/rails server --help` for more startup options
Puma starting in single mode...
* Puma version: 5.6.5 (ruby 3.2.0-p0) ("Birdie's Version")
*  Min threads: 5
*  Max threads: 5
*  Environment: development
*          PID: 94159
* Listening on http://127.0.0.1:3000
* Listening on http://[::1]:3000
Use Ctrl-C to stop
^C- Gracefully stopping, waiting for requests to finish
=== puma shutdown: 2023-05-18 15:38:57 -0700 ===
- Goodbye!
Exiting
➜  favorite_movies git:(main) ✗ rails s
=> Booting Puma
=> Rails 7.0.4.3 application starting in development 
=> Run `bin/rails server --help` for more startup options
Puma starting in single mode...
* Puma version: 5.6.5 (ruby 3.2.0-p0) ("Birdie's Version")
*  Min threads: 5
*  Max threads: 5
*  Environment: development
*          PID: 94212
* Listening on http://127.0.0.1:3000
* Listening on http://[::1]:3000
Use Ctrl-C to stop
^C- Gracefully stopping, waiting for requests to finish
=== puma shutdown: 2023-05-18 15:39:45 -0700 ===
- Goodbye!
Exiting
➜  favorite_movies git:(main) ✗ rails c 
Loading development environment (Rails 7.0.4.3)
3.2.0 :001 > rails g model Movie title:string, category:string
(irb):1:in `<main>': undefined local variable or method `string' for main:Object (NameError)                                                   
                                                               
rails g model Movie title:string, category:string              
                          ^^^^^^                               
Did you mean?  String                                          
3.2.0 :002 > rails g model Movie title:String, category:String
(irb):2:in `<main>': undefined method `Movie' for main:Object (NoMethodError)
                                                               
rails g model Movie title:String, category:String              
              ^^^^^                                            
3.2.0 :003 > rails generate model Movie title:string category:string
/Users/learnacademy/.rvm/gems/ruby-3.2.0/gems/irb-1.6.4/lib/irb/workspace.rb:113:in `eval': (irb):3: syntax error, unexpected label, expecting `do' or '{' or '(' (SyntaxError)                                                
...el Movie title:string category:string
...                      ^~~~~~~~~

3.2.0 :004 > rails generate model movie title:string category:string
/Users/learnacademy/.rvm/gems/ruby-3.2.0/gems/irb-1.6.4/lib/irb/workspace.rb:113:in `eval': (irb):4: syntax error, unexpected label, expecting `do' or '{' or '(' (SyntaxError)                                 
...el movie title:string category:string        
...                      ^~~~~~~~~              
                                              
3.2.0 :005 > rails g model Movie title:string, category:string
(irb):5:in `<main>': undefined local variable or method `string' for main:Object (NameError)                                  
                                              
rails g model Movie title:string, category:string
                          ^^^^^^              
Did you mean?  String                         
3.2.0 :006 > rails g model Movie title:string, category:string
                                          
                                          
                                          
                                          
                                          
