# Start from the code-server Debian base image
FROM codercom/code-server:3.11.1

USER coder

# Use bash shell
ENV SHELL=/bin/bash

# Install unzip + rclone (support for remote filesystem)
RUN sudo apt-get update \
 && sudo apt-get install unzip -y
RUN curl https://rclone.org/install.sh | sudo bash

# Install a VS Code extension:
RUN code-server --install-extension eamodio.gitlens \
 && code-server --install-extension hashicorp.terraform \
 && code-server --install-extension ms-python.python \
 && code-server --install-extension robbowen.synthwave-vscode

# Port
ENV PORT=8443

# Use our custom entrypoint script first
COPY entrypoint.sh /usr/bin/deploy-container-entrypoint.sh
ENTRYPOINT ["/usr/bin/deploy-container-entrypoint.sh"]
