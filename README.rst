=======================
Python ENDESIVE library
=======================

The ASN.1 implementation depends on `asn1crypto`_.
Cryptographic routines depend on `oscrypto`_ and `cryptography`_ libraries, so everything is
'pure python'.

For certificate verification OpenSSL is used but I would not trust it,
next version should switch to `certvalidator`_ or `pycrypto`_.

This library implements S/MIME handler which can encrypt and decrypt S/MIME messages
using a public RSA key, in AES-128/192/256 CBC/OFB modes.
It can also sign and verify S/MIME messages.

This library implements CAdES-B handler for signing and verifying PDF documents in
Adobe.PPKLite/adbe.pkcs7.detached form.
It can sign documents during generation using a modified version of `pyfpdf` which is
included in this library. It can also sign documents generated by external programms.

This library implements XADES-BES handler for creating signed xml files.

This library implements CMS handler for signing and verifying plain text files with
detached signature files.

License
=======

This software is licensed under the MIT License. See the LICENSE file in
the top distribution directory for the full license text.


Requirements
============

* Python 3.*
* `cryptography`_
* `asn1crypto`_
* `oscrypto`_
* `pdfminer.six`_
* `lxml`_

Examples
========

cert-make.py
    Create required certificates (password is 1234)

pdf-make.py
    Create simple two paged PDF document which is used in pdf-sign-cms.py.
pdf-sign-cms.py
    Create signature in externally created PDF.
pdf-sign-fpdf.py
    Create signature while creating PDF.
pdf-verify.py
    Verify prevously generated files (cms/pdf).

plain-make.py
    Create simple UTF-8 text file.
plain-openssl.sh
    Sign, encrypt and decrypt text file with help of openssl executable.
plain-sign-attr.py
    Sign text file with 'extended' CMS attributes.
plain-sign-noattr.py
    Sign text file without 'extended' CMS attributes.
plain-verify.py
    Verify all generated signatures for text file.

smime-make.py
    Create simple UTF-8 text file for use in following examples.
smime-openssl.sh
    Create signed S/MIME file, encrypted S/MIME file and decrypt generated S/MIME file
    with help of openssl executable.
smime-encrypt.py
    Create encrypted S/MIME file.
smime-decrypt.py
    Decrypt encrypted S/MIME file.
smime-sign-attr.py
    Create signed S/MIME file with 'extended' CMS attributes.
smime-sign-noattr.py
    Create signed S/MIME file without 'extended' CMS attributes.
smime-verify.py
    Verify all generated S/MIME files.

xml-make.py
    Create simple xml file for use in following examples.
xml-xades-bes-sign-b64.py
    Create xml file with base64 encoded embedded source file inside own content.
xml-xades-bes-sign-xml.py
    Create xml file with no encoded but still embedded source file inside own content.
xml-xades-bes-read.py
    Decode generated xml signatures and extract their content.

.. _cryptography: https://github.com/pyca/cryptography
.. _asn1crypto: https://github.com/wbond/asn1crypto
.. _oscrypto: https://github.com/wbond/oscrypto
.. _certvalidator: https://github.com/wbond/certvalidator
.. _pyfpdf: https://github.com/reingart/pyfpdf
.. _pdfminer.six: https://pypi.org/project/pdfminer.six/
.. _lxml: https://pypi.org/project/lxml/