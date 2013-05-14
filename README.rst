phpMyAdmin on dotCloud
======================

This sample creates an application with three services: PHP and two MySQL. 
This is just an example to show how a single phpMyAdmin can access more than one MySQL service in the same application.

To deploy `phpMyAdmin <http://www.phpmyadmin.net/>`_ on dotCloud::

    git clone git://github.com/dotcloud/phpmyadmin-on-dotcloud
    cd phpmyadmin-on-dotcloud
    dotcloud create phpmyadmin
    dotcloud push
    dotcloud open

At the end of the build you can visit the url displayed and login into
phpMyAdmin (that's what ``dotcloud open`` does). 
You will need the password for the root user of the MySQL
database to login, find it out with::

    dotcloud env list | grep -i mysql

Using phpMyAdmin in Your Application
------------------------------------

This sample uses an `approot <http://docs.dotcloud.com/guides/build-file/#specifying-the-root-directory-of-a-service>`_ 
to make it easy to include the code in your own application. Just copy the whole ``pmaroot`` directory
to your application and add copy the ``pma`` section from ``dotcloud.yml`` to your ``dotcloud.yml``.

This service discovers the MySQL servers in your application by
reading the `Environment File <http://docs.dotcloud.com/guides/environment/>`_.  If you use multiple
MySQL servers, phpMyAdmin will display a drop down list that lets you
select which server you want to log into.
