---
title: /notifications
position_number: 1
type: post
description: Payment notifications happen once payment reach the PSP, they will be submitted to the merchant notification url previously configured on the merchant portal.

content_markdown: |-

    📌 All notification communications must be encrypted under TLS/SSL 
        
    ##### Notification body request

    #####  Once notification reach merchant systems it MUST be replied back returning a HTTP response with 200 status code, otherwise Kibramoa system will re-send every hour.
    
    ##### Merchant is able to resubmit a notification manually using the merchant portal.
     
    #### Transaction status table

    | Status| Description|
    | ------------- |:-------------:|
    | INIT          | Transaction initiated|
    | USER_CANCEL   | User cancel        |
    | PROCESSING    | Transaction is sent to PSP and waiting to be settled|
    | COMPLETED     | Transaction is settled and confirmed.|
    | ERROR         | Error happened during the processing.|
    | DECINED       | Transaction was declined by PSP.|
    | EXPIRED       | Expired transaction.|
    | REFUNDED      | Refund transaction completed.|

right_code_blocks:
  - code_block: |1-    
      {
        "internalId": "ee40a31b-a14f-48e2-a272-e3fc013f4735",
        "sessionId": "35eac8b8-e40b-447e-a214-8dd1f0e23996",
        "merchantName": "Fer Merchant",
        "userId": "Merch_User_123",
        "type": "BANK",
        "paymentOptionName": "Lottery",
        "country": "BR",
        "currency": "BRL",
        "paymentAmount": 130,
        "merchantReference": "orde123",
        "status": "COMPLETED",
        "language": "ES",
        "paymentReference": "Invoice ABC123",
        "storedToken": "index-stored",
        "extra1": "extraData001",
        "extra2": "extraData002",
        "extra3": "extraData003",
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
        "orderDetails": [
            {
            "productName": "shirt-1233474",
            "quantity": 1,
            "dimensions": "85x51",
            "description": "Blue sports t-shirt "
            }
        ],
        "shippingAddress": {
            "street": "32 Windsor Gardens",
            "streetNumber": "24",
            "country": "GB",
            "zipCode": "W9 3RG",
            "city": "London",
            "state": "Great London."
        }
      }
    title: Notification Payload
    language: json
  - code_block: |2-    
      {
        "statusCode": 404,
        "message": [
          "Not found"
        ],
        "error": "Not found"
       }
    title: Error 404
    language: json
---