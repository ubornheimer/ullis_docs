```
FROM pengwyn/julia-python-baseRUN apt-get update --fix-missing# for jupyterlab extension: install node  
ENV NODE_OPTIONS=--max-old-space-size=8192  
RUN curl -sL [https://deb.nodesource.com/setup_15.x](https://deb.nodesource.com/setup_15.x) | bash -  
RUN apt-get install -y nodejs  
RUN curl -sL [https://dl.yarnpkg.com/debian/pubkey.gpg](https://dl.yarnpkg.com/debian/pubkey.gpg) | apt-key add -  
RUN echo "deb [https://dl.yarnpkg.com/debian/](https://dl.yarnpkg.com/debian/) stable main" | tee /etc/apt/sources.list.d/yarn.list  
RUN apt-get update && apt-get install -y yarn# Danny's workdir is (see his dockerfile) /usr/src/app/  
# Jupyter Lab is started from there  
RUN mkdir notebooks  
RUN mkdir librariesRUN pip3 install --no-cache-dir coolname  
RUN pip3 install --no-cache-dir rx==3.1.0 nest_asyncio==1.2.3 websockets==8.1 pyfunctional==1.3.0 toolz==0.10.0 jedi==0.17.2 openpyxl==3.0.6#jupyterlab version set back to 2.0.1 to make qgrid work?  
RUN pip3 install --no-cache-dir notebook==6.1.5 jupyterhub==1.3.0 jupyterlab==2.0.1  
RUN pip3 install --no-cache-dir ipywidgets==7.5.1 bqplot==0.12.20 ipyevents==0.8.1 qgrid==1.3.1 ipycanvas==0.8.0# Install notebook extensions  
RUN jupyter nbextension enable --py --sys-prefix bqplot  
RUN jupyter nbextension enable --py --sys-prefix qgrid  
RUN jupyter nbextension listRUN jupyter serverextension enable --py jupyterlabRUN jupyter labextension install @jupyter-widgets/jupyterlab-manager --minimize=False  
RUN jupyter labextension install bqplot --minimize=False  
RUN jupyter labextension install ipycanvas --minimize=False  
RUN jupyter labextension install @jupyter-widgets/jupyterlab-manager ipycanvas --minimize=False  
RUN jupyter labextension install qgrid2 --minimize=False  
RUN jupyter labextension listRUN jlpkg registry add General# default port where jupyter lab hosts inside  
EXPOSE 8888  
ENTRYPOINT ["jupyter", "lab", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]
```

```
#! /usr/bin/bash
echo "---------- building docker dev-impundulu image ------------------"
cd /mnt/e/Dropbox/synchronous/Giulini/libraries/arachne/libraries/UGLI
docker build --build-arg  GIT_CREDENTIALS=$(cat ~/.git-credentials) --build-arg ZEFHUB_AUTH_KEY=$(cat /mnt/e/Dropbox/synchronous/zefDB/zefhub.key) -t dev-impundulu .
```

