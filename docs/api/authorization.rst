Authorization
=============

`endpoint: https://api.frogster.app/`


Registration
------------

.. http:post:: /auth/registration/

    Register an account with frogster.

    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H https://api.frogster.app/auth/registration/ \
              -H "Content-Type: application/json" \
              -d @body.json
            
        .. code-tab:: javascript

            fetch('https://api.frogster.app/auth/registration/',{
                method:'POST',
                headers:{
                    'content-type': 'application/json'
                },
                body:JSON.stringify(body.json)
            })
            .then(res=> res.json())
            .then(data => console.log(data))

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.frogster.app/auth/registration/'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(
                URL,
                json=data,
            )
            print(response.json())

    The content of ``body.json``,

    .. sourcecode:: json

        {
            "username": "frogster",
            "email": "play@frogster.app",
            "password": "Pr7!U4fS2PNn"
        }

    **Example response**:

    .. sourcecode:: json

        {
            "status": "ok",
            "message": "User registered, check inbox for verification email"
        }

    .. note::

       .. FIXME: we can't use :query string: here because it doesn't render properly

      :Request JSON Object:

         * **username** (*string*) [*required*] -- Must be utf-8 encoded, 4-16 characters long, and must not contain any spaces or special characters.
         * **email** (*string*) [*required*] -- A valid email address.
         * **password** (*string*) [*required*] -- Must be utf-8 encoded, 12-64 characters long.


Login
-----

.. http:post:: /auth/Login/

    Login to a frogster account.

    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H https://api.frogster.app/auth/login/ \
              -H "Content-Type: application/json" \
              -d @body.json

        .. code-tab:: javascript

            fetch('https://api.frogster.app/auth/login/',{
                method:'POST',
                headers:{
                    'content-type': 'application/json'
                },
                body:JSON.stringify(body.json)
            })
            .then(res=> res.json())
            .then(data => console.log(data))

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.frogster.app/auth/login/'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(
                URL,
                json=data,
            )
            print(response.json())

    The content of ``body.json``,

    .. sourcecode:: json

        {
            "username": "frogster",
            "password": "Pr7!U4fS2PNn",
            "client": "webapp",
            "code": "123456"
        }

    **Example response**:

    .. sourcecode:: json

        {
            "status": "ok",
            "message": "Logged in successfully",
            "data": {
                "client": "webapp",
                "token": "069d45d2abb7b24961da4231f13848b12f2d579cf650c6f8d016f8b28ea402c863b6265557c922283c9cbe5f2529c72dddd120b10c42f538aa8dcddf53a5dd005cf1e7e5c3a3ae3078748bc13230216db105c6c4b41a44c95947c3847412a2c1830667d0",
                "username": "frogster",
                "email": "play@frogster.app",
                "id": 0
            }
        }

    .. note::

       .. FIXME: we can't use :query string: here because it doesn't render properly

      :Request JSON Object:

         * **username** (*string*) [*required*] -- Must be utf-8 encoded, 4-16 characters long, and must not contain any spaces or special characters.
         * **password** (*string*) [*required*] -- Must be utf-8 encoded, 12-64 characters long.
         * **client** (*string*) [*required*] -- The client type, either ``webapp`` or ``mobile``.
         * **code** (*string*) [*optional*] -- The 6-digit found from your authentication app.

Verify email
------------

.. http:get:: /auth/verify/(string:token)/

    Login to a frogster account.

    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H https://api.frogster.app/auth/verify/XXXXXXXXXX.../ \
              -H "Content-Type: application/json"
            
        .. code-tab:: javascript

            fetch('https://api.frogster.app/auth/verify/XXXXXXXXXX.../',{
                method:'GET',
            })
            .then(res=> res.json())
            .then(data => console.log(data))

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.frogster.app/auth/verify/XXXXXXXXXX.../'
            response = requests.get(
                URL
            )
            print(response.json())

    **Example response**:

    .. sourcecode:: json

        {
            "status": "ok",
            "message": "Account verified"
        }

2FA
---

Add 2FA
~~~~~~~

.. http:post:: /auth/2fa/add/

    Add 2FA to a frogster account.

    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H https://api.frogster.app/auth/2fa/add/ \
              -H "Content-Type: application/json" \
              -d @body.json

        .. code-tab:: javascript

            fetch('https://api.frogster.app/auth/2fa/add/',{
                method:'POST',
                headers:{
                    'content-type': 'application/json'
                },
                body:JSON.stringify(body.json)
            })
            .then(res=> res.json())
            .then(data => console.log(data))

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.frogster.app/auth/2fa/add/'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(
                URL,
                json=data,
            )
            print(response.json())

    The content of ``body.json``,

    .. sourcecode:: json

        {
            "username": "frogster",
            "password": "Pr7!U4fS2PNn"
        }

    **Example response**:

    .. sourcecode:: json

        {
            "status": "ok",
            "message": "2FA secret generated",
            "data": {
                "secret": "WAZZUXKDCG7NHJCMCNTZADFY6ZHOWPMZ",
                "uri": "otpauth://totp/Frogster%3Aplays%40frogster.app?secret=WAZZUXKDCG7NHJCMCNTZADFY6ZHOWPMZ&issuer=Frogster",
                "qr": "https://chart.googleapis.com/chart?chs=166x166&chld=L|0&cht=qr&chl=otpauth://totp/Frogster%3Aplay%40frogster.app%3Fsecret=WAZZUXKDCG7NHJCMCNTZADFY6ZHOWPMZ%26issuer=Frogster"
            }
        }

    .. note::

       .. FIXME: we can't use :query string: here because it doesn't render properly

      :Request JSON Object:

         * **username** (*string*) [*required*] -- Must be utf-8 encoded, 4-16 characters long, and must not contain any spaces or special characters.
         * **password** (*string*) [*required*] -- Must be utf-8 encoded, 12-64 characters long.

Activate 2FA
~~~~~~~~~~~~

.. http:post:: /auth/2fa/activate/

    Activate 2FA to a frogster account.

    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H https://api.frogster.app/auth/2fa/activate/ \
              -H "Content-Type: application/json" \
              -d @body.json

        .. code-tab:: javascript

            fetch('https://api.frogster.app/auth/2fa/activate/',{
                method:'POST',
                headers:{
                    'content-type': 'application/json'
                },
                body:JSON.stringify(body.json)
            })
            .then(res=> res.json())
            .then(data => console.log(data))

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.frogster.app/auth/2fa/activate/'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(
                URL,
                json=data,
            )
            print(response.json())

    The content of ``body.json``,

    .. sourcecode:: json

        {
            "username": "frogster",
            "password": "Pr7!U4fS2PNn",
            "code": "123456"
        }

    **Example response**:

    .. sourcecode:: json

        {
            "status": "ok",
            "message": "2FA active"
        }

    .. note::

       .. FIXME: we can't use :query string: here because it doesn't render properly

      :Request JSON Object:

         * **username** (*string*) [*required*] -- Must be utf-8 encoded, 4-16 characters long, and must not contain any spaces or special characters.
         * **password** (*string*) [*required*] -- Must be utf-8 encoded, 12-64 characters long.
         * **code** (*string*) [*optional*] -- The 6-digit found from your authentication app.


Remove 2FA
~~~~~~~~~~

.. http:post:: /auth/2fa/remove/

    Remove 2FA to a frogster account.

    **Example request**:

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H https://api.frogster.app/auth/2fa/remove/ \
              -H "Content-Type: application/json" \
              -d @body.json

        .. code-tab:: javascript

            fetch('https://api.frogster.app/auth/2fa/remove/',{
                method:'POST',
                headers:{
                    'content-type': 'application/json'
                },
                body:JSON.stringify(body.json)
            })
            .then(res=> res.json())
            .then(data => console.log(data))

        .. code-tab:: python

            import requests
            import json
            URL = 'https://api.frogster.app/auth/2fa/remove/'
            data = json.load(open('body.json', 'rb'))
            response = requests.post(
                URL,
                json=data,
            )
            print(response.json())

    The content of ``body.json``,

    .. sourcecode:: json

        {
            "username": "frogster",
            "password": "Pr7!U4fS2PNn",
            "code": "123456"
        }

    **Example response**:

    .. sourcecode:: json

        {
            "status": "ok",
            "message": "2FA removed"
        }

    .. note::

       .. FIXME: we can't use :query string: here because it doesn't render properly

      :Request JSON Object:

         * **username** (*string*) [*required*] -- Must be utf-8 encoded, 4-16 characters long, and must not contain any spaces or special characters.
         * **password** (*string*) [*required*] -- Must be utf-8 encoded, 12-64 characters long.
         * **code** (*string*) [*optional*] -- The 6-digit found from your authentication app.