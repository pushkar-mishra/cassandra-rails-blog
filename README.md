# cassandra-rails-blog

Open new terminal window

Download Cassandra

$ cd
$ wget http://archive.apache.org/dist/cassandra/2.2.0/apache-cassandra-2.2.0-bin.tar.gz
Installing Cassandra

$ cd
$ gzip -dc apache-cassandra-2.2.0-bin.tar.gz | tar xf -

Update .profile with the following lines:

set environment variables for Cassandra.
export CASSANDRA_VERSION=2.2.0
export CASSANDRA_HOME=${HOME}/apache-cassandra-${CASSANDRA_VERSION}
export PATH=${CASSANDRA_HOME}/bin:${PATH}

Then execute the following command within the terminal:

$ . ~/.profile

Start Cassandra

$ cassandra -f
rails new blog



    1. Remove database adapter gems from your Gemfile (mysql2, sqlite3, etc.)
    
    2. Change your config/application.rb
    
    Remove require 'rails/all line and require frameworks you want to use, for example:
    
    require "action_controller/railtie"
    require "action_mailer/railtie"
    require "sprockets/railtie"
    require "rails/test_unit/railtie"
    3. Delete your config/database.yml file, db/schema.rb and migrations (if any)
    
    4. Delete migration check in test/test_helper.rb
    
    5. Delete any ActiveRecord configuration from your config/environments files (this is what is causing your error)

go to rails app directory and open Gemfile
add

gem 'cequel'

bundle install


Generate scaffold of the application

$ rails g scaffold post title body

Add the following as the first route within config/routes.rb file:

root 'posts#index'  #Chnage it latter

Create app/models/post.rb file with the following content:
```ruby
class Post
  include Cequel::Record

  key :id, :timeuuid, auto: true
  column :title, :text
  column :body, :text

  timestamps
end
```
Create a default Cassandra configuration file

$ rails g cequel:configuration
Initialize Cassandra keyspace (database)

$ rake cequel:keyspace:create
Synchronize your Rails model schemas with Cassandra keyspace

$ rake cequel:migrate
Start the Rails server

$ rails s




