<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=24&height=120&section=header"/>

<h1 align="center">👾 Space Invaders</h1>

<p align="center">
  Recriação do clássico arcade Space Invaders, direto no navegador — com sons, explosões, partículas e sistema de pontuação.
</p>

<div align="center">

  [![Demo](https://img.shields.io/badge/🌐%20Jogar%20Agora-2482FF?style=for-the-badge)](https://https-shini.github.io/space-invaders/)
  [![Código](https://img.shields.io/badge/Ver%20Código-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/https-shini/space-invaders)

</div>

---

## 📌 O que é este projeto?

Uma recriação do famoso jogo **Space Invaders** feita com JavaScript puro e a API Canvas do navegador. O jogador controla uma nave espacial e precisa destruir ondas de invasores antes de ser atingido.

Cada fase traz uma nova grade de inimigos com tamanho aleatório, e os invasores ficam progressivamente **mais rápidos** conforme avançam — tornando o jogo cada vez mais desafiador.

---

## 🎮 Como jogar

| Tecla | Ação |
|---|---|
| `A` | Mover a nave para a esquerda |
| `D` | Mover a nave para a direita |
| `Enter` | Atirar |

**Objetivo:** destrua todos os invasores antes que eles cheguem até você. Cada invasor eliminado vale **10 pontos**.

> 💡 Use os obstáculos vermelhos como escudo para se proteger dos tiros inimigos! Eles bloqueiam tanto os tiros dos invasores quanto os seus.

---

## ✨ Funcionalidades

- Ondas de invasores com quantidade **aleatória** de linhas e colunas a cada fase
- Invasores ficam **mais rápidos** a cada vez que descem uma fileira
- **Sistema de pontuação** com score atual, nível e recorde da sessão (high score)
- **Tiros automáticos** dos invasores a cada 1 segundo, disparados por um inimigo aleatório
- **Obstáculos** que bloqueiam tiros dos dois lados — e são destruídos se um invasor os alcançar
- **Efeitos sonoros** para tiro, acerto, explosão e novo nível
- **Partículas de explosão** coloridas ao eliminar inimigos ou ao ser atingido
- **Fundo estrelado** animado com 100 estrelas caindo em velocidades diferentes
- Nave do jogador com **sprite animado** do motor e **inclinação** ao se mover
- Tela de **início**, tela de **game over** com animação de zoom e opção de reiniciar

---

## 🌐 Experimente agora

Você pode jogar sem precisar baixar nada:

👉 **[https://https-shini.github.io/space-invaders/](https://https-shini.github.io/space-invaders/)**

Basta abrir o link no navegador e clicar em **Play**!

---

## 🛠️ Tecnologias utilizadas

- **HTML5 Canvas** — renderização de todos os elementos do jogo
- **JavaScript ES6+** — lógica, classes e módulos (`import/export`)
- **CSS3** — telas de UI, HUD e animações
- **Web Audio API** — efeitos sonoros nativos do navegador
- **Google Fonts (Press Start 2P)** — fonte estilo arcade

> Nenhuma biblioteca ou framework externo foi utilizado.

---

## 🗂️ Estrutura de arquivos

```
space-invaders/
│
├── index.html                  → Página principal, HUD e telas de UI
│
└── src/
    ├── index.js                → Loop principal, controles e lógica de colisão
    ├── style.css               → Visual das telas, HUD e animações
    │
    ├── utils/
    │   └── constants.js        → Caminhos dos assets e estados do jogo
    │
    ├── classes/
    │   ├── Player.js           → Nave do jogador (movimento, tiro, sprite animado)
    │   ├── Invader.js          → Invasor individual (movimento, tiro, colisão)
    │   ├── Grid.js             → Grade de invasores (organiza e movimenta o grupo)
    │   ├── Projectile.js       → Tiro (do jogador e dos invasores)
    │   ├── Obstacle.js         → Obstáculo de proteção vermelho
    │   ├── Particle.js         → Partícula de explosão
    │   ├── Star.js             → Estrela do fundo animado
    │   └── SoundEffects.js     → Gerenciador de efeitos sonoros
    │
    └── assets/
        ├── images/
        │   ├── spaceship.png
        │   ├── engine.png
        │   ├── engine_sprites.png
        │   └── invader.png
        └── audios/
            ├── shoot.mp3
            ├── hit.mp3
            ├── explosion.mp3
            └── next_level.mp3
```

---

## 🧩 Classes do projeto

### 🚀 Player
A nave do jogador. Renderiza três camadas de imagem sobrepostas: o corpo da nave, o motor e um sprite animado do motor com 3 frames. Move-se horizontalmente e atira projéteis para cima (velocidade `-10`).

### 👾 Invader
Um invasor individual. Move-se para os lados e para baixo quando a grade atinge as bordas. Atira projéteis para baixo (velocidade `+10`) e acelera a cada descida. Detecta colisão com projéteis e com obstáculos.

### 🔲 Grid
Organiza todos os invasores em linhas e colunas. Controla a direção do grupo, detecta quando algum invasor tocou a borda e ordena a descida. A cada descida, todos os invasores ganham um boost de velocidade de `0.1`.

### 💥 Projectile
Um tiro retangular (`2x20px`) branco. A direção é definida pela velocidade: negativa sobe (jogador), positiva desce (invasores).

### 🟥 Obstacle
Retângulo vermelho que serve de escudo. Bloqueia qualquer projétil que o atravesse — e é destruído se um invasor colidir diretamente com ele.

### ✨ Particle
Círculo pequeno gerado nas explosões. Move-se em direção aleatória e desaparece gradualmente (opacidade diminui `0.008` por frame).

### ⭐ Star
Círculo branco de tamanho e velocidade aleatórios que desce pela tela. Ao sair pela parte inferior, reaparece no topo em posição aleatória, criando o efeito de campo estelar em movimento.

### 🔊 SoundEffects
Gerencia 4 tipos de áudio. Para tiros e acertos, usa um pool de **5 instâncias** do mesmo arquivo, permitindo que o mesmo som seja reproduzido em sobreposição sem cortes.

| Som | Volume | Quando toca |
|---|---|---|
| `shoot.mp3` | 50% | Ao atirar |
| `hit.mp3` | 20% | Ao acertar um invasor |
| `explosion.mp3` | 20% | Ao ser atingido (game over) |
| `next_level.mp3` | 40% | Ao eliminar todos os invasores |

---

## 🔄 Estados do jogo

| Estado | O que acontece |
|---|---|
| `START` | Tela inicial com botão de jogar, estrelas animadas ao fundo |
| `PLAYING` | Jogo em andamento — nave, invasores, tiros, partículas e HUD visíveis |
| `GAME_OVER` | Explosão tripla do jogador, tela de game over com animação de zoom |

---

## 🚀 Como rodar localmente

O projeto usa **módulos ES6** (`import/export`), então precisa ser servido por um servidor local — não funciona abrindo o `index.html` diretamente no navegador.

**1. Clone o repositório**
```bash
git clone https://github.com/https-shini/space-invaders.git
cd space-invaders
```

**2. Inicie um servidor local**

Com a extensão **Live Server** no VS Code, clique com o botão direito no `index.html` e selecione *"Open with Live Server"*.

Ou via terminal:
```bash
npx serve .
```

**3. Acesse no navegador**
```
http://localhost:3000
```

---

<div align="center">

Feito com 💙 — destrua os invasores e bata seu próprio recorde!

⭐ Se gostou, deixe uma estrela no repositório!

</div>

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=24&height=120&section=footer"/>
