---
title: /direct-payment
position_number: 2
type: post
description: Payment API endpoint to complete the session previously generated on Kibramoa.

content_markdown: |-
  #### Direct API payment endpoint

  {: .info }
  https://api.{env}.kibramoa.net/direct-payment

  Last endpoint for complete the payment session and connect with the payment processors.

  You must previously initiate a session and retreive a correct paymentOptionId to this endpoint to get a proper response

  Request parameters:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | *sessionId | string | UUID of the session generated previously. |
  | *paymentOptionId | string | Payment option string. |
  | bankId | string | Bank id chosen by the end user. |
  | extraData | array | Set of extra parameters taken from end-user input. |
 
  {: .info }
  The responses from this endpoint differ depending on the payment option chosen on the /payment-options call, please reveiw the statusCode response parameter on the table below.

  Response have the following schema:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | *statusCode | string | Code indicating the action.<br /> Values: <br />000 -> 'success': payment completed with success. <br /> 300 -> 'redirect': redirect end user. <br /> 081 -> 'qrcode': display or render QR code. <br /> 082 -> 'request': build a HTTP request with provided details. <br /> 083 ->'receipt': print a recepit to end user with the provided details. <br /> 084 -> 'info': display instructions about the payment before redirect. <br />  999 -> 'error': payment failed. | 
  | resultType | string | Action to execute after the payment, could be redirect to new page, build a request, etc. | 
  | result | object | Details result with next step to take in order to complete the payment process. | 

  {: .info }
  **Note**: The `Content-Type` header should be set to `application/json` along with the merchant API key

right_code_blocks:
  - code_block: |1-
      {
          "sessionId": "3b21a1e2-e8c2-4e86-8de8-8441ea5c7dba",
          "paymentOptionId": "4fb6f4dfab76be51616d18e1f679409cc1d0711dc597c86033235ab72a85d384492e19f8f90e8bff04638c3579290bd336986ca9ff432de17fbb20ee659fe797eb35395b8d9f67f0fb21ec0069bee85083eb22057f6a40152b9d7507f0b895851ebbbbbca679092323",
          "bankId": null,
          "extraData": {
            "cardnum": "520000*0007",
            "expiryyear": "2023",
            "expirymonth": "01",
            "cardcvv": "111",
            "cardholder": "cardholder name"
          }
      }
    title: Request
    language: json
  - code_block: |2-
      {
        "statusCode": "000",
        "resultType": "success",
        "result": {
            "transactionId": "15be2828-c286-48f0-ae73-7a9f151dc0f2"
          }
      }
    title: Success
    language: json
  - code_block: |3-    
       {
         "statusCode": "300",
         "resultType": "redirect",
         "result": {
             "redirectUrl": "https://sandbox.kibramoa.net/paycc.aspx?authcode=276c69d5-1a75-41c6-a6d6-398e4a52e72e&token=QfZSjdyG8HT%2b464XqRkil42Jr0zCGY%2bZ",
             "transactionId": "f5773e8a-697e-4b25-a01d-bd3701091a8f"
          }
        }
    title: Redirect
    language: json
  - code_block: |4-    
         {
            "statusCode": "081",
            "resultType": "qrcode",
            "result": {
                "qrCodeString": "00020126600014BR.GOV.BCB.PIX011434882109000111022022120528C2DB42465B9D5204000053039865406130.005802BR5909Transfero6012RioDeJaneiro6224052022120528C2DB42465B9D6304108C",
                "base64QRCode": "iVBORw0KGgoAAAANSUhEUgAAAVkAAAFZCAYAAAAy8lzbAAAAAXNSR0IArs4c...VVXXdC+J/.YII=",
                "transactionId": "08174da1-9b12-431f-a1b2-0b676b9b80ea"
            }
         }
    title: QRCode
    language: json
  - code_block: |5-    
          {
            "statusCode": "082",
            "resultType": "request",
            "result": {
              "targetUrl": "https://sandbox.paymentgt.com/fundtransfer",
              "method": "POST",
              "contentType": "application/json",
              "externalId": "my-00002",
              "status": "PROCESSING",
              "bodyPayload": {
                "bankcode": "RHB",
                "merchant": "Surepay88",
                "amount": "130",
                "refid": "my-00002",
                "token": "a883c0f2c78cf5c0815ed97c1c06a5a5",
                "customer": "Merch_User_123",
                "currency": "MYR",
                "language": "en",
                "clientip": "84.232.140.77",
                "post_url": "https://api.dev.kibramoa.net/notifications/surepay-apm/987441d2-c3b1-41e5-941a-000867bbd4a6",
                "failed_return_url": "https://merchant.io/where-to-go",
                "return_url": "https://merchant.io/where-to-go"
              },
              "queryParams": null,
              "transactionId": "33aa5301-4056-41bb-99db-33b56121de37"
            }
          }
    title: Request
    language: json 
  - code_block: |6-
          {
            "statusCode": "083",
            "resultType": "receipt",
            "result": {
                "sessionId": "bdfa8140-e0a3-49e0-8b3a-7717be3a1a76",
                "transactionId": "85fb951a-e8b9-4451-9007-2e8c1d582061",
                "bankName": "Any Emirate Bank",
                "paymentDetails": [
                    {
                        "label": "Rate",
                        "value": 3.72387
                    },
                    {
                        "label": "Amount",
                        "value": 3161.3
                    },
                    {
                        "label": "Currency",
                        "value": "AED"
                    },
                    {
                        "label": "Account info",
                        "value": "asdd12121212121"
                    },
                    {
                        "label": "Payment info",
                        "value": "Recipient_Name"
                    }
                ]
            }
           }
    title: Receipt
    language: json
  - code_block: |7-    
           {
            "statusCode": "084",
            "resultType": "info",
            "result": {
              "transactionId": "f5659201-a219-4be3-b14f-f2513280f236",
              "bankName": "Banco do Brasil",
              "paymentDetails": [],
              "paymentLocations": [
                {
                  "name": "Banco do Brasil",
                  "instructions": [
                    "Após clicar no link para o seu Internet Banking, seguir as instruções abaixo",
                    "Selecione a opção \"Débito em Conta\" e informe sua agência e conta corrente",
                    "Verifique se seu nome aparece corretamente e digite sua senha eletrônica",
                    "Digite sua senha de 6 dígitos e clique no botão continuar",
                    "Clique no botão \"Concordo\" e confirme sua compra"
                  ]
                }
              ],
              "redirectUrl": "https://sandbox-gateway.safetypay.com/banksgateway/9165/251168"
            }
           }
    title: Info
    language: json
  - code_block: |8-    
            {
              "statusCode": "999",
              "resultType": "error",
              "result": {
                  "errors": [
                      {
                          "code": "2005 - 2005205",
                          "message": "Non 3DS card is not allowed"
                      }
                  ],
                  "transactionId": "6bbffe09-429f-4929-8a9b-934792099164"
              }
            }
    title: Declined
    language: json 
  - code_block: |8-    
             {
              "statusCode": 400,
              "message": [
                  "This session was completed."
              ]
             }
    title: Error
    language: json 
---