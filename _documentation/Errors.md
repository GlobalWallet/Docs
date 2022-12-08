---
title: Errors
position_number: 5
parameters:
  - name:
    content:
content_markdown: |-
  Kibramoa uses conventional HTTP response codes to indicate the success or failure of an API response. 

  Http status code in 2xx range means a correct response, 4xx for request validation, resources access, etc and 5xx indicate errors with Kibramoa servers (rarely you will get an 5xx error, but if it happens, please let us know!).

  Error response will return an HTTP 4xx or 5xx status code and have the following schema:

  | Field   | Type   | Description                        |
  | ------- | ------ | ---------------------------------- |
  | *statusCode | integer | Status code. |
  | *message | array | Array containing all the error messages. |
  | error | string | Error description. |
  
  #### Errors vs Declines

  {: .warning }
  Errors are different from declines. Declines will always have a correct HTTP status code 2xx, and means, for some reason, the processor got the request but decided to decline the payment. 
  
  See more error details on the right side of the screen.

right_code_blocks:
  - code_block: |1-
      {
        "200 - 201": "OK Request processed.",
        "400": "Bad Request Required parameter is missing.",
        "401": "Unauthorized	No valid API key provided.",
        "402": "Request Failed.",
        "403": "Forbidden Your API-KEY doesn't have permissions.",
        "404": "Not Found Resource doesn't exist.",
        "429": "Too Many Requests.",
        "500 - 502 - 503 - 504": "Server Errors."
       }
    title: HTTP status codes
    language: json
  - code_block: |2-
       {
        "statusCode": 400,
        "message": [
          "currency must be a string"
        ],
        "error": "Bad Request"
       }
    title: Error response example
    language: json
---

