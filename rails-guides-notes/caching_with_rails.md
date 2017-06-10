[Source](http://guides.rubyonrails.org/caching_with_rails.html)

#### [back to rails nuances index](../rails-nuances.md)

* 3 types of caching techniques: page, action, and fragment caching
* Rails by default provides fragment caching
  * for the other 2, will need to add `actionpack-page_caching` and `actionpack-action_caching` to your Gemfile
* by default, caching only enabled in prod env so for local env, need to set `config.action_controller.perform_caching` to true in the relevant `config/environments/*.rb` file
