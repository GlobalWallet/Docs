---
title: Transaction Object
position_number: 1
type: Data
description: Transaction data and types stored on Kibramoa systems, this details will be returned by the [/\payments/transactionId](#transaction-querygetTransaction) request.
content_markdown: |-
  Result data of the [/payments/:transactionId](#transaction-querygetTransaction) call, the transaction object stored on Kibramoa DB has the following parameters:
  

    | **Parameter**         | **Type** | **Example**                     | **Description**                                                       |
    | --------------------- | ------------- | ------------------------------- | --------------------------------------------------------------------- |
    | **id\***         | string        | c31cd72b-0c46-4c4c-a499-1d4040af44cc | Uuid of the transaction on kibramoa                                   |
    | **sessionId\***         | string        | c12cd72b-0c46-4c4c-a499-1d4040ax0321 | Uuid of the payment session                                   |
    | **country\***         | string        | BR                              | Alpha-2 ISO Country code                                              |
    | **currency\***        | string        | BRL                             | ISO Currency code                                                     |
    | **paymentAmount\***   | number        | 10.00                            | Amount. |
    | **status**          | string        | INIT                              | Refer to notification status table.                                    |
    | **merchantReference** | string        | order\_ticket\_123              | Merchant reference, must be unique and generated in merchant system.  |
    | **paymentReference**  | string        | Invoice ABC123                  | Reference to be used for the Payment.                                 |
    | **redirectUrl\***     | string        | https://merchant.io/where-to-go | Merchant redirect page after payment.                                 |
    | **customer\***            | object |    | Json object with the following details.                           | 
    | **customer.name\***       | string        | Pepe Doe               | User / payer full name.                  |
    | **customer.email\***      | string        | pepe@test.test  | User / payer email.                      |
    | **customer.phone\***      | string        | 34666999666  | User / payer phone number.               |
    | **customer.userDevice\*** | string        | User device.  | ENUM: [ MOBILE, DESKTOP, TABLET] |
    | **customer.userAgent\***  | string        | Mozilla/5.0 (X11; Linux x86\_64) ... hrome/51.0.2704.103 Safari/37.  | Browser User Agent data.  |
    | **customer.ip\***         | string        | 84.232.140.77 |   |
    | **customer.address\***            | object        |  | End user address.  |
    | **customer.address.street\***     | string        | 32 Windsor Gardens | First line of the address. |
    | **customer.address.streetNumber*** | string        | 24                 | Street address number.     |
    | **customer.address.country\***    | string        | GB                 | Alpha-2 ISO Country code   |
    | **customer.address.zipCode\***    | string        | W9 3RG             | Customer Postcode          |
    | **customer.address.city***         | string        | London             | Shipping City/Town         |
    | **customer.address.state**        | string        | Great London.      | Shipping State/ Region.    |
    | **customer.identify\***           | object        |  | User legal document details.  |
    | **customer.identify.number\***    | string        | 76486883X        | ID Number from end user.                         |
    | **customer.identify.type\***        | string        | DNI              | ID number type.                                  |
    | **shippingAddress**  | object    |                 | Shipping address object.     |
    | **shippingAddress.street***      | string        | 32 Windsor Gardens | First line of the address. |
    | **shippingAddress.streetNumber** | string        | 24                 | Street address number.     |
    | **shippingAddress.country**      | string        | GB                 | Alpha-2 ISO Country code   |
    | **shippingAddress.zipCode\***    | string        | W9 3RG             | The postcode.              |
    | **shippingAddress.city***        | string        | London             | Shipping City/Town         |
    | **shippingAddress.state**        | string        | Great London.      | Shipping State/ Region.    |
    | **orderDetails**        | array        |      | Array with products details.    |
    | **orderDetails.productName** | string        | shirt-1233474 | Product name. |
    | **orderDetails.quantity**    | number        | 1                   | Units. |
    | **orderDetails.dimensions**  | string        | 85x51               | Product size. |
    | **orderDetails.description** | string        | Blue sports t-shirt | Free description of the order. |
    | **errors**      | object        | - | Error reasons.          |
    | **createdAt**      | string        | 2022-12-09T11:07:05.484Z | DB timestamp.          |
    | **updatedAt**      | string        | 2022-12-12T09:15:01.891Z | DB timestamp.            |

right_code_blocks:
  - code_block: |1-
     {
        "id": "d31cd72b-0c46-4c4c-a499-1d4040af44cc",
        "sessionId": "17faf8e7-5170-4719-b797-7acba3e7cd05",
        "country": "BR",
        "currency": "BRL",
        "paymentAmount": 130.00,
        "status": "INIT",
        "paymentReference": "Invoice ABC123",
        "merchantReference": "asdaº123",
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
            "description": "Blue sports t-shirt ",
            "_id": "9cead2b4-0e6a-4a78-9726-d2ff7c05644a"
          }
        ],
        "customer": {
          "customerId": "84b79373-c84a-4e0a-9b73-899320fe42fa",
          "email": "john@email.test",
          "name": "John Doe",
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
            "number": "36570630563",
            "type": "BRA_CPF"
          },
          "_id": "f05577a3-c60c-48e8-8aa3-d2254f7c6ed0"
        },
        "errors": null,
        "createdAt": "2022-12-09T11:07:05.484Z",
        "updatedAt": "2022-12-09T11:07:05.484Z"
      }
    title: Transaction Object Example
    language: json
---