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
* [rails logging for any cli task]()
  ```
  task log: :environment do
    ActiveRecord::Base.logger = Logger.new(STDOUT)
  end
  ```
  
