#Challenges

##Create three owners and save them in the database

    class CreditCard < ApplicationRecord
    belongs_to :owner
    end

    class Owner < ApplicationRecord
    has_many :credit_cards
    end


    Owner.create(name:"Surielis", address:"5724 Andros 
    Pl")

    Owner.create(name:"Yuehan", address:"2255 Newberry 
    Lane")

    Owner.create(name:"Oscar", address:"833 Grove Ave")


##Create a credit card in the database for each owner

    suri.credit_cards.create card_number:"1234567890", 
    exp_date:20250507, owner_id:1


    yuehan.credit_cards.create card_number:"6789054321"
    , exp_date:20270730, owner_id:2



    oscar.credit_cards.create card_number:"1234509876",
    exp_date:20300910, owner_id:3


##Add two more credit cards to one of the owners

    suri.credit_cards.create card_number:"902178436754"
    , exp_date:20281205, owner_id:1

    suri.credit_cards.create card_number:"8008509876", 
    exp_date:20230817, owner_id:1

#Stretch Challenge

Add a credit limit to each card

    surilimit.credit_limit=12500
    surisecond.credit_limit=10000
    surithird.credit_limit=17000

    oscarlimit.credit_limit=15000
    
    yuehanlimit.credit_limit=10000





