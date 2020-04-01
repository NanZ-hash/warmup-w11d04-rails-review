# Rails Review

For each of the following topics, please answer each of the questions. You can use links and images to support your answer. Once done please make a pull request.

## Has many Through

- [Rails Active Record Intro](https://github.com/sei-entropy/lesson-w11d02-rails-active-record#active-record-associations)
-[Hospital App](https://github.com/sei-entropy/hw-w11d02-rails-hospital)

### Questions

1. What is the role of a join table in a many-to-many relationship?

answer : 
It creates a set that can be saved as a table or used as it is. we can say I want to see how many courses the student has and who teaches them so I'll join the student with course table asking only for the instructor column


2. What two columns must be present in a join table?

answer : 
primary key and foreign  key 


3. Given the example below, edit the code to define a has many :through relationship.

    ```ruby
    class Customer < ActiveRecord::Base
        has_many  :purchases
    end

    class Product < ActiveRecord::Base
        belong_to :purchase
    end

    class Purchase < ActiveRecord::Base
        has_many  :products
    end
    ```


4. Based on #3, give an example of associating two instances via the join model.
    ----------------------------------------------------------------------
    | purchased |   coustomer_id   | coustomer_name  | Date_of_purchased |
    +-----------+------------------+-----------------+--------------------
    |  Books    |         34       |    Mark         |   2020-3-20       |
    +-----------+------------------+-----------------+--------------------
    |     pen   |         83       |    Sami         |   2020-4-1        |
    +-----------+------------------+-----------------+--------------------





## Devise

- [Devise Lesson](https://github.com/sei-entropy/lesson-w11d03-rails-devise)

### Questions

1. What does the `current_user` method that the Devise gem provides?

answer : 
For the current signed-in user, to add a welcome message 

2. What does the `authenticate_user!` method that the Devise gem provides?

answer : 
to set up user authentication model and helpers inside the controller. 

3. Write a signout link using the `link_to` rails helper and a devise path.

answer : 
<%= link_to 'Sign Out' , destroy_user_session_path , method: :delete %>

4. How do I generate a devise model in the terminal?

answer : 
rails generate devise MODEL   replace model with any model name 

5. What are the trade offs for using a gem for authentication over a handrolled solution? (no real right answer)

answer : more secure since a lot of People has worked on it for years and some of them maybe in the information security fields



## Validations

- [Validations Lesson](https://github.com/sei-entropy/lesson-w11d03-rails-model-validations)

### Questions

1. Which component, of Rails MVC, is responsible for the business logic?

answer : 
Model 

2. Assume the user's age is an optional field.  Write the validation to verify that a User's age is between 13 and 125 (inclusive).

answer : 
  validates :age { in: 13..125 }
3. What would `user.errors.messages` return (for the above User), if you assigned `user.age = 12`?

answer : 
"user are not allowed until they 13 or above "


4. Assume you visit "/customers/new" and enter some invalid information.  Given this controller code, what url would your browser be on after pressing "Create Customer"?

``` ruby
class CustomersController < ApplicationController
  def new
    @customer = Customer.new
  end

  def create
    @customer = Customer.new(customer_params)
    if @customer.save
      redirect_to customer_path(@customer)
    else
      render :new
    end
  end
  ...
  private
  def customer_params
    params.require(:customer).permit(:first_name, :last_name, :age)
  end
end
```


5. Give one reason why we might have the similar validations in the browser, model, and database layer of our application.


