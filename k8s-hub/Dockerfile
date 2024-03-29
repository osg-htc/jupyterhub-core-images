# JupyterHub with customizations for OSG.
#
# For use with Zero to JupyterHub for Kubernetes (https://z2jh.jupyter.org/).

FROM quay.io/jupyterhub/k8s-hub:3.2.1

# Reference: https://github.com/hadolint/hadolint/wiki/DL4006

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# We install oauthenticator>=15.0.0 in order to accommodate JupyterHub
# instances with multiple public URLs. That is the first released version
# to include https://github.com/jupyterhub/oauthenticator/pull/503.

USER root
WORKDIR /tmp
RUN true \
    && apt-get update -y \
    && apt-get upgrade -y \
    && python3 -m pip install -U --no-cache-dir \
        git+https://github.com/brianaydemir/jupyterhub-oauthenticator.git@15.1.0+osg.3 \
        git+https://github.com/osg-htc/jupyterhub-hooks.git@7.0.0 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && true

USER $NB_UID:$NB_GID
