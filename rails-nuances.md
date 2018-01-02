# rails-nuances

#### [back to index](readme.md)

* [how to create a reference db migration](https://stackoverflow.com/questions/13694654/specifying-column-name-in-a-references-migration)
* [how to revert a db migration](https://stackoverflow.com/questions/7694487/ruby-on-rails-how-can-i-revert-a-migration-with-rake-dbmigrate)
* [giant pool of guides that I will eventually annotate](http://guides.rubyonrails.org/)
  * [active record basics](rails-guides-notes/active-record-basics.md)
  * [active record callbacks](rails-guides-notes/active-record-callbacks.md)
  * [active record migrations](rails-guides-notes/active-record-migrations.md)
  * [active record querying](rails-guides-notes/active-record-querying.md)
  * [active record validations](rails-guides-notes/active-record-validations.md)
  * [rails initialization process](rails-guides-notes/rails-initialization-process.md)
* [explanation of change from ActiveRecord::Base to ApplicationRecord](http://blog.bigbinary.com/2015/12/28/application-record-in-rails-5.html)
* [rails logging for any cli task - second answer](https://stackoverflow.com/questions/2246141/puts-vs-logger-in-rails-rake-tasks)
  ```
  task log: :environment do
    ActiveRecord::Base.logger = Logger.new(STDOUT)
  end
  ```
* [resource vs resources explanation](https://stackoverflow.com/questions/9194767/difference-between-resource-and-resources-methods)
* [ruby lambda syntax explanation](https://stackoverflow.com/questions/8476627/what-do-you-call-the-operator-in-ruby)
* [when you want more complex presentational logic but want to keep them in the presentation layer and not in a model](https://github.com/drapergem/draper)
* [rails model cheatsheet](https://gist.github.com/rstacruz/1569572)
* [when auto pathing for a resource goes wrong (you need custom functionality)](https://stackoverflow.com/questions/37556575/module-route-in-rails-with-form-forobject)
* [refactoring rails code using adapter, services, and decorator pattern (parts 2 and 3 are linked at bottom of article)](http://www.thegreatcodeadventure.com/rails-refactoring-part-i-the-adapter-pattern/)
* [solid rails digital book](https://handbook.infinum.co/books/rails)
