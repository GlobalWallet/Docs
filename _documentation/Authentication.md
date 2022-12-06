---
title: Authentication
position_number: 2
parameters:
  - name:
    content:
content_markdown: |-

  API requests must be authenticated using an API key, tied to the merchant configuration and generated during the boarding process. 
  
  {: .info }
  The X-API-KEY header grant access to merchant servers on kibramoa API, all the requests that contain this header must be executed from a back-end. 
  
  See the example of the headers included on this authenticated request in right side of the screen.
  

right_code_blocks:
  - code_block: |1-
     POST /direct-payment HTTP/1.1
     Host: api.dev.kibramoa.net
     X-API-KEY: PoQFx3ZBafIXsyA06vN7h3HJNu9...xZI=.c4c1f3748b3982162
     Content-Type: application/json
    title: HTTP
    language: http
---

