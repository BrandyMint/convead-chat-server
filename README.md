convead-chat-server
===================

Данный проект содержит только документацию по чату.

[ChatAPIv2](https://github.com/BrandyMint/convead-chat-server/wiki/ChatAPIv2)

Процедура инициализации чата
============================

* Пользователь заходит на сайт с установленным виджетом
* Виджет получает visitor_id от logger'a
* Виджет подписывается на канал `/service/:visitor_id`
* При открытии окна чата пользователем посылается запрос на `/chat/service/:visitor_id`
* В случае успешного создания `conversation` сервер отправляет в канал `/service/:visitor_id` уведомление о создании `conversation`
* Виджет получает `conversation` по сервисному каналу и подписывается на канал `/conversations/:conversation_id`
* Дежурный менеджер подписанный на общий сервисный канал `/service/*` получает `conversation` и если он выбран контрагентом то у него открывается оно чата и он также подписывается на канал `/conversations/:conversation_id`
