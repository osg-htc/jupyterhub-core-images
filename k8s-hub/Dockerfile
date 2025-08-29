# JupyterHub with customizations for OSG.
#
# For use with Zero to JupyterHub for Kubernetes (https://z2jh.jupyter.org/).

FROM quay.io/jupyterhub/k8s-hub:4.0.0

# Reference: https://github.com/hadolint/hadolint/wiki/DL4006

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# We install oauthenticator>=15.0.0 in order to accommodate JupyterHub
# instances with multiple public URLs. That is the first released version
# to include https://github.com/jupyterhub/oauthenticator/pull/503.

USER root
RUN true \
    && apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y \
          procps \
    && python3 -m pip install -U --no-cache-dir \
        jupyterhub-fancy-profiles \
        git+https://github.com/brianaydemir/jupyterhub-oauthenticator.git@a52c1d2c7dc2b98a2da8cd1b71e1060232dbd2ce \
        git+https://github.com/osg-htc/jupyterhub-hooks.git@d1e9fe1217bef54c6428050f6fa237972f0e933b \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && true

USER jovyan:jovyan
