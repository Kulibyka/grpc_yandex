# grpc_yandex
tg: @Vzyhovich

Данный проект представляет собой доработку прошлого.

В данной версии добавлены: авторизация и хранение информации в базе данных sqlite

Я прикладываю файл "yandex.postman_collection.json" для тестирования сервера. Там показан пример взаимодействия со всеми 6 хэндлерами.

Для начала работы сервера, запустить файл main.go в папке cmd/final-project. В папке storage должен лежать только текстовый файл, если там до Вашего первого запуска уже лежит бд, её надо удалить. При Вашем запуске создастя новая чистая бд.

При первом запуске в папке storage (которая находится в корне проекта) создаться файл с 2 табоицами, для записи зарегистрированных пользователей и для записи задач.

Хэндлер "/register": в Body надо отправить данные в формате JSON

![image](https://github.com/Kulibyka/grpc_yandex/assets/59702274/3eaa9a3a-8e8e-44e6-b164-99727a3682f4)

Хэндлер "/login": также, как и при регистриции надо отправить данные в JSON формате

![image](https://github.com/Kulibyka/grpc_yandex/assets/59702274/20df6b21-723d-4748-b5a5-e8a8d8d8f29e)


При выполненной регистрации сервер в ответ пришлёт JWT токен. 

Для теста всех остальных хэндлеров будет необходимо использовать полученный токен, выбираем Bearer token, и он либо автоматически подставиться, либо придётся это сделать вручную (так лучше, тк иногда он неправильно подставляет)

![image](https://github.com/Kulibyka/grpc_yandex/assets/59702274/f73f3d0d-7ed6-48a3-86ac-e5e8f3ebed4d)

Хэндлер "/tasks/add": добавляет задачу для решения, на сервер нужно отправить выражения в JSON формате (ну и токен естественно). В ответ вернёт id задачи

![image](https://github.com/Kulibyka/grpc_yandex/assets/59702274/cc248491-e812-49bb-8937-9108aedc5569)

Хэндлер "/tasks": выводит список поставленных задач с их статусами, кроме токена ничего не нужно отправлять.

![image](https://github.com/Kulibyka/grpc_yandex/assets/59702274/3acbd0dc-c1eb-4142-934c-28693ed78d7e)

Хэндлер "/tasks/{id}/result": вернёт результат конкретной задачи, кроме токена ничего не нужно отправлять.

![image](https://github.com/Kulibyka/grpc_yandex/assets/59702274/741e43d9-82f6-49e1-8b08-f86556ab6f89)

![image](https://github.com/Kulibyka/grpc_yandex/assets/59702274/fe0f951e-791f-4096-a7f3-e9b36126119b)

Хэндлер "/operations": вернёт список доступных операций и время их выполнения

![image](https://github.com/Kulibyka/grpc_yandex/assets/59702274/3c3ac0ad-e6ed-40e7-b82d-b4ca5d1febce)
