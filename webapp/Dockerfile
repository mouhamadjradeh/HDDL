# Utiliser une image Python légère
FROM python:3.12.2-slim
# Installer les dépendances de base
RUN apt-get update && apt-get install -y \
    curl \
    build-essential \
    libssl-dev \
    pkg-config

# Installer Rust via rustup
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y

# Ajouter le chemin Cargo à l'environnement Docker
ENV PATH="/root/.cargo/bin:${PATH}"

# Vérifier que Rust et Cargo sont installés correctement
RUN rustc --version
RUN cargo --version


# Définir le répertoire de travail
WORKDIR /app

# Copier le fichier requirements spécifique au Webapp
COPY requirements-webapp.txt /app/requirements-webapp.txt

# Installer les dépendances spécifiques au Webapp
RUN pip install --no-cache-dir -r /app/requirements-webapp.txt

# Copier les fichiers du Webapp dans le conteneur
COPY . /app

# Exposer le port utilisé par Gradio
EXPOSE 7860

# Commande pour démarrer l'application Gradio
CMD ["python", "cvae_gradio.py"]
