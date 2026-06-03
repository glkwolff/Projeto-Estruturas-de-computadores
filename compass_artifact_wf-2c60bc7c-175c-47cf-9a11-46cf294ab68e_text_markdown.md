# Relatório de Verificação Acadêmica — 2ª Passada
**Arquitetura de Servidores (contexto brasileiro · ABNT NBR 6023)**
*Data da verificação: 3 de junho de 2026*

## TL;DR
- **Das 12 correções aplicadas, 8 estão totalmente corretas (✅)** — Windows Internals, JEDEC DDR5, Gemini Canvas, Schroeder (números do abstract), QPI 5 camadas, Hamming SEC/SECDED, Amdahl e TOP500 — e **4 ainda têm problema residual (⚠)**: Morimoto (designação "2. ed." indevida), Love (CFS ok, mas namespaces/cgroups permanecem anacrônicos), Rowhammer/Kim (editora mais precisa = ACM/IEEE) e CVE-2015-0565 (frase imprecisa); o **bônus Schaerbeek** está substancialmente correto, com ressalva de grafia do nome.
- **Os 3 itens não-verificáveis da 1ª passada foram FECHADOS** mediante leitura do texto integral do PDF de Schroeder (cs.toronto.edu) e do site oficial da NVIDIA: a estatística de UE é **por máquina (1,3%)**, não por DIMM; **não existe número "~70% hard errors"** no paper (a dominância é argumentada qualitativamente); e a URL canônica do whitepaper Grace Hopper foi identificada.
- **Nenhuma correção introduziu erro novo grave**; as pendências são de precisão bibliográfica/factual e cada uma vem com texto corrigido pronto para colar.

---

## Key Findings
| Item | Veredito | Essência |
|---|---|---|
| 1. Windows Internals | ✅ | Ordem Yosifovich; Ionescu; Russinovich; Solomon confirmada na página de copyright |
| 2. Morimoto Hardware II | ⚠ | É 1ª edição da obra-sucessora; remover "2. ed." |
| 3. JEDEC JESD79-5D | ✅ | Versão vigente, 01/11/2025; sem revisão mais nova |
| 4. Gemini (Canvas) | ✅ | "Canvas" é o nome oficial, mantido em PT-BR |
| 5. Love (CFS/cgroups/namespaces) | ⚠ | Metadados e CFS ok; namespaces/cgroups exigem fonte adicional |
| 6. Rowhammer / Kim et al. | ⚠ | Páginas/autores/local ok; editora melhor = ACM/IEEE |
| 7. Schroeder (FIT/Mbit, 8%) | ✅ | Paráfrase fiel ao abstract |
| 8. QPI 5 camadas | ✅ | Transport opcional confirmado no white paper Intel |
| 9. Hamming SEC vs SECDED | ✅ | (12,8) SEC → (13,8) SECDED corretos |
| 10. Amdahl | ✅ | Paper de 1967 = argumento; equação é posterior |
| 11. TOP500 | ✅ | 66ª lista (nov/2025) confirma El Capitan e Frontier |
| 12. CVE-2015-0565 | ⚠ | Cobre só o escape NaCl; frase precisa de ajuste |
| Bônus. Schaerbeek | ⚠ | Fatos corretos; grafia do nome a revisar |
| B1. UE por DIMM-ano | Fechado | Unidade correta = por máquina (1,3%); por DIMM = 0,22% |
| B2. % hard errors | Fechado | "~70%" NÃO existe no paper |
| B3. URL Grace Hopper | Fechado | URL canônica do whitepaper identificada |

---

## Details

### BLOCO ✅ — Correções confirmadas como corretas

**ITEM 1 — Windows Internals (ordem dos autores). ✅ CORRETO.**
A página de copyright do livro registra textualmente: *"Copyright © 2017 by Pavel Yosifovich, Alex Ionescu, Mark E. Russinovich and David A. Solomon"*, ordem idêntica à da Microsoft Learn (*"written by Pavel Yosifovich, Alex Ionescu, Mark Russinovich and David Solomon"*). ISBN 9780735684188 e ano 2017 conferem. A ordem oficial correta é, portanto, **YOSIFOVICH; IONESCU; RUSSINOVICH; SOLOMON** — exatamente a aplicada. Observação: alguns varejistas (Microsoft Press Store, Amazon, VitalSource) listam a sequência Yosifovich/Russinovich/Ionescu/Solomon em metadados de catálogo, mas a fonte canônica (página de copyright + Microsoft Learn) confirma a ordem aplicada. *Fontes: microsoftpressstore.com; learn.microsoft.com/sysinternals; página de copyright reproduzida em dokumen.pub.*

**ITEM 3 — JEDEC JESD79-5D. ✅ CORRETO.**
A página oficial da JEDEC "Main Memory: DDR SDRAM, HBM" afirma: *"JEDEC published its widely-anticipated JESD79-5 DDR5 SDRAM standard in July 2020, and the most recent update, JESD79-5D, in November 2025."* O registro de norma confirma a data exata **01/11/2025** (JESD79-5D:2025). Em junho de 2026 **não existe** revisão mais nova (não há JESD79-5E). A entrada corrigida está correta. *Fontes: jedec.org/standards-documents/docs/jesd79-5d; jedec.org/category/technology-focus-area/main-memory-ddr-sdram.*

**ITEM 4 — Gemini (Canvas). ✅ CORRETO.**
"Canvas" é a nomenclatura oficial do Google e é mantida **sem tradução** também no suporte em português do Brasil — a Central de Ajuda PT-BR usa "Canvas" e "Adicionar Canvas" (não "modo Canvas" nem "tela"). Remover a palavra "modo" alinha-se ao uso oficial. *Fontes: gemini.google/br/overview/canvas (página "Gemini Canvas"); support.google.com/gemini/answer/16047321 (PT-BR).*

**ITEM 7 — Schroeder (números corrigidos). ✅ CORRETO.**
Lido no texto integral: o abstract afirma literalmente *"25,000 to 70,000 errors per billion device hours per Mbit and more than 8% of DIMMs affected by errors per year"* e *"We provide strong evidence that memory errors are dominated by hard errors, rather than soft errors, which previous work suspects to be the dominant error mode."* A paráfrase aplicada ("25.000 a 70.000 FIT por Mbit … mais de 8% dos DIMMs … predominantemente hard errors") é fiel ao paper. *Fonte: cs.toronto.edu/~bianca/papers/sigmetrics09.pdf (texto integral).*

**ITEM 8 — QPI (5 camadas). ✅ CORRETO.**
O white paper Intel "An Introduction to the Intel QuickPath Interconnect" (doc. 320412-001US, jan. 2009) lista no sumário as cinco camadas: **Physical, Link, Routing, Transport, Protocol**. A descrição da camada Transport como opcional é confirmada: *"The transport layer is not needed and is not present in devices that are intended for only point-to-point connections"* — em processadores ponto-a-ponto (Core i7-9xx, Xeon DP) ela está ausente e a camada de roteamento é mínima. A correção está tecnicamente correta. *Fontes: intel.com/.../quick-path-interconnect-introduction-paper.pdf; en.wikipedia.org/wiki/Intel_QuickPath_Interconnect.*

**ITEM 9 — Hamming SEC vs SECDED. ✅ CORRETO.**
A distinção está tecnicamente precisa: 8 bits de dados + 4 bits de paridade nas posições 2^k = **Hamming(12,8)**, código SEC (distância mínima 3, corrige 1 erro). O acréscimo de **um bit de paridade global** eleva a distância de Hamming a 4, gerando o código estendido **(13,8) SECDED**, que *corrige 1 erro e detecta (mas não corrige) 2 erros simultâneos*. A Wikipedia confirma: *"extended Hamming codes are single-error correcting and double-error detecting, abbreviated as SECDED."* *Fontes: en.wikipedia.org/wiki/Hamming_code; techtarget.com/whatis/definition/Hamming-code.*

**ITEM 10 — Amdahl (formulação moderna). ✅ CORRETO.**
A atribuição agora está adequada: o paper de 1967 (AFIPS Spring Joint Computer Conference, v. 30, p. 483-485) traz apenas o **argumento qualitativo**, não a equação explícita. Confirmação direta em Hill & Marty, "Amdahl's Law in the Multicore Era" (IEEE Computer/Google Research): *"Without presenting an equation, he noted that the speedup on n processors is governed by..."* — ou seja, a equação Speedup(N) = 1/((1-P) + P/N) é formulação posterior derivada do argumento original. *Fontes: research.google.com/pubs/archive/34400.pdf; PDF do paper original em www3.cs.stonybrook.edu/~rezaul/.../Amdahl-1967.pdf.*

**ITEM 11 — TOP500 atualizado. ✅ CORRETO E ATUAL.**
A lista mais recente disponível em 3 de junho de 2026 é a **66ª edição (nov/2025, anunciada no SC25)**; a 67ª edição (junho/2026, ISC) ainda não havia sido publicada. Verificações:
- **El Capitan (LLNL)** é o nº 1 do TOP500 desde nov/2024 e foi **remedido em 1,809 EFlop/s** na 66ª lista (alta de ~4% sobre os 1,742 EFlop/s de jun/2025), conforme o TOP500: *"The HPE Cray EX255a system was remeasured with 1.809 Exaflop/s on the HPL benchmark"* — 11.340.000 cores, AMD EPYC 4ª geração de 24 núcleos a 1,8 GHz + AMD Instinct MI300A.
- **Frontier (ORNL)** é o nº 2, **1,353 EFlop/s**, arquitetura **HPE Cray EX235a** com AMD EPYC de 3ª geração + AMD Instinct MI250X, totalizando **9.066.176 cores** (o número "9.408 nós" do texto refere-se à contagem de nós de computação do sistema, dado historicamente publicado; a métrica oficial de cores na 66ª lista é 9.066.176 cores — recomenda-se citar a contagem de cores para evitar ambiguidade).
- Nenhum sistema novo ultrapassou os dois. **JUPITER Booster** (EuroHPC/Jülich; BullSequana XH3000 da Eviden com NVIDIA GH200, 4.801.344 cores) tornou-se o **nº 4 com exatamente 1,000 EFlop/s na HPL**, primeiro sistema exascale europeu.
- A afirmação "nº 1 desde nov/2024" para El Capitan está correta.
*Fontes: top500.org (66ª edição, "El Capitan Retains #1 as JUPITER Becomes Europe's First Exascale System"); llnl.gov.*

---

### BLOCO ⚠ — Correções com problema residual (com texto corrigido)

**ITEM 2 — Morimoto, Hardware II. ⚠ PROBLEMA: designação "2. ed." é incorreta.**
A loja/ficha oficial da editora (editorasulina.com.br) registra **ISBN 978-85-99593-16-5** e classifica a obra como **"1ª edição"** (a página mostra "Edição: 1ª edição – 4ª reimpressão – 2015"). O plano de ensino do IFPB também cita "1ª Edição". *"Hardware II: o guia definitivo"* (2010) é uma **obra-sucessora expandida** de *"Hardware, o Guia Definitivo"* (2007) — publicada como **1ª edição da nova obra, SEM designação de edição**. Local (Porto Alegre) e ano (2010) estão corretos; o ISBN 9788599593165 confere. A inclusão de "2. ed." deve ser removida.
> **Texto corrigido sugerido:**
> *MORIMOTO, Carlos E. **Hardware II: o guia definitivo**. Porto Alegre: Sul Editores, 2010.*
*Fontes: editorasulina.com.br/detalhes.php?id=505; estudante.ifpb.edu.br (plano de ensino); estantevirtual.com.br.*

**ITEM 5 — Love (CFS/cgroups/namespaces). ⚠ PARCIALMENTE CORRETO.**
(a) **Metadados corretos.** LOVE, Robert. *Linux Kernel Development*. 3. ed. Upper Saddle River: Addison-Wesley, 2010. ISBN 9780672329463. O local **"Upper Saddle River, NJ"** é confirmado (Open Library: *"Published in Upper Saddle River, NJ"*; página de copyright Pearson). Nota: o autor reside em Boston, mas a sede editorial da Addison-Wesley/Pearson para a obra é Upper Saddle River — local correto para citação.
(b) **CFS: adequado.** O cap. 4 (Process Scheduling) cobre o Completely Fair Scheduler com árvore rubro-negra e vruntime; a 3ª edição é baseada na série 2.6 (cobrindo o CFS). A descrição de árvore rubro-negra/vruntime/O(log n) é sustentável por Love (2010).
(c) **PROBLEMA residual.** O foco do livro é escalonador, gerenciamento de memória, VFS, sincronização e interrupções; **cgroups e namespaces não recebem tratamento aprofundado**. Além disso, os **user namespaces só foram completados no kernel 3.8 (2013)**, posterior à publicação de Love (2010). Atribuir a Love a **lista completa** de namespaces (incluindo "user") permanece **anacrônico**.
> **Sugestão:** manter o CFS atribuído a Love (2010) e **acrescentar fonte adicional** para namespaces/cgroups, por exemplo:
> *THE LINUX KERNEL ORGANIZATION. **namespaces(7) — Linux manual page**. Disponível em: https://man7.org/linux/man-pages/man7/namespaces.7.html. Acesso em: 3 jun. 2026.*
> e/ou *THE LINUX KERNEL ORGANIZATION. **Control Group v2**. Disponível em: kernel.org (Documentation/admin-guide/cgroup-v2). Acesso em: 3 jun. 2026.*
*Fontes: openlibrary.org (registro da 3ª ed.); ptgmedia.pearsoncmg.com/.../9780672329463 (página de copyright); informit.com; oreilly.com.*

**ITEM 6 — Rowhammer (Kim et al.). ⚠ REFINAMENTO MENOR (editora).**
Verificações que **conferem**: páginas **361-372**; **ISCA 2014 em Minneapolis, MN** (14-18 jun. 2014); ordem de autores correta — **Yoongu Kim; Ross Daly; Jeremie Kim; Chris Fallin; Ji Hye Lee; Donghyuk Lee; Chris Wilkerson; Konrad Lai; Onur Mutlu**; DOIs válidos (ACM: 10.1145/2678373.2665726; IEEE: 10.1109/ISCA.2014.6853210).
**Ponto de precisão:** os proceedings do ISCA '14 foram publicados pela **IEEE Computer Society** (ISBN 978-1-4799-4396-8) sob patrocínio conjunto **ACM/IEEE** (o texto também figura no *ACM SIGARCH Computer Architecture News*, v. 42, n. 3). "IEEE Press" é aceitável, mas a forma mais precisa é **"ACM/IEEE"** ou **"IEEE Computer Society"**.
> **Texto sugerido:** *KIM, Yoongu et al. Flipping bits in memory without accessing them: an experimental study of DRAM disturbance errors. In: 41st Annual International Symposium on Computer Architecture (ISCA '14), Minneapolis, 2014. Proceedings. Piscataway: IEEE Computer Society, 2014. p. 361-372.*
*Fontes: dblp.org/rec/conf/isca/2014.html; dl.acm.org/doi/10.1145/2678373.2665726; iscaconf.org/isca2014; users.ece.cmu.edu/~yoonguk/papers/kim-isca14.pdf.*

**ITEM 12 — CVE-2015-0565. ⚠ IMPRECISÃO NA FRASE.**
O NVD e o post do Project Zero confirmam que o **CVE-2015-0565 cobre especificamente o escape do sandbox NaCl** (mitigado proibindo a instrução CLFLUSH no validador x86 do NaCl). Porém o post do Project Zero (Mark Seaborn, com contribuição de Thomas Dullien, 9 de março de 2015) apresentou **DOIS exploits práticos em x86**: (1) escape do NaCl — *coberto* pelo CVE-2015-0565 — e (2) **escalada de privilégio em kernel Linux x86-64 via alteração de PTEs** (sem CVE específico). O próprio post afirma: *"We built two working privilege escalation exploits that use this effect. One exploit uses rowhammer-induced bit flips to gain kernel privileges on x86-64 Linux… We have mitigated this by changing NaCl's x86 validator to disallow the CLFLUSH instruction (tracked by CVE-2015-0565)."* Logo, chamar o CVE-2015-0565 de "a primeira exploração prática em x86" é **impreciso** — ele é apenas um dos dois exploits.
> **Texto corrigido sugerido:**
> *"Rowhammer: acessos repetidos a uma linha de DRAM induzem bit-flips em linhas vizinhas (KIM et al., ISCA 2014). O Project Zero (SEABORN; DULLIEN, 2015) demonstrou as primeiras explorações práticas em x86: o escape do sandbox NaCl do Chrome — registrado como CVE-2015-0565 e mitigado proibindo a instrução CLFLUSH — e a escalada de privilégios em kernel Linux x86-64 via alteração de PTEs (sem CVE específico)."*
*Fontes: nvd.nist.gov/vuln/detail/CVE-2015-0565; projectzero.google/2015/03/exploiting-dram-rowhammer-bug-to-gain.html; en.wikipedia.org/wiki/Row_hammer.*

**BÔNUS — Schaerbeek. ⚠ RESSALVA DE GRAFIA / FONTE PRIMÁRIA.**
Os fatos da nova redação estão alinhados às fontes: **eleição FEDERAL belga de 18 de maio de 2003**; **4.096 votos extras** (= 2^12, bit na posição 13); atribuição a **single-event upset como hipótese provável, nunca comprovada definitivamente**. A correção editorial da VICE/Motherboard confirma a ressalva: *"Correction: …the 2003 Schaerbeek election… was a federal election. An SEU was also not definitely confirmed to have been the reason for the error, though it is the most likely option after process of elimination."* A Wikipedia ("Electronic voting in Belgium") registra a explicação oficial como *"the spontaneous creation of a bit at the position 13 in the memory of the computer"*.
**Ressalvas:** (a) a **grafia do nome varia** entre fontes — "Maria Vindevogel", "Maria Vindevoghel" e "Marie Vindevogel"; a forma mais usada para a política belga (PVDA/Partij van de Arbeid) é **"Maria Vindevoghel"** — recomenda-se padronizar para esta grafia. (b) **Não foi possível acessar o relatório oficial belga** ("Rapport concernant les élections du 18 mai 2003" do colégio de peritos) diretamente — a verificação apoiou-se em fontes secundárias confiáveis (Wikipedia, VICE com correção, Grokipedia). Este ponto permanece **parcialmente não-verificável na fonte primária**.
*Fontes: en.wikipedia.org/wiki/Electronic_voting_in_Belgium; vice.com (artigo AAAS 2017, com correção); xda-developers.com.*

---

### PARTE B — Fechamento dos 3 não-verificáveis (lidos no texto integral)

**B1 — Schroeder, taxa de UE por DIMM-ano. ✅ FECHADO.**
A leitura integral confirma que a **unidade correta da estatística "~1,3%" é POR MÁQUINA, não por DIMM**: *"Across the entire fleet, 1.3% of machines are affected by uncorrectable errors per year, with some platforms seeing as many as 2-4% affected"* (Seção 3.1). A Conclusão 1 resume: *"The annual incidence of uncorrectable errors was 1.3% per machine and 0.22% per DIMM."* Pela Tabela 1, a incidência de UE **por DIMM** é **0,22% no geral**, variando de **0,05% a 0,39%** conforme a plataforma (A 0,05%; C 0,28%; D 0,25%; E 0,08%; F 0,39%). Quanto a CE: **8,2% dos DIMMs** afetados/ano (média ~3.751 CE/DIMM-ano; ~22.696 CE/máquina-ano).
> **Forma correta para eventual reinserção:** *"~1,3% das máquinas e ~0,22% dos DIMMs são afetados por erros incorrigíveis (UE) por ano (variando de 0,05% a 0,39% por DIMM conforme a plataforma)."*

**B2 — Schroeder, percentual de hard errors. ✅ FECHADO — o número "~70%" NÃO existe no paper.**
A leitura integral confirma que **não há qualquer percentual numérico de hard errors** no paper. Pelo contrário, na Seção 2.1 os autores afirmam que **sequer conseguem distinguir** os dois tipos: *"Our measurement infrastructure captures both hard and soft errors, but does not allow us to reliably distinguish these types of errors. All our numbers include both hard and soft errors."* A dominância de hard errors é argumentada **qualitativamente** (Seção 5.3 e Conclusão 7, baseada no efeito da utilização em sistemas com scrubber e na forte correlação temporal de erros no mesmo DIMM). **Atenção a uma armadilha:** existe um "70-80%" no paper, mas refere-se a **UEs precedidos por CE** (*"In 70-80% of the cases an uncorrectable error is preceded by a correctable error"*, Conclusão 2) — conceito distinto, provavelmente a origem da confusão do "~70% hard errors". **A remoção do "~70% hard errors" foi acertada.**
> **Frases quantitativas citáveis que PODEM substituir** (caso se queira um número): *"in more than 93% of the cases a machine that sees a correctable error experiences at least one more correctable error in the same year"* (Seção 3.1) e *"In more than 85% of the cases a correctable error is followed by at least one more correctable error in the same month"* (Seção 4.1) — evidências da repetição de erros que sustentam a tese de hard errors. **Não citar um percentual de "hard errors" como se fosse do paper.**

**B3 — NVIDIA Grace Hopper, URL canônica. ✅ FECHADO.**
A URL testada `https://resources.nvidia.com/en-us-grace-cpu/grace-hopper-superchip` **aponta para o Data Sheet, não para o whitepaper de arquitetura**. A URL canônica do whitepaper de arquitetura é:
`https://resources.nvidia.com/en-us-data-center-overview/nvidia-grace-hopper-superchip-architecture-whitepaper` (página oficial NVIDIA ativa; existe também a variante `resources.nvidia.com/en-us-grace-cpu/nvidia-grace-hopper`). O documento (versão V1.12, "NVIDIA GH200 Grace Hopper Superchip Architecture") é o whitepaper de 2023.
> **Citação ABNT sugerida (com URL verificada e data de acesso):**
> *NVIDIA CORPORATION. **NVIDIA Grace Hopper Superchip Architecture Whitepaper**. Santa Clara: NVIDIA, 2023. Disponível em: https://resources.nvidia.com/en-us-data-center-overview/nvidia-grace-hopper-superchip-architecture-whitepaper. Acesso em: 3 jun. 2026.*
*Fontes: resources.nvidia.com (páginas oficiais NVIDIA); developer.nvidia.com/blog/nvidia-grace-hopper-superchip-architecture-in-depth.*

---

## Recommendations
**Ação imediata (corrigir antes de publicar):**
1. **Item 2 (Morimoto):** remover "2. ed." → usar a forma sem designação de edição (texto fornecido acima). Risco de erro factual ABNT alto e correção trivial.
2. **Item 12 (CVE-2015-0565):** substituir a frase pela redação refinada que distingue os dois exploits do Project Zero (texto fornecido). Evita afirmação imprecisa de "primeira exploração prática".
3. **Item 5 (Love):** manter Love (2010) para o CFS, mas **acrescentar** a fonte `namespaces(7)` (man7.org) e/ou `cgroup-v2` (kernel.org) para sustentar a afirmação sobre contêineres/namespaces — elimina o anacronismo dos user namespaces (kernel 3.8, 2013).

**Ação recomendada (melhora a precisão):**
4. **Item 6 (Rowhammer):** trocar "IEEE Press" por "IEEE Computer Society" ou "ACM/IEEE" na entrada.
5. **Bônus (Schaerbeek):** padronizar a grafia para **"Maria Vindevoghel"** e, idealmente, localizar o relatório oficial belga de 2003 para citação primária (atualmente apoiado só em fontes secundárias).
6. **Item 11 (TOP500):** considerar citar a contagem de **cores (9.066.176)** do Frontier em vez de "9.408 nós" para alinhar exatamente à métrica publicada na 66ª lista; reavaliar após a divulgação da 67ª lista (ISC, junho/2026), pois os valores de El Capitan/Frontier podem ser atualizados.

**Benchmarks que mudariam estas recomendações:** se a 67ª lista TOP500 (junho/2026) for publicada e alterar posições/Rmax, reverificar o Item 11; se a JEDEC publicar JESD79-5E, reverificar o Item 3; se for obtido acesso ao relatório oficial belga, promover o bônus Schaerbeek de ⚠ para ✅.

## Caveats
- **Leitura em texto integral vs. fonte secundária:** os itens 7, B1 e B2 (Schroeder) foram verificados no **PDF integral** (cs.toronto.edu). O item 1 (página de copyright do Windows Internals) foi lido em reprodução de terceiros (dokumen.pub), mas **corroborado** pela Microsoft Learn oficial. O bônus Schaerbeek **não** pôde ser confirmado na fonte primária belga (apenas secundárias).
- **Item 11:** a expressão "9.408 nós" do texto original do usuário é um dado historicamente publicado para o Frontier; a métrica oficial corrente da 66ª lista é em **cores (9.066.176)**. Não é erro factual, mas há ambiguidade entre "nós" e "cores".
- **Item 6:** "IEEE Press" não está errado (o paper é IEEE/ACM); trata-se de refinamento de precisão, não de erro grave.
- **CVE-2015-0565:** o NVD redireciona via JavaScript e não foi possível extrair o texto literal do registro NVD por fetch direto; a descrição foi confirmada por VulDB, Vulmon, Wikipedia e pelo **post primário do Project Zero**, que são consistentes entre si.
- Nenhuma URL ou número neste relatório foi inventado; onde a confirmação foi indireta, isso está sinalizado explicitamente.