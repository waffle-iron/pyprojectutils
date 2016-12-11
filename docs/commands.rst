********
Commands
********

initproject
===========

Initialize a project, creating various common files using intelligent defaults. Or at least *some* defaults.


lsprojects
==========

Find, parse, and collect project information.

.. code-block:: plain

    usage: lsprojects.py [-h] [-a] [-c= CLIENT_CODE] [--dirty] [-d]
                     [-n= PROJECT_NAME] [-p= PROJECT_HOME] [-s= STATUS]
                     [-t= PROJECT_TYPE] [-v] [--version]

    optional arguments:
      -h, --help            show this help message and exit
      -a, --all             Show projects even if there is no project.ini
      -c= CLIENT_CODE, --client= CLIENT_CODE
                            Filter by client organization. Use ? to list
                            organizations
      --dirty               Only show projects with dirty repos
      -d, --disk            Calculate disk space. Takes longer to run.
      -n= PROJECT_NAME, --name= PROJECT_NAME
                            Find a project by name and display it's information.
      -p= PROJECT_HOME, --path= PROJECT_HOME
                            Path to where projects are stored. Defaults to
                            /Users/shawn/Work
      -s= STATUS, --status= STATUS
                            Filter by project status. Use ? to list available
                            statuses.
      -t= PROJECT_TYPE, --type= PROJECT_TYPE
                            Filter by project type. Use ? to list available types.
      -v                    Show version number and exit.
      --version             Show verbose version information and exit.

Format of INI
-------------

You can provide a ``project.ini`` file to provide detail on the project that
cannot be gleaned from the file system.

.. code-block:: ini

    [project]
    category = django
    description = A description of the project.
    status = development
    tags = CRM, Sales
    title = Project Title
    type = website

    [business]
    code = PTL
    name = Pleasant Tents, LLC

    [client]
    code = ACME
    name = ACME, Inc

    [domain]
    name = example
    tld = com

The ``tags``, ``type``, ``scope``, and ``status`` may be whatever you like.

Sections
--------

Attributes of ``[project]`` section are used as is. ``[business]`` and
``[client]`` are used to identify the beneficiary and/or developer of the
project.

Other sections may be added as you see fit. For example, the ``[domain]``
section above.

Additional Data
---------------

Additional data may be displayed in the list output and when using the
``--name`` switch.

- The SCM and disk usage of the project may be automatically determined.
- The project tree is obtained with the ``tree`` command.

Generating a README
-------------------

The ``--name`` switch searches for a specific project and (if found) outputs
project information in `Markdown`_ format:

.. _Markdown: http://daringfireball.net/projects/markdown/

.. code-block:: bash

    cd example_project;
    lsprojects --name=example_project > README.markdown;

Although you'll likely want to customize the output, this is handy for
creating (or recreating) a README for the project.