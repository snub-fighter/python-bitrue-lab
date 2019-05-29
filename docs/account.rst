Account Endpoints
=================

Orders
------

Order Validation
^^^^^^^^^^^^^^^^

Bitrue has a number of rules around symbol pair orders with validation on minimum price, quantity and total order value.

Read more about their specifics in the `Filters <https://github.com/Bitrue-exchange/bitrue-official-api-docs#exchange-information-some-fields-not-support-only-reserved>`_
section of the official API.

It can be helpful to format the output using the following snippet

.. code:: python

    amount = 0.000234234
    precision = 5
    amt_str = "{:0.0{}f}".format(amount, precision)


`Fetch all orders <bitrue.html#bitrue.client.Client.get_all_orders>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    orders = client.get_all_orders(symbol='XRPUSDT', limit=10)


`Place an order <bitrue.html#bitrue.client.Client.create_order>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Place an order**

Use the `create_order` function to have full control over creating an order

.. code:: python

    from bitrue.enums import *
    order = client.create_order(
        symbol='XRPUSDT',
        side=SIDE_BUY,
        type=ORDER_TYPE_LIMIT,
        timeInForce=TIME_IN_FORCE_GTC,
        quantity=100,
        price='0.00001')

**Place a limit order**

Use the helper functions to easily place a limit buy or sell order

.. code:: python

    order = client.order_limit_buy(
        symbol='XRPUSDT',
        quantity=100,
        price='0.00001')

    order = client.order_limit_sell(
        symbol='XRPUSDT',
        quantity=100,
        price='0.00001')


**Place a market order**

Use the helper functions to easily place a market buy or sell order

.. code:: python

    order = client.order_market_buy(
        symbol='XRPUSDT',
        quantity=100)

    order = client.order_market_sell(
        symbol='XRPUSDT',
        quantity=100)

`Place a test order <bitrue.html#bitrue.client.Client.create_test_order>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Creates and validates a new order but does not send it into the exchange.

.. code:: python

    from bitrue.enums import *
    order = client.create_test_order(
        symbol='XRPUSDT',
        side=SIDE_BUY,
        type=ORDER_TYPE_LIMIT,
        timeInForce=TIME_IN_FORCE_GTC,
        quantity=100,
        price='0.00001')

`Check order status <bitrue.html#bitrue.client.Client.get_order>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    order = client.get_order(
        symbol='XRPUSDT',
        orderId='orderId')


`Cancel an order <bitrue.html#bitrue.client.Client.cancel_order>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    result = client.cancel_order(
        symbol='XRPUSDT',
        orderId='orderId')


`Get all open orders <bitrue.html#bitrue.client.Client.get_open_orders>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    orders = client.get_open_orders(symbol='XRPUSDT')

`Get all orders <bitrue.html#bitrue.client.Client.get_all_orders>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    orders = client.get_all_orders(symbol='XRPUSDT')


Account
-------

`Get account info <bitrue.html#bitrue.client.Client.get_account>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    info = client.get_account()

`Get asset balance <bitrue.html#bitrue.client.Client.get_asset_balance>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    balance = client.get_asset_balance(asset='BTC')

`Get account status <bitrue.html#bitrue.client.Client.get_account_status>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    status = client.get_account_status()

`Get trades <bitrue.html#bitrue.client.Client.get_my_trades>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    trades = client.get_my_trades(symbol='XRPUSDT')

`Get trade fees <bitrue.html#bitrue.client.Client.get_trade_fee>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    # get fees for all symbols
    fees = client.get_trade_fee()

    # get fee for one symbol
    fees = client.get_trade_fee(symbol='XRPUSDT')

`Get asset details <bitrue.html#bitrue.client.Client.get_asset_details>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    details = client.get_asset_details()

`Get dust log <bitrue.html#bitrue.client.Client.get_dust_log>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    log = client.get_dust_log()
