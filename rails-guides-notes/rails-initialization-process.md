[Source](http://guides.rubyonrails.org/initialization.html)

#### [back to rails nuances index](../rails-nuances.md)

* `rails server` is equivalent to `exec ruby bin/rails server` which runs `rails.rb` in the bin folder
  * loads up `config/application.rb` for the application itself
  * loads up `config/boot.rb` which loads and sets up Bundler
  * loads up `rails/command.rb` which helps expand the cli aliases and runs the commands
    * for example, `rails s` expands into `rails server` and then "`cd`'s" into the Rails root directory before booting up the `Rails::Server` class
* `Rails::Server` inherits from `Rack::Server` which creates a common server interface for all Rack-based applications
* I could take more notes on the details that follow in the article, but I don't see too much value doing so at the moment, so I'm just treating the rest of the article as casual reading.
