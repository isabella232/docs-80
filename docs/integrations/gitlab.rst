GitLab
======

GitLab.com
----------

Before being able to add projects from gitlab.com, Gemnasium Enterprise needs to be configured to be able to access it.

This is a two steps process: first, create an OAuth application on GitLab then configure Gemnasium Enterprise to use that application.

Adding the OAuth application on GitLab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The first step we need to do create a new OAuth application.

To do that:

- go on https://gitlab.com/profile/applications
- fill the form "Add new application":

  - **Name:** "Gemnasium Enterprise"
  - **Redirect URI:** ::``{GEMNASIUM_INSTANCE_URL}/auth/auth/{GITLAB_HOST}/sync/callback`` where you replace ``{GEMNASIUM_INSTANCE_URL}`` with the url of your Gemnasium Enterprise instance and ``{GITLAB_HOST}`` with 'gitlab.com' (example: "https://gemnasium.example.com/auth/auth/gitlab.com/sync/callback")

- Enable the "api" Scope
- Click on the "Save application" button.

You will need the application Id & secret you see on the confirmation page for the next section.

Configure Gemnasium Enterprise to use GitLab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A convenient script is provided to add everything at once:

.. code-block:: console

  docker exec -it gemnasium configure

Select "GitLab.com", and then fill the corresponding fields with the values from the apps created above.

Your Gemnasium Enterprise users are now able to login using their GitLab account.
A new source named "GitLab" is also available on the "Add Project" screen.


GitLab CE/EE
------------

GitLab CE/EE is no different than GitLab, the steps are the same as above. Just replace ``{GITLAB_HOST}`` with your private GitLab instance host.
(example: "https://gemnasium.example.com/auth/auth/gitlab.example.com/sync/callback")

When using the configuration script, make sure to select "GitLab CE/EE" instead of "GitLab.com". The script will ask for your GitLab instance URL, and to name it.

Several GitLab instances can be configured, just name them accordingly.

Requirements
^^^^^^^^^^^^

Gemnasium Enteprise is compatible with GitLab >= 8.14.
There is a bug in nginx affecting lower versions of GitLab.
