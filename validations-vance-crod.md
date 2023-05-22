Validations Challenges
Create a Rails application called company_contacts. The app will have a PostgreSQL database.
Generate a model called Account that has a username, a password, and an email.
All stories should have accompanying model specs.
Developer Stories

As a developer, I need username, password, and email to be required.

1) Account is not valid without a user_name
     Failure/Error: expect(halie.errors[:user_name]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:6:in `block (2 levels) in <top (required)>'

  2) Account is not valid without a password
     Failure/Error: expect(ramgel.errors[:password]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:11:in `block (2 levels) in <top (required)>'

  3) Account is not valid without a email
     Failure/Error: expect(vance.errors[:email]).to_not be_empty
       expected `[].empty?` to be falsey, got true

As a developer, I need every username to be at least 5 characters long.



As a developer, I need each username to be unique.
As a developer, I need each password to be at least 6 characters long.
As a developer, I need each password to be unique.
As a developer, I want my Account model to have many associated Addresses.
As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers.
As a developer, I want to validate the presence of all fields on Address.

require 'rails_helper'

RSpec.describe Address, type: :model do
  it 'is not valid without a street_number' do
    ramgel = Address.create street_name: 'bogo', city: 'racoon', state: 'CA', zip: 12345
    expect(ramgel.errors[:street_number]).to_not be_empty
  end

  it 'is not valid without a street_name' do
    ramgel = Address.create street_number: 8574, city: 'racoon', state: 'CA', zip: 12345
    expect(ramgel.errors[:street_name]).to_not be_empty
  end

  it 'is not valid without a city' do
    ramgel = Address.create street_name: 'bogo', street_number: 8574, state: 'CA', zip: 12345
    expect(ramgel.errors[:city]).to_not be_empty
  end

  it 'is not valid without a state' do
    ramgel = Address.create street_name: 'bogo', city: 'racoon', street_number: 8574, zip: 12345
    expect(ramgel.errors[:state]).to_not be_empty
  end

  it 'is not valid without a zip' do
    ramgel = Address.create street_name: 'bogo', city: 'racoon', state: 'CA', street_number: 8574
    expect(ramgel.errors[:zip]).to_not be_empty
  end
end

annnddddddd.......

class Address < ApplicationRecord
    belongs_to :account
    validates :street_number, :street_name, :city, :state, :zip, presence: true
end

Stretch Challenges

As a developer, I need each Account password to have at least one number.
HINT: Read about custom validations in the Active Record validation docs.
As a developer, I want to validate that Address street_number, street_name, zip are unique for within an account.
HINT: Read about :scope in the Active Record validation docs.
As a developer, I want to validate that the Address street_number and zip are numbers.
HINT: Read about numericality in the Active Record validation docs.
As a developer, I want to see a custom error message that says "Please, input numbers only" if street_number or zip code are not numbers.
HINT: Read about message in the validation docs.
