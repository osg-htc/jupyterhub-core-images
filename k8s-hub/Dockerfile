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
        git+https://github.com/brianaydemir/jupyterhub-oauthenticator.git@0a45e7b5046bce31f99d5e460c6070c7d08dff4a \
        git+https://github.com/brianaydemir/osg-jupyter.git@4e2f3438cc998d3a70c6e096e0673354ec721239 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER jovyan
