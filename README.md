# Simple Books API #
This API allows you to reserve a book.

The API is available at https://simple-books-api.glitch.me


## Endpoints ##

### Status ###
GET /status
### Retruns the status of the API. ###

### List of books ###
GET /books

Returns a list of books

Optional query parameters:

type: fiction or non-fiction
limit: a number between 1 and 20.

### Get a single book ###
GET /books/:bookId

Retrive detailed information about a book.

### Submit an order ###
POST /orders

Allows you to submit a new order. Requires authentication.

The request body needs to be in JSON format and include the following properties:
 - `bookId` - Integer - Required
 - `customerName` - String - Required
Example

```
POST /orders/
Authorization: Bearer <YOUR TOKEN>

{
  "bookId": 1,
  "customerName": "John"
}
```
The response body will contain the access token.

### Get all orders ###

GET /orders

Allows you to view all orders. Requires authentication.

### Get an order ###

GET /orders/:orderId

Allows you to view an existing order. Requires authentication.

### Update an order ###

PATCH /orders/:orderId

Update an existing order. Requires authentication.

The request body needs to be in JSON format and allows you to update the following properties:

 - `customerName` - String
Example

```
PATCH /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>

{
  "customerName": "John"
}
```

### Delete an order ###

DELETE /orders/:orderId

Delete an existing order. Requires authentication.

The request body needs to be empty.

 Example
```
DELETE /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>
```

## API Authentication ##

To submit or view an order, you need to register your API client.

POST /api-clients/

The request body needs to be in JSON format and include the following properties:

 - `clientName` - String
 - `clientEmail` - String
 
 Example
 
 ```
 {
    "clientName": "zoxed",
    "clientEmail": "kaabi.mohamed@exemple.fr"
}
 ```
 
The response body will contain the access token.
