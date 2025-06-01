FROM debian:bullseye-slim

# Mettre à jour les paquets et installer les dépendances système
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    python3 \
    python3-pip \
    python3-venv \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Installer Jupyter et les bibliothèques Python nécessaires
RUN pip3 install --no-cache-dir \
    jupyterlab \
    pandas \
    numpy \
    matplotlib \
    seaborn \
    statsmodels \
    plotly \
    scikit-learn \
    scipy \
    ipython \
    pmdarima

# Configurer le dossier de travail
WORKDIR /app

# Copier les fichiers locaux
COPY resources/ /app

# Exposer le port de Jupyter
EXPOSE 8888

# Lancer Jupyter Lab sans mot de passe ni token
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root", "--NotebookApp.token=", "--NotebookApp.password="]
