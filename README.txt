pymembase: The Couchbase Python Client
======================================

INSTALL
=======
Standard Python module build/install process.  
Use sudo or run as admin/root for installing system-wide.

$ python setup.py build
$ python setup.py install

TEST
====
A simple import of the new module is a good test that it 
was installed properly.

$ python
Python 2.6.7 (r267:88850, Jul 18 2011, 14:32:54) 
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import pymembase
>>>

EXAMPLE
=======
Comprehensive Getting Started and Tutorial guides are available
on couchbase.org.

The following example shows the minimal usage required to
set/get data from membase using the pymembase module.

from pymembase.membaseclient import VBucketAwareMembaseClient as membaseClient

server = {"ip": "127.0.0.1", "port": "8091",
    "rest_username": "Administrator", "rest_password": "password",
    "username": "Administrator", "password": "password"
    }

v = membaseClient(server, 'default')
key = "ABCD"
setstatus = v.set(key, 0, 0, "basic data string")
getstatus = v.get(key)
print getstatus[2]
v.done()
