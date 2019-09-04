# Sapphire
勉強用Webアプリケーション
## 仕様
- Docker
- docker-compose
- Ruby
- Rails
- Nuxt
- mysql
## Setup
```sh
$ docker-compose run --rm back rails db:create
$ docker-compose run --rm back rails db:migrate
$ docker-compose up

# attach

$ docker attach sapphire_back
$ docker attach sapphire_front
```
## API 解放PORT
- front: 8080
- back: 3000
## cURL sample
```
$ curl http://localhost:3000/users

# new

$ curl -X POST http://localhost:3000/users -d 'user[name]=test'
```
## docker参考元
- https://qiita.com/at-946/items/08de3c9d7611f62b1894

