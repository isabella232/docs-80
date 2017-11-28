Welcome
=======

Welcome to the Gemnasium Enterprise |version| documentation, where you can find information and guides to help you with Gemnasium Enterprise and start exploring its features.

Use the left navigation bar to browse the documentation, the Search bar in the top-left to look for something specific, or the links below to access some highlights.

.. note:: Gemnasium Enterprise Edition will be referred as "GEE" in this documentation

Release Notes
=============

1.4.3 - 2017-11-28
------------------

* [BUG] Fix Bitbucket Server oauth sign-in when hosted in a subdirectory (e.g.: https://example.com/bitbucket)
* [BUG] Fix the commit date displayed on the project page.
* [FEATURE] Plain sign-up (with user/password) can now be disabled with the env var `DISABLE_PLAIN_AUTH`


1.4.2 - 2017-11-15
------------------

* [BUG] Fix Bitbucket Server integration when hosted in a subdirectory (e.g.: https://example.com/bitbucket)

1.4.1 - 2017-11-13
------------------

* [BUG] Fix a regression affecting Bitbucket Server integration

1.4.0 - 2017-10-26
------------------

* [FEATURE] Java (Maven support)

1.3.1 - 2017-06-20
------------------

* [SECURITY] CSP headers have been refined
* [BUG] Fix a bug randomly preventing some users to auth with user / password (when OAuth login sources are present)
* [BUG] Fix a bug in Slack hook creation (returned URL was escaped twice)
* [BUG] Fix sidebar when browsing GEE anonymously
* [BUG] Fix broken page when coming back from Slack OAuth with error
* [BUG] Fix projects not being removed from dashboard after deletion
* [BUG] Repos metadata were not synchronized before the project was actually synced
* [BUG] Other minor fixes

1.3.0 - 2017-05-19
------------------

* [FEATURE] Allow to search and filter projects and project dependencies.
* [BUG] Fix project settings for synced projects

1.2.2 - 2017-05-03
------------------

* [FEATURE] Project repositories are now synced daily. In case a webhook is not working, the project will be up-to-date at least once per day
* [FEATURE] Project logs improved, displaying the user (with their IP) who triggered the entry
* [FEATURE] Add link to team invitation, in case the email is not received by the invitee (particularly usefull if SMTP is not configured)
* [BUG] Some logs were not flushed to disk on exit (when restarting Gemnasium Enteprise)

1.2.1 - 2017-04-19
------------------

* [FEATURE] Add :ref:`letsencrypt` support
* [FEATURE] Support Python "compatible release" operator (``~=``) as specified in `PEP 440 <https://www.python.org/dev/peps/pep-0440/#compatible-release>`_
* [BUG] Invitations to team were sent again if role was updated

1.2.0 - 2017-04-10
------------------

* [FEATURE] Add package pages
* [FEATURE] Add Packages changelogs
* [FEATURE] Project page revamped
* [FEATURE] Add Yarn support
* [DOC] Fix documentation for integrations
* [BUG] Fix a bug with PHP dependencies using the caret operator
* [BUG] The button "Refresh repositories" was emptying the list with bitbucket.org

1.1.3 - 2017-03-21
------------------

* Gemnasium Enterprise is now also available on Quay.io

1.1.2 - 2017-02-16
------------------

* [BUG] Minor bug and fixes
* [BUG] UI pages now expose an error to the user if the backend is not available.
* [FEATURE] New button to copy the notification channels of a project to all the projects of the team
* [FEATURE] New ``MAILER_EMAIL_FROM`` env var to specify the sender of GEE email notifications
* [DOC] Added documentation for CA certs used in integrations
* [DOC] Added documentation for users behind proxies

1.1.1 - 2017-02-03
------------------

* [BUG] Fix webhook handler. The service in charge of receiving and triggering a project sync was returning a 200 and dropping the event in some cases.

1.1.0 - 2017-01-31
------------------

* [FEATURE] Add Bitbucket Server support
* [BUG] Weekly digests are now sent on Monday mornings, 8am, instead of Sunday at midnight
* [BUG] Adding an empty project from GitHub/Gitlab/bitbucket.org was causing
  the webhook registration to fail. The project bootstrapping was considered
  as finished, and the project was not synced after the first commit.

Note: We have switched to `Webpack 2 <https://webpack.js.org/>`_ for assets bundling, this is transparent for users.

1.0.0 - 2017-01-27
------------------

Same as 1.0.0-rc1.


1.0.0-rc1 - 2017-01-16
----------------------

This is the last pre-release before 1.0.0, if no bug is found.

* [FEATURE] Add Bitbucket.org (Bitbucket Cloud) Support
* [FEATURE] Add project logs with realtime update
* [FEATURE] Improve project notification channels configuration
* [FEATURE] Allow to edit existing project notification channel
* [FEATURE] Improve user notifications configuration
* [BUG] Fix various UI bugs
* [BUG] Some PHP packages were not fully synced

1.0.0-beta4 - 2016-12-15
------------------------

* [FEATURE] "New package release" notifications via Slack and email
* [BUG] Fix file upload form when adding unsupported file
* [BUG] Fix left menu bar behavior on small devices layout
* [BUG] Fix oauth signup error handling

1.0.0-beta3 - 2016-11-29
------------------------

* [FEATURE] GitLab Support
* [FEATURE] New notifications in the UI


Known issues:

* [BUG][GITLAB] Symlinks on dependency files are not followed
* [BUG][GITLAB] Dependency files greater than 2MB are ignored
* [BUG] Can't sign-in using an oauth account if the same email is already used

1.0.0-beta2 - 2016-11-18
------------------------

* [FEATURE] Display commits in project page
* [FEATURE] Internal logging (live feeds will be available in beta3)

* [BUG] Fix a security issue when adding a project to a team. The tokens of the team owner were used instead of the user's.
* [BUG] Fix display issues in Firefox
* [BUG] Fix UI Cache issues
* [BUG] Offline projects color was not updated when pushing new dependency files
* [BUG] Sync was failing when commit already existed
* [BUG] Fix a bug preventing to upload new files in Offline projects

Known issues:

* [FEATURE] Gitlab support is delayed to beta3
* [BUG] Can't sign-in using an oauth account if the same email is already used

1.0.0-beta1 - 2016-10-21
------------------------

* First private beta
* GitHub.com and GitHub Enterprise support
* Slack integration for notifications
