[WavePlay.md](https://github.com/user-attachments/files/31493487/WavePlay.md)
# WavePlay

A modern desktop music player for Windows and Linux, built with Electron and designed for local music collections.

Um player de música desktop moderno para Windows e Linux, desenvolvido com Electron e projetado para coleções de músicas locais.

[English](#english) · [Português-Brasil](#português-brasil)

<img width="1321" height="776" alt="Captura de tela 2026-08-26 213301" src="https://github.com/user-attachments/assets/8d6a3a55-eb55-42e2-9aa7-7a0704b643b5" />


---

## English

### Overview

WavePlay is a lightweight and customizable desktop music player for managing and playing local music files. It combines a clean interface with playlists, metadata and album cover support, system tray controls, multiple library views, and portable or installable distributions for Windows and Linux.

The application is designed to keep your music collection local. Folders can be scanned recursively, new tracks can be detected automatically, and your playback preferences, playlists, favorites, volume, and window state can be preserved between sessions.

### Features

| Feature | Description |
|---|---|
| Local music library | Scan individual files or complete folders, including subfolders. |
| Drag and drop | Add music files and folders by dragging them into the application. |
| Metadata and covers | Display title, artist, album, year, genre, and embedded album artwork when available. |
| Broad audio support | Uses Chromium codecs for common formats and FFmpeg fallback support for additional formats. |
| Playlists | Create, manage, import, and export custom playlists as JSON files. |
| Favorites | Mark tracks as favorites and keep them at the top of the list. |
| Playback queue | Add tracks to a queue and manage upcoming playback. |
| Playback modes | Supports shuffle, repeat one track, and repeat all tracks. |
| Automatic monitoring | Detect newly added music in configured library folders. |
| Library views | Choose Default, List, Large Icons, Medium Icons, Small Icons, By Artist, or By Album. |
| Themes | Dark theme by default, with an optional light theme. |
| Languages | Portuguese Brazilian and English, with system language detection. |
| System tray | Minimize the player to the system tray and configure tray actions for reopening or pausing playback. |
| Persistent settings | Save volume, playback preferences, playlists, window position, window size, and maximized state. |

### Supported audio formats

WavePlay supports common audio formats through the native Chromium audio stack and an integrated FFmpeg fallback. Supported formats include MP3, WAV, FLAC, OGG, OGA, Opus, M4A, AAC, WMA, AIFF, APE, WV, TTA, ALAC, AC3, DTS, AMR, MKA, MP4, and WebM.

### Installation and development

Clone the repository, install the dependencies, and start the Electron application:

```bash
git clone https://github.com/YOUR_USERNAME/waveplay.git
cd waveplay
pnpm install --no-frozen-lockfile
node node_modules/electron/install.js
pnpm start
```

For local development on Linux, WavePlay can use an FFmpeg binary available in the system `PATH`. Packaged distributions include the FFmpeg binaries provided in the project `bin/` directory.

### Distribution packages

The repository provides the following distribution formats:

| Platform | Package | Description |
|---|---|---|
| Windows x64 | `WavePlay-*-win-portable.zip` | Complete portable application. Extract the folder and run `WavePlay.exe`; no installation is required. |
| Windows x64 | `WavePlay-*-win-portable.exe` | Single-file portable executable. |
| Windows x64 | `WavePlay-*-win-installer.exe` | NSIS installer. |
| Linux x64 | `WavePlay-*-linux-x86_64.AppImage` | Portable Linux application. |
| Linux x64 | `WavePlay-*-linux-amd64.deb` | Debian/Ubuntu package. |

The complete Windows portable ZIP includes the application executable, Electron resources, FFmpeg, and the WavePlay icon embedded in the executable. It can be extracted to any folder and launched directly without a traditional installation.

### Building packages

```bash
# Linux: AppImage and Debian package
pnpm run dist:linux

# Windows: portable executable and NSIS installer
pnpm exec electron-builder --win portable nsis --publish never
```

Build artifacts are generated in the `dist/` directory. Windows packages are configured for x64 and are not digitally signed by default, so Windows may show its standard warning for unsigned applications.

### Project structure

| Path | Purpose |
|---|---|
| `src/main.js` | Electron main process, system tray, file dialogs, library scanning, and FFmpeg integration. |
| `src/preload.js` | Secure bridge between the renderer and Electron APIs. |
| `src/index.html` | Application layout and user interface structure. |
| `src/styles.css` | Themes, responsive layout, player controls, and library view styles. |
| `src/renderer.js` | Library state, playback logic, playlists, translations, and user interactions. |
| `assets/` | Application artwork, default cover, and generated icon assets. |
| `bin/` | FFmpeg binaries used by packaged distributions. |
| `dist/` | Generated installers, portable builds, packages, source archives, and checksums. |

### Technology

WavePlay is built with [Electron](https://www.electronjs.org/), [electron-builder](https://www.electron.build/), [music-metadata](https://github.com/Borewit/music-metadata), and [FFmpeg](https://ffmpeg.org/).

### License

WavePlay is distributed under the MIT License. See the `LICENSE` file for details.

---

## Português-Brasil

### Visão geral

O WavePlay é um player de música desktop leve e personalizável para gerenciar e reproduzir arquivos de música locais. Ele combina uma interface limpa com playlists, suporte a metadados e capas de álbuns, controles pela bandeja do sistema, vários modos de exibição da biblioteca e distribuições portáteis ou instaláveis para Windows e Linux.

O aplicativo foi projetado para manter sua coleção de músicas local. As pastas podem ser lidas recursivamente, novas faixas podem ser detectadas automaticamente e suas preferências de reprodução, playlists, favoritos, volume e estado da janela podem ser preservados entre as sessões.

### Recursos

| Recurso | Descrição |
|---|---|
| Biblioteca local | Leia arquivos individuais ou pastas completas, incluindo subpastas. |
| Arrastar e soltar | Adicione músicas e pastas arrastando-as para a interface. |
| Metadados e capas | Exiba título, artista, álbum, ano, gênero e a capa incorporada quando disponível. |
| Amplo suporte de áudio | Usa os codecs do Chromium para formatos comuns e fallback com FFmpeg para formatos adicionais. |
| Playlists | Crie, gerencie, importe e exporte playlists personalizadas em arquivos JSON. |
| Favoritos | Marque faixas como favoritas e mantenha-as no topo da lista. |
| Fila de reprodução | Adicione músicas à fila e gerencie as próximas faixas. |
| Modos de reprodução | Suporta aleatório, repetir uma faixa e repetir todas as faixas. |
| Monitoramento automático | Detecta músicas novas nas pastas configuradas da biblioteca. |
| Modos da biblioteca | Escolha Padrão, Lista, Ícones Grandes, Ícones Médios, Ícones Pequenos, Por Artista ou Por Álbum. |
| Temas | Tema escuro por padrão, com opção de tema claro. |
| Idiomas | Português do Brasil e inglês, com detecção do idioma do sistema. |
| Bandeja do sistema | Minimize o player para a bandeja e configure ações para reabrir ou pausar a reprodução. |
| Configurações persistentes | Salva volume, preferências de reprodução, playlists, posição, tamanho e maximização da janela. |

### Formatos de áudio

O WavePlay suporta formatos comuns por meio do sistema de áudio nativo do Chromium e de um fallback integrado com FFmpeg. Os formatos reconhecidos incluem MP3, WAV, FLAC, OGG, OGA, Opus, M4A, AAC, WMA, AIFF, APE, WV, TTA, ALAC, AC3, DTS, AMR, MKA, MP4 e WebM.

### Instalação e desenvolvimento

Clone o repositório, instale as dependências e inicie o aplicativo Electron:

```bash
git clone https://github.com/SEU_USUARIO/waveplay.git
cd waveplay
pnpm install --no-frozen-lockfile
node node_modules/electron/install.js
pnpm start
```

No desenvolvimento local em Linux, o WavePlay pode usar um binário FFmpeg disponível no `PATH` do sistema. As distribuições empacotadas incluem os binários FFmpeg fornecidos na pasta `bin/` do projeto.

### Pacotes de distribuição

O repositório fornece os seguintes formatos:

| Plataforma | Pacote | Descrição |
|---|---|---|
| Windows x64 | `WavePlay-*-win-portable.zip` | Aplicação portátil completa. Extraia a pasta e execute `WavePlay.exe`; não é necessário instalar. |
| Windows x64 | `WavePlay-*-win-portable.exe` | Executável portátil em arquivo único. |
| Windows x64 | `WavePlay-*-win-installer.exe` | Instalador NSIS. |
| Linux x64 | `WavePlay-*-linux-x86_64.AppImage` | Aplicativo portátil para Linux. |
| Linux x64 | `WavePlay-*-linux-amd64.deb` | Pacote para Debian/Ubuntu. |

O ZIP portátil completo do Windows inclui o executável do aplicativo, os recursos do Electron, o FFmpeg e o ícone do WavePlay incorporado no executável. Basta extrair o ZIP para qualquer pasta e executar o programa diretamente, sem uma instalação tradicional.

### Compilação dos pacotes

```bash
# Linux: AppImage e pacote Debian
pnpm run dist:linux

# Windows: executável portátil e instalador NSIS
pnpm exec electron-builder --win portable nsis --publish never
```

Os artefatos de compilação são gerados na pasta `dist/`. Os pacotes Windows são configurados para x64 e não possuem assinatura digital por padrão; por isso o Windows pode exibir o aviso padrão para aplicativos sem assinatura.

### Estrutura do projeto

| Caminho | Finalidade |
|---|---|
| `src/main.js` | Processo principal do Electron, bandeja do sistema, diálogos, leitura da biblioteca e integração com FFmpeg. |
| `src/preload.js` | Ponte segura entre o renderer e as APIs do Electron. |
| `src/index.html` | Estrutura da interface e do layout do aplicativo. |
| `src/styles.css` | Temas, layout responsivo, controles do player e estilos dos modos da biblioteca. |
| `src/renderer.js` | Estado da biblioteca, reprodução, playlists, traduções e interações do usuário. |
| `assets/` | Imagens do aplicativo, capa padrão e assets de ícone gerados. |
| `bin/` | Binários FFmpeg usados pelas distribuições empacotadas. |
| `dist/` | Instaladores, versões portáteis, pacotes, arquivos-fonte e hashes gerados. |

### Tecnologias

O WavePlay utiliza [Electron](https://www.electronjs.org/), [electron-builder](https://www.electron.build/), [music-metadata](https://github.com/Borewit/music-metadata) e [FFmpeg](https://ffmpeg.org/).

### Licença

O WavePlay é distribuído sob a licença MIT. Consulte o arquivo `LICENSE` para obter os detalhes.

---

## Contributions / Contribuições

Suggestions, bug reports, and pull requests are welcome. Please describe the problem or proposed improvement clearly and include the operating system and reproduction steps when applicable.

Sugestões, relatos de bugs e pull requests são bem-vindos. Descreva claramente o problema ou a melhoria proposta e, quando aplicável, informe o sistema operacional e os passos para reproduzir o comportamento.
