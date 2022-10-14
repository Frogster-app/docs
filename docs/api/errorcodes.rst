Error codes
=============

.. code-block:: TXT
    000 000 000
    ┃   ┃   ┖ Identifying code
    ┃   ┖ Route id
    ┖ Http error code

    Example:
    422 001 001
    ┃   ┃   ┖ Email address validation
    ┃   ┖ Authentication
    ┖ Unprocessable Entity

409 Errors
-----------

``409001004``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25
   :header-rows: 0

   * - Message
     - Reason
   * - Email is already in use
     - Email is already in use by another account

``409001005``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25
   :header-rows: 0

   * - Message
     - Reason
   * - Username is already in use
     - Username is already in use by another account

422 Errors
-----------

``422001000``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25
   :header-rows: 0

   * - Message
     - Reason
   * - Registration is disabled
     - Registration has been disabled server wide.

``422001001``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25 50
   :header-rows: 0

   * - Message
     - Reason
     - Additional info
   * - Invalid email 
     - Email inputted didnt pass regex
     - regex: /^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$/

``422001002``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25 50
   :header-rows: 0

   * - Message
     - Reason
     - Additional info
   * - Invalid username 
     - Username inputted didnt pass regex
     - regex: /^[a-zA-Z0-9_]{4,16}$/

``422001003``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25 50
   :header-rows: 0

   * - Message
     - Reason
     - Additional info
   * - Invalid password
     - Password inputted didnt pass regex
     - regex: /^[\x00-\x7F]{12,64}$/

500 Errors
-----------

``500001006``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25
   :header-rows: 0

   * - Message
     - Reason
   * - Database error
     - There was an error inserting user into the database

``500001007``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25
   :header-rows: 0

   * - Message
     - Reason
   * - Database error
     - There was an error inserting user into the database for verifying emails

``500001008``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25
   :header-rows: 0

   * - Message
     - Reason
   * - Error sending verification email
     - There was an error sending email verification email

``500001009``
~~~~~~~~~

.. list-table:: 
   :widths: 25 25
   :header-rows: 0

   * - Message
     - Reason
   * - Database error
     - Error selecting user from database