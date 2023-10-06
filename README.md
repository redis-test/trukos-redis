# trukos-redis

## Correr un contenedor con Redis
```
docker run -d --name miredis -p 6379:6379 redis
```

## Entramos al contenedor
```
marlonfalcon@MacBook-Pro-de-Marlon-3 ~ % docker exec -it fd842b15f611c86876248612364612f4869d3109887bfc863997d40b7a6b0ec5 /bin/sh
```

## Entramos al cli
```
redis-cli
```

## Listamos todas los campos
```
keys *
```

## Insertamos un valor
```
set saludos "Hola Mundo"
```

## Obtenemos el valor
```
get saludos
```

## Creamos un arreglo
```
lpush marcas *adidas* *nike* *puma*
```

# Redis Comander
```
docker run --rm --name redis-commander-2 -d  --env REDIS_HOST=local:host.docker.internal:6379  -p 8081:8081 \
  ghcr.io/joeferner/redis-commander:latest
```
