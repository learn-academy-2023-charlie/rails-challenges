

Banking Challenge
Setup
Create a new rails application and database
Create a model for owner
An owner has a name and address, and can have multiple credit cards

3.2.0 :018 > Owner.all
  Owner Load (24.8ms)  SELECT "owners".* FROM "owners"
 =>                                                          
[#<Owner:0x00000001099e4440                                  
  id: 1,                                                     
  name: "Goku",                                              
  address: "Planet Namek",                                   
  created_at: Fri, 19 May 2023 17:42:06.610014000 UTC +00:00,
  updated_at: Fri, 19 May 2023 17:42:06.610014000 UTC +00:00>,
 #<Owner:0x00000001099e3fe0                                  
  id: 2,                                                     
  name: "Howl",                                              
  address: "Ingary",                                         
  created_at: Fri, 19 May 2023 17:43:07.442655000 UTC +00:00,
  updated_at: Fri, 19 May 2023 17:43:07.442655000 UTC +00:00>,
 #<Owner:0x00000001099e3f40                                  
  id: 3,
  name: "Myrtle",
  address: "2nd floor restroom",
  created_at: Fri, 19 May 2023 17:52:44.207274000 UTC +00:00,
  updated_at: Fri, 19 May 2023 17:52:44.207274000 UTC +00:00>] 



Create a model for credit card
A credit card has a number, an expiration date, and an owner
Challenges
Create three owners and save them in the database
Create a credit card in the database for each owner
Add two more credit cards to one of the owners

CreditCard Load (12.8ms)  SELECT "credit_cards".* FROM "credit_cards"
 =>                                                               
[#<CreditCard:0x000000010a92c6c8                                  
  id: 1,                                                          
  number: "4859837493849054",                                     
  expiration: Tue, 09 May 2023,                                   
  owner_id: 1,                                                    
  created_at: Fri, 19 May 2023 17:59:18.331507000 UTC +00:00,     
  updated_at: Fri, 19 May 2023 17:59:18.331507000 UTC +00:00>,    
 #<CreditCard:0x000000010a92c588                                  
  id: 2,                                                          
  number: "9364728976290192",                                     
  expiration: Tue, 22 Feb 2028,                                   
  owner_id: 2,                                                    
  created_at: Fri, 19 May 2023 18:02:31.766354000 UTC +00:00,     
  updated_at: Fri, 19 May 2023 18:02:31.766354000 UTC +00:00>,
 #<CreditCard:0x000000010a92c448
  id: 3,
  number: "9381628905478301",
  expiration: Tue, 01 Jan 2030,
  owner_id: 3,
  created_at: Fri, 19 May 2023 18:05:07.267369000 UTC +00:00,
  updated_at: Fri, 19 May 2023 18:05:07.267369000 UTC +00:00>,
 #<CreditCard:0x000000010a92c308
  id: 4,
  number: "0987654321098765",
  expiration: Sun, 04 Mar 2029,
  owner_id: 1,
  created_at: Fri, 19 May 2023 18:06:20.198100000 UTC +00:00,
  updated_at: Fri, 19 May 2023 18:06:20.198100000 UTC +00:00>] 

Stretch Challenge
Add a credit limit to each card



Find the total credit extended to the owner with multiple credit cards