osg-jupyter-docker
==================

OSG's container images for customizing Jupyter


Images
------

- `<k8s-hub/>`_:
  The main "hub" image for `Z2JH`_.
  Includes a custom version of the `oauthenticator`_ package.
  Includes the `osg-jupyter`_ package.

- `<sssd/>`_:
  An image for running `sssd <https://sssd.io>`_.
  Requires configuration.

.. _Z2JH: https://z2jh.jupyter.org/
.. _oauthenticator: https://github.com/brianaydemir/jupyterhub-oauthenticator
.. _osg-jupyter: https://github.com/brianaydemir/osg-jupyter
