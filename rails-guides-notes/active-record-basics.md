[Source](http://guides.rubyonrails.org/active_record_basics.html)

#### [back to rails nuances index](rails-nuances.md)

* Active Record is the M in MVC ==> follows the idea that objects carry both persistent data and behavior which operates on that data
* Active Record is an ORM framework essentially
* uses integer `id` column by default as primary key
* `created_at` and `updated_at` are also automatically created for Active Record instances
* `.create()` creates and saves a new record while `.new` returns a new object ==> calling `.save` will save the new object to the database
* data access is made easy [see more](active-record-querying.md)
  * `.all`
  * `.first`
  * `.find_by(example_field: 'example value')`
  * `.where(example_field: 'example_value')`
* can add validations to an Active Record model [see more](active-record-validations.md)
* can add callbacks to certain events in life-cycle of an Active Record model [see more](active-record-callbacks.md)
* Rails provides a domain-specific language for managing a database schema called migrations [see more](active-record-migrations)
  * `rails db:migrate`
  * `rails db:rollback`
