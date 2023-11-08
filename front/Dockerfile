# Utilisez une image Node.js en tant qu'image de base
FROM node:21.1.0

# Définissez le répertoire de travail à l'intérieur du conteneur
WORKDIR /app

# Copiez les fichiers de votre application dans le conteneur
COPY . .

# Installez les dépendances de votre application
RUN npm install

# Exécutez la commande de build de votre application Angular
RUN npm run build

# Exposez le port sur lequel votre application écoute
EXPOSE 80

# Commande pour démarrer votre application
CMD [ "npm", "start" ]
