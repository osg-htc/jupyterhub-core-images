# JupyterHub with customizations for OSG.
#
# For use with Zero to JupyterHub for Kubernetes (https://z2jh.jupyter.org/).

FROM jupyterhub/k8s-hub:0.11.1

USER root

# We install oauthenticator>=15.0.0 in order to accommodate JupyterHub
# instances with multiple public URLs. That is the first released version
# to include https://github.com/jupyterhub/oauthenticator/pull/503.

RUN apt-get update \
    && apt-get upgrade -y \
    && python3 -m pip install -U --no-cache-dir \
        git+https://github.com/brianaydemir/jupyterhub-oauthenticator.git@15.1.0-osg.2 \
        git+https://github.com/brianaydemir/osg-jupyter.git@4df3f3399c92e2de8f451ce5dc048be1b16de1d3 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER $NB_UID:$NB_GID
