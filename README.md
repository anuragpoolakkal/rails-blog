# Blog using Ruby on Rails

Blog application which allows to create posts using WYSWYG editor, edit posts, add comments. It sends new comments to the blog owner by email.<br>
Turbo Stream is used to deliver partial page updates asynchronously over a web socket connection. That means creation, updation and deletion of the comment is reflected on the page without refreshing.

Create new Ruby on Rails application:
`rails new blog`

Run Rails server:
`rails server`

Create posts model:
`rails g scaffold post title:string, content:rich_text`

Add actions_text for rich text:
`rails action_text:install`

Migrate database:
`rails db:migrate`

Generate mailer helper:
`rails g mailer comments submitted`

Run tests:
`rails test`

Change SQLite database to PostgreSQL:
`rails db:system:change --to-postgresql`

### Host on Render.com

To host for free on Render.com, we have to setup Web Service, PostgreSQL and Redis manually. Follow [this video](https://www.youtube.com/watch?v=XCBWda8moVk).

Create a web service by adding git repository of the project. Add RAILS_MASTER_KEY as environment variable and paste the key stored in /config/master.key as the value.

Create PostgreSQL and paste its internal database URL to the web service environment variable with name DATABASE_URL.

Create Redis and paste its internal URL to the web service environment varaible with name REDIS_URL.

Create /bin/render-build.sh file in the Rails project and paste the following content.

```sh
#!usr/bin/env bash
# exit on error

set -o errexit

bundle install
./bin/rails assets:precompile
./bin/rails assets:clean
```

Make the file executable by running the command `chmod a+b bin/render-build.sh`.

OR you can replace these two steps (creating the file and making it executable) by adding a gem.<br>
Add the gem: `bundle add render_build_setup`<br>
Then run `rails g render_build_setup` for it to create the file and make it executable.

Commit and push your changes.
