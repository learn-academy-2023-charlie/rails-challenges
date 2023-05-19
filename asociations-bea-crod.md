5/19/23 Active Record Associations

Banking Challenge

Setup

Create a new rails application and database
Create a model for owner

An owner has a name and address, and can have multiple credit cards

Create a model for credit card

A credit card has a number, an expiration date, and an owner


#Challenges

##Create three owners and save them in the database
```
    Owner.create(name: 'CRod', address: 'Baltic Ave')
    Owner.create(name: 'Bea', address: 'Park Place')
    Owner.create(name: 'Suri', address: 'Boardwalk')
 ```
##Create a credit card in the database for each owner
```
    crod = Owner.first
    crod.credit_cards.create number:'123456789', expiration_date: '5/25'
    bea = Owner.second
    bea.credit_cards.create number:'987654321', expiration_date: '6/26'
    suri = Owner.third
    suri.credit_cards.create number:'5678943210', expiration_date: '6/27'

```
##Add two more credit cards to one of the owners
```
    crod.credit_cards.create number:'45678901234', expiration_date: '7/27'
    crod.credit_cards.create number:'23456789123', expiration_date: '4/26'
```

#Stretch Challenge

##Add a credit limit to each card
```
    rails g migration add_column_credit_limit_to_credit_card
    rails db:migrate
```

    Then in the AddColumnCreditLimitToCreditCard file add:
```
    add_column :credit_cards, :credit_limit, :integer

```
    Then in rails console set each card as a variable and updated the credit limit 
    example
```
    card2.update(credit_limit: 6000)

```
##Find the total credit extended to the owner with multiple credit cards
```