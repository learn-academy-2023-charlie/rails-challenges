1 example, 0 failures

learnacademy@MacBook-Air-5 company_contacts % rspec spec/models/account_spec.rb
.F

Failures:

  1) Account is not valid without a password
     Failure/Error: expect(will.errors[:password]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:12:in `block (2 levels) in <top (required)>'

Finished in 0.02598 seconds (files took 0.70714 seconds to load)
2 examples, 1 failure

Failed examples:

rspec ./spec/models/account_spec.rb:10 # Account is not valid without a password

learnacademy@MacBook-Air-5 company_contacts % rspec spec/models/account_spec.rb
..

Finished in 0.01934 seconds (files took 0.65928 seconds to load)
2 examples, 0 failures

learnacademy@MacBook-Air-5 company_contacts % rspec spec/models/account_spec.rb
..F

Failures:

  1) Account is not valid without a email
     Failure/Error: expect(will.errors[:email]).to_not be_empty
       expected `[].empty?` to be falsey, got true
     # ./spec/models/account_spec.rb:17:in `block (2 levels) in <top (required)>'

Finished in 0.02734 seconds (files took 0.53977 seconds to load)
3 examples, 1 failure

Failed examples:

rspec ./spec/models/account_spec.rb:15 # Account is not valid without a email

learnacademy@MacBook-Air-5 company_contacts % rspec spec/models/account_spec.rb
...

Finished in 0.02057 seconds (files took 0.54868 seconds to load)
3 examples, 0 failures