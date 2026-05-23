# 🕹️ PONG // NEON RETRO

Um jogo de Pong completo para navegador com visual **Synthwave / Cyberpunk**, efeitos sonoros sintetizados via Web Audio API e ranking local persistente — tudo em um único arquivo HTML.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Canvas](https://img.shields.io/badge/Canvas-000000?style=flat&logo=html5&logoColor=white)

---

## ✨ Funcionalidades

| Recurso | Descrição |
|---------|-----------|
| **Visual Neon Retro** | Paleta ciano/verde/laranja com glows, scanlines CRT e grade synthwave |
| **Partículas** | Rastro luminoso atrás da bola + fagulhas neon nas colisões |
| **Modos de Jogo** | Jogador vs Computador (IA progressiva) e Jogador vs Jogador local |
| **Áudio Sintetizado** | Beeps, arpejos de vitória e sons graves de ponto via Web Audio API |
| **Ranking Local** | Top 10 salvo no `localStorage` com nome, placar, modo e data |
| **Responsivo** | Canvas adapta ao tamanho da janela mantendo proporção 5:3 |
| **Touch Support** | Zonas de toque nas laterais para dispositivos móveis |

---

## 🎮 Como Jogar

### Abrir o Jogo

Basta abrir o arquivo `index.html` em qualquer navegador moderno (Chrome, Edge, Firefox).

```
Jogo/index.html
```

> Nenhuma instalação, servidor ou dependência externa necessária (apenas Google Fonts via CDN).

### Controles

| Jogador | Teclado | Touch (Mobile) |
|---------|---------|-----------------|
| **Jogador 1** (esquerda) | `W` ↑ / `S` ↓ | Toque na metade esquerda da tela |
| **Jogador 2** (direita) | `↑` / `↓` | Toque na metade direita da tela |

### Regras

- A partida vai até **7 pontos** (configurável pela constante `WINNING_SCORE` no código).
- No modo **vs Computador**, a IA fica progressivamente mais rápida a cada ponto.
- A velocidade da bola aumenta a cada rebatida (rally), tornando o jogo mais intenso.
- Ao final, o vencedor pode registrar seu nome no ranking neon.

---

## 🎨 Design

### Paleta de Cores

| Elemento | Cor | Hex |
|----------|-----|-----|
| Fundo | Preto profundo | `#050505` |
| Jogador 1 / Raquete esquerda | Ciano Neon | `#00f5ff` |
| Jogador 2 / IA | Verde Ácido | `#00ff88` |
| PvP Jogador 2 | Laranja Neon | `#ff5e00` |
| Bola | Amarelo Neon | `#fffb00` |
| Grade retro | Vermelho escuro | `#200000` |

### Efeitos Visuais

- **Scanlines CRT** — gradiente linear com flicker sutil simulando tela analógica
- **Glow Neon** — múltiplas camadas de `box-shadow` e `text-shadow`
- **Trail da Bola** — rastro com fade de opacidade e escala decrescente
- **Fagulhas** — partículas em leque emitidas em cada colisão
- **Tipografia** — fonte [Orbitron](https://fonts.google.com/specimen/Orbitron) (Google Fonts)

---

## 🏗️ Arquitetura

O projeto inteiro está contido em um único arquivo `index.html`, organizado nas seguintes seções:

```
index.html
├── <head>
│   ├── Meta tags (SEO + Open Graph)
│   ├── Google Fonts (Orbitron)
│   └── <style> — CSS completo
│       ├── 1. Variáveis de design
│       ├── 2. Container + Canvas responsivo
│       ├── 3. Overlays de UI (menu, ranking, vitória)
│       └── 4. Acessibilidade (prefers-reduced-motion)
│
├── <body>
│   ├── HUD do jogo
│   ├── Canvas (1000×600 virtual)
│   ├── Menu Principal (overlay)
│   ├── Tela de Ranking (overlay)
│   └── Tela de Vitória (overlay)
│
└── <script> — JavaScript completo
    ├── 4.1 Constantes do sistema
    ├── 4.2 AudioSynth (Web Audio API)
    ├── 4.3 GameState (estado central)
    ├── 4.4 Controles (teclado + touch)
    ├── 4.5 Renderização (Canvas 2D)
    ├── 4.6 Física (AABB, partículas, IA)
    ├── 4.7 Ranking (localStorage)
    └── 4.8 Event listeners de UI
```

### Constantes Configuráveis

| Constante | Valor Padrão | Descrição |
|-----------|-------------|-----------|
| `WINNING_SCORE` | `7` | Pontos para vencer a partida |
| `PADDLE_SPEED` | `450` | Velocidade das raquetes (px/s) |
| `BALL_START_SPEED` | `350` | Velocidade inicial da bola (px/s) |
| `BALL_SPEED_INCREMENT` | `1.07` | Fator de aceleração por rebatida |
| `BALL_MAX_SPEED` | `900` | Velocidade máxima da bola (px/s) |

---

## 🏆 Ranking

O ranking é salvo automaticamente no `localStorage` do navegador com a chave `pong_neon_ranking`.

**Critério de ordenação:**
1. Maior **margem de vitória** (ex: 7-0 > 7-6)
2. Em caso de empate, o resultado **mais recente** aparece primeiro

**Dados salvos por entrada:**
- Nome do vencedor (até 10 caracteres)
- Placar final
- Modo de jogo (VS COM / VS JOG)
- Data e hora

O ranking pode ser limpo a qualquer momento pelo botão na tela de classificação.

---

## ⚙️ Requisitos Técnicos

| Requisito | Detalhe |
|-----------|---------|
| **Navegador** | Chrome 69+, Edge 79+, Firefox 62+, Safari 15.4+ |
| **API** | Canvas 2D, Web Audio API, localStorage |
| **Rede** | Apenas para carregar a fonte Orbitron (Google Fonts) |
| **Servidor** | Nenhum — funciona com `file://` ou qualquer servidor HTTP |

---

## 📂 Estrutura do Projeto

```
Jogo/
├── index.html    ← Arquivo único com HTML + CSS + JS
└── README.md     ← Este arquivo
```

---

## 📜 Licença

Este projeto é de uso livre para fins educacionais e de aprendizado.
