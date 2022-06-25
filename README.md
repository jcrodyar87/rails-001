# Rails 7.0.3 on Docker

## Build the project
```
    docker compose run --no-deps web rails new . --force --database=postgresql
```

## Initial setup
```
cp .env.example .env
docker compose build
docker compose run --rm web bin/rails db:setup
```

## Running the Rails app
```
docker compose up
```

## Running the Rails console
When the app is already running with `docker-compose` up, attach to the container:
```
docker compose exec web bin/rails c
```

When no container running yet, start up a new one:
```
docker compose run --rm web bin/rails c
```

## Running tests
```
docker compose run --rm web bin/rspec
```

## Updating gems
```
docker compose run --rm web bundle update
docker compose up --build
```

## Production build

```
docker build -f production.Dockerfile .
```
