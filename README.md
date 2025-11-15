
# Redis Docker Container

![Redis Logo](https://upload.wikimedia.org/wikipedia/commons/6/6b/Redis_Logo.svg)


## Описание

**Redis Docker Container** — это контейнер, предназначенный для запуска *in-memory* базы данных **Redis**.  
Контейнер используется для кеширования, хранения структур данных и брокера сообщений.

> **Назначение:** обеспечить простой и настраиваемый способ запуска Redis в Docker.

---

## Поддерживаемые аргументы образа

| Аргумент            | Описание                                               |
|---------------------|--------------------------------------------------------|
| `REDIS_VERSION`     | Версия Redis, используемая при сборке образа.         |
| `REDIS_PORT`        | Внутренний порт Redis (по умолчанию `6379`).          |
| `REDIS_USER`        | Пользователь, под которым запускается Redis.          |
| `REDIS_CONFIG_FILE` | Путь к конфигурационному файлу внутри контейнера.     |

---

## Переменные окружения

| Переменная         | Описание                                 | Пример     |
|--------------------|------------------------------------------|------------|
| `REDIS_PASSWORD`   | Пароль для подключения к Redis.          | `secret`   |
| `REDIS_APPENDONLY` | Включение режима AOF (`yes` / `no`).    | `yes`      |
| `REDIS_MAXMEMORY`  | Ограничение памяти Redis.                | `512mb`    |
| `REDIS_BIND`       | Адрес, на котором Redis принимает запросы. | `0.0.0.0`  |

---

## Пример запуска контейнера

```bash
docker run -d \
  --name my-redis \
  -p 6379:6379 \
  -e REDIS_PASSWORD=supersecret \
  -e REDIS_APPENDONLY=yes \
  -e REDIS_MAXMEMORY=512mb \
  -e REDIS_BIND=0.0.0.0 \
  my-redis-image:latest
````

---

## Настройка через переменные окружения

### Основные параметры

* `REDIS_PASSWORD` — **устанавливает пароль доступа**.
* `REDIS_APPENDONLY` — включает *Append Only File*.
* `REDIS_MAXMEMORY` — задаёт *лимит памяти*.
* `REDIS_BIND` — устанавливает адрес привязки Redis.

### Примеры значений

```
REDIS_APPENDONLY=yes
REDIS_MAXMEMORY=512mb
REDIS_BIND=0.0.0.0
```

---

## Полезные ссылки

* [Redis Documentation](https://redis.io)
* [Docker Hub — Redis](https://hub.docker.com/_/redis)

---

## Примечания

> Для сохранения данных рекомендуется использовать Docker Volumes,
> так как Redis хранит данные в оперативной памяти и может потерять их при перезапуске.

```
