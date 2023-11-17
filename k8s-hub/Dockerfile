# JupyterHub with customizations for OSG.
#
# For use with Zero to JupyterHub for Kubernetes (https://z2jh.jupyter.org/).

FROM jupyterhub/k8s-hub:2.0.0

USER root

# We install oauthenticator>=15.0.0 in order to accommodate JupyterHub
# instances with multiple public URLs. That is the first released version
# to include https://github.com/jupyterhub/oauthenticator/pull/503.

RUN apt-get update \
    && apt-get upgrade -y \
    && python3 -m pip install -U --no-cache-dir \
        git+https://github.com/brianaydemir/jupyterhub-oauthenticator.git@15.1.0+osg.3 \
        git+https://github.com/osg-htc/jupyterhub-hooks.git@b04793e492ec0cc92a3bcc90113d024755b485e6 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER $NB_UID:$NB_GID
