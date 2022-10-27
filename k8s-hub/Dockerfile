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
        git+https://github.com/brianaydemir/jupyterhub-oauthenticator.git@80e07d2bdeab972599442b4a1e01babe0ebd6f51 \
        git+https://github.com/brianaydemir/osg-jupyter.git@0315c619a17725eb4ea9925157a079af0a9be861 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER jovyan
