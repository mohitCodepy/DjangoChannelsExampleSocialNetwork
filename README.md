# Django Channels Example Social Network

This is an example real-time Social built using [DjangoChannelsRestFramework](https://github.com/hishnash/djangochannelsrestframework).

See our [blog](https://lostmoa.com/blog/ARealtimeSocialNetworkExample/) for a detail breakdown of this example and other Django related posts.

## Running this example server

```bash
python manager.py migrate
```
```bash
python manage.py runserver 0.0.0.0:8000
```


### Playing with this example server

This project does not include any frontend elements so you will need to write your own or use a websocket client, like [Cleora](https://cleora.app).

#### Logging in

There is a simple example login eondptoin:
```HTTP
GET /login/{username}
```

This will log you (and create a new user account if the user name does not already exist). 

## Can i just deploy this as is?

No this **IS NOT** production/deploy ready!

This example uses the `InMemoryChannelLayer` in production you should use something else, see [here](djangochannelsrestframework).
