# 🚀 ROADMAP: ARCH LINUX DEV STATION 2026 (T480 SUPREME EDITION)

Este guia definitivo transforma seu **ThinkPad T480** em uma máquina de guerra para desenvolvimento Android e modding de Hytale (Java), equilibrando performance bruta, economia de recursos e uma estética impecável.

---

## 🛠️ 1. HARDWARE E BIOS (PRE-INSTALL)
Antes de formatar, garanta que o hardware esteja otimizado:
* **RAM:** Mínimo 16GB (O T480 suporta até 64GB DDR4).
* **SSD:** NVMe (Crucial para velocidade de leitura do Gradle/Compilação).
* **BIOS Settings:**
    * Disable **Secure Boot**.
    * Set **Thunderbolt** to "User Authorization" ou "Disabled" (se não for usar) para segurança.
    * Set **Graphics Memory** para 512MB (Melhora performance da iGPU).

---

## 🏗️ 2. INSTALAÇÃO DO SISTEMA BASE
Use o comando `archinstall` e selecione as seguintes opções:
* **Audio:** Pipewire (Padrão moderno).
* **Kernel:** `linux-zen` (Kernel otimizado para desktop e baixa latência).
* **Graphics:** Intel (Open-source mesa drivers).
* **Network:** NetworkManager.

**Drivers Complementares (Pós-instalação):**
```bash
sudo pacman -S mesa intel-media-driver libva-intel-driver vulkan-intel
```

---

## 🎨 3. INTERFACE GRÁFICA (A CARA DO SISTEMA)
Escolha o seu ambiente de trabalho (Window Manager ou Desktop Environment):

| Opção | Nome | Perfil |
| :--- | :--- | :--- |
| **1. Moderna** | **Hyprland** | Tiling Wayland com animações fluidas, blur (GPU) e cantos arredondados. O ápice da estética atual. |
| **2. Completa** | **KDE Plasma 6** | Customização extrema via interface visual. Ideal para workflow tipo macOS/Windows. |
| **3. Estável** | **Sway** | O "i3wm para Wayland". Extremamente leve, sólido e focado em produtividade sem firulas. |

---

## 💻 4. TERMINAL EMULATORS (ONDE A MÁGICA ACONTECE)
O T480 brilha com emuladores acelerados por GPU:

1. **Ghostty:** A sensação de 2026. Rápido, nativo, acelerado por GPU e consome quase nada de CPU.
2. **Kitty:** O rei da customização. Suporta imagens no terminal, abas e configuração via arquivo simples.
3. **WezTerm:** Escrito em Rust, configurado em Lua, multiplataforma e extremamente potente.

---

## 🐚 5. SHELLS (INTERAÇÃO E PRODUTIVIDADE)
1. **Zsh (+ Oh My Zsh):** O padrão da indústria. Milhares de plugins e temas (Recomendado usar com `zsh-autosuggestions`).
2. **Fish:** Inteligente "out-of-the-box". Sugestões automáticas baseadas no histórico sem configurar quase nada.
3. **Nushell:** O shell moderno. Trata tudo como dados/tabelas. Incrível para manipular JSON/YAML de Android.

---

## ⚡ 6. OTIMIZAÇÃO DE PERFORMANCE (O SEGREDO)

### ZRAM (Dobra a eficiência da sua RAM)
Instale o gerador: `sudo pacman -S zram-generator`
Crie/Edite o arquivo `/etc/systemd/zram-generator.conf`:

```ini
[zram0]
zram-size = ram / 1
compression-algorithm = zstd
swap-priority = 100
```

**Algoritmos de Compressão:**
* **zstd (Recomendado):** Melhor compressão (economiza mais RAM, usa um pouco mais de CPU).
* **lz4:** Mais rápido (quase zero uso de CPU, mas comprime menos).
* **zswap:** Alternativa apenas se o seu SSD for muito lento (não recomendado para o NVMe do T480).

**Ative com:** `sudo systemctl daemon-reload && sudo systemctl start /dev/zram0`

### TLP (Bateria e Temperatura do ThinkPad)
```bash
sudo pacman -S tlp tlp-rdw
sudo systemctl enable --now tlp
```

---

## ☕ 7. WORKFLOW JAVA (ANDROID & HYTALE)

### SDKs Necessários:
```bash
# Java 17 (Hytale) e Java 21 (Android Moderno)
sudo pacman -S jdk17-openjdk jdk21-openjdk

# AUR Helper (yay)
git clone [https://aur.archlinux.org/yay.git](https://aur.archlinux.org/yay.git) && cd yay && makepkg -si

# Android SDK, Platform Tools e Scrcpy
yay -S android-sdk android-sdk-platform-tools android-sdk-build-tools scrcpy
```

### Escolha sua IDE (Workflow):
* **A "Oficial":** **Android Studio + IntelliJ.** O caminho padrão, pesado, mas completo para Hytale/Android.
* **A "Hacker":** **Neovim + LSP.** Customização infinita, tudo via teclado e uso zero de RAM.
* **A "Equilibrada":** **VS Code (Codium).** Leve, extensível e fácil de trocar temas e plugins rapidamente.

---

## 🎨 8. TEMAS E ESTÉTICA (THE RICE)
Escolha uma paleta de cores para aplicar em todo o sistema (Terminais, Editores e UI):

1. **Catppuccin:** Tons pastéis e suaves. A paleta mais completa e famosa de 2026.
2. **Tokyo Night:** Estética futurista de "Cyberpunk Noturno".
3. **Gruvbox:** O clássico estilo "retro-orgânico", excelente para não cansar a vista.

**Fontes Obrigatórias (Nerd Fonts):**
```bash
sudo pacman -S ttf-jetbrains-mono-nerd ttf-font-awesome
```

---

## 📱 9. WORKFLOW DE DESENVOLVIMENTO
* **Para Android:** Use um celular físico via USB + `scrcpy`. Isso poupa ~3GB de RAM que o emulador usaria, deixando o T480 focado na compilação.
* **Para Hytale:** Use o IntelliJ configurado com o JDK 17. Use o terminal integrado para rodar comandos `./gradlew build` e mantenha o `btop` aberto em outro workspace para vigiar o consumo.

---

## 📅 10. CRONOGRAMA DE ESTUDO 2026
* **Semana 1:** Configuração do Arch, atalhos do Window Manager, Dotfiles e Shell.
* **Semana 2:** Lógica de Java Intermediária (Streams, Lambdas) aplicada ao Modding de Hytale.
* **Semana 3:** Arquitetura Android Moderna (MVVM, Jetpack Compose, Kotlin Multiplatform).
* **Semana 4:** Git Flow avançado e publicação de Mods/APKs.

---

## 🏆 11. COMANDOS ÚTEIS DO THINKPAD NO ARCH
* `tlp-stat -b`: Verifica a saúde e ciclos das suas duas baterias.
* `nmtui`: Interface de terminal fácil para conectar no Wi-Fi.
* `btop`: Monitor de recursos elegante para vigiar CPU/RAM.
* `xbacklight -set 50`: Ajusta brilho via terminal (se usar X11).

---

## 📜 SCRIPT DE INSTALAÇÃO RÁPIDA (CONSOLIDADO)
```bash
# 1. Terminais e Shells
sudo pacman -S ghostty kitty wezterm zsh fish btop

# 2. Desenvolvimento e Java
sudo pacman -S jdk17-openjdk jdk21-openjdk intellij-idea-community-edition scrcpy
yay -S android-studio visual-studio-code-bin

# 3. Estética e Plugins
sudo pacman -S ttf-jetbrains-mono-nerd ttf-font-awesome
git clone [https://github.com/zsh-users/zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone [https://github.com/zsh-users/zsh-syntax-highlighting.git](https://github.com/zsh-users/zsh-syntax-highlighting.git) ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
