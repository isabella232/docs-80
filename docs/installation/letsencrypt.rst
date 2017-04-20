.. _letsencrypt:

Let's Encrypt Certificates
==========================

Let's Encrypt is a free, automated, and open Certificate Authority (CA). You can obtain a valid certificate for your Gemnasium Enterprise instance.
There are two different ways to configure your instance to use Let's Encrypt: Using the integrated client, or using a custom process.

.. seealso::

    `Let's Encrypt documentation online <https://letsencrypt.org/how-it-works/>`_ for detailled information


Integrated Let's Encrypt client
-------------------------------

Gemnasium Entreprise features a Let's Encrypt client with:

- Automatic renewal (one week before expiration)
- TLS-SNI domain validation

The generated certificate will be saved in ``/etc/gemnasium/ssl`` along with its private key. If you want to cache/persist these files, mount a volume into your container for this path.

Limitations
^^^^^^^^^^^

By default, the client proves control by answering an HTTPS-based challenge. This requires the host name to resolve to the IP address of a (single) computer running Gemnasium Enterprise.
Typically, the challenge won't work on a shared SSL LoadBalancer with SNI, because let's encrypt will use server names like ``*.acme.invalid``.

This also means you will probably not be able to get a certificate for your local machine (unless it's exposed directly to the internet).

Custom process
--------------

EFF is providing a full-featured acme client:

https://certbot.eff.org/

Getting the certificate, renew it, etc. must be done outside the Gemnasium container, otherwise your changes will be lost during next Gemnasium update deployment.
The generated certificate and key should be installed (ie: mounted into the docker container) directly in ``/etc/gemnasium/ssl`` as explained in the :ref:`ssl_configuration` section.
