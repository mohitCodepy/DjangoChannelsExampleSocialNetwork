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


## Playing with this example server

This project does not include any frontend elements so you will need to write your own or use a websocket client, like [Cleora](https://cleora.app).

#### Logging in

There is a simple example login eondptoin:
```HTTP
GET /login/{username}
```

This will log you (and create a new user account if the user name does not already exist). 

### Using the Websocket API

Every message you send from your [client](https://cleora.app) to the server should include a `request_id`. This should be a random string or int. When the server responses you your message it will include the `request_id` of the request that is is responding to. This is use-full client-side so that you can create a Promise/Futures based api interface.

The consumer uses the `action` value to determine what `action` to call from your consumer. The RestApi style mixin actions provided by [DjangoChannelsRestFramework](https://github.com/hishnash/djangochannelsrestframework) expect additional data for the DjangoRestFramwork sterilisers to be nested within a `data` property.    

#### Creating a Post

```JSON
{ "action": "create", "request_id": 42, "data": {"body": "#Django is an epic #Framework for #WedDevelopment"} }
```

#### Updating a Post

```JSON
{ "action": "patch", "request_id": 43, "pk": 3, "data": {"body": "#Django is an epic #Framework for #WedDevelopment"} }
```

#### Retrieving a Post

```JSON
{ "action": "retrieve", "request_id": 44, "pk": 3 }
```

#### Deleting a Post

```JSON
{ "action": "delete", "request_id": 44, "pk": 3 }
```

#### Subscribing to a Hashtag
```JSON
{ "action": "subscribe_to_hashtag", "request_id": 45, "hashtag": "python" }
```

#### Un-Subscribing from a Hashtag
```JSON
{ "action": "unsubscribe_from_hashtag", "request_id": 46, "hashtag": "python" }
```

#### Subscribing to all Posts
```JSON
{ "action": "subscribe_to_list", "request_id": 47}
```

#### Un-Subscribing from all Posts
```JSON
{ "action": "unsubscribe_from_list", "request_id": 48}
```


## Can I just deploy this as is?

No this **IS NOT** production/deploy ready!

This example uses the `InMemoryChannelLayer` in production you should use something else, see [here](djangochannelsrestframework).
