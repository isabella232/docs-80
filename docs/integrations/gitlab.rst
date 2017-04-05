GitLab
======

GitLab.com
----------

Before being able to add projects from gitlab.com, Gemnasium Enterprise needs to be configured to access it.

This is a two steps process: firs you need to create an OAuth application on GitLab and then configure Gemnasium Enterprise to use that application.

.. _gitlab_add_oauth_application:

1. Adding the OAuth application on GitLab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- go on https://gitlab.com/profile/applications
- fill the form "Add new application":

  - **Name:** "Gemnasium Enterprise"
  - **Redirect URI:** ``{GEMNASIUM_INSTANCE_URL}/auth/auth/gitlab.com/sync/callback`` where you replace ``{GEMNASIUM_INSTANCE_URL}`` with the url of your Gemnasium Enterprise instance (example: `https://gemnasium.example.com/auth/auth/gitlab.com/sync/callback`)
  - **Scopes:** api

- Click on the "Save application" button.

You will need the "Application Id" and the "Secret" you see on the confirmation page for the next section.

2. Configure Gemnasium Enterprise to use GitLab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _gitlab_automatic_configuration:

A. Automatic configuration
**************************

A convenient script is provided to add both Sign In/up and project synchronization with Gitlab at once. If you don't want both features, check :ref:`gitlab_advanced_configuration`.

.. code-block:: console

  docker exec -it gemnasium configure

Select "GitLab.com", and then fill the corresponding fields with the values from the application created above.

Your Gemnasium Enterprise users are now able to login using their GitLab account.
A new source named "GitLab" is also available on the "Add Project" screen.

.. _gitlab_advanced_configuration:

B. Advanced configuration
*************************

The automatic configuration described above enables both Sign In/Up and project synchronization with Gitlab. This advanced configuration makes it possible to restrict the integration to one of these two features.

To enable Gitlab Sign In/Up only, run these commands:

.. code-block:: console

  docker exec -it gmenasium auth providers create gitlab.com gitlab 2.0 https://gitlab.com/oauth/authorize https://gitlab.com/oauth/token
  docker exec -it gemnasium auth clients create gitlab.com login {OAUTH_APPLICATION_ID} {OAUTH_APPLICATION_SECRET} api

To enable Gitlab Synchronization only, run these commands:

.. code-block:: console

  docker exec -it gmenasium auth providers create gitlab.com gitlab 2.0 https://gitlab.com/oauth/authorize https://gitlab.com/oauth/token
  docker exec -it gemnasium auth clients create gitlab.com sync {OAUTH_APPLICATION_ID} {OAUTH_APPLICATION_SECRET} api
  docker exec -it gemnasium repo-syncer sources create gitlab.com "Gitlab" gitlab https://api.gitlab.com/

``{OAUTH_APPLICATION_ID}`` and ``{OAUTH_APPLICATION_SECRET}`` must be replaced with the id and the secret of the OAuth application created on Gitlab.
See :ref:`gitlab_add_oauth_application` above.


GitLab CE/EE
------------

GitLab CE/EE is no different than GitLab.com, the steps are the same.

In step :ref:`gitlab_add_oauth_application`, just replace ``gitlab.com`` with your private GitLab CE/EE instance host (example: `https://gemnasium.example.com/auth/auth/private-gitlab.example.com/sync/callback`).


When using :ref:`gitlab_automatic_configuration`, make sure to select "GitLab CE/EE" instead of "GitLab.com". The script will ask for your GitLab instance URL, and to name it.

When using :ref:`gitlab_advanced_configuration`, make sure to replace all occurences of ``gitlab.com`` with your private GitLab CE/EE instance host. You also need to replace ``"Gitlab"`` with the name you want in the last command to enable synchronization feature. This is the name of the source that will show up in the "Add projects" page.

Several GitLab CE/EE instances can be configured, just name them accordingly to avoid confusion.

Requirements
^^^^^^^^^^^^

Gemnasium Enteprise is compatible with GitLab >= 8.14.
There is a bug in nginx affecting lower versions of GitLab.
