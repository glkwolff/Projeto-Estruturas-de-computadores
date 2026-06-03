# Roteiro de Apresentação — Defesa do Projeto

**Disciplina:** Fundamentos de Estruturas de Computadores
**Prof.:** Rubem Koide
**Universidade Positivo · 2026.1**

**Duração total:** 15 minutos (rígido)
**Critério de nota:** 2,5 pontos individuais (cada integrante apresenta o módulo que dominou)
**Formato sugerido:** 14 slides, ~60–90 s cada
**Apoio visual:** demonstração ao vivo do `projeto.html` em tela cheia (alternar entre slides e navegador)

---

## Divisão de responsabilidades

| Integrante | Bloco de apresentação | Tempo estimado |
|---|---|---|
| **Gabriel Wolff** | Abertura + Módulo 1 + síntese (Mód. 6) | ~4 min |
| **Vitor Camillo** | Módulo 2 — RAID + Amdahl | ~2 min |
| **João Victor Alvarez** | Módulo 3 — ECC + Hamming | ~2 min |
| **Lucas Ashikaga** | Módulo 4 — Hierarquia + NUMA | ~2 min |
| **Wellington Fonseca** | Módulo 5 — Virtualização | ~2 min |
| Encerramento (rotativo) | Conclusão + Q&A | ~3 min compartilhados |

> **Dica:** cada apresentador deve, no início de seu bloco, abrir o módulo correspondente do infográfico ao vivo. Isso vale mais que slide estático.

---

## Slide 1 — Capa (00:00 → 00:20)

**Apresentador:** Gabriel
**Conteúdo:**
- Título: "Arquitetura de Servidores — Infográfico Interativo"
- Subtítulo: "Fundamentos de Estruturas de Computadores · 2026.1"
- Equipe (5 nomes) + Universidade Positivo + Prof. Rubem Koide

**Fala-chave:** "Boa noite, professor. Somos a equipe Gabriel, Vitor, João, Lucas e Wellington, e vamos apresentar o infográfico interativo de arquitetura de servidores. Em 15 minutos vamos passar pelos seis módulos, demonstrando cada um ao vivo."

---

## Slide 2 — Agenda (00:20 → 00:50)

**Apresentador:** Gabriel
**Conteúdo:**
- 1. Problema e objetivos
- 2. Visão geral do artefato
- 3. Demonstração dos 6 módulos
- 4. Resultados consolidados
- 5. Conclusão + perguntas

**Fala-chave:** "A apresentação tem essa estrutura. O foco está na parte 3 — a demo dos módulos — onde cada integrante mostra o que aprofundou."

---

## Slide 3 — Problema e objetivos (00:50 → 01:50)

**Apresentador:** Gabriel
**Conteúdo:**
- **Contexto:** projeto bimestral da disciplina, cobrir aulas 6 a 12 num artefato didático
- **Problema enfrentado:** primeira entrega (abril/2026) foi avaliada como "muito básica" pelo professor
- **Decisão:** segunda iteração focada em **profundidade técnica**, não em mais código
- **Métrica do salto:** 1.060 linhas → 2.554 linhas · 3 referências → 17 referências · 0 fórmulas → 4 fórmulas · 5 simuladores → 8 simuladores

**Fala-chave:** "Quando o professor disse que estava muito básico, a tentação era acrescentar mais animações. Decidimos o oposto: aprofundar o que já existia, com tabelas reais, fórmulas explícitas e referência formal a Stallings, Patterson e Hamming. O dev quase não mudou; o conteúdo dobrou."

---

## Slide 4 — Visão geral do artefato (01:50 → 02:30)

**Apresentador:** Gabriel
**Conteúdo:**
- Screenshot da home com a nav lateral (7 itens) + módulo 1 ativo
- Stack: HTML5 + CSS3 + JS ES6+ puro, **sem dependências**
- Executa abrindo o arquivo no navegador (offline)
- 6 módulos temáticos + 1 índice de referências clicáveis

**Fala-chave:** "Decisão técnica: arquivo único, sem framework, sem build. Toda a energia da segunda iteração foi para o conteúdo. Agora vamos ao vivo no navegador."

> **AÇÃO:** abrir o navegador em tela cheia (F11) e mostrar a tela inicial. Daqui em diante, alternar entre browser e slides.

---

## Slide 5 — Módulo 1: Desktop vs Servidor (02:30 → 04:30, 2 min)

**Apresentador:** Gabriel
**No navegador, demonstrar:**

1. Aba **Visão Geral**: comparativo lado-a-lado
2. Aba **Interconexão CPU**: tabela QPI/UPI/Infinity Fabric/NVLink + diagrama dual-socket
3. Aba **Barramentos**: tabela PCIe 3.0/4.0/5.0 + NVMe + 100 GbE
4. Aba **IA & HPC**: card do Grace Hopper / TPU v5p / Frontier

**Falas-chave:**
- *"O que parece 'um computador maior' são na verdade subsistemas redundantes em todos os pontos: fontes N+1, multi-socket, ECC, BMC."*
- *"O QPI tem 4 camadas — espelha o modelo OSI. Por isso a Intel demorou tanto para abandonar o FSB."*
- *"O Frontier do Oak Ridge é a referência do que servidor virou em 2024: 9.408 nós EPYC + GPU MI250X, 1,2 exaFLOPs."*

---

## Slide 6 — Módulo 2: RAID + Amdahl (04:30 → 06:30, 2 min)

**Apresentador:** Vitor
**No navegador, demonstrar:**

1. Aba **Simulador**: trocar entre RAID 0/1/5/10 e clicar nos discos para falhar
2. Aba **Calculadora**: alterar nº de discos e nível, mostrar mudança em IOPS de escrita
3. Aba **Amdahl**: explicar o exemplo do servidor WWW da Aula 9

**Falas-chave:**
- *"RAID 5 sobrevive a 1 falha — clico aqui... veja, o array vai pra DEGRADED, reconstruindo a paridade na hora. Mas se eu clico no segundo, perde tudo."*
- *"A fórmula da paridade é simples: `P = A XOR B XOR C`. Se C for perdido, calculo `C = A XOR B XOR P` — recupero o dado bit a bit."*
- *"O grande ensinamento da Lei de Amdahl: o professor cita na Aula 9 que num servidor WWW, 99,3% do tempo é latência de disco. Mesmo com infinitos discos em paralelo, o ganho máximo é 1,007×. A lição: não paralelize o que já é serial — troque por SSD."*

> **AÇÃO Vitor:** no slider de Amdahl, mostrar P=0,007 → speedup teto absurdo de 1,007×.

---

## Slide 7 — Módulo 3: Memória ECC + Hamming (06:30 → 08:30, 2 min)

**Apresentador:** João Victor
**No navegador, demonstrar:**

1. Aba **Simulador**: clicar no botão "Disparar Raio Cósmico" e mostrar o lado da RAM comum (kernel panic) vs RAM ECC (corrige sozinha)
2. Aba **Como funciona**: explicar o layout dos 12 bits Hamming, tabela de cobertura das paridades
3. Aba **Soft errors no mundo real**: citar o estudo Google + o caso da eleição da Bélgica

**Falas-chave:**
- *"Não é teoria: o estudo do Google em 2009 mediu 25.000 a 70.000 erros corrigíveis por DIMM por ano. 8% dos pentes têm pelo menos 1 erro/ano."*
- *"Aqui está o pulo do gato do Hamming: os bits de paridade ficam em posições de potência de 2. Por quê? Porque o síndrome em binário aponta exatamente a posição do bit corrompido. Síndrome 0101 = 5 = D2 corrompido. O hardware inverte o bit 5 e entrega o dado certo, sem o SO saber."*
- *"Caso real: eleição de Schaerbeek, Bélgica, 2003. Uma candidata recebeu 4.096 votos extras. Por quê? Bit flipou na posição 12, e 2¹² = 4096. Sistema sem ECC."*

---

## Slide 8 — Módulo 4: Hierarquia + NUMA (08:30 → 10:30, 2 min)

**Apresentador:** Lucas
**No navegador, demonstrar:**

1. Aba **Pirâmide & Latências**: hover na pirâmide + tabela "latência em escala humana"
2. Aba **Cache na prática**: tabela com specs do i7-5960X + simulador de hit/miss (clicar várias vezes)
3. Aba **NUMA & Coerência**: diagrama dual-socket + tabela MESI
4. Aba **Paginação & TLB**: huge pages + page walk

**Falas-chave:**
- *"Se 1 ciclo de CPU fosse 1 segundo, ler da RAM remota NUMA seriam 8 minutos. Ler do HDD: 1 ano. Por isso cache é tudo."*
- *"O i7-5960X tem 20 MB de L3 compartilhada entre 8 cores. Cada linha tem 64 bytes — é a unidade indivisível. Quando leio 1 byte, trago 63 vizinhos. Por isso `for` em array é rápido e `for` em linked list é lento."*
- *"MESI mantém os 8 cores enxergando o mesmo dado. Quando escrevo numa linha Shared, invalido em todos os outros cores — custo de centenas de ciclos. É o famoso false sharing dos livros."*

---

## Slide 9 — Módulo 5: Virtualização (10:30 → 12:30, 2 min)

**Apresentador:** Wellington
**No navegador, demonstrar:**

1. Aba **Simulador**: criar VMs até o host saturar (mostrar barra ficando vermelha)
2. Aba **Tipo 1 vs Tipo 2**: explicar ESXi vs VirtualBox + diagrama dos anéis de proteção
3. Aba **VM vs Contêiner**: tabela comparativa + código `unshare`
4. Aba **Kernels & Escalonador**: árvore rubro-negra do CFS

**Falas-chave:**
- *"Tipo 1 é bare metal — VMware ESXi, KVM, Proxmox — é o próprio SO. Tipo 2 é hosted, tipo VirtualBox, que o próprio professor usou na Aula 12."*
- *"VT-x da Intel introduziu o Ring −1. Antes, para virtualizar x86 era preciso binary translation. Hoje qualquer Xeon faz nativo em hardware."*
- *"Contêiner ≠ VM: contêiner é só processo + namespaces + cgroups. Mesmo kernel do host. Boot em 100 ms, footprint de MBs. Por isso Kubernetes consegue 2.000 pods num host."*
- *"O CFS escolhe sempre a task mais à esquerda da árvore rubro-negra — quem rodou menos. O.log n, mas com latência muito previsível."*

---

## Slide 10 — Módulo 6: Stack Completo (12:30 → 13:30, 1 min)

**Apresentador:** Gabriel
**No navegador, demonstrar:**

- Clicar nas 9 camadas e mostrar o painel de detalhe à direita
- Fechar com a curiosidade do "GET /produto/123"

**Falas-chave:**
- *"Esse módulo foi a maior adição da segunda iteração. Os cinco módulos anteriores não são pilares isolados — são camadas. Aqui mostramos o stack completo, da PSU até o Nginx, com 9 camadas clicáveis."*
- *"Olha o que acontece numa única requisição HTTP de e-commerce: passa pela rede (8), pelo container (2), pela VM (3), pelo hypervisor (4), executa em CPU NUMA-aware (5), aloca em RAM ECC (6), lê de RAID NVMe (7), e responde voltando toda a cadeia em 10 milissegundos. Cada camada custou microssegundos."*

---

## Slide 11 — Resultados consolidados (13:30 → 14:00, 30 s)

**Apresentador:** rotativo (a equipe combina)
**Conteúdo (tabela compacta):**

| Métrica | 1ª iteração | 2ª iteração | Δ |
|---|---|---|---|
| Linhas de código | 1.060 | 2.554 | +141% |
| Referências bibliográficas | 3 | 17 | +467% |
| Tabelas técnicas | 0 | 11 | — |
| Fórmulas matemáticas | 0 | 4 | — |
| Simuladores interativos | 5 | 8 | +60% |
| Sub-abas (granularidade) | 0 | 21 | — |

**Fala-chave:** "A segunda iteração não foi 'mais código' — foi mais conteúdo. O número de linhas só dobrou porque tabelas, fórmulas e referências precisam de markup."

---

## Slide 12 — Conclusão + trabalhos futuros (14:00 → 14:30, 30 s)

**Apresentador:** rotativo
**Conteúdo:**
- O artefato atende aos 6 objetivos específicos
- **Limitações:** simuladores são determinísticos, não medem hardware real
- **Trabalhos futuros:** animação MESI, page-walk visual, integração com `fio`/`stress-ng`, tradução para inglês (recurso aberto CC-BY), auditoria WCAG 2.1 AA

**Fala-chave:** "O salto de profundidade entre as duas versões mostra que profundidade técnica é decisão de conteúdo, não de stack. Manter um arquivo HTML sem dependências facilitou justamente esse foco."

---

## Slide 13 — Referências (14:30 → 14:45, 15 s)

**Apresentador:** rotativo
**Conteúdo:** lista compacta das 5 referências mais usadas (Stallings, Patterson & Hennessy, Russinovich, Hamming 1950, Schroeder et al. 2009).

**AÇÃO:** abrir o módulo Referências no navegador e clicar em qualquer `[n]` inline pra mostrar a navegação clicável funcionando.

**Fala-chave:** "Todas as 17 referências estão acessíveis diretamente do infográfico — qualquer citação `[n]` é um link clicável."

---

## Slide 14 — Agradecimento + Q&A (14:45 → 15:00 + tempo de perguntas)

**Apresentador:** Gabriel
**Conteúdo:** "Obrigado, professor. Estamos abertos a perguntas."

**Perguntas que podem vir do professor — preparar respostas curtas:**

| Pergunta esperada | Quem responde | Resposta-base |
|---|---|---|
| "Por que não usaram React/Vue?" | Gabriel | "Foco era arquitetura de computadores, não engenharia de front-end. Arquivo único facilita execução offline." |
| "RAID 5 ou RAID 10 para banco?" | Vitor | "RAID 10. RAID 5 tem write penalty de 4× — péssimo para OLTP." |
| "ECC vs ECC on-die DDR5?" | João | "On-die só protege dentro da célula. Verdadeiro ECC RDIMM protege o datapath inteiro DIMM↔CPU." |
| "Diferença prática entre MESI e MOESI?" | Lucas | "MOESI adiciona estado Owned — permite write-back lazy, reduz tráfego em sistemas com muitos cores escrevendo." |
| "Por que VT-x se já existia binary translation?" | Wellington | "Performance. Binary translation era 30–50% mais lento. VT-x dá quase nativo, e suporta migração ao vivo." |
| "Vocês usaram IA para fazer o projeto?" | Gabriel | "Sim — Gemini Canvas na primeira versão e Claude Code na segunda iteração. Ambas declaradas no Materiais e Métodos. O discernimento técnico e a verificação dos números foi nossa." |

---

## Anexo — Comandos úteis durante a demo

```bash
# Em caso de problema técnico, recuperar rápido:
xdg-open /caminho/para/projeto.html

# Ou via servidor local instantâneo:
python3 -m http.server 8000  # depois abrir http://localhost:8000/projeto.html
```

## Anexo — Checklist pré-defesa

- [ ] Notebook conectado ao projetor 24h antes (testar resolução)
- [ ] Browser em modo apresentação (F11)
- [ ] Zoom de tela 110–125% para fundo da sala enxergar
- [ ] Modo escuro do navegador desativado (infográfico já é dark)
- [ ] Bateria carregada + carregador em mãos
- [ ] Backup: PDF do relatório + cópia do `projeto.html` em pendrive
- [ ] Cronômetro discreto no celular (alarme em 14:30 para acelerar Q&A)
- [ ] Cada apresentador revisou seu bloco e treinou ao menos 2× sozinho
- [ ] Combinaram entre si quem responde qual pergunta esperada
