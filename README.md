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

# Python y Redis
```
import redis

r = redis.Redis(host='localhost', port=6379, db=0)

marcas = r.lrange('marcas', 0, -1)
for marca in marcas:
    print(marca.decode('utf-8'))


saludos = r.get('saludos')
print(saludos.decode('utf-8'))


r.set('despedida', 'Hasta luego')
despedida = r.get('despedida')
print(despedida.decode('utf-8'))

r.delete('despedida')
despedida = r.get('despedida')
print(despedida)
```

# Python y Redis
```
import redis
import json

r = redis.Redis(host='localhost', port=6379, db=0)

# Array Json
alumnos = [
    {
        "nombre": "Juan",
        "apellido": "Perez",
        "edad": 20
    },
    {
        "nombre": "Maria",
        "apellido": "Gomez",
        "edad": 18
    },
    {
        "nombre": "Jose",
        "apellido": "Garcia",
        "edad": 22
    }
]


# Check if key exists
if r.exists('alumnos'):
    print('Key exists')
else:
    json_string = json.dumps(alumnos)
    r.set('alumnos', json_string)

# Get key
json_string = r.get('alumnos')
alumnos = json.loads(json_string)
print(alumnos)
print(alumnos[0]['nombre'])
```
