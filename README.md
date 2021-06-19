# Fitur Chatting

## Connect to Socket.io

### End Point

`http://localhost:3000`

### Params

```
{
    user_type: integer|1=user,2=admin,
    user_id: integer
}
```

### Example 

```
var socket = io("http://localhost:3000?user_type=1&user_id=1);
```


## Send Chat

### Protokol : 

`WS Socket.io`

### Event : 

`send-chatting`

### Data Payload :

```

{
    "from": integer,
    "from_type": integer|1=user,2=admin,
    "to": integer,
    "to_type": integer|1=user,2=admin,
    "type": string|text,product,image,
    "message": string,
    "product_id": integer,
    "variant_id": integer,
    "image": base64
}

```

### Example :

```
socket.emit('send-chatting', {
    "from": integer,
    "from_type": integer|1=user,2=admin,
    "to": integer,
    "to_type": integer|1=user,2=admin,
    "type": string|text,product,image,
    "message": string,
    "product": integer,
    "variant_id": integer,
    "image": base64
}, (data) => {
    //code for callback
});

socket.on('send-chatting', function(data){
    console.log(data);
});
```

**Data Callback**

```
{
    "success": true,
    "data": {
        "channel": "e4da3b7fbbce2345d7772b0674a318d5",
        "from": 1,
        "to": 1,
        "from_data": {
            "id": 1,
            "name": "usertest",
            "image": null,
            "user_type": 1
        },
        "to_data": {
            "id": 1,
            "name": "usertest",
            "last_sign_in_at": null,
            "user_type": 2
        },
        "data": {
            "message": "hi go 123",
            "product": {
                "id": 2,
                "title": "Carla Levy",
                "image": "9a8601cefa6cc152809da4d47db785bd.png",
                "price": 80000,
                "link": "http://localhost:8000/product/2"
            },
            "image": null,
            "is_read": false,
            "type": "text"
        },
        "updated_at": "2021-06-05T14:56:05.000000Z",
        "created_at": "2021-06-05T14:56:05.000000Z",
        "id": 19
    },
    "message": "Berhasil simpan data"
}

```


## Last Chat Contact

### Protokol

`REST API`

### Request

**Method** : `GET`

**URL** : `/api/last-chat-contact`

**Headers** : 

```
{
    'Accept': 'application/json',
    'Content-type: 'application/json' 
}
```
**Params** :

```
{
    user_type: integer|1=user,2=admin,
    user_id: integer
}
```

### Response

```
{
    "success": true,
    "data": {
        "current_page": 1,
        "data": [
            {
                "id": 3,
                "user_id": 1,
                "user_type": 1,
                "channel": "e4da3b7fbbce2345d7772b0674a318d5",
                "to": 1,
                "to_data": {
                    "id": 1,
                    "name": "usertest",
                    "user_type": 2,
                },
                "last_data": {
                    "type": "text",
                    "image": null,
                    "is_read": false,
                    "message": "ulala",
                    "product": null
                },
                "is_read": 1,
                "deleted_at": null,
                "created_at": "2021-06-05T14:22:37.000000Z",
                "updated_at": "2021-06-05T17:22:05.000000Z"
            }
        ],
        "first_page_url": "http://localhost:8000/api/last-chat-contact?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://localhost:8000/api/last-chat-contact?page=1",
        "next_page_url": null,
        "path": "http://localhost:8000/api/last-chat-contact",
        "per_page": 10,
        "prev_page_url": null,
        "to": 1,
        "total": 1
    },
    "message": null
}

```

## History Chat / Detail Chat

## Mark as read - Last Chat Contact

### Protokol

`REST API`

### Request

**Method** : `GET`

**URL** : `/api/chat`

**Headers** : 

```
{
    'Accept': 'application/json',
    'Content-type: 'application/json' 
}
```
**Params** :

```
{
    channel: string
}
```

### Response

```
{
    "success": true,
    "data": {
        "current_page": 1,
        "data": [
            {
                "id": 19,
                "channel": "e4da3b7fbbce2345d7772b0674a318d5",
                "from": 1,
                "to": 1,
                "from_data": {
                    "id": 1,
                    "name": "usertest",
                    "image": null,
                    "user_type": 1,
                },
                "to_data": {
                    "id": 1,
                    "name": "usertest",
                    "user_type": 2,
                },
                "data": {
                    "type": "text",
                    "image": null,
                    "is_read": true,
                    "message": "hi go 123",
                    "product": null
                },
                "deleted_at": null,
                "created_at": "2021-06-05T14:56:05.000000Z",
                "updated_at": "2021-06-05T15:27:36.000000Z"
            },
            {
                "id": 18,
                "channel": "e4da3b7fbbce2345d7772b0674a318d5",
                "from": 1,
                "to": 1,
                "from_data": {
                    "id": 1,
                    "dob": "2020-05-19",
                    "name": "usertest",
                    "image": null,
                    "user_type": 1,
                },
                "to_data": {
                    "id": 1,
                    "name": "usertest",
                    "user_type": 2,
                },
                "data": {
                    "type": "text",
                    "image": null,
                    "is_read": true,
                    "message": "hi go 123",
                    "product": null
                },
                "deleted_at": null,
                "created_at": "2021-06-05T14:54:39.000000Z",
                "updated_at": "2021-06-05T15:27:36.000000Z"
            },
            ...
        ],
        "first_page_url": "http://localhost:8000/api/chat?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://localhost:8000/api/chat?page=1",
        "next_page_url": null,
        "path": "http://localhost:8000/api/chat",
        "per_page": 10,
        "prev_page_url": null,
        "to": 8,
        "total": 8
    },
    "message": ""
}
```

## Mark as read - Last Chat Contact

### Protokol : 

`WS Socket.io`

### Event : 

`mark-as-read`

### Data Payload :

```
{
    id: integer,
    to: integer,
    to_type: integer|1=user,2=admin
}

```

### Example :

```
socket.emit('mark-as-read', {
    id: integer,
    to: integer,
    to_type: integer|1=user,2=admin
});

socket.on('mark-as-read', function (data) {
    console.log(data);
});

```

**Data Callback**

```
{
    "success": true,
    "data": [
        47,
        48
    ],
    "message": "Berhasil update status read"
}

```

## Listen Online User - Last Chat Contact

### Protokol : 

`WS Socket.io`

### Event : 

`user-online`

### Data Payload :

```
[
    {
        socket_id: "J7FdltfukpktsmimAAAA"
        user_id: "1"
        user_type: "2"
    },
    {
        socket_id: "J7FdltfukpktsmimAAAe"
        user_id: "2"
        user_type: "2"
    },
]

```

### Example :

```

socket.on('user-online', function (data) {
    console.log(data);
});

```