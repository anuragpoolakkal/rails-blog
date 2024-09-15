# Blog using Ruby on Rails

Simple blog application which allows to create posts, add comments.

Create new Ruby on Rails application:
`rails new blog`

Run Rails server
`rails server`

Create posts model
`rails g scaffold post title:string, content:text`

Migrate database
`rails db:migrate`

Generate mailer helper
`rails g mailer comments submitted`
