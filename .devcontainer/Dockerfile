# Usa la imagen base
FROM mcr.microsoft.com/devcontainers/javascript-node:18

RUN apt-get update && apt-get install -y \
    zsh \
    git \
    curl \
    wget \
    && rm -rf /var/lib/apt/lists/*


RUN apt-get update && apt-get install -y xdg-utils


# Instala oh-my-zsh
# Instalar oh-my-zsh solo si no está instalado
RUN if [ ! -d "/root/.oh-my-zsh" ]; then \
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" && \
    chsh -s $(which zsh); \
    fi

# Instala el tema Powerlevel10k (opcional, para personalización avanzada)
RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k \
    && sed -i 's/ZSH_THEME=".*"/ZSH_THEME="powerlevel10k\/powerlevel10k"/g' ~/.zshrc

# Instala zsh-autosuggestions y zsh-syntax-highlighting
RUN git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions \
    && git clone https://github.com/zsh-users/zsh-syntax-highlighting ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting

    # Configura zsh como shell predeterminado
SHELL ["/bin/zsh", "-c"]

RUN npm install -g @shopify/cli

WORKDIR /workspace

COPY . /workspace/

RUN chmod -R 777 /workspace

RUN cd /workspace

RUN git clone https://jesusuzcategui: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@github.com/eatbobos/eatbobos-theme.git

# Crea el usuario vscode si no existe
RUN useradd -m vscode \
    && echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode

# Establece el usuario predeterminado
#USER vscode