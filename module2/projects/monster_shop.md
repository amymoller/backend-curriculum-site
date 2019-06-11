# Solo Project - Tiny Shop

## Learning Goals
### Rails
* Implement CRUD functionality for a resource using forms (form_tag or form_for), buttons, and links
* Use MVC to organize code effectively, limiting the amount of logic included in views and controllers
* Create routes for
  * standalone resources
  * nested resources
* Template a view in Rails using a templating language (eg, `erb`)
* Implement CRUD functionality for nested resources


### ActiveRecord
* Create instance methods on a Rails model that use ActiveRecord associations
* Use built-in ActiveRecord methods to:
  * create, read, update, and destroy records in a database
  * create records with relationships to other records in a database

### Databases
* Describe Database Relationships, including the following terms:
  * Primary Key
  * Foreign Key
  * One to Many
* Write migrations to create tables and relationships between tables
* Describe ORMs and their advantages and use cases

### Testing and Debugging
* Write feature tests utilizing:
  * RSpec and Capybara
  * CSS selectors to target specific areas of a page
* Use Pry or Byebug in Rails files to get more information about an error
* Use `save_and_open_page` to view the HTML generated when visiting a path in a feature test
* Utilize the Rails console as a tool to get more information about the current state of a development database
* Use `rails routes` to get additional information about the routes that exist in a Rails application

### Styling
* Create basic Web Pages using the following tags
  * `<h1>`, `<h2>`, etc.
  * `<p>`
  * `<body>`
  * `<a>` and the `href` attribute
  * `<img>` and the `src` attribute
  * `<div>`
  * `<section>`
  * `<ul>`, `<ol>`, and `<li>`
  * `<form>`
  * `<input>`
* Select HTML elements using classes and ids

### Web Applications
* Describe the HTTP request/response cycle
* Describe the different parts of HTTP requests and responses


## Tables and Relationships
* Merchants
  * have many items
  * Attributes
    * name
    * Address
    * City
    * State
    * Zip

* Items
  * belong to merchants
  * Attributes
    * name
    * active?
    * price
    * description
    * image
    * inventory
    * merchant_id


## High Level Tasks
* Merchant Index, Show
  * Instance methods using relationships
  * ex: number of items per merchant
* Item Index, Show
  * Instance methods using relationships
  * ex: merchant that sells the item
* CRUD Merchant
* CRUD Item (nested under a merchant)


## Rubric Notes
* Make `within` a requirement


------------------


# Paired Project

## Learning Goals
### Rails
* Use path helpers
* Describe use cases for a model that inherits from ApplicationRecord vs. a PORO
* Make use of flash messages
* Use Inheritance from ApplicationController or a student created controller to store methods that will be used in multiple controllers
* Use POROs to logically organize code for objects not stored in the database


### ActiveRecord
* Use built-in ActiveRecord methods to:
  * create queries that calculate, select, filter, and order data from a single table


### Databases
* Describe Database Relationships, including the following terms:
  * Many to Many
  * Join Table

### Testing and Debugging
* Write feature tests utilizing
  * Sad Path Testing
* Write model tests with RSpec including validations, and class and instance methods

### Web Applications
* Explain how Cookies/Sessions are used to create and maintain application state
* Describe and implement ReSTful routing
* Identify use cases for, and implement non-ReSTful routes
* Identify the different components of URLs(protocol, domain, path, query params)

## Tables and Relationships
* Existing: Merchant, Item
  * item has many order items
  * item has many orders
  * item has many reviews
* Orders
  * has many order items
  * has many items
  * attributes
  * name (of the person who made the order)
  * address
  * city
  * state
  * zip
* OrderItems
  * belongs to item
  * belongs to order
  * price (price of item at time of order)
  * quantity
* Reviews
  * belongs to item
  * title
  * description
  * rating


## High Level Tasks
* Use POROs/sessions to create a cart
  * visitor can add items to their cart
  * v can add/reduce number of specific item in cart
  * v can clear cart
  * cart should be visible on all pages
* Allow visitor to create an order by checking out
* Order show page
  * including subtotals, grand total, ship to address, and merchant
* CRUD reviews (nested under an item) (recommend pairing to review this concept)
  * using flashes to indicate to user when something went wrong
* Update Merchant/Item CRUD for sad-path (flash messaging)
* Single Table Statistics
  * Add to existing pages
* Extension - Order UD with verification code
  * visitor would get verification code upon creation of the order, would need to use that code to update or delete the order later.

## User Stories

### Navigation

```
[ ] User Story

As a visitor
With the exception of an item's show page,
Anywhere I see an item name on the site,
I can click on the item name to go to that item's show page.
```

```
[ ] User Story

As a visitor
With the exception of an merchant's show page,
Anywhere I see an merchant name on the site,
I can click on the merchant name to go to that merchant's show page.
```

### Cart & Order

```
[ ] User Story

As a visitor
I see a cart indicator in my navigation bar
The cart indicator shows a count of items in my cart
I can see this cart indicator from any page in the application
```

```
[ ] User Story

As a visitor
When I visit an item's show page from the items index
I see a link or button to add this item to my cart
And I click this link or button
I am returned to the item index page
I see a flash message indicating the item has been added to my cart
The cart indicator in the navigation bar increments my cart count
```

```
[ ] User Story

As a visitor
When I have added items to my cart
And I visit my cart ("/cart")
I see all items I've added to my cart
And I see a link to empty my cart
Each item in my cart shows the following information:
  - the name of the item
  - a very small thumbnail image of the item
  - the merchant I'm buying this item from
  - the price of the item
  - my desired quantity of the item
  - a subtotal (price multiplied by quantity)

I also see a grand total of what everything in my cart will cost
```

```
[ ] User Story

As a visitor
When I add NO items to my cart yet
And I visit my cart ("/cart")
I see a message that my cart is empty
I do NOT see the link to empty my cart
```

```
[ ] User Story

As a visitor
When I have items in my cart
And I visit my cart ("/cart")
And I click the link to empty my cart
Then I am returned to my cart
All items have been completely removed from my cart
The navigation bar shows 0 items in my cart
```

```
[ ] User Story

As a visitor
When I have items in my cart
And I visit my cart
Next to each item in my cart
I see a button or link to remove that item from my cart
- clicking this button will remove the item but not other items
```

```
[ ] User Story

As a visitor
When I have items in my cart
And I visit my cart
Next to each item in my cart
I see a button or link to increment the count of items I want to purchase
I cannot increment the count beyond the merchant's inventory size
```

```
[ ] User Story

As a visitor
When I have items in my cart
And I visit my cart
Next to each item in my cart
I see a button or link to decrement the count of items I want to purchase
If I decrement the count to 0 the item is immediately removed from my cart
```

```
[ ] User Story

As a visitor
When I have items in my cart
And I visit my cart
I see a button or link to Checkout
When I click that button, I am taken to an order creation page
```

```
[ ] User Story

As a visitor
When I check out from my cart
On the order creation page I see the details of my cart:
  - the name of the item
  - the merchant I'm buying this item from
  - the price of the item
  - my desired quantity of the item
  - a subtotal (price multiplied by quantity)
  - a grand total of what everything in my cart will cost
I also see a form to enter my information for the order:
  - name
  - address
  - city
  - state
  - zip
I also see a button to 'Create Order'
```

```
[ ] User Story

As a visitor
When I fill out all information on the order creation page
And click on 'Create Order'
An order is created and saved in the database
And I am redirected to that order's show page with the following information:
  - My name and address (shipping information)
  - Details of the order:
    - the name of the item
    - the merchant I'm buying this item from
    - the price of the item
    - my desired quantity of the item
    - a subtotal (price multiplied by quantity)
    - a grand total of what everything in my cart will cost
    - the date when the order was created
```

```
[ ] User Story

As a visitor
From the order creation page
When I click 'Create Order' without completing the order form
I see a flash message indicating that I need to complete the form for successful order creation
```

### Item Reviews

```
[ ] User Story

As a Visitor,
When I visit an item's show page,
I see the item information (same information from tiny shop)
I also see a list of reviews for that item

Each review will have:
  - title
  - content of the review
  - rating (1 to 5)
```

```
[ ] User Story

When I visit an item's show page,
I see an area on the page for statistics about reviews:
- the top three reviews for this item (title and rating only)
- the bottom three reviews for this item  (title and rating only)
- the overall average rating of all reviews for this item
```

```
[ ] User Story

As a Visitor,
When I visit an item's show page
I see a link to add a new review for this item.
When I click on this link, I am taken to a new review path
And that path is nested under the item (ex: '/items/5/reviews/new').
On this new page, I see a form where I must enter:
- a review title
- a numeric rating that can only be a number from 1 to 5
- some text for the review itself
When the form is submitted, I should return to that item's
show page and I should see my review text.
```

```
[ ] User Story

As a Visitor,
When I fail to fully complete the new review form, but still try to submit the form
I see a flash message indicating that I need to complete the form in order to submit a review
```


```
[ ] User Story

As a Visitor,
When I visit an item's show page
I see a link to edit the review next to each review.
When I click on this link, I am taken to an edit review path
And that path is nested under the item (ex: '/items/5/reviews/edit').
On this new page, I see a form that is prepopulated with the form's existing:
- title
- numeric rating
- text of the review itself
I can update any of these fields and submit the form.
When the form is submitted, I should return to that item's
show page and I should see my updated review
```

```
[ ] User Story

As a Visitor,
When I visit an item's show page,
I see a link next to each review to delete the review.
When I delete a review I am returned to the item's show page
Then I should no longer see that review.
```

### Merchant

```
[ ] User Story

As a visitor
If a merchant has items that have been ordered
I can not delete that merchant
Either:
  - there is no button visible for me to delete the merchant
  - if I click on the delete button, I see a flash message indicating that the merchant can not be deleted.
```

```
[ ] User Story

As a visitor
When I am updating or creating a new merchant
If I try to submit the form with incomplete information
I see a flash message indicating which field(s) I am missing
```

```
[ ] User Story

As a visitor
When I visit a merchant's show page
I see statistics for that merchant, including:
  - count of items for that merchant
  - average price of that merchant's items
  - Distinct cities where my items have been ordered
```

### Item

```
[ ] User Story

As a visitor
When I delete an item
All reviews associated with that item are also deleted
```

```
[ ] User Story

As a visitor
If an item has been ordered
I can not delete that item
Either:
  - there is no button visible for me to delete the item
  - if I click on the delete button, I see a flash message indicating that the item can not be deleted.
```

```
[ ] User Story

As a visitor
When I am updating or creating a new item
If I try to submit the form with incomplete information
I see a flash message indicating which field(s) I am missing
```


### Extensions

```
[ ] User Story

As a Visitor,
When I visit an item's show page to see their reviews,
I see additional links to sort their reviews in the following ways:
- sort reviews by highest rating, then by descending date
- sort reviews by lowest rating, then by ascending date
```

```
[ ] User Story

As a visitor,
When I visit an merchant's show page
I see the top 3 highest rated items for that merchant (by average rating)
```

```
[ ] User Story

As a visitor
When I check out
I see a flash message with a randomly generated, 10 digit verification code associated with that order

I can use that verification code to search for an order through the nav bar.
If an order is found, I am redirected to a verified order page ('/verified_order')
On that verified order page, I can:
  - click a link to delete the order
  - update the shipping address for an order
  - remove items from the order
```

------------------

# Group Project

## Learning Goals
### Rails
* Create routes for namespaced routes
* Implement partials to break a page into reusable components
* Use Sessions to store information about a user and implement login/logout functionality
* Use filters (e.g. `before_action`) in a Rails controller
* Limit functionality to authorized users
* Use BCrypt to hash user passwords before storing in the database

### ActiveRecord
* Use built-in ActiveRecord methods to join multiple tables of data, calculate statistics and build collections of data grouped by one or more attributes

### Databases
* Design and diagram a Database Schema
* Write raw SQL queries (as a debugging tool for AR)


## Tables and Relationships
* Existing: Merchants, Items, Orders, OrderItems, Reviews
  * Orders will now belong to user (instead of the address nonsense)
  * Reviews belong to a user
  * Orders will have a status (pending, packaged, shipped, cancelled)
  * Order Items will have a fulfilled indicator
  * Merchants have many reviews through items

* Users
  * have one merchant (as in, this person works for a merchant/shop)
  * have many orders
    * have many order items through orders
    * have many items through order items
  * have many reviews
  * attributes
    * role
    * name
    * address fields
    * merchant_id
    * password
    * email


## High Level Tasks
* Authentication
  * visitor can register as a user
  * visitor can log in
* As a registered user
  - Create orders through cart checkout
  - Cancel pending order
  - CRUD their profile (excluding merchant id and role)
  - log out
  - CRUD their reviews (for items they have ordered)

* As an admin user
  - ship an order
  - can assign a user to a merchant or remove a user from a merchant
  - and all merchant responsibilities
  - and all user responsibilities
  - some sort of statistics !

* As a 'merchant' user
  - fulfill order items
  - can add user to the merchant (using email as identifier)
  - can remove users from the merchant
  - CRUD only their items
    * can not delete item that has been ordered
  - some sort of statistics !

* Merchant index - will show all users who work for that merchant
* User profile page
  - including their orders
* Admin and Merchant dashboards
  - statistics
  - links to accomplish their role's tasks


------------------

# Solo Project
## Learning Goals
### Databases
* Write migrations to alter existing database tables