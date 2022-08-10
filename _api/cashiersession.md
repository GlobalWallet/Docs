---
title: /payment-session
position_number: 1
type: post
description: To create a payments page (cashier) session

content_markdown: |-
  📌 To add a new riddle to the database

    | HTTP Method | Endpoint | Summary                           |
    | ----------- | -------- | --------------------------------- |
    | `POST`      | /riddles | Adds a new riddle to the database |

    Use the JSON request body to add a new Riddle object to the database.

    The request body should use the following schema:
    
    | Field    | Type   | Required | Description                                                                                                                                                                                               |
    | -------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | riddle   | string | Required | The riddle's question                                                                                                                                                                                     |
    | answer   | string | Required | The riddle's answer                                                                                                                                                                                       |
    | category | string | Required | A one-word classification of the riddle. It should not contain spaces. The original database includes the categories: easy, hard, funny, kids, math, and word. This is not an enum and more can be added. |
    | source   | string | Optional | The source of the riddle

    {: .error }
    **Note**: The `Content-Type` header should be set to `application/json`.

    {: .success }
  **Example request**

    A curl request to add a new riddle:

    ```
    curl -X POST \
    'https://api.dev.kibramoa.net/payment-session' \
    -H 'accept: application/json' \
    -H 'X-API-KEY: 5TDI6o6keGvH9Di+umZj6wGkMZBE7Ukrb8+8A4WErq0=.b8987f40-e1cf-488c-843a-7a634f245a81' \
    -H 'Content-Type: application/json' \
    -d '{
    "country": "BR",
    "currency": "BRL",
    "amount": 13000,
    "redirectUrl": "https://merchant.io/where-to-go",
    "language": "ES",
    "customer": {
      "name": "John Doe",
      "email": "john@email.test",
      "phone": "+34666999666",
      "userDevice": "MOBILE",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36",
      "ip": "84.232.140.77",
      "address": {
        "street": "32 Windsor Gardens",
        "streetNumber": "24",
        "country": "GB",
        "zipCode": "W9 3RG",
        "city": "London",
        "state": "Great London."
      },
      "identify": {
        "number": "76486883X",
        "type": "DNI"
      }
    },
    "merchantReference": "mustbe18cars",
    "paymentReference": "Invoice ABC123",
    "userId": "Merch_User_123",
    "extra1": "extraData001",
    "extra2": "extraData002",
    "extra3": "extraData003",
    "storedToken": "index-stored",
    "tax": "21%",
    "shippingAddress": {
      "street": "32 Windsor Gardens",
      "streetNumber": "24",
      "country": "GB",
      "zipCode": "W9 3RG",
      "city": "London",
      "state": "Great London."
    },
    "orderDetails": [
      {
        "productName": "shirt-1233474",
        "quantity": 1,
        "dimensions": "85x51",
        "description": "Blue sports t-shirt "
      }
    ]
  }'

    ```

    A successful response will return an HTTP status code of `201` and have the following schema:

    | Field   | Type   | Description                        |
    | ------- | ------ | ---------------------------------- |
    | message | string | A brief success message            |
    | content | object | Top-level containing Riddle object |

    Where the Riddle object has this schema:

    | Field    | Type   | Description                                                                                                                                                        |
    | -------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | \_id     | string | The database id for the Riddle object                                                                                                                              |
    | riddle   | string | The riddle's question                                                                                                                                              |
    | answer   | string | The riddle's answer                                                                                                                                                |
    | category | string | A classification of the riddle. The original database includes the categories: easy, hard, funny, kids, math, and word. This is not an enum and more can be added. |
    | source   | string | The source of the riddle                                                                                                                                           |
    | \_\_v    | number | An internal versioning number used by Mongoose (the Object Data Model library used to connect to the MongoDB database).

    {: .success }
    **Example response**

    **Example response**

    A successful response to a `POST` request is an object like below:

    ```
    HTTP/1.1 201 Created
    Content-Type: application/json; charset=utf-8

    {
    "message": "Successfully added new riddle",
    "content": {
        "_id": "60bd0708d7dcc31bd9376abe",
        "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
        "answer": "A candle",
        "category": "easy",
        "source": "https://parade.com/947956/parade/riddles/",
        "__v": 0
    }
    }
    ```

    {: .error }
    **Possible error responses**

    A `POST` request to the /riddles endpoint may return the following errors.

    | Error code | Description                                                                                                                                |
    | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
    | 400        | `Bad Request`: This error will be returned if a required field in the request body is missing or if the `category` field contains a space. |
    | 500        | `Internal Server Error`: An unexpected error occurred on the server.                                                                       |

    {: .info }
      **Data Table**
      The following are the parameteres needed along with the data types that are used.
      

    | **Parameter**   | **Data Type** | **Example**         | **Description**                                                                                             |
    | --------------- | ------------- | ------------------- | ----------------------------------------------------------------------------------------------------------- |
    | **productName** | string        | shirt-1233474       | ID Number from end user.                                                                                    |
    | **quantity**    | number        | 1                   | Product quantity.                                                                                           |
    | **dimensions**  | string        | 85x51               | Product size dimension.                                                                                     |
    | **ApplyPromo**  | boolean       | 1                   | Merchant will send 1 or 0 across as to whether a promotion or bonus code will be applied. **– Coming soon** |
    | **description** | string        | Blue sports t-shirt | Free description of the order.                                                                              |



right_code_blocks:
  - code_block: |1-
        {
        
        "cashierUrl": "https://cashier.dev.kibramoa.net?sessionId=54ed4d33-9c24-4ef0-a7f8-242920a657u5"
 
        }
    title: Response
    language: json
  - code_block: |2-    
          {

          "statusCode": 401,
          "message": "Unauthorized"
          
          }
    title: Error 401
    language: json
   
---
