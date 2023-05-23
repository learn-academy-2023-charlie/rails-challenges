<!-- Validations Challenges
Create a Rails application called company_contacts. The app will have a PostgreSQL database.
Generate a model called Account that has a username, a password, and an email.
All stories should have accompanying model specs. -->
<!-- setup -->
rails new validations -d postgresql -T
cd validations
rails db:create
bundle add rspec-rails
rails generate rspec:install
rails generate rspec:install

<!-- new model for Accounts -->
rails g model Account username:string password:string email:string  
rails db:migrate


<!-- Developer Stories

As a developer, I need username, password, and email to be required. -->

rspec spec/models/account_spec.rb
  <!-- 1) Account is not valid without a username, email, and password
     Failure/Error: expect(has_name.errors[:username]).to_not be_empty
       expected `[].empty?` to be falsey, got true -->

rspec spec/models/account_spec.rb
<!-- Finished in 0.09587 seconds (files took 3.09 seconds to load)
1 example, 0 failures -->

<!-- adjusted into 3 separate it statements, still failed appropriately -->
rspec spec/models/account_spec.rb
.FF

Failures:

  1) Account is not valid without a password
     Failure/Error: expect(has_name.errors[:password]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:11:in `block (2 levels) in <top (required)>'

  2) Account is not valid without a email
     Failure/Error: expect(has_name.errors[:email]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:16:in `block (2 levels) in <top (required)>'

rspec spec/models/account_spec.rb
...

Finished in 0.14193 seconds (files took 4.38 seconds to load)
3 examples, 0 failures

<!-- As a developer, I need every username to be at least 5 characters long. -->
<!-- As a developer, I need each password to be at least 6 characters long. -->

rspec spec/models/account_spec.rb
.F.F.

Failures:

  1) Account is not valid if username is less than 5 characters
     Failure/Error: expect(has_name.errors[:username]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:12:in `block (2 levels) in <top (required)>'

  2) Account is not valid if password less than 6 characters
     Failure/Error: expect(has_name.errors[:password]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:23:in `block (2 levels) in <top (required)>

rspec spec/models/account_spec.rb
.....

Finished in 0.15884 seconds (files took 3.96 seconds to load)
5 examples, 0 failures

<!-- As a developer, I need each username to be unique.
As a developer, I need each password to be unique. -->
1) Account does not allow duplicate usernames
     Failure/Error: expect(has_name.errors[:username]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:18:in `block (2 levels) in <top (required)>'

  2) Account does not allow duplicate passwords
     Failure/Error: expect(has_name.errors[:password]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:34:in `block (2 levels) in <top (required)>

rspec spec/models/account_spec.rb
.......

Finished in 0.34112 seconds (files took 5.22 seconds to load)
7 examples, 0 failures

<!-- As a developer, I want my Account model to have many associated Addresses. -->
<!-- As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers. -->

Account.all
  Account Load (0.4ms)  SELECT "accounts".* FROM "accounts"
 => 
[#<Account:0x0000000107700820
  id: 1,
  username: "meatball",
  password: "[FILTERED]",
  email: "pizzameats@toppings.com",
  created_at:
   Mon, 22 May 2023 22:28:50.618159000 UTC +00:00,
  updated_at:
   Mon, 22 May 2023 22:28:50.618159000 UTC +00:00>,
 #<Account:0x0000000107700780
  id: 2,
  username: "duckface123",
  password: "[FILTERED]",
  email: "jamespond@learn.org",
  created_at:
   Mon, 22 May 2023 22:31:19.110691000 UTC +00:00,
  updated_at:
   Mon, 22 May 2023 22:31:19.110691000 UTC +00:00>] 

Address.all
  Address Load (0.4ms)  SELECT "addresses".* FROM "addresses"
 => 
[#<Address:0x00000001086ac6c0
  id: 1,
  street_number: 390,
  street_name: "lilmarco",
  city: "Spaghetti Town",
  state: "confusion",
  zip: 83749,
  created_at:
   Mon, 22 May 2023 22:54:28.016606000 UTC +00:00,
  updated_at:
   Mon, 22 May 2023 22:54:28.016606000 UTC +00:00,
  account_id: 1>,
 #<Address:0x00000001086ac580
  id: 2,
  street_number: 39,
  street_name: nil,
  city: nil,
  state: nil,
  zip: nil,
  created_at:
   Mon, 22 May 2023 22:55:29.173101000 UTC +00:00,
  updated_at:
   Mon, 22 May 2023 22:55:29.173101000 UTC +00:00,
  account_id: 2>,
 #<Address:0x00000001086ac440
  id: 3,
  street_number: 98475,
  street_name: "wouldn'tyou",
  city: "like",
  state: "taknow",
  zip: 98375,
  created_at:
   Mon, 22 May 2023 22:57:51.022443000 UTC +00:00,
  updated_at:
   Mon, 22 May 2023 22:57:51.022443000 UTC +00:00,
  account_id: 2>] 

<!-- As a developer, I want to validate the presence of all fields on Address. -->
Failures:

  1) Address is not valid without a street_number
     Failure/Error: valid_address = street_name:'calle', city:'thisone', state:'here', zip: '29837', account_id: '1'
     
     NoMethodError:
       undefined method `street_name' for #<RSpec::ExampleGroups::Address "is not valid without a street_number" (./spec/models/address_spec.rb:4)>
     # ./spec/models/address_spec.rb:5:in `block (2 levels) in <top (required)>'

  2) Address is not valid without a street_name
     Failure/Error: valid_address = street_number:'348762', city:'thisone', state:'here', zip: '29837', account_id: '1'
     
     NoMethodError:
       undefined method `street_number' for #<RSpec::ExampleGroups::Address "is not valid without a street_name" (./spec/models/address_spec.rb:9)>
     # ./spec/models/address_spec.rb:10:in `block (2 levels) in <top (required)>'

  3) Address is not valid without a city
     Failure/Error: valid_address = street_name:'calle', street_number:'98374', state:'here', zip: '29837', account_id: '1'
     
     NoMethodError:
       undefined method `street_name' for #<RSpec::ExampleGroups::Address "is not valid without a city" (./spec/models/address_spec.rb:14)>
     # ./spec/models/address_spec.rb:15:in `block (2 levels) in <top (required)>'

  4) Address is not valid without a state
     Failure/Error: valid_address = street_name:'calle', city:'thisone', street_number:'3284', zip: '29837', account_id: '1'
     
     NoMethodError:
       undefined method `street_name' for #<RSpec::ExampleGroups::Address "is not valid without a state" (./spec/models/address_spec.rb:19)>
     # ./spec/models/address_spec.rb:20:in `block (2 levels) in <top (required)>'

  5) Address is not valid without a zip
     Failure/Error: valid_address = street_name:'calle', city:'thisone', state:'here', street_number: '29837', account_id: '1'
     
     NoMethodError:
       undefined method `street_name' for #<RSpec::ExampleGroups::Address "is not valid without a zip" (./spec/models/address_spec.rb:24)>
     # ./spec/models/address_spec.rb:25:in `block (2 levels) in <top (required)>'

  6) Address is not valid without a account_id
     Failure/Error: valid_address = street_name:'calle', city:'thisone', state:'here', zip: '29837', street_number:'93842'
     
     NoMethodError:
       undefined method `street_name' for #<RSpec::ExampleGroups::Address "is not valid without a account_id" (./spec/models/address_spec.rb:29)>
     # ./spec/models/address_spec.rb:30:in `block (2 levels) in <top (required)>'

Finished in 0.07229 seconds (files took 2.73 seconds to load)
6 examples, 6 failures



Stretch Challenges

<!-- As a developer, I need each Account password to have at least one number.
HINT: Read about custom validations in the Active Record validation docs. -->
<!-- As a developer, I want to validate that Address street_number, street_name, zip are unique for within an account.
HINT: Read about :scope in the Active Record validation docs. -->
<!-- As a developer, I want to validate that the Address street_number and zip are numbers.
HINT: Read about numericality in the Active Record validation docs. -->
<!-- As a developer, I want to see a custom error message that says "Please, input numbers only" if street_number or zip code are not numbers.
HINT: Read about message in the validation docs. -->


Password requirements stretch goal: symbols, etc.