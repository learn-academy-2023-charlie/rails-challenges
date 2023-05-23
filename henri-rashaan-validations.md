* ...
<!-- Validations Challenges
Create a Rails application called company_contacts. The app will have a PostgreSQL database.
Generate a model called Account that has a username, a password, and an email. ✅
All stories should have accompanying model specs.
Developer Stories
As a developer, I need username, password, and email to be required.✅
As a developer, I need every username to be at least 5 characters long.✅
As a developer, I need each username to be unique.✅
As a developer, I need each password to be at least 6 characters long.✅
As a developer, I need each password to be unique.✅
As a developer, I want my Account model to have many associated Addresses.✅
As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers.✅
As a developer, I want to validate the presence of all fields on Address.✅

Stretch Challenges - TBD

As a developer, I need each Account password to have at least one number.
HINT: Read about custom validations in the Active Record validation docs.
As a developer, I want to validate that Address street_number, street_name, zip are unique for within an account.
HINT: Read about :scope in the Active Record validation docs.
As a developer, I want to validate that the Address street_number and zip are numbers.
HINT: Read about numericality in the Active Record validation docs.
As a developer, I want to see a custom error message that says "Please, input numbers only" if street_number or zip code are not numbers.
HINT: Read about message in the validation docs. -->

# README
## schema.rb
ActiveRecord::Schema[7.0].define(version: 2023_05_22_224741) do
  # These are extensions that must be enabled in order to support this database
  enable_extension "plpgsql"

  create_table "accounts", force: :cascade do |t|
    t.text "username"
    t.text "password"
    t.text "email"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.integer "account_id"
  end

  create_table "addresses", force: :cascade do |t|
    t.integer "street_num"
    t.string "street_name"
    t.string "city"
    t.string "state"
    t.integer "zip_code"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.integer "account_id"
  end

end

## app/models/account.rb

class Account < ApplicationRecord
    validates :username, :password, :email, presence:true
    validates :username, length: {minimum: 5}
    validates_uniqueness_of :username
    validates :password, length: {minimum: 6}
    validates_uniqueness_of :password
    has_many :addresses
end

## spec/models/account_spec.rb
require 'rails_helper'

RSpec.describe Account, type: :model do
  it 'is not valid without a username' do 
    user1 = Account.create(password:'henri3', email:'henri@gmail.com', account_id: 4)
    # p "basic username", user1
    expect(user1.errors[:username]).to_not be_empty
  end
  it 'is not valid without a password' do 
    user1 = Account.create(username: 'henrike', email:'henri@gmail.com',account_id: 4)
    expect(user1.errors[:password]).to_not be_empty
  end
  it 'is not valid without a email' do 
    user1 = Account.create(username: 'henrike', password:'henri3', account_id: 4)
    # p "basic username", user1
    expect(user1.errors[:email]).to_not be_empty
  end
end

## app/models/address.rb

class Address < ApplicationRecord
 validates :street_num, :street_name , :city, :state, :zip_code, presence:true
 belongs_to :account
end

## spec/models/address_spec.rb

require 'rails_helper'

RSpec.describe Address, type: :model do
  it 'is not valid without a username' do 
    address1 = Address.create(street_name:'onetwo', city:'san diego', state: 'cali', zip_code: 384738472, account_id: 4)
    expect(address1.errors[:street_num]).to_not be_empty
  end
  it 'is not valid without a street name' do 
    address1 = Address.create(street_num: 325, city:'san diego', state: 'cali', zip_code: 384738472, account_id: 4)
    expect(address1.errors[:street_name]).to_not be_empty
  end
  it 'is not valid without a city' do 
    address1 = Address.create(street_num: 325 , street_name:'onetwo', state: 'cali', zip_code: 384738472, account_id: 4)
    expect(address1.errors[:city]).to_not be_empty
  end
  it 'is not valid without a state' do 
    address1 = Address.create(street_num: 325 , street_name:'onetwo', zip_code: 384738472, account_id: 4)
    expect(address1.errors[:state]).to_not be_empty
  end
  it 'is not valid without a zip code' do 
    address1 = Address.create(street_num: 325 , street_name:'onetwo', state: 'cali', account_id: 4)
    expect(address1.errors[:zip_code]).to_not be_empty
  end
end




