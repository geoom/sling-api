## About

Sling is a Slack clone built with Phoenix and React. Check out the blog post on medium.

https://medium.com/@benhansen/lets-build-a-slack-clone-with-elixir-phoenix-and-react-part-1-project-setup-3252ae780a1


#### Running the Phoenix app

Download dependencies

```
cd api
mix deps.get
mix deps.compile
```

Edit the database connection config in `/config/dev.exs` or `config/dev.secret.exs`
with your postgres user info if needed

Create and migrate the database

```
mix ecto.create
mix ecto.migrate
```

Start the server

```
mix phoenix.server
```


docker build  --no-cache -t sling-api-img .

docker run -d --name sling-api --rm -v $(pwd):/usr/src/app/sling-api --net nginx-proxy --link shared-postgres:postgres --expose 4000 -e VIRTUAL_HOST=dev-sling-api.tk -e VIRTUAL_PROTO=http -e VIRTUAL_PORT=4000 sling-api-img

docker exec -ti sling-api /bin/bash