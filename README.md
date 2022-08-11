
<h1>Messaging App Backend</h1>

This app is the backend to a messging app using django channels to open a websocket and receive and send messages.

The front end is here: https://github.com/minmin777/messaging_app_ui/tree/master/message-app


Make sure you installed redis

`brew install redis`

you can start redis by doing `redis-start` or you can run through docker `docker run --name redis:5 -d redis `


Run these commands:

`pip install requirements.txt ` - to instal the dependencies

`cd messagingapp`

`python3 manage.py migrate`- it uses a default sqlite database and a db.sqlite3 will be created

`python3 manage.py runserver`

<h2>Components of project</h2>

This project uses django channels (https://channels.readthedocs.io/en/latest/index.html) to create a web socket for this chat app using this endpoint in messenger/routing.py:
```buildoutcfg
websocket_urlpatterns = [
    re_path(r'^ws/chat$', consumer.ChatConsumer.as_asgi()),
]
```

All the logic for consuming and sending messages are in messenger/consumer.py where a WebsocketConsumer is created to handle all the logic such as
creating a new user by a username, getting n (where n is the number you specify in the request but defaulted to 20) previous messages and creating a new message.

The data models are in messenger/models.py where there are User and Message models.

User and Message have a one to many relationship as a user can create many messages, however I added a users_read field in the Message model that has a many to many relationship.
The fields in the models aren't all being used as this is still a basic chat app but I added the fields that I think would be good for future development 
such as knowing which users are online and when they were last online, having a message be an image and knowing which users have read the message.