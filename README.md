## Rails 6 docker starter
Official Docker Rails sample application page https://docs.docker.com/samples/rails/ is outdated, so I created my own quickstart guide.

### Setup

Copy these files (except README) into your new empty project directory. Generate your app with `rails new`, for example:

`docker-compose run --no-deps web rails new . -T --webpack=react --force --database=postgresql`

Once you got a new Gemfile you need to rebuild the image:

`docker-compose build`

Replace the contents of config/database.yml with the following:

```
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password: password
  pool: 5

development:
  <<: *default
  database: app_development

test:
  <<: *default
  database: app_test
```

Start it:

`docker-compose up`

Create dbs:

`docker exec <web_container> rails db:create`
