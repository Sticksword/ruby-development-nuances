[Source](http://guides.rubyonrails.org/active_record_querying.html)

#### [back to rails nuances index](../rails-nuances.md)

* Active Record acts like an ORM and is DB agnostic
* there are many methods that insulate a developer from using raw SQL such as `find`, `group`, `having`, etc.
* the methods that return a collection, such as `group`, return an instance of `ActiveRecord::Relation` whereas methods that find a single entity, such as `first`, return a single instance of the model
* can do things in batches via `find_each` (batch fetch, single yield) and `find_in_batches` (batch fetch, batch yield)
* can use conditions that are the SQL equivalent of a WHERE clause:
  * `Client.where(orders_count: [1,3,5])`
  * `Client.where(created_at: (Time.now.midnight - 1.day)..Time.now.midnight)`
  * `Article.where(author: author)`
* can order via both symbol and string representation of the column:
  * `Client.order(:created_at)` (ascending by default)
  * `Client.order("created_at DESC")`
  * `Client.order(:orders_count, created_at: :desc)`
* can select specific fields just like in SQL:
  * `Client.select("viewable_by, locked")` == `SELECT viewable_by, locked FROM clients`
* can use distinct just like in SQL:
  * `Client.select(:name).distinct`
* can limit and offset queries:
  * `Client.limit(5).offset(30)`
* can group by columns:
  * `Order.select("date(created_at) as ordered_date, sum(price) as total_price").group("date(created_at)")`
  * to get total of grouped items on a single query: `Order.group(:status).count`
* the WHERE for GROUP BY: HAVING -> Rails version:
  * `Order.select("date(created_at) as ordered_date, sum(price) as total_price").
  group("date(created_at)").having("sum(price) > ?", 100)`
* can override conditions for debugging and other random purposes (?)
  * `unscope` remove a condition (by default removes the last one)
  * `only` only trigger certain conditions
  * `reorder`
  * `reverse_order`
  * `rewhere`
* can return null via `Article.none` in the case where you want to return a null value due to bad input
* Active Record provides two locking mechanisms for atomic updates:
  * optimistic locking - assumes minimum conflicts with data and will throw `StaleObjectError` if you update something that was already updated since the time you first retrieved the object (will need to handle exception yourself)
  * pessimistic locking - uses a locking mechanism provided by the underlying database, basically allowing only 1 party to have write access to a record
* can do joins! just use the names of the associations defined on the model as a shortcut for specifying JOIN clauses
  * `Category.joins(:articles)`
  * multiple joins: `Article.joins(:category, :comments)`
  * joining nested associations: `Article.joins(comments: :guest)` - "return all articles that have a comment made by a guest"
  * you can join nested associations on a multi level scope, but let's hope we never get to that. can always google it
* can add conditions to joined tables too:
  * `Client.joins(:orders).where(orders: { created_at: time_range })`
* there's also an option for LEFT OUTER JOINS: `Author.left_outer_joins(:posts)`
* can eager load associations by specifying `includes`
  * good against the N + 1 queries problem (1 original + N associations), reducing to only 1 (original) + 1 (extra query specifying the data you want from the associated table) queries
  * `Article.includes(:category, :comments)` - loads all the articles and the associated category and comments for each article
  * can also specify conditions on eager loaded associations
* scopes! you can use commonly used queries as method calls on a model -> equivalent to defining a class method
  * `scope :published, -> { where(published: true) }`
  * you can chain/merge scopes together when calling (since they're just more clauses)
  * scopes can take arguments -> eg. `scope :created_before, ->(time) { where("created_at < ?", time)` and calling it: `Article.created_before(Time.zone.now)`
  * can use conditionals with scopes: `scope :created_before, ->(time) { where("created_at < ?", time) if time.present? }`
  * can specify default scope: `default_scope { where("removed_at IS NULL") }` -> WARNING/CAVEAT: try not to use because it's applied to all scope and where conditions
  * removing all scopes: `<Model>.unscoped.load`
* Active Record provides dynamic finders! They're basically finder methods for all the fields in the model included for free by default
* Enums: [see more](http://api.rubyonrails.org/v5.1.1/classes/ActiveRecord/Enum.html)
  * maps int column to set of possible values
  * also creates corresponding scopes to query the model
  * can switch between each of the states in an enum and can query current state too
* Active Record allows for method chaining if all previous method calls return an `ActiveRecord::Relation`
  * eg. `Person
  .select('people.id, people.name, comments.text')
  .joins(:comments)
  .where('comments.created_at > ?', 1.week.ago)`
* If you feel gross and want to use raw SQL: `<Object>.find_by_sql("SQL SQL SQL SQL SQL")`
* can select certain columns via `pluck(:column, :another_column)`
* can perform calculations on queries:
  * `Client.count` -> `SELECT count(*) AS count_all FROM clients`
  * `Client.average("orders_count")`
  * `Client.minimum("age")`
  * `Client.maximum("age")`
  * `Client.sum("orders_count")`
* EXPLAIN works in Rails too!! (highly useful)
  * try this: `User.where(id: 1).joins(:articles).explain`
