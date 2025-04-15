# Étape 1 : Image de base Jenkins Inbound Agent
FROM jenkins/inbound-agent

# Passer à l'utilisateur root pour installer des outils
USER root

# Mettre à jour les paquets et installer curl
RUN apt update && apt install -y curl

# Installer Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt install -y nodejs

# Vérifier la version de Node.js et npm
RUN node -v && npm -v

# Installer Next.js globalement (optionnel, si nécessaire pour des tests)
RUN npm install -g next

# Revenir à l'utilisateur jenkins pour des raisons de sécurité
USER jenkins

# Définir le répertoire de travail (dans lequel Jenkins travaillera)
WORKDIR /home/jenkins/agent

# C'est ici que le processus d'agent Jenkins sera démarré (par défaut)
ENTRYPOINT ["java", "-jar", "/usr/share/jenkins/agent.jar", "-url", "http://172.17.0.2:8080", "69666fd10128ae07698725ca5435aef2982b5e51339cec937458d897c5d1ce85", "next_CICDCD"]

