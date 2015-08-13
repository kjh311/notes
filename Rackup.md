#Sinatra with ActiveRecords & Migration

###Setup

First step: Create a `Gemfile`

Gemfile keeps the list of gem dependencies of your Rails application. The dependencies are met by Bundler by running. bundle install. According to Bundler: The best way to manage a Ruby application's gems. Bundler maintains a consistent environment for ruby applications.

*Link to your ruby gems!!*

```
source 'https://rubygems.org'

gem 'sinatra'
gem 'sqlite3'
gem 'activerecord'
gem 'sinatra-activerecord'

```

Second step: Create a `Rakefile`

Rake is Ruby Make, a standalone Ruby utility that replaces the Unix utility 'make', and uses a 'Rakefile' and .rake files to build up a list of tasks. In Rails, Rake is used for common administration tasks, especially sophisticated ones that build off of each other.

You can get a list of Rake tasks available to you, which will often depend on your current directory, by typing rake --tasks. Each task has a description, and should help you find the thing you need.



```
require './app' 
require 'sinatra/activerecord/rake'

```

Third step: Create a `config.ru`

```
require './app'
run Sinatra::Application
```

###Create the app

In our `app.rb`, we can do our code for our application

```

require 'sinatra'
require 'sinatra/activerecord'

# Connect the database
db_options = {adapter: 'sqlite3', database: 'sinatra_test'}
ActiveRecord::Base.establish_connection(db_options)


# Set up the model
class Note < ActiveRecord::Base
end


# Set up the routing
get '/' do
    @notes = Note.order("created_at DESC");
    redirect "/new" if @notes.empty?
    erb :index
end

get "/new" do
    erb :new
end

post "/new" do
    @note = Note.new(params[:note])
    if @note.save
        redirect "note/#{@note.id}"
    else
        erb :new
    end
end

get "/note/:id" do
    @note = Note.find_by_id(params[:id])
    erb :note
end

```

Create our first migration

Run:


	$ rake db:create_migration NAME=create_notes
	
	
	
*a new DB folder with a timestamp file will be created, add a table/s inside*

` def up
        create_table :notes do |t|
            t.string :title
            t.text :body
            t.timestamps
        end
    end
    def down
        drop_table :notes
    end`
    
  *rake db:create*
  *rake db:migrate*
Put this into the file *SCHEMA.RB*

```
class CreateNotes < ActiveRecord::Migration
  def up
    create_table :notes do |t|
      t.string :title
      t.text :body

      t.timestamps
    end
  end

  def down
    drop_table :notes
  end
end
```

###Creating views

Create the files: {IN THE VIEW FOLDER!!!!}

*CD out of views!!!*

`index.erb, layout.erb, new.erb, note.erb`

In `index.erb`

```
<h1>Notes</h1>
<ul>
    <% @notes.each do |note| %>
        <li>
            <h2>
                <a href="/note/<%= note.id %>"><%= note.title %></a>
            </h2>
        </li>
    <% end %>
</ul>
<a href="/new">New note</a>
```
In `layout.erb`

```
<html>
    <head>
        <meta http-equiv="content-type" content="text/html; charset=utf-8" />

        <title>Notes</title>

    </head>
    <body>
        <%= yield %>
    </body>
</html>
```

In `new.erb`

```
<h1>New Note</h1>
<form action="/new" method="post">
    <label for="title">Title</label><br />
    <input id='title' name='note[title]' type='text' />
    <br />
    <label for="body">Body:</label>
    <br />
    <textarea id="body" name="note[body]" rows="10"></textarea>
    <br />

    <button type="submit">Save</button>

</form>
```
In `note.erb`

```
<h1><%= @note.title %></h1>
<p><%= @note.body %></p>
<a href="/">All notes</a>
```

*bundle install*
*bundle exec* to download the most current version of gems



###Running the app

Run this command

	$ bundle exec rackup
	
Access our app at: `http://localhost:9292/`

*rake db:rollback* to undo



