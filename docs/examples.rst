##############################################
How to Use
##############################################

Authentication
==============

By default you can get all the information from Netbox if the login_required option is set to False. If the option is
set to True, you can access the api by username and password to GET the information. The API is only writable if you
have a Token.

* Use the auth_token parameter for the writeable api
* Use the auth parameter to use username and password. The auth parameter is a tuple ('username','password')

Usage
=====

To start with python-netbox client:

    >>> from netbox import NetBox
    >>> netbox = NetBox(host='127.0.0.1', port=32768, use_ssl=False, auth_token='token')

Examples
========

Get all devices:

    >>> netbox.dcim.get_devices()

Get devices per rack:

    >>> netbox.dcim.get_devices_per_rack('rack_name')

Get device by name

    >>> netbox.dcim.get_device_by_name('device_name')

Get per device the primary ip and mac address:

    >>> output = []
    >>> for item in a.dcim.get_devices():
    >>>    device_name = item['name']
    >>>
    >>>    if item['primary_ip'] is not None:
    >>>        primary_ip_id = item['primary_ip']['id']
    >>>        get_ips = a.ipam.get_ip_by_id(primary_ip_id)
    >>>
    >>>        output.append({'name': device_name, 'ip': get_ips['address'], 'mac': get_ips['interface']['mac_address']})
    >>>    else:
    >>>         print('{} has no primary_ip'.format(item['name']))
    >>>
    >>>    print(output)

Create a site:

    >>> netbox.dcim.create_site('site1', 'site1')

Delete a site:

    >>> netbox.dcim.delete_site('site1')