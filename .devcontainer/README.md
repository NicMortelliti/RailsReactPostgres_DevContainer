# Dev Container for Rails, React and Postgres Development

This dev container is based on: [ruby-rails-postgres](https://github.com/devcontainers/templates/tree/main/src/ruby-rails-postgres)

## Steps to set up project

1. Run `bundle install` if this is a freshly build container.

1. Run `rails new ./ --api -d postgresql -M -T`

    This will create a rails app at the same level as .devcontainer.
    *The new master.key resides in config/. Be sure not to commit it, but also don't lose track of it!*

    -M: Skips mailer

    -T: Skips test suite

1. Run `rails c`

1. The config/database.yml should use the user and password you set in docker-compose.yml, and host "db" (as that's the name of this service). You can use whatever database name you want.

    ```yml
    development:
      <<: *default
      host: db
      username: postgres
      password: postgres
      database: myapp_development
    ```

1. Use `bin/rails db:prepare` to create the database.

## Running Project
1. PostgreSQL server should already be running in its container.
    
    *Since it's in its own container, commands like "psql" in the Rails container will return "command not found: psql".

1. Start Rails server with: ```rails s```

1. Start Rails console (IRB) with: ```rails c```
