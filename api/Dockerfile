# Utiliser une image Python légère
FROM python:3.12.2-slim

# Définir le répertoire de travail
WORKDIR /app

# Copier le fichier requirements spécifique à l'API
COPY requirements-api.txt /app/requirements-api.txt

# Installer les dépendances spécifiques à l'API
RUN pip install --no-cache-dir -r /app/requirements-api.txt

# Copier les fichiers de l'API dans le conteneur
COPY . /app

# Exposer le port utilisé par Flask
EXPOSE 5000

# Commande pour démarrer l'API
CMD ["python", "cvae_api.py"]
