# Validations Challenges
Create a Rails application called company_contacts. The app will have a PostgreSQL database.
Generate a model called Account that has a username, a password, and an email.
All stories should have accompanying model specs.

## Developer Stories
As a developer, I need username, password, and email to be required.

Failed examples:
rspec ./spec/models/account_spec.rb:4 # Account is not valid without a username
rspec ./spec/models/account_spec.rb:8 # Account is not valid without a password
rspec ./spec/models/account_spec.rb:12 # Account is not valid without a email

As a developer, I need every username to be at least 5 characters long.

rspec ./spec/models/account_spec.rb:16 # Account is not valid if username has less than 5 characters

As a developer, I need each username to be unique.

rspec ./spec/models/account_spec.rb:20 # Account does not allow duplicate usernames

As a developer, I need each password to be at least 6 characters long.

rspec ./spec/models/account_spec.rb:25 # Account is not valid if password is less than 6 characters

As a developer, I need each password to be unique.

rspec ./spec/models/account_spec.rb:29 # Account does not allow duplicate passwords

As a developer, I want my Account model to have many associated Addresses.
As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers.
As a developer, I want to validate the presence of all fields on Address.

Failed examples:
rspec ./spec/models/address_spec.rb:4 # Address is not valid without a street number
rspec ./spec/models/address_spec.rb:8 # Address is not valid without a street name
rspec ./spec/models/address_spec.rb:12 # Address is not valid without a zip

## Stretch Challenges
### As a developer, I need each Account password to have at least one number.
HINT: Read about custom validations in the Active Record validation docs.

validates :password, presence:true, uniqueness:true, length:{minimum: 6}, with: /\d/

rspec ./spec/models/account_spec.rb:34 # Account does not allow passwords without at least one digit

### As a developer, I want to validate that Address street_number, street_name, zip are unique for within an account.
HINT: Read about :scope in the Active Record validation docs.
    - validates :street_name, presence:true, uniqueness:true
    - validates :street_number, presence:true, uniqueness:true
    - validates :zip, presence:true, uniqueness:true

### As a developer, I want to validate that the Address street_number and zip are numbers.
HINT: Read about numericality in the Active Record validation docs.
it 'is not valid if zip are not numbers' do
  jess = Address.create(street_name: 'Park Ave', street_number: 65432, zip: LOL12)
  expect(jess.error[:zip]).to_not be_empty
end

it 'is not valid if street numbers are not numbers' do
  jess = Address.create(street_name: 'Park Ave', street_number:LOL, zip: 90210)
  expect(jess.error[:street_number]).to_not be_empty
end

rspec ./spec/models/address_spec.rb:12 # Address is not valid if zip are not numbers
rspec ./spec/models/address_spec.rb:16 # Address is not valid if street numbers are not numbers

### As a developer, I want to see a custom error message that says "Please, input numbers only" if street_number or zip code are not numbers.
HINT: Read about message in the validation docs.
    validates :street_number, presence:true, uniqueness:true, numericality:true, message: "Please, input numbers only"
    validates :zip, presence:true, uniqueness:true, numericality:true, message: "Please, input numbers only"
