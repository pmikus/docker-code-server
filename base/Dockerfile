# Start from the code-server Debian base image
FROM codercom/code-server:4.2.0

USER coder

# Use bash shell
ENV SHELL=/bin/bash

# Install unzip + rclone (support for remote filesystem)
RUN sudo apt-get update \
 && sudo apt-get install unzip -y \
 && curl https://rclone.org/install.sh | sudo bash

# Install a VS Code extension:
RUN code-server --install-extension eamodio.gitlens \
 && code-server --install-extension hashicorp.terraform \
 && code-server --install-extension ms-python.python \
 && code-server --install-extension shan.code-settings-sync \
 && code-server --install-extension robbowen.synthwave-vscode \
 && code-server --install-extension github.github-vscode-theme

# Port
ENV PORT=8443

# Use our custom entrypoint script first
COPY entrypoint.sh /usr/bin/deploy-container-entrypoint.sh
ENTRYPOINT ["/usr/bin/deploy-container-entrypoint.sh"]
