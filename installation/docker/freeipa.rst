
Freeipa LDAP version: 4.4.0
=========================================

Docker
-----------------
FreeIPA server can be run in a Docker container for testing or demo purposes. It makes it possible to run all the processes comprising the server in an isolated way, leaving the host free to run other software, not clashing with the FreeIPA server.

This install is done on Ubuntu 16.04. FreeIPA is focused on Linux (and other standards compliant) systems. FreeIPA is focused on Linux (and other standards compliant) systems. Therefore, in our knowledge, you cannot run a container of a FreeIPA server on **Mac** or **Windows**. However, any help in this direction is very welcomed!!


Follow these steps to run our FreeIPA server docker:

1 Create a directory which will hold the server data:

.. code-block:: bash

   mkdir /var/lib/ipa-data

2  Edit */etc/hosts* and ensure that the IPA server address is listed. This is required for Apache to work properly. You have to change IPA_SERVER_IP with the ipa server ip:

.. code-block:: bash

       127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
       ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
       IPA_SERVER_IP	ipa.example.test


3 Finally, You run the container:

.. code-block:: bash

    docker run -it -p 389:389 -p 443:443 -p 636:636 --name freeipaldap --cap-add SYS_ADMIN --security-opt seccomp:unconfined -v /sys/fs/cgroup:/sys/fs/cgroup:ro --tmpfs /run --tmpfs /tmp -v /var/lib/ipa-data:/data:Z -h ipa.example.test italia/freeipa-server --ds-password=The-directory-server-password --admin-password=The-admin-password

where:

- *--cap-add SYS_ADMIN*, performs a range of system administration operations (see `here <https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities>`_ for more details ).
- *--security-opt seccomp:unconfined* to run a container without the default seccomp profile (see `here <https://docs.docker.com/engine/security/seccomp/>`_ for more details ).
- *-v /var/lib/ipa-data:/data:Z* to store data and configurations in the folder */var/lib/ipa-data/*
Answer to the question:

        Do you want to configure integrated DNS (BIND)? [no]:   --> press "Enter"

        Server host name [ipa.example.test]:                    --> press "Enter"

        Please confirm the domain name [example.test]:          --> press "Enter"

        Please provide a realm name [EXAMPLE.TEST]:             --> press "Enter"

        Continue to configure the system with these values? [no]:  --> type "y" and press "Enter"

Wait some time until freeipa server is completely configured and started.
The server is ready when on the shell appear the followuing message:

        FreeIPA server configured.

NOTE: Only first time that build image and run docker you need to ask to previous questions.

- You can connect to Freeip Server with web interface:
        https://IPA_SERVER_IP:443
        USER admin
        PW adminpassword

- You can also connect with LDP client with Server IP address IPA_SERVER_IP

- The container can the be started and stopped with the following commands:

        docker stop freeipaldap

        docker start freeipaldap


References
-----------------
[1] `FreeIpa docker-hub documentation <https://hub.docker.com/r/freeipa/freeipa-server/>`_.

[2] `Using Free Ipa for user authentication <https://annvix.com/using_freeipa_for_user_authentication>`_.

[3] `FreeIpa website <https://www.freeipa.org/page/Docker>`_.
