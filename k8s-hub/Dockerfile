# JupyterHub with customizations for OSG.
#
# For use with Zero to JupyterHub for Kubernetes (https://z2jh.jupyter.org/).

FROM quay.io/jupyterhub/k8s-hub:3.3.8

# Reference: https://github.com/hadolint/hadolint/wiki/DL4006

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# We install oauthenticator>=15.0.0 in order to accommodate JupyterHub
# instances with multiple public URLs. That is the first released version
# to include https://github.com/jupyterhub/oauthenticator/pull/503.

USER root
RUN true \
    && apt-get update -y \
    && apt-get upgrade -y \
    && python3 -m pip install -U --no-cache-dir \
        git+https://github.com/brianaydemir/jupyterhub-oauthenticator.git@d45c4e2c7fd3762638a99c46a5dde0c4b2ecd611 \
        git+https://github.com/osg-htc/jupyterhub-hooks.git@7.1.1 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && true

USER $NB_UID:$NB_GID
