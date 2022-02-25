Welcome to Lumache's documentation!
===================================

**Lumache** (/lu'make/) is a Python library for cooks and food lovers
that creates recipes mixing random ingredients.
It pulls data from the `Open Food Facts database <https://world.openfoodfacts.org/>`_
and offers a *simple* and *intuitive* API.
Lumache has its documentation hosted on Read the Docs.

Check out the :doc:`usage` section for further information, including
how to :ref:`installation` the project.

.. note::

   This project is under active development.
 
.. table:: 
 :width: 100 
 :widths: 25 20 20 35 
 :class: tight-table

 +--------------------------+--------------------+----------------------+-----------------------------------+
 |Property name             |Type                |Default value \/      |Description                        |
 |                          |                    |mandatory             |                                   |
 +==========================+====================+======================+===================================+
 |container.security.       |[ALLOW, DENY]       |ALLOW                 |Controls whether proxy             |
 |truststore.allowProxy     |                    |                      |certificates are supported.        |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |[keystore, openssl, |mandatory to be set   |The truststore type.               |
 |truststore.type           |directory]          |                      |                                   |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |integer number      |600                   |How often the truststore should    |
 |truststore.               |                    |                      |be reloaded, in seconds. Set to    |
 |updateInterval            |                    |                      |negative value to disable          |
 |                          |                    |                      |refreshing at runtime. (runtime    |
 |                          |                    |                      |updateable)                        |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |integer number      |15                    |Connection timeout for fetching    |
 |truststore.               |                    |                      |the remote CA certificates in      |
 |directoryConnectionTimeout|                    |                      |seconds.                           |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |filesystem path     |\-                    |Directory where CA certificates    |
 |truststore.               |                    |                      |should be cached, after            |
 |directoryDiskCachePath    |                    |                      |downloading them from a remote     |
 |                          |                    |                      |source. Can be left undefined if   |
 |                          |                    |                      |no disk cache should be used.      |
 |                          |                    |                      |Note that directory should be      |
 |                          |                    |                      |secured, i.e. normal users should  |
 |                          |                    |                      |not be allowed to write to it.     |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |[PEM, DER]          |PEM                   |For directory truststore controls  |
 |truststore.               |                    |                      |whether certificates are encoded   |
 |directoryEncoding         |                    |                      |in PEM or DER. Note that the PEM   |
 |                          |                    |                      |file can contain arbitrary number  |
 |                          |                    |                      |of concatenated, PEM\-encoded      |
 |                          |                    |                      |certificates.                      |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |list of properties  |\-                    |List of CA certificates locations. |
 |truststore.               |with a common       |                      |Can contain URLs, local files and  |
 |directoryLocations.\*     |prefix              |                      |wildcard expressions. (runtime     |
 |                          |                    |                      |updateable)                        |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |string              |\-                    |The keystore type (jks, pkcs12)    |
 |truststore.               |                    |                      |in case of truststore of keystore  |
 |keystoreFormat            |                    |                      |type.                              |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |string              |\-                    |The password of the keystore type  |
 |truststore.               |                    |                      |truststore.                        |
 |keystorePassword          |                    |                      |                                   |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |string              |\-                    |The keystore path in case of       |
 |truststore.keystorePath   |                    |                      |truststore of keystore type.       |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |[true, false]       |false                 |In case of openssl truststore,     |
 |truststore.               |                    |                      |specifies whether the trust store  |
 |opensslNewStoreFormat     |                    |                      |is in openssl 1.0.0+ format        |
 |                          |                    |                      |(true) or older openssl 0.x        |
 |                          |                    |                      |format (false)                     |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |[GLOBUS_EUGRIDPMA,  |EUGRIDPMA_GLOBUS      |In case of openssl truststore,     |
 |truststore.opensslNsMode  |EUGRIDPMA_GLOBUS,   |                      |controls which (and in which       |
 |                          |GLOBUS, EUGRIDPMA,  |                      |order) namespace checking rules    |
 |                          |GLOBUS_EUGRIDPMA\_  |                      |should be applied. The REQUIRE     |
 |                          |REQUIRE, EUGRIDPMA\_|                      |settings will cause that all       |
 |                          |GLOBUS_REQUIRE,     |                      |configured namespace definitions   |
 |                          |GLOBUS_REQUIRE,     |                      |files must be present for each     |
 |                          |EUGRIDPMA_REQUIRE,  |                      |trusted CA certificate (otherwise  |
 |                          |EUGRIDPMA_AND\_     |                      |checking will fail). The AND       |
 |                          |GLOBUS, EUGRIDPMA\_ |                      |settings will cause to check both  |
 |                          |AND_GLOBUS_REQUIRE, |                      |existing namespace files.          |
 |                          |IGNORE]             |                      |Otherwise the first found is       |
 |                          |                    |                      |checked (in the order defined by   |
 |                          |                    |                      |the property).                     |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |filesystem path     |\/etc\/grid\-         |Directory to be used for opeenssl  |
 |truststore.opensslPath    |                    |security\/certificates|truststore.                        |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |integer number      |15                    |Connection timeout for fetching    |
 |truststore.               |                    |                      |the remote CRLs in seconds (not    |
 |crlConnectionTimeout      |                    |                      |used for Openssl truststores).     |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |filesystem path     |\-                    |Directory where CRLs should be     |
 |truststore.               |                    |                      |cached, after downloading them     |
 |crlDiskCachePath          |                    |                      |from remote source. Can be left    |
 |                          |                    |                      |undefined if no disk cache should  |
 |                          |                    |                      |be used. Note that directory       |
 |                          |                    |                      |should be secured, i.e. normal     |
 |                          |                    |                      |users should not be allowed to     |
 |                          |                    |                      |write to it. Not used for Openssl  |
 |                          |                    |                      |truststores.                       |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |list of properties  |\-                    |List of CRLs locations. Can        |
 |truststore.crlLocations.  |with a common       |                      |contain URLs, local files and      |
 |\*                        |prefix              |                      |wildcard expressions. Not used     |
 |                          |                    |                      |for Openssl truststores. (runtime  |
 |                          |                    |                      |updateable)                        |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |[REQUIRE, IF_VALID, |IF_VALID              |General CRL handling mode. The IF\_|
 |truststore.crlMode        |IGNORE]             |                      |VALID setting turns on CRL         |
 |                          |                    |                      |checking only in case the CRL is   |
 |                          |                    |                      |present.                           |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |integer number      |600                   |How often CRLs should be updated,  |
 |truststore.               |                    |                      |in seconds. Set to negative value  |
 |crlUpdateInterval         |                    |                      |to disable refreshing at runtime.  |
 |                          |                    |                      |(runtime updateable)               |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |integer number      |3600                  |For how long the OCSP responses    |
 |truststore.ocspCacheTtl   |                    |                      |should be locally cached in        |
 |                          |                    |                      |seconds (this is a maximum value,  |
 |                          |                    |                      |responses won't be cached after    |
 |                          |                    |                      |expiration)                        |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |filesystem path     |\-                    |If this property is defined then   |
 |truststore.ocspDiskCache  |                    |                      |OCSP responses will be cached on   |
 |                          |                    |                      |disk in the defined folder.        |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |list of properties  |\-                    |Optional list of local OCSP        |
 |truststore.               |with a common       |                      |responders                         |
 |ocspLocalResponders.      |prefix              |                      |                                   |
 |\<NUMBER\>                |                    |                      |                                   |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |[REQUIRE, IF\_      |IF_AVAILABLE          |General OCSP ckecking mode.        |
 |truststore.ocspMode       |AVAILABLE, IGNORE]  |                      |REQUIRE should not be used unless  |
 |                          |                    |                      |it is guaranteed that for all      |
 |                          |                    |                      |certificates an OCSP responder is  |
 |                          |                    |                      |defined.                           |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |integer number      |10000                 |Timeout for OCSP connections in    |
 |truststore.ocspTimeout    |                    |                      |miliseconds.                       |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |[CRL_OCSP, OCSP\_   |OCSP_CRL              |Controls overal revocation         |
 |truststore.               |CRL]                |                      |sources order                      |
 |revocationOrder           |                    |                      |                                   |
 +--------------------------+--------------------+----------------------+-----------------------------------+
 |container.security.       |[true, false]       |false                 |Controls whether all defined       |
 |truststore.               |                    |                      |revocation sources should be       |
 |revocationUseAll          |                    |                      |always checked, even if the first  |
 |                          |                    |                      |one already confirmed that a       |
 |                          |                    |                      |checked certificate is not         |
 |                          |                    |                      |revoked.                           |
 +--------------------------+--------------------+----------------------+-----------------------------------+


Hallo


Contents
--------

.. toctree::

   usage
   api
