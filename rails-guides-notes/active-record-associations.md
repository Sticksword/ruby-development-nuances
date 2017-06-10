[Source](http://guides.rubyonrails.org/association_basics.html)

#### [back to rails nuances index](../rails-nuances.md)

* associations allow for declarative creation and deletion (no need to explicitly create and delete associations)
* six types of associations
  * `belongs_to` (one to one, declared on child)
  * the declaring class gains 5 methods related to the association (example using Book model that belongs_to Author)
    * .association (eg. `@author = @book.author`)
    * .association=(associate) (eg. `@book.author = @author`)
    * build_association(attributes = {}) (eg. `@author = @book.build_author(author_number: 123, author_name: 'John Doe')`) - this returns a new object of the associated type instantiated from the passed attributes but object is not yet saved
    * create_association(attributes = {}) (eg. `@author = @book.create_author(author_number: 123, author_name: 'John Doe')`) - this does same thing but associated object is saved
    * create_association!(attributes = {}) - same as `creation_association` above but raises `ActiveRecord::RecordInvalid` if record is invalid
    * can add custom options (can kind of guess behavior from name)
      * :autosave
      * :class_name
      * :counter_cache
      * :dependent
      * :foreign_key
      * :primary_key
      * :inverse_of
      * :polymorphic
      * :touch
      * :validate
      * :optional
    * can scope belongs_to via a scope block with query methods
      * where
      * includes
      * readonly
      * select
  * `has_one` (one to one, declared on parent)
    * gets same 5 methods like `belongs_to`
  * `has_many` (one to many, declared on parent)
  * `has_many :through` (many to many, `:through` model is the mapping model)
    * also good for setting up "shortcuts" through nested has_many associations
  * `has_one :through` (one to one, similar to `has_many :through`, `:through` model is the middle mapping model)
  * `has_and_belongs_to_many` (direct many to many relationship, no third model but Rails does generate a third underlying mapping table, typically use this if the many to many relationship is simple)
* can have polymorphic associations where a model can belong to more than one other model
* can have self joins where a model has relationship with itself (eg. Employee class that `has_many` subordinates and `belongs_to` a manager)
* by default, associations look for objects only within the current module's scope
  * to associate a model in a different namespace, you have to specify the complete class name in association declaration via `class_name: <blah::blah::blah>`
* can have bi-directional associations
* can have association callbacks (eg. when creating this belonging to that, make sure this passes some criteria before/after adding to that)
