Ruby
====

Supported features
------------------

* Gemfile and Gemfile.lock files are supported
* Gemspec files are supported
* Security advisories
* AutoUpdate

Limitations
------------

* Gemfile with ruby code to be evaluated are not interpreted. Most of the time, this is not an issue, because the Gemfile.lock is a static, generated yaml file.
* Private repositories and gems are not supported. They will be listed, but no status can be determined.

