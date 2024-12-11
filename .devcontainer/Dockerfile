# Usa la imagen base
FROM mcr.microsoft.com/devcontainers/javascript-node:18

RUN npm install -g @shopify/cli

WORKDIR /workspace

COPY . /workspace/

RUN chmod -R 777 /workspace

# Crea el usuario vscode si no existe
RUN useradd -m vscode \
    && echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode

# Establece el usuario predeterminado
USER vscode