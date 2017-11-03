Java
====

Supported features
------------------

* Maven packages hosted on Maven Central
* Maven POM XML
* Security advisories

Limitations
------------

* Gradle config files are not yet supported
* Ivy config files
* What's not supported in POM XML:

  - Inheritance (coming soon)
  - Aggregation
  - Repositories
  - Plugins

Tools
-----------------

To draw full benefit from the Maven support we recommend to use the `Gemnasium Maven Plugin <https://github.com/gemnasium/gemnasium-maven-plugin>`_.

.. note:: Gemnasium doesn't process the repositories element since it only knows about the artefacts hosted on Maven Central.

