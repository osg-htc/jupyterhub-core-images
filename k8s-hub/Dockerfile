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
        git+https://github.com/brianaydemir/osg-jupyter.git@b6553c5fe46617cbc729c3f536054b9aa3b46530 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER jovyan
