Troubleshooting
===============

Read container logs::

    docker logs -f gemnasium

Enter running container::

    docker exec -it gemnasium /bin/bash

Known issues
^^^^^^^^^^^^

Gemnasium Enterprise is using ``setcap`` to allow our process running on port 80 and 443 (unless SSL is disabled via ``REDIRECT_HTTP_TO_HTTPS`` to false).
Some kernels don't support capacities operations inside containers, especially when AUFS is being used.
To avoid an error while running Gemnasium Enterprise, the api server will fallback to use a setuid bit on the server, meaning in the case the service is running as root inside the container.
While this is not a security issue for your host, it means the api has full control inside the container, including reading passwords and tokens.

If you are unsure your system is affected by this issue, check the logs of the api service in ``/var/log/gemnasium/api/current``. If ``setcap`` is failing, the message ``Warning: setcap not available, falling back to setuid`` will be displayed at the top of the log file.

If you want to avoid this issue, you can bind your own ports, higher then 1024, using the env vars ``GEMNASIUM_API_PORT_8080_TCP_PORT`` ``GEMNASIUM_API_SSL_PORT_8443_TCP_PORT``. If they are both above 1024, no setcap or setuid method will be used, and the webserver will run as a limited-rights user.
