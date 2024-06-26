# Dockerfile for creating a Docker image with net-tools and a custom start script.

# Use the donch/net-tools image as the base image.
# This image likely contains network utilities like netstat, ifconfig, etc.
FROM donch/net-tools

# Créer un utilisateur non-root
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Copier le script start.sh dans le répertoire de l'utilisateur non-root
COPY start.sh /home/appuser/start.sh

# Rendre le script exécutable
RUN chmod +x /home/appuser/start.sh

# Expose port 4321 in the container.
# This makes the port accessible to processes outside of the container.
EXPOSE 4321

# Changer l'utilisateur courant
USER appuser

# Set /home/appuser/start.sh as the entrypoint of the image.
# The entrypoint is the command that is run when a container is started from this image.
ENTRYPOINT ["/home/appuser/start.sh"]

# Set "nc -l 4323" as the default command of the image.
# This command will be run when a container is started from this image, unless the command is overridden.
CMD ["nc", "-l", "4323"]
