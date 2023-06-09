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

In terminal
```
    rails g migration add_column_credit_limit_to_credit_card
    
```

Then in the AddColumnCreditLimitToCreditCard.rb file  on Vscode add:
```
    add_column :credit_cards, :credit_limit, :integer

```
Then back in terminal 
```
    rails db:migrate
    rails c
```    
Then in rails console set each card as a variable and update the credit limit for the card using the variable.
example as follows:
```
    card2.update(credit_limit: 6000)

```
##Find the total credit extended to the owner with multiple credit cards
```
    crod_cc = crod.credit_cards <--set a variable to see all credit cards one person has.
```
Then enter the following command in rails console. 
```
    crod_cc.sum(:credit_limit)
```
Output will be the total of the credit_limit values 
    //output: 26000

   