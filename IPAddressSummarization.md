

# Overview #

Summarize a range of IP Addresses, e.g. 192.168.1.0 to 192.168.1.50, to
a group of networks. e.g. 192.168.1.0/27, 192.168.1.32/28, 192.168.1.48/31,
192.168.1.50.

# Requirements #

The IPy module is required for this to function. It can be obtained from
http://pypi.python.org/pypi/IPy.

# Installation #

## From Source ##

Download wadofstuff-ip from http://code.google.com/p/wadofstuff/downloads/list.

To install it, run the following command inside the unpacked source directory:

```
python setup.py install
```

## From PYPI ##

If you have the Python ```easy_install``` utility available, you can
also type the following to download and install in one step::

```
easy_install wadofstuff-ip
```

Or if you're using ```pip```::

```
pip install wadofstuff-ip
```

Or if you'd prefer you can simply place the included ```wadofstuff```
directory somewhere on your Python path, or symlink to it from
somewhere on your Python path; this is useful if you're working from a
Subversion checkout.

Note that this application requires Python 2.4 or later. You can obtain
Python from http://www.python.org/.

# Functions #

## summarize(first, last) ##

Summarize a network range given a first and last IP addresses.

```
>>> summarize('192.168.1.0', '192.168.1.50')
['192.168.1.0/27', '192.168.1.32/28', '192.168.1.48/31', '192.168.1.50']
>>> summarize('192.168.0.1', '192.168.2.255')
['192.168.0.1', '192.168.0.2/31', '192.168.0.4/30', '192.168.0.8/29',
'192.168.0.16/28', '192.168.0.32/27', '192.168.0.64/26', '192.168.0.128/25',
'192.168.1.0/24', '192.168.2.0/24']
>>> summarize('192.168.0.1', '192.168.2.254')
['192.168.0.1', '192.168.0.2/31', '192.168.0.4/30', '192.168.0.8/29',
'192.168.0.16/28', '192.168.0.32/27', '192.168.0.64/26', '192.168.0.128/25',
'192.168.1.0/24', '192.168.2.0/25', '192.168.2.128/26', '192.168.2.192/27',
'192.168.2.224/28', '192.168.2.240/29', '192.168.2.248/30',
'192.168.2.252/31', '192.168.2.254']
>>> summarize('192.168.0.0', '192.168.5.253')
['192.168.0.0/22', '192.168.4.0/24', '192.168.5.0/25', '192.168.5.128/26',
'192.168.5.192/27', '192.168.5.224/28', '192.168.5.240/29',
'192.168.5.248/30', '192.168.5.252/31']
>>> summarize('192.168.0.0', '192.168.255.254')
['192.168.0.0/17', '192.168.128.0/18', '192.168.192.0/19',
'192.168.224.0/20', '192.168.240.0/21', '192.168.248.0/22',
'192.168.252.0/23', '192.168.254.0/24', '192.168.255.0/25',
'192.168.255.128/26', '192.168.255.192/27', '192.168.255.224/28',
'192.168.255.240/29', '192.168.255.248/30', '192.168.255.252/31',
'192.168.255.254']
>>> summarize('::', '1::fffe')
['::/16', '1::/113', '1::8000/114', '1::c000/115', '1::e000/116',
'1::f000/117', '1::f800/118', '1::fc00/119', '1::fe00/120', '1::ff00/121',
'1::ff80/122', '1::ffc0/123', '1::ffe0/124', '1::fff0/125', '1::fff8/126',
'1::fffc/127', '1::fffe']
```

Worst case for summarising almost the whole IPv4 address range

```
>>> summarize('0.0.0.0', '255.255.255.254')
['0.0.0.0/1', '128.0.0.0/2', '192.0.0.0/3', '224.0.0.0/4', '240.0.0.0/5',
'248.0.0.0/6', '252.0.0.0/7', '254.0.0.0/8', '255.0.0.0/9',
'255.128.0.0/10', '255.192.0.0/11', '255.224.0.0/12', '255.240.0.0/13',
'255.248.0.0/14', '255.252.0.0/15', '255.254.0.0/16', '255.255.0.0/17',
'255.255.128.0/18', '255.255.192.0/19', '255.255.224.0/20',
'255.255.240.0/21', '255.255.248.0/22', '255.255.252.0/23',
'255.255.254.0/24', '255.255.255.0/25', '255.255.255.128/26',
'255.255.255.192/27', '255.255.255.224/28', '255.255.255.240/29',
'255.255.255.248/30', '255.255.255.252/31', '255.255.255.254']
```