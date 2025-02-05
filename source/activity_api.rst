************************************
Activity API
************************************

1. Get Activity List
====================
| URL endpoint: https://stamps.co.id/api/v3/activities/
| Allowed method: GET
| Requires authentication: Yes


A. Request
----------

You can query a user's activity list by calling the API with these parameters. Only 20 activities will be returned per API call.

=================== =========== =======================
Parameter           Required    Description
=================== =========== =======================
user                Yes         Email/mobile number identifying the member
token               Yes         Merchant's Authentication token
older_than          No          Activity ID. 20 activities will be returned that are older than this ID. If not provided, will return the latest 20 activities.
=================== =========== =======================

Here's an example of a Activity List API call using cURL.

.. code-block :: bash

    $ curl 'https://stamps.co.id/api/v3/activities?token=abc&user=customer@stamps.co.id'

B. Response
-----------

On a successful API call, Stamps will reply with 20 (maximum) activities in a JSON List:

=================== ==================
Variable            Description
=================== ==================
activities          Activity list.
                    Contains id, :ref:`activity type <Activity Type>` and other details.
                    Object may vary depending on the activity type.
error_messages      Errors encountered when parsing data (if any)
=================== ==================

C. Example Response
-------------------

Below is an example response on successful API call.

.. code-block:: javascript

    HTTP/1.0 200 OK
    Allow: GET, HEAD, OPTIONS
    Content-Type: application/json
    Date: Wed, 15 Dec 2020 07:02:10 GMT
    Server: WSGIServer/0.1 Python/2.7.4
    Vary: Accept, Cookie

    {
        "activities": [
            {
                "id": 704,
                "type": 0,
                "created": 1661925661,
                "notes": "Acvitity notes",
                "merchant": {
                    "id": 5,
                    "name": "Ace Hardware"
                },
                "store": {
                    "name": "A301",
                    "display_name": "ST ACE KARAWACI MAL"
                },
                "transaction": {
                    "stamps": 20,
                    "name": "Transaction #493",
                    "status": 2,
                    "invoice_number": "INV-17",
                    "channel": "Mobile App"
                }
            },
            {
                "id": 2590959,
                "type": 1,
                "created": 1607049764,
                "notes": "",
                "merchant": {
                    "id": 2,
                    "name": "Levi's"
                },
                "store": {
                    "name": "L123",
                    "display_name": "Levi Store"
                },
                "redemption": {
                    "stamps": 0,
                    "name": "Update Database Voucher IDR 100,000",
                    "status": 2,
                    "channel": "POS"
                }
            },
            {
                "id": 2590960,
                "type": 2,
                "created": 1607049764,
                "notes": "",
                "merchant": {
                    "id": 2,
                    "name": "Levi's"
                },
                "award": {
                    "stamps": 0,
                    "name": "Update Database Voucher IDR 100,000",
                    "status": 2
                }
            },
            {
                "id": 2590961,
                "type": 7,
                "created": 1607049764,
                "notes": "",
                "merchant": {
                    "id": 2,
                    "name": "Levi's"
                },
                "store": {
                    "name": "L123",
                    "display_name": "Levi Store"
                },
                "balance_update": {
                    "transaction_number": "ABCDE123",
                    "amount": 120000,
                    "status": 1,
                    "balance_type": 1
                }
            },
            {
                "id": 2590962,
                "type": 8,
                "created": 1607049764,
                "notes": "",
                "survey": {
                    "name": "Test Survey",
                    "transaction_id": null
                }
            },
            {
                "id": 2590963,
                "type": 9,
                "created": 1607049764,
                "notes": "",
            },
            {
                "id": 2590964,
                "type": 10,
                "created": 1607049764,
                "notes": "",
                "stamps_deduction": {
                    "stamps": 100,
                    "status": 1,
                    "notes": ""
                }
            },
            {
                "id": 2590965,
                "type": 11,
                "created": 1607049764,
                "notes": "",
                "merchant": {
                    "id": 2,
                    "name": "Levi's"
                },
                "store": {
                    "name": "L123",
                    "display_name": "Levi Store"
                },
                "transaction_modification": {
                    "root_transaction": {
                        "id": 12,
                        "invoice_number": "ABC-123"
                    },
                    "original_transaction": {
                        "id": 13,
                        "invoice_number": "ABC-123.1"
                    },
                    "modified_transaction": {
                        "id": 14,
                        "invoice_number": "ABC-123.2"
                    }
                    "stamps_delta": -10,
                    "stamps_delta_override": 0,
                    "stamps_refund_from_payments": 0,
                    "total_stamps_delta": -10,
                    "subtotal_delta": -100000,
                    "grand_total_delta": -100000,
                    "invoice_number": "ABC-123.2",
                    "channel": "POS"
                }
            },
            {
                "id": 2590966,
                "type": 11,
                "created": 1607049764,
                "notes": "",
                "merchant": {
                    "id": 2,
                    "name": "Levi's"
                },
                "store": {
                    "name": "L123",
                    "display_name": "Levi Store"
                },
                "transaction_modification": {
                    "root_transaction": {
                        "id": 20,
                        "invoice_number": "ABC-2"
                    },
                    "original_transaction": {
                        "id": 20,
                        "invoice_number": "ABC-2"
                    },
                    "modified_transaction": nil,
                    "stamps_delta": -10
                    "stamps_delta_override": 0,
                    "stamps_refund_from_payments": 0,
                    "total_stamps_delta": -10,
                    "subtotal_delta": -100000,
                    "grand_total_delta": -100000,
                    "invoice_number": "ABC-2.2",
                    "channel": "POS"
                }
            },
            {
                "id": 2590967,
                "type": 12
                "notes": "",
            },
            {
                "id": 2590968,
                "type": 13,
                "notes": "",
            },
            {
                "id": 2590969,
                "type": 14,
                "notes": "",
            },
            {
                "id": 25909610,
                "type": 15,
                "created": 1607049764,
                "expired_stamps": 102,
                "notes": "",
            },
            {
                "id": 25909611,
                "type": 16,
                "created": 1607049764,
                "notes": "",
                "merchant": {
                    "id": 2,
                    "name": "Levi's"
                },
                "store": {
                    "name": "L123",
                    "display_name": "Levi Store"
                },
                "transaction_modification": {
                    "root_transaction": {
                        "id": 30,
                        "invoice_number": "ABC-16"
                    },
                    "original_transaction": {
                        "id": 30,
                        "invoice_number": "ABC-16"
                    },
                    "modified_transaction": {
                        "id": 31,
                        "invoice_number": "ABC-16.2"
                    }
                    "stamps_delta": -10,
                    "stamps_delta_override": 0,
                    "stamps_refund_from_payments": 100,
                    "total_stamps_delta": 90,
                    "subtotal_delta": -100000,
                    "grand_total_delta": -100000,
                    "invoice_number": "ABC-16.2",
                    "channel": "POS"
                }
            },
        ]
    }


2. Get Activity List by Merchant Group
====================
| URL endpoint: https://stamps.co.id/api/v3/activities/by-merchant-group
| Allowed method: GET
| Requires authentication: Yes


A. Request
----------

You can query a user's activity list in a merchant group by calling this API.
Returns 20 activities per API call.

=================== =========== =======================
Parameter           Required    Description
=================== =========== =======================
user                Yes         Email/mobile number identifying the member
token               Yes         Merchant's Authentication token
merchant_id         No          An array of merchant IDs to filter activities.
older_than          No          Activity ID. 20 activities will be returned that are older than this ID. If not provided, will return the latest 20 activities.
=================== =========== =======================

Here's an example of a Activity List API call using cURL.

.. code-block :: bash

    $ curl 'https://stamps.co.id/api/v3/activities/by-merchnat-group?token=abc&user=customer@stamps.co.id'

B. Response
-----------

On a successful API call, Stamps will reply with 20 (maximum) activities in a JSON List:

=================== ==================
Variable            Description
=================== ==================
activities          Activity list.
                    Contains id, :ref:`activity type <Activity Type>` and other details.
                    Object may vary depending on the activity type.
error_messages      Errors encountered when parsing data (if any)
=================== ==================

C. Example Response
-------------------

Below is an example response on successful API call.

.. code-block:: javascript

    HTTP/1.0 200 OK
    Allow: GET, HEAD, OPTIONS
    Content-Type: application/json
    Date: Wed, 15 Dec 2020 07:02:10 GMT
    Server: WSGIServer/0.1 Python/2.7.4
    Vary: Accept, Cookie

    {
        "activities": [
            {
                "id": 704,
                "type": 0,
                "created": 1661925661,
                "notes": "",
                "merchant": {
                    "id": 5,
                    "name": "Ace Hardware"
                },
                "store": {
                    "name": "A301",
                    "display_name": "ST ACE KARAWACI MAL"
                },
                "transaction": {
                    "stamps": 20,
                    "name": "Transaction #493",
                    "status": 2,
                    "invoice_number": "INV-17",
                    "channel": "Mobile App"
                }
            },
            {
                "id": 2590959,
                "type": 1,
                "created": 1607049764,
                "notes": "",
                "merchant": {
                    "id": 2,
                    "name": "Levi's"
                },
                "store": {
                    "name": "L123",
                    "display_name": "Levi Store"
                },
                "redemption": {
                    "stamps": 0,
                    "name": "Update Database Voucher IDR 100,000",
                    "status": 2,
                    "channel": "POS"
                }
            }
        ]
    }




Miscellaneous
------------------------------

Activity Type
^^^^^^^^^^^^^^^^^^^^^
=================== ===========
Code                Description
=================== ===========
0                   Transaction
1                   Redemption
2                   Awarded Stamps
7                   Change Balance
8                   Survey Submission
9                   Completed Registration
10                  Deduct Stamps
11                  Return transaction
12                  Membership Level Override
13                  Merged with Legacy Member
14                  Legacy Member Activated
15                  Stamps Expired
16                  Refund Stamps
=================== ===========


Status
^^^^^^^^^^
=================== ===========
Code                Description
=================== ===========
1                   Created
2                   Canceled
3                   Open
=================== ===========
