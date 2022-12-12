Docker Images for OSG's JupyterHub Instance
===========================================

These images are used to customize Zero to JupyterHub with Kubernetes
(Z2JH_) with software that makes it easier to integrate the JupyterHub
instance with the OSPool_.

.. _Z2JH: https://z2jh.jupyter.org/
.. _OSPool: https://osg-htc.org/services/open_science_pool.html


Overview
--------

- `<k8s-hub/>`_:

  - The main "hub" image for Z2JH.
  - Includes a custom version of the oauthenticator_ package.
  - Includes the osg-jupyterhub-hooks_ package.

- `<sssd/>`_:

  - An image for running sssd_.
  - Requires configuration.

.. _oauthenticator: https://github.com/brianaydemir/jupyterhub-oauthenticator
.. _osg-jupyterhub-hooks: https://github.com/osg-htc/jupyterhub-hooks
.. _sssd: https://sssd.io


Development
-----------

GitHub Actions are used to build and push these images whenever a branch or
version tag of the form ``x.y*`` is pushed.

This project uses pre-commit_ to ensure commits meet minimum requirements:

1. Install Poetry_.

2. Run ``poetry update`` to install dependencies.

3. Run ``poetry run pre-commit install`` to install the Git hooks.

.. _Poetry: https://python-poetry.org/
.. _pre-commit: https://pre-commit.com/
