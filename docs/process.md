1. Create new Rails app: rails new -d postgresql -T family_share_bourbon
2. Add to gemfile: gem 'rspec-rails'
3. Add Travis CI to repository.
   - Go to https://travis-ci.org/profile/schmidtsusanr, click Sync
   - Select this repo
   - Add .travis.yml file to repo with content: 
      language: ruby
      rvm:
        - 2.0.0
      env:
        - DB=postgresql
      script:
        - bundle exec rake spec
      before_script:
        - bundle exec rake db:create RAILS_ENV=test
        - bundle exec rake db:migrate
        - bundle exec rake db:test:prepare
4.

