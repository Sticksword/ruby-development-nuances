[Source](http://guides.rubyonrails.org/active_record_callbacks.html)

#### [back to rails nuances index](../rails-nuances.md)

#### Active Record Object Life Cycle: Available Callbacks

##### Creating an Object
* before_validation
* after_validation
* before_save
* around_save
* before_create
* around_create
* after_create
* after_save
* after_commit/after_rollback

##### Updating an Object
* before_validation
* after_validation
* before_save
* around_save
* before_update
* around_update
* after_update
* after_save
* after_commit/after_rollback

##### Destroying an Object
* before_destroy
* around_destroy
* after_destroy
* after_commit/after_rollback

* can add relational callbacks, such that if the parent is deleted, the dependents are also deleted
* can have (multiple) conditional callbacks
* if a callback is really useful and used a lot in various files, can move to separate Callback Class
