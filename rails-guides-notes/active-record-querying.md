[Source](http://guides.rubyonrails.org/active_record_querying.html)

#### [back to rails nuances index](../rails-nuances.md)

* Active Record acts like an ORM and is DB agnostic
* there are many methods that insulate a developer from using raw SQL such as `find`, `group`, `having`, etc.
* the methods that return a collection, such as `group`, return an instance of `ActiveRecord::Relation` whereas methods that find a single entity, such as `first`, return a single instance of the model
