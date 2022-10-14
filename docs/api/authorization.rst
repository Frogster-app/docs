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

    The content of ``body.json`` is like,

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

    The content of ``body.json`` is like,

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
         * **code** (*string*) [*required*] -- The 6-digit found from your authentication app.

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
