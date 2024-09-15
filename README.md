# Blog using Ruby on Rails

Blog application which allows to create posts using WYSWYG editor, edit posts, add comments. It sends new comments to the blog owner by email.<br>
Turbo Stream is used to deliver partial page updates asynchronously over a web socket connection. That means creation, updation and deletion of comments is reflected on the page without refreshing.

Create new Ruby on Rails application:
`rails new blog`

Run Rails server:
`rails server`

Create posts model:
`rails g scaffold post title:string, content:text`

Migrate database:
`rails db:migrate`

Generate mailer helper:
`rails g mailer comments submitted`

Run tests:
`rails test`
