# Challenge: Rolodex

### Add five family members into the Person table in the Rails console.

#<Person:0x0000000111731f10
id: 1,                                                                         
 first_name: "Bea",                                                             
 last_name: "Elvira",                                                           
 phone: "561999999999",                                                         
 created_at: Thu, 18 May 2023 17:52:32.325379000 UTC +00:00,                    
 updated_at: Thu, 18 May 2023 17:52:32.325379000 UTC +00:00> 

#<Person:0x0000000113317450
id: 2,                                                                         
 first_name: "Kyle",                                                            
 last_name: "Lohman",                                                           
 phone: "123456789",                                                            
 created_at: Thu, 18 May 2023 17:53:46.446607000 UTC +00:00,                    
 updated_at: Thu, 18 May 2023 17:53:46.446607000 UTC +00:00>  

#<Person:0x000000011683c450   
 id: 3,                                                                         
 first_name: "Beyonce",                                                         
 last_name: "Knowles-Carter",                                                   
 phone: "9990001234",                                                           
 created_at: Thu, 18 May 2023 17:57:46.873450000 UTC +00:00,                    
 updated_at: Thu, 18 May 2023 17:57:46.873450000 UTC +00:00> 

#<Person:0x00000001139fca90  
id: 4,                                                                          
 first_name: "Megan",                                                            
 last_name: "Thee Stallion",                                                     
 phone: "3019874321",                                                            
 created_at: Thu, 18 May 2023 17:58:45.324482000 UTC +00:00,                     
 updated_at: Thu, 18 May 2023 17:58:45.324482000 UTC +00:00>

#<Person:0x000000011681f288                                                      
 id: 5,                                                                          
 first_name: "Ice",                                                              
 last_name: "Spice",                                                             
 phone: "8773124567",                                                            
 created_at: Thu, 18 May 2023 17:59:32.899746000 UTC +00:00,                     
 updated_at: Thu, 18 May 2023 17:59:32.899746000 UTC +00:00>        

### Retrieve all the items in the database.
Person.all
  Person Load (1.0ms)  SELECT "people".* FROM "people"
 =>                                                           
[#<Person:0x00000001168dbf50                                  
  id: 1,                                                      
  first_name: "Bea",                                          
  last_name: "Elvira",                                        
  phone: "561999999999",                                      
  created_at: Thu, 18 May 2023 17:52:32.325379000 UTC +00:00, 
  updated_at: Thu, 18 May 2023 17:52:32.325379000 UTC +00:00>,
 #<Person:0x00000001168dbe10                                  
  id: 2,                                                      
  first_name: "Kyle",                                         
  last_name: "Lohman",                                        
  phone: "123456789",                                         
  created_at: Thu, 18 May 2023 17:53:46.446607000 UTC +00:00, 
  updated_at: Thu, 18 May 2023 17:53:46.446607000 UTC +00:00>,
 #<Person:0x00000001168dbcd0
  id: 3,
  first_name: "Beyonce",
  last_name: "Knowles-Carter",
  phone: "9990001234",
  created_at: Thu, 18 May 2023 17:57:46.873450000 UTC +00:00,
  updated_at: Thu, 18 May 2023 17:57:46.873450000 UTC +00:00>,
 #<Person:0x00000001168dbb90
  id: 4,
  first_name: "Megan",
  last_name: "Thee Stallion",
  phone: "3019874321",
  created_at: Thu, 18 May 2023 17:58:45.324482000 UTC +00:00,
  updated_at: Thu, 18 May 2023 17:58:45.324482000 UTC +00:00>,
 #<Person:0x00000001168dba50
  id: 5,
  first_name: "Ice",
  last_name: "Spice",
  phone: "8773124567",
  created_at: Thu, 18 May 2023 17:59:32.899746000 UTC +00:00,
  updated_at: Thu, 18 May 2023 17:59:32.899746000 UTC +00:00>] 
  #<Person:0x0000000104ef1e10                                                      
 id: 6,                                                                          
 first_name: "Jon",                                                              
 last_name: "Elvira",                                                            
 phone: "5613219876",                                                            
 created_at: Thu, 18 May 2023 18:02:20.925718000 UTC +00:00,                     
 updated_at: Thu, 18 May 2023 18:02:20.925718000 UTC +00:00> 

### Retrieve all the entries that have the same last_name as you.
Person.where last_name: "Elvira"
  Person Load (0.3ms)  SELECT "people".* FROM "people" WHERE "people"."last_name" = $1  [["last_name", "Elvira"]] 

### Update the phone number of the last entry in the database.
Person Load (0.6ms)  SELECT "people".* FROM "people" WHERE "people"."id" = $1 LIMIT $2  [["id", 6], ["LIMIT", 1]]                                   
 =>                                                                  
#<Person:0x00000001168d6a50   
jon.phone = 5613449876
 => 5613449876 
3.2.0 :014 > jon.save
  TRANSACTION (0.2ms)  BEGIN
  Person Update (2.4ms)  UPDATE "people" SET "phone" = $1, "updated_at" = $2 WHERE "people"."id" = $3  [["phone", "5613449876"], ["updated_at", "2023-05-18 18:07:08.097345"], ["id", 6]]                                             
  TRANSACTION (0.4ms)  COMMIT                                       
 => true                                     

### Retrieve the first_name of the third Person in the database.
Person.find 3
Person Load (0.4ms)  SELECT "people".* FROM "people" WHERE "people"."id" = $1 LIMIT $2  [["id", 3], ["LIMIT", 1]]                            
 =>                                                           
#<Person:0x00000001168d6cd0                                   
 id: 3,                                                       
 first_name: "Beyonce",        

### Stretch Challenges

### Update all the family members with the same last_name as you, to have the same phone number as you.
elvira.update phone: "5617951489"
  TRANSACTION (0.4ms)  BEGIN
  Person Update (0.7ms)  UPDATE "people" SET "phone" = $1, "updated_at" = $2 WHERE "people"."id" = $3  [["phone", "5617951489"], ["updated_at", "2023-05-18 18:29:02.787545"], ["id", 1]]
  TRANSACTION (0.5ms)  COMMIT                              
  TRANSACTION (0.1ms)  BEGIN                               
  Person Update (0.2ms)  UPDATE "people" SET "phone" = $1, "updated_at" = $2 WHERE "people"."id" = $3  [["phone", "5617951489"], ["updated_at", "2023-05-18 18:29:02.792641"], ["id", 6]]
  TRANSACTION (0.2ms)  COMMIT                              
 =>                                                        
[#<Person:0x000000011685e398                               
  id: 1,                                                   
  first_name: "Bea",                                       
  last_name: "Elvira",                                     
  phone: "5617951489",                                     
  created_at: Thu, 18 May 2023 17:52:32.325379000 UTC +00:00,
  updated_at: Thu, 18 May 2023 18:29:02.787545000 UTC +00:00>,
 #<Person:0x000000011685e258
  id: 6,
  first_name: "Jon",
  last_name: "Elvira",
  phone: "5617951489",
  created_at: Thu, 18 May 2023 18:02:20.925718000 UTC +00:00,
  updated_at: Thu, 18 May 2023 18:29:02.792641000 UTC +00:00>]

### Remove all family members that do not have your last_name.
everyone = [2,3,4,5]
 => [2, 3, 4, 5] 
3.2.0 :039 > Person.destroy(everyone)
  Person Load (2.1ms)  SELECT "people".* FROM "people" WHERE "people"."id" IN ($1, $2, $3, $4)  [["id", 2], ["id", 3], ["id", 4], ["id", 5]]                             
  TRANSACTION (0.1ms)  BEGIN                                             
  Person Destroy (0.3ms)  DELETE FROM "people" WHERE "people"."id" = $1  [["id", 2]]
  TRANSACTION (0.4ms)  COMMIT                                            
  TRANSACTION (0.1ms)  BEGIN                                             
  Person Destroy (0.2ms)  DELETE FROM "people" WHERE "people"."id" = $1  [["id", 3]]
  TRANSACTION (0.2ms)  COMMIT                                            
  TRANSACTION (0.1ms)  BEGIN                                             
  Person Destroy (0.2ms)  DELETE FROM "people" WHERE "people"."id" = $1  [["id", 4]]
  TRANSACTION (0.1ms)  COMMIT                                            
  TRANSACTION (0.1ms)  BEGIN                                             
  Person Destroy (0.3ms)  DELETE FROM "people" WHERE "people"."id" = $1  [["id", 5]]
  TRANSACTION (0.1ms)  COMMIT                          