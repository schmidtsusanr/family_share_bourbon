1. Create new Rails app: rails new -d postgresql -T family_share_bourbon
2. Add to gemfile: gem 'rspec-rails'
3. Add Travis CI to repository.
   - Go to https://travis-ci.org/profile/schmidtsusanr, click Sync
   - Select this repo
   - Add .travis.yml file to repo with content: 
      language: ruby
      rvm:
        - 2.2.2
      env:
        - DB=postgresql
      script:
        - bundle exec rake spec
      before_script:
        - bundle exec rake db:create RAILS_ENV=test
        - bundle exec rake db:migrate
        - bundle exec rake db:test:prepare
4. Add Bourbon (https://github.com/thoughtbot/bourbon)
   - Add to gemfile: gem 'bourbon'
   - Run: bundle install
   - In app/assets/stylesheets, rename application.css to application.scss
   - In application.scss, delete require_tree and require_self, and add: @import "bourbon";
   - Note: All additional stylesheets should be imported below Bourbon.
5. Add Neat (https://github.com/thoughtbot/neat#requirements)
   - Add to gemfile: gem 'neat'
   - Run: bundle install
   - In application.scss, add after bourbon: @import "neat";
6. Add Bitters (https://github.com/thoughtbot/bitters#installation)
   - Install Bitters: gem install bitters
   - Navigate to app/assets/stylesheets, then run: bitters install
   - In application.scss, between bourbon and neat, add: @import "base/base";
   - In _base.scss, uncomment @import "grid-settings";
7. Add .gitignore file (https://github.com/github/gitignore/blob/master/Rails.gitignore)
8. Add Devise (https://github.com/plataformatec/devise)
   - Add to gemfile: gem 'devise'
   - Run: bundle install
   - Generate devise: rails g devise:install
   - Add action mailer default url options to config/environments/development.rb: config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
   - Add notice actions (flashes) to application.html.erb above yield, add _flashes.scss stylesheetm, and add @import "flashes"; to _base.scss.
   -
