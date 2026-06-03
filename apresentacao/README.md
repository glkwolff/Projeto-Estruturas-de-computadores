# Apresentação de Defesa — Marp

Slides em formato **Marp** (Markdown Presentation Ecosystem). Edição como texto, exportação como `.pptx`, `.pdf` ou `.html`.

## Arquivos

- `presentation.md` — slides + notas do apresentador (palavra por palavra)
- `README.md` — este arquivo

## Como editar (recomendado: VSCode)

1. Instale a extensão **Marp for VS Code** (`marp-team.marp-vscode`).
2. Abra `presentation.md`.
3. Clique no ícone de **preview** no canto superior direito — preview ao vivo dos slides.
4. Edite à vontade. O `---` separa slides; os comentários HTML `<!-- ... -->` no fim de cada slide são as **notas do apresentador**, que aparecem no modo apresentação do PowerPoint mas **não** nos slides projetados.

## Como exportar

### Opção A — Via VSCode (mais fácil)

Com o `presentation.md` aberto:

1. `Ctrl+Shift+P` → digite `Marp: Export Slide Deck`
2. Escolha o formato:
   - **PowerPoint Document (.pptx)** — abre no PowerPoint, LibreOffice Impress, Google Slides (importando)
   - **PDF Document (.pdf)** — pronto pra projetar/distribuir
   - **HTML Slide Deck** — apresenta no navegador

### Opção B — Via linha de comando (Marp CLI)

Instale uma vez:
```bash
npm install -g @marp-team/marp-cli
```

Depois:
```bash
# PowerPoint
marp presentation.md --pptx --allow-local-files

# PDF
marp presentation.md --pdf --allow-local-files

# HTML autocontido
marp presentation.md --html --allow-local-files
```

> A flag `--allow-local-files` é necessária porque o Slide 3 usa uma imagem do diretório `../relatorio/figuras/mod1.png`.

## Como apresentar

**Modo recomendado:** exportar pra `.pptx` e usar o **Modo Apresentador do PowerPoint**, que mostra os slides na tela do projetor + as notas + cronômetro na tela do notebook.

Atalhos no PowerPoint:
- `F5` — começar apresentação do início
- `Shift+F5` — começar do slide atual
- `B` — tela preta (pra puxar atenção da banca)
- `Esc` — sair

Alternativa: exportar pra PDF e apresentar com qualquer leitor de PDF em tela cheia (`F11`).

## Estrutura da apresentação

| # | Slide | Apresentador | Tempo |
|---|---|---|---|
| 1 | Capa | Gabriel | 30s |
| 2 | Por que esse projeto? | Gabriel | 1min |
| 3 | Como o infográfico funciona | Gabriel | 30s |
| 4 | Módulo 1 — Desktop vs Servidor | Gabriel | 2min |
| 5 | Módulo 2 — RAID | Vitor | 2min |
| 6 | Módulo 3 — Memória ECC | João Victor | 2min |
| 7 | Módulo 4 — Hierarquia de memória | Lucas | 2min |
| 8 | Módulo 5 — Virtualização | Wellington | 2min |
| 9 | Módulo 6 — Stack Completo | Gabriel | 1min |
| 10 | Conclusão + trabalhos futuros | rotativo | 30s |
| 11 | Bibliografia | rotativo | 15s |
| 12 | Obrigado / Q&A | Gabriel | restante |

**Total fechado:** ~13 min de apresentação + ~2 min de margem + Q&A.

## Antes da defesa — checklist

- [ ] Cada apresentador leu suas notas (palavra por palavra) **2× sozinho** em voz alta
- [ ] Equipe ensaiou junta **1× completa** com cronômetro
- [ ] Notebook + carregador + adaptador HDMI/VGA testados na sala
- [ ] `.pptx` no notebook **e** em pendrive de backup
- [ ] `projeto.html` aberto numa aba do navegador (pra demo ao vivo)
- [ ] Combinaram quem responde cada pergunta esperada (ver últimas notas do `presentation.md`)

## Dúvidas comuns sobre Marp

**"Onde aparecem as notas do apresentador?"**
Tudo dentro de `<!-- ... -->` no fim de cada slide. No preview do VSCode e no `.pptx` exportado, elas aparecem no painel de notas do apresentador (no PowerPoint: ative o "Modo Apresentador" com `Alt+F5`).

**"As cores não estão batendo com o infográfico."**
O tema customizado está no topo de `presentation.md`, dentro do bloco `style:`. Os hexadecimais batem com o `:root` do `projeto.html`. Pra trocar o esquema, edite ali.

**"Posso adicionar mais slides?"**
Sim. Crie um novo bloco separado por `---` (3 hifens em linha) e siga o padrão dos outros. Mantenha as notas `<!-- -->` no fim pra preservar o roteiro detalhado.
