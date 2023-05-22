Banking Challenge
Setup
Create a new rails application and database
Create a model for owner
An owner has a name and address, and can have multiple credit cards
Create a model for credit card
A credit card has a number, an expiration date, and an owner
Challenges
Create three owners and save them in the database
Create a credit card in the database for each owner
Add two more credit cards to one of the owners
Stretch Challenge
Add a credit limit to each card
Find the total credit extended to the owner with multiple credit cards


Loading development environment (Rails 7.0.4.3)
3.2.0 :001 > Owner.all
  Owner Load (0.4ms)  SELECT "owners".* FROM "owners"
 =>                                                          
[#<Owner:0x0000000107f1fc40                                  
  id: 1,                                                     
  name: "Scott",                                             
  address: "1234 Learn Dr. Sand Diego, CA 92123",            
  created_at: Fri, 19 May 2023 17:34:49.537425000 UTC +00:00,
  updated_at: Fri, 19 May 2023 17:34:49.537425000 UTC +00:00>,
 #<Owner:0x00000001082f0ab8                                  
  id: 2,                                                     
  name: "Jessica",                                           
  address: "2234 Learn Dr. Sand Diego, CA 92123",            
  created_at: Fri, 19 May 2023 17:35:31.538256000 UTC +00:00,
  updated_at: Fri, 19 May 2023 17:35:31.538256000 UTC +00:00>,
 #<Owner:0x00000001082f0a18                                  
  id: 3,
  name: "Charlean",
  address: "3234 Learn Dr. San Diego, CA 92123",
  created_at: Fri, 19 May 2023 17:36:10.759871000 UTC +00:00,
  updated_at: Fri, 19 May 2023 17:36:10.759871000 UTC +00:00>] 

  3.2.0 :003 > scott = Owner.find 1
  Owner Load (0.2ms)  SELECT "owners".* FROM "owners" WHERE "owners"."id" = $1 LIMIT $2  [["id", 1], ["LIMIT", 1]]                                              
 =>                                                                  
#<Owner:0x00000001082b5f08                                           
...                                                                  
3.2.0 :004 > scott.credit_cards.create number: "1111-2222-3333-4444"
/usr/local/rvm/gems/ruby-3.2.0/gems/activemodel-7.0.4.3/lib/active_model/attribute_assignment.rb:51:in `_assign_attribute': unknown attribute 'owner_id' for CreditCard. (ActiveModel::UnknownAttributeError)                                              
                                                                     
          raise UnknownAttributeError.new(self, k.to_s)              
          ^^^^^                                                      
3.2.0 :005 > exit
➜  banking_challenge git:(main) ✗ rails generate migration owner_column_modify     
      invoke  active_record
      create    db/migrate/20230519180319_owner_column_modify.rb
➜  banking_challenge git:(main) ✗ rails db:migrate
== 20230519180319 OwnerColumnModify: migrating ================================
== 20230519180319 OwnerColumnModify: migrated (0.0000s) =======================

➜  banking_challenge git:(main) ✗ rails db:migrate                        
➜  banking_challenge git:(main) ✗ rails db:drop
PG::ObjectInUse: ERROR:  database "banking_challenge_development" is being accessed by other users

    AFTER THIS => All of our information was lost in the Owner model database.
    Output was an empty array when we ran Owner.all

