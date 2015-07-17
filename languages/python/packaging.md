Python Examples
===============

Package with console scripts
----------------------------

    setup(
        ...
        entry_points={
            'console_scripts': [
                'foo = bin.foo_sript:main',
            ],
        },
        ...
    )

This calls into the script located in your ```bin``` directory and runs the ```main``` function inside the ```foo_script``` file.

Windows will create a binary called foo.exe that can be ran from the command line.


Reference Data Files from inside an egg
---------------------------------------

I ran into the issue on either always having zip_safe set to false for every package or I would have to copy config/data files from my package directory into the python Scripts directory.

After months of just ignoring the issue I decided to solve the issue and quickly found the answer.

Do not use os.path(__file__) as your reference but use the Package resource manager provided by setuptools.

    logging_config = resource_filename(__name__, 'logging.ini')

For the full manual and advanced stuff you can find the documentation [here](https://pythonhosted.org/setuptools/pkg_resources.html).
