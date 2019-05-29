Withdraw Endpoints
==================

`Place a withdrawal <bitrue.html#bitrue.client.Client.withdraw>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Make sure you enable Withdrawal permissions for your API Key to use this call.

You must have withdrawn to the address through the website and approved the withdrawal via email before you can withdraw using the API.

Raises a `BitrueWithdrawException <bitrue.html#bitrue.exceptions.BitrueWithdrawException>`_ if the withdraw fails.

.. code:: python

    from bitrue.exceptions import BitrueAPIException, BitrueWithdrawException
    try:
        # name parameter will be set to the asset value by the client if not passed
        result = client.withdraw(
            asset='ETH',
            address='<eth_address>',
            amount=100)
    except BitrueAPIException as e:
        print(e)
    except BitrueWithdrawException as e:
        print(e)
    else:
        print("Success")

    # passing a name parameter
    result = client.withdraw(
        asset='ETH',
        address='<eth_address>',
        amount=100,
        name='Withdraw')

    # if the coin requires a extra tag or name such as XRP or XMR then pass an `addressTag` parameter.
    result = client.withdraw(
        asset='XRP',
        address='<xrp_address>',
        addressTag='<xrp_address_tag>',
        amount=10000)

`Fetch deposit history <bitrue.html#bitrue.client.Client.get_deposit_history>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    deposits = client.get_deposit_history()
    btc_deposits = client.get_deposit_history(asset='BTC')


`Fetch withdraw history <bitrue.html#bitrue.client.Client.get_withdraw_history>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    withdraws = client.get_withdraw_history()
    btc_withdraws = client.get_withdraw_history(asset='BTC')

`Get deposit address <bitrue.html#bitrue.client.Client.get_deposit_address>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    address = client.get_deposit_address(asset='BTC')

`Get withdraw fee <bitrue.html#bitrue.client.Client.get_withdraw_fee>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: python

    address = client.get_withdraw_fee(asset='BTC')
