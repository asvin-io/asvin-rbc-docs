API Endpoint Security
=====================

asvin components expose their services using RESTful API endpoints. They are secured using Jason Web Token(JWT). It is required to obtain a JWT from
OAuth server. Only thereafter the endpoints can accessed successfully. The :ref:`Login` API endpoint is used to get JWT from OAuth. 

.. _Access Signature:

Access Signature
################
The :code:`access_signature` used in the The :ref:`Login` API is a hashed-based message authentication code (MAC). It consists of cryptographic hash 
function (HMAC-SHA256) and secret key. In psuedocode, it can be illustrated as :code:`HMAC-SHA256(key, message)`. Here, message is :code:`timestamp+access_key` and key is :code:`customer_key`. So, the 
:code:`access_signature` is calculated as

.. code-block::

   access_signature = HMAC-SHA256(customer_key, timestamp+access_key)

The customer_key and access_key are acquired from `RBC Platform <https://app.rbc.asvin.io>`_. One needs to make a account there. The code block below
shows the :code:`access_signature` generation.

.. tabs::

  .. code-tab:: bash 

     #!/bin/bash
     customer_key="my-customer-key"
     access_key="my-access-key"
     timestamp=$(date +%s)
     access_signature=$(echo -n $timestamp$access_key | openssl dgst -sha256 -hmac $customer_key)
     echo $access_signature
 
  .. code-tab:: python

     import hmac
     import hashlib
     from time import time
     customer_key = "my-customer-key"
     access_key = "my-access-key"
     timestamp = str(math.floor(time()))
     access_signature = hmac.new(customer_key, msg=timestamp+access_key, digestmod=hashlib.sha256).hexdigest().upper()
     print access_signature
  

  .. code-tab:: js

     const CryptoJS = require("crypto-js");
     const dateNow = new Date();
     const customerKey = "my-customer-key";
     const accessKey =  "my-access-key";
     const timestamp = Math.floor(dateNow.getTime() / 1000);
     const accessSignature = CryptoJS.HmacSHA256(timestamp + accessKey, customerKey).toString(CryptoJS.digest);
     console.log(accessSignature)