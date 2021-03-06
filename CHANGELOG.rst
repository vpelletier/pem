.. :changelog:

Changelog
=========

Versions are year-based with a strict backward compatibility policy.
The third digit is only for regressions.


16.2.0 (UNRELEASED)
-------------------

Changes:
^^^^^^^^

*none*


----


16.1.0 (2016-04-08)
-------------------

Deprecations:
^^^^^^^^^^^^^

- Passing ``dhParameters`` to ``pem.twisted.certifateOptionsFromPEMs`` and ``certificateOptionsFromFiles`` is now deprecated;
  instead, include the DH parameters in the PEM objects or files.

Backward-incompatible changes:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- Python 3.3 and 2.6 aren't supported anymore.
  They may work by chance but any effort to keep them working has ceased.

  The last Python 2.6 release was on October 29, 2013 and isn't supported by the CPython core team anymore.
  Major Python packages like Django and Twisted dropped Python 2.6 a while ago already.

  Python 3.3 never had a significant user base and wasn't part of any distribution's LTS release.

Changes:
^^^^^^^^

- ``pem.twisted.certificateOptionsFromPEMs`` and ``certificateOptionsFromFiles`` will now load Ephemeral Diffie-Hellman parameters if found.
  `#21 <https://github.com/hynek/pem/pull/21>`_
- PEM objects now correctly handle being constructed with unicode and bytes on both Python 2 and 3.
  `#24 <https://github.com/hynek/pem/pull/24>`_
- PEM objects now have an ``as_bytes`` method that returns the PEM-encoded content as bytes, always.
  `#24 <https://github.com/hynek/pem/pull/24>`_
- PEM objects are now hashable and comparable for equality.
  `#25 <https://github.com/hynek/pem/pull/25>`_



----


16.0.0 (2016-02-05)
-------------------

Changes:
^^^^^^^^

- PKCS #8 keys are now supported.
  `#14 <https://github.com/hynek/pem/pull/14>`_
- ``pem`` is now fully functional without installing Twisted.
  `#16 <https://github.com/hynek/pem/pull/16>`_


----


15.0.0 (2015-07-10)
-------------------

Deprecations:
^^^^^^^^^^^^^

- The usage of Twisted helpers from the pem module is deprecated.
  Use their pendants from the ``pem.twisted`` module now.
- The usage of the backport of ephemeral Diffie-Hellman support is hereby deprecated.
  Nobody should use a Twisted release that is older than 14.0.0 because it contains essential SSL/TLS fixes.

Changes:
^^^^^^^^

- Support PEM strings that do not end with a new line.
  `#12 <https://github.com/hynek/pem/pull/12>`_
- Support PEM strings that end with ``\r\n``.
- The Twisted-related helpers have been moved to ``pem.twisted``.


----


0.3.0 (2014-04-15)
------------------

Changes:
^^^^^^^^

- Load PEM files as UTF-8 to allow for non-ASCII comments (like in certifi).
- Allow keys, primary certificates, and chain certificates to occur in any order.


----


0.2.0 (2014-03-13)
------------------

Changes:
^^^^^^^^

- Add forward-compatible support for DHE.


----


0.1.0 (2013-07-18)
------------------

Initial release.
