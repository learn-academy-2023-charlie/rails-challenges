# Validations Challenges
Create a Rails application called company_contacts. The app will have a PostgreSQL database.✅
-   $ rails new company_contacts -d postgreql -T

Generate a model called Account that has a username, a password, and an email.✅
-   $ rails g model Account user_name:string email:string password:string
All stories should have accompanying model specs.

# Developer Stories

As a developer, I need username, password, and email to be required.✅
-   account.rb 
    *   validates :user_name, :password, :email, presence: true, 
    
-   account_spec.rb
    *   RSpec.describe Account, type: :model do
  it 'is not valid without a username' do
    yuehan123 = Account.create password: '12345', email: 'yuehan@gmail.com'
    expect(yuehan123.errors[:user_name]).to_not be_empty
  end
  it 'is not valid without a password' do
    yuehan123 = Account.create user_name: 'yuehan', email: 'yuehan@gmail.com'
    expect(yuehan123.errors[:password]).to_not be_empty
  end
  it 'is not valid without a email' do
    yuehan123 = Account.create password: '12345', user_name: 'yuehan'
    expect(yuehan123.errors[:email]).to_not be_empty
  end
end

As a developer, I need every username to be at least 5 characters long.✅
-   account.rb
    *   validates :user_name, length: { minimum: 5 }

-   account_spec.rb
    *   it 'is not valid if username is atleast 5 characters long' do
        yuehan123 = Account.create password: '12345', email: 'yuehan@gmail.com', user_name: 'yue'
        expect(yuehan123.errors[:user_name]).to_not be_empty
        end

As a developer, I need each username to be unique.✅
-   account.rb
    *   validates :user_name, uniqueness: true
 
-   account_spec.rb
    *    it 'username is taken' do
        Account.create(user_name: 'yuehan', email: 'yuehan@gmail.com', password: '1234567')
        yuehan123 = Account.create(user_name: 'yuehan', email: 'yuehan@gmail.com', password: '1234567')
        expect(yuehan123.errors[:user_name]).to_not be_empty
        end

As a developer, I need each password to be at least 6 characters long.✅
-   account.rb
    *   validates :password, length: { minimum: 6 }

-   account_spec.rb
    *   it 'is not a valid password if less than 6 characters long' do
        yuehan123 = Account.create user_name: 'yuehan', email: 'yuehan@gmail.com', password: '12345'
        expect(yuehan123.errors[:password]).to_not be_empty
        end

As a developer, I need each password to be unique.
As a developer, I want my Account model to have many associated Addresses.
As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers.
As a developer, I want to validate the presence of all fields on Address.

# Stretch Challenges

As a developer, I need each Account password to have at least one number.
HINT: Read about custom validations in the Active Record validation docs.
As a developer, I want to validate that Address street_number, street_name, zip are unique for within an account.
HINT: Read about :scope in the Active Record validation docs.
As a developer, I want to validate that the Address street_number and zip are numbers.
HINT: Read about numericality in the Active Record validation docs.
As a developer, I want to see a custom error message that says "Please, input numbers only" if street_number or zip code are not numbers.
HINT: Read about message in the validation docs.

account.rb 
class Account < ApplicationRecord
    validates :user_name, :password, :email, presence: true
    validates :user_name, length: { minimum: 5 }
    validates :user_name, uniqueness: true
    validates :password, length: { minimum: 6 }

end

account_spec.rb
require 'rails_helper'

RSpec.describe Account, type: :model do
  it 'is not valid without a username' do
    yuehan123 = Account.create password: '12345', email: 'yuehan@gmail.com'
    expect(yuehan123.errors[:user_name]).to_not be_empty
  end
  it 'is not a valid if username is atleast 5 characters long' do
    yuehan123 = Account.create password: '12345', email: 'yuehan@gmail.com', user_name: 'yue'
    expect(yuehan123.errors[:user_name]).to_not be_empty
  end
  it 'username is taken' do
    Account.create(user_name: 'yuehan', email: 'yuehan@gmail.com', password: '1234567')
    yuehan123 = Account.create(user_name: 'yuehan', email: 'yuehan@gmail.com', password: '1234567')
    expect(yuehan123.errors[:user_name]).to_not be_empty
  end
  it 'is not valid without a password' do
    yuehan123 = Account.create user_name: 'yuehan', email: 'yuehan@gmail.com'
    expect(yuehan123.errors[:password]).to_not be_empty
  end
  it 'is not a valid password if less than 6 characters long' do
    yuehan123 = Account.create user_name: 'yuehan', email: 'yuehan@gmail.com', password: '12345'
    expect(yuehan123.errors[:password]).to_not be_empty
  end
  it 'is not valid without a email' do
    yuehan123 = Account.create password: '12345', user_name: 'yuehan'
    expect(yuehan123.errors[:email]).to_not be_empty
  end
end
