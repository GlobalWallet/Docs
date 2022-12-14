---
title: Signature Verification
position_number: 2
parameters:
  - name:
    content:
description: Payment notifications security are based on signature hashing, your system must verify the integrity of the notification request received using your merchant signature secret key to verify the hash.
content_markdown: |-

    📌 Notifications headers arrives with x-signature header, it includes the expected result hash. 
    
    #### How to obtain the signature
    - ##### Get the json notification payload from the request.

    - ##### Use your signature secret key to calculate the signature hash using HMAC algorithm with sha256.
    
    - ##### Encode the HMAC result using base64 and compare the result with the one provided on the x-signature header.
    
    - ##### Both hashes must match in order to consider the notification as valid.

    - ##### Process the notification acordingly and respond to Kibramoa with 200 status code.
     
    {: .info }
    **Note:** For obtain the signature secret key attached to your merchant please contact kibramoa support.

right_code_blocks:
  - code_block: |1-    
     crypto.createHmac('sha256', 'SECRET').update(JSON.stringify(notificationPayload)).digest('base64')
    title: NodeJs
    language: javascript
  - code_block: |2-    
      <?php 
        base64_encode(hash_hmac('sha256', json_encode($requestBody), $secret, true));
      ?>
    title: PHP
    language: php
---