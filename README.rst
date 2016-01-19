Fat Tire
----------

Fat Tire (fat-tire) creates a single, fat Python wheel out of multiple skinny ones.

Rationale
^^^^^^^^^^^

The primary purpose for fat-tire is to make it easy to distribute python source
packages which include proprietary or otherwise code that can be installed by
pip. By private, meaning that the source package includes code that is not
available on a public PyPI mirror. Let's call this resulting package a
"FatTire." The FatTire emulates the `"fat jar"
<http://www.javacodegeeks.com/2012/11/packing-your-java-application-as-one-or-fat-jar.html>`_
concept popular in Java-Land. One nice side-effect of FatTire is that you do not need
Internet access to install one as all dependencies are included.

How it Works
^^^^^^^^^^^^

The `fat-tire` command takes a `requirements.txt` file and the path to a target python
project with a valid `setup.py` script. fat-tire builds or downloads wheels for each dependency listed
in the requirements.txt and builds a wheel for the current project. Next, fat-tire unpacks all of the resulting wheels and repacks them in into a single wheel named after the target project.

For those not familiar with `requirements files <https://pip.pypa.io/en/stable/user_guide/#requirements-files>`_, they can pull
dependencies from various sources, including `private source control
repositories <https://pip.pypa.io/en/stable/reference/pip_install/#git>`_.

Here is the structure of the `fat-tire` command::

  # fat-tire [-r REQUIREMENTS_FILE] [PATH_TO_PYTHON_PROJECT]

And an actual invocation::

  # cd mypythonproject
  # fat-tire -r requirements.txt .

The output will be `dist/mypythonproject-0.0.1-py2-none-any.whl` and it will include the content of all
the wheels for the dependencies specified in requirements.txt



Author
^^^^^^^

`Bryan W. Berry <mailto:bryan.berry@gmail.com>`_
