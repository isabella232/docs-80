GitHub
======

GitHub.com
----------

Before being able to add projects from github.com, Gemnasium Enterprise needs to be configured to access it.

This is a two steps process: firs you need to create OAuth applications on GitHub and then configure Gemnasium Enterprise to use them.

.. _github_add_oauth_applications:

1. Adding OAuth applications on GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Gemnasium Enterprise needs **two different OAuth applications**. One to enable "Login with GitHub" and one to synchronize projects.

To do that:

- go on https://github.com/settings/developers (or alternatively, add the application to an organization: https://github.com/organizations/[your_org]/settings/applications)
- click on the "Register a new application" and fill the form:

  - **Name:** "Gemnasium Enterprise Login"
  - **Homepage URL:** your Gemnasium Enterprise base URL (example: `https://gemnasium.example.com/`)
  - **Authorization callback URL:** ``{GEMNASIUM_INSTANCE_URL}/auth/auth/github.com/login/callback`` where you replace ``{GEMNASIUM_INSTANCE_URL}`` with the url of your Gemnasium Enterprise instance (example: `https://gemnasium.example.com/auth/auth/github.com/login/callback`)

- Click on the "Register application" button.

You will need the "Client ID" and "Client Secret" you see on the confirmation page for the next section. You can keep that tab open and open a new tab to https://github.com/settings/developers to create the second application.

To create the second application required:

- go on https://github.com/settings/developers
- click on the "Register a new application"  and fill the form:

  - **Name:** "Gemnasium Enterprise Sync"
  - **Homepage URL:** your Gemnasium Enterprise base URL (example: `https://gemnasium.example.com/`)
  - **Authorization callback URL:** ``{GEMNASIUM_INSTANCE_URL}/auth/auth/github.com/sync/callback`` where you replace ``{GEMNASIUM_INSTANCE_URL}`` with the url of your Gemnasium Enterprise instance (example: `https://gemnasium.example.com/auth/auth/github.com/sync/callback`)

- Click on the "Register application" button.

.. _github_configuration:

2. Configure Gemnasium Enterprise to use GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A convenient script is provided to configure your instance:

.. code-block:: console

  docker exec -it gemnasium configure

Select "GitHub.com", and then fill the corresponding fields with the values from the applications created above. Be careful not to confuse **Sync** and **Login** applications!

Your Gemnasium Enterprise users are now able to login using their GitHub account.
A new source named "GitHub" is also available on the "Add Project" screen.


GitHub Enterprise
-----------------

GitHub Enterprise is no different than GitHub.com, the steps are the same.

In step :ref:`github_add_oauth_applications`, just replace ``github.com`` with your private GitHub Enterprise instance host (example: `https://gemnasium.example.com/auth/auth/private-github.example.com/login/callback`).

In step :ref:`github_configuration`, make sure to select "GitHub Enterprise" instead of "GitHub.com". The script will ask for your GitHub Enterprise instance URL, and to name it.

Several GitHub Enterprise instances can be configured, just name them accordingly to avoid confusion.


Requirements
^^^^^^^^^^^^

Gemnasium Enterprise has been tested against GitHub Enterprise >=2.7.X.
If your version is older than 2.7 series, please contact our support.
