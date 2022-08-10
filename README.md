
<h1>Messaging App Backend</h1>

This app is the backend to a messging app using django channels to open a websocket and receive and send messages.

The front end is here: 


Make sure you installed redis

`brew install redis`

you can start redis by doing `redis-start` or you can run through docker `docker run --name redis:5 -d redis `


Run these commands:

`pip install requirements.txt ` - to instal the dependencies

`cd messagingapp`

`python3 manage.py migrate`- it uses a default sqlite database and a db.sqlite3 will be created

`python3 manage.py runserver`