pem: Easy PEM file parsing
==========================

.. image:: https://readthedocs.org/projects/pem/badge/?version=stable
  :target: https://pem.readthedocs.io/en/stable/?badge=stable
  :alt: Documentation Status

.. image:: https://travis-ci.org/hynek/pem.svg?branch=master
   :target: https://travis-ci.org/hynek/pem
   :alt: CI status

.. image:: https://codecov.io/gh/hynek/pem/branch/master/graph/badge.svg
   :target: https://codecov.io/github/hynek/pem
   :alt: Coverage

.. image:: https://www.irccloud.com/invite-svg?channel=%23cryptography-dev&amp;hostname=irc.freenode.net&amp;port=6697&amp;ssl=1
   :target: https://www.irccloud.com/invite?channel=%23cryptography-dev&amp;hostname=irc.freenode.net&amp;port=6697&amp;ssl=1

.. teaser-begin

``pem`` is an MIT_-licensed Python module for parsing and splitting of `PEM files`_, i.e. Base64 encoded DER keys and certificates.

It runs on Python 2.7, 3.4+, and PyPy 2.0+, has no dependencies and does not attempt to interpret the certificate data in any way.
``pem`` is intended to ease the handling of PEM files in combination with pyOpenSSL_ and – by extension – Twisted_.

It’s born from the need to load keys, certificates, trust chains, and DH parameters from various certificate deployments: some servers (like Apache_) expect them to be a separate file while others (like nginx_) expect them concatenated to the server certificate.
To be able to cope with both scenarios in Python, ``pem`` was born:

.. code-block:: pycon

   >>> import pem
   >>> certs = pem.parse_file("chain.pem")
   >>> certs
   [<Certificate(PEM string with SHA-1 digest '...')>, <Certificate(PEM string with SHA-1 digest '...')>]
   >>> str(certs[0])
   '-----BEGIN CERTIFICATE-----\n...'

Additionally to the vanilla parsing code, ``pem`` also contains helpers for Twisted that save a lot of boilerplate code.

``pem``\ ’s documentation lives at `Read the Docs <https://pem.readthedocs.io/>`_, the code on `GitHub <https://github.com/hynek/pem>`_.


.. _MIT: http://choosealicense.com/licenses/mit/
.. _`PEM files`: https://en.wikipedia.org/wiki/X.509#Certificate_filename_extensions
.. _Apache: https://httpd.apache.org
.. _nginx: http://nginx.org/en/
.. _pyOpenSSL: http://www.pyopenssl.org/
.. _Twisted: https://twistedmatrix.com/documents/current/api/twisted.internet.ssl.Certificate.html#loadPEM
