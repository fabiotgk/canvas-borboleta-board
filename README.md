# Board Borboleta 🦋↔

Board **interativo** (estilo draw.io/excalidraw) da **Arquitetura Borboleta** — canvas navegável
com **pan, zoom vetorial** (nunca perde qualidade), **post-its** e **conectores (setas)**.

**Ao vivo:** https://fabiotgk.github.io/canvas-borboleta-board/
**Versão A3 para impressão:** https://fabiotgk.github.io/canvas-borboleta/ · [repo](https://github.com/fabiotgk/canvas-borboleta)

---

## Diferença entre as duas peças

| | Este board (tela) | [Canvas A3](https://github.com/fabiotgk/canvas-borboleta) (impressão) |
|---|---|---|
| Uso | Navegar, apresentar, facilitar ao vivo | Imprimir em A3 e colar post-it físico |
| Canvas | "Infinito" com pan + zoom | Proporção A3 travada |
| Extras | Conectores (setas), minimapa, post-it livre | Layout fixo, rodapé impresso |

## Como usar

- **Navegar:** arraste o fundo · **zoom:** scroll do mouse / pinça (vetorial, sempre nítido) · botões **− / % / + / Ajustar**.
- **Post-it:** clique num slot de etapa (cola já etiquetado) ou **+ Post-it** (livre). Editar (duplo-clique), trocar cor, arrastar, remover.
- **Conectar:** botão **↔ Conectar** e clique em 2 itens (post-its ou slots) — ou o ícone de corrente no post-it. A seta acompanha ao mover. Clique na seta para selecionar e apagar (✕ / Delete).
- **Minimapa** (canto inferior direito): visão geral + retângulo do que está na tela; clique para navegar.
- Tudo é salvo no navegador (`localStorage`).

## Estrutura

```
canvas-borboleta-board/
├── index.html                 ← board inteiro (HTML+CSS+JS inline, zero dependências)
├── README.md
└── .github/workflows/deploy.yml  ← deploy automático no GitHub Pages (Actions)
```

## Manutenção

Tudo em `index.html`, dentro do `<script>`:

- **Conteúdo do método:** `ZONES`, `FUNNEL`, `CHAN_L`/`CHAN_R` (iguais à versão A3).
- **Forma das asas / slots:** `FORE`/`HIND`, `FORE_SLOTS`/`HIND_SLOTS`.
- **Pan/zoom:** funções `applyVB`, `fit`, `setZoomAround` (o zoom é feito mexendo no `viewBox` do SVG — é o que mantém tudo vetorial e nítido).
- **Post-its:** `makeNote` / `addNote` (dimensão `NW`×`NH`, cores `RAW`).
- **Conectores:** `renderConns`, `clip` (recorte da seta na borda da caixa), `pickAnchor`.
- **Minimapa:** `updateMinimap`.

### Rodar localmente

```bash
cd canvas-borboleta-board
python3 -m http.server 8000    # abrir http://localhost:8000
```

### Deploy

Automático: qualquer `git push` na branch `master` dispara o GitHub Actions que republica o Pages em ~1 min.

## Ideias de evolução

- Exportar/importar o board (JSON) para salvar sessões.
- Conectores curvos e rotulados.
- Snap dos post-its aos slots.

---

Feito por DevNX.
