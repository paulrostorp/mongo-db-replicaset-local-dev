# mongo-db-replicaset-local-dev
This docker aims at simplifying local development against a mongoDB replicaSet.
This should not be used in production.
This is based on original work from @prisma, see: https://github.com/prisma/docs/issues/2795#issuecomment-1041887647


### Docker compose example

```yaml
version: "3.7"

services:
  mongo-replicaset:
    image: ghcr.io/paulrostorp/mongo-db-replicaset-local-dev:latest
    environment:
      MONGO_REPLICA_PORT: 27017
    ports:
      - 27017:27017
    volumes:
      - mongodb_data_container:/data/db

volumes:
  mongodb_data_container:

```

Mongo uri:

```mongodb://localhost:27017/<db-name>?directConnection=true```

Databases are created dynamically on connection, so you can do:
```mongodb://localhost:27017/db-a?directConnection=true```
```mongodb://localhost:27017/db-b?directConnection=true```
```mongodb://localhost:27017/db-c?directConnection=true```
