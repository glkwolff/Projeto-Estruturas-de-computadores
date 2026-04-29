# Infográfico Interativo: Arquitetura de Servidores

> Projeto desenvolvido para a disciplina **Fundamentos de Estruturas de Computadores**  
> Universidade Positivo · Prof. Rubem Koide · 2026.1

---

##  Descrição

Infográfico interativo que explora visualmente a arquitetura de servidores modernos, diferenciando-os de computadores pessoais. Desenvolvido em HTML, CSS e JavaScript puro — sem dependências externas — e pode ser executado diretamente no navegador.

O projeto é dividido em **5 módulos navegáveis**:

| Módulo | Conteúdo |
|---|---|
|  Desktop vs Servidor | Comparativo de propósito, redundância, form factor e gerenciamento remoto |
|  Array RAID Interativo | Simulação dos níveis RAID 0, 1, 5 e 10 com falha de disco em tempo real |
|  Memória ECC | Demonstração de bit flip por raio cósmico com detecção e correção automática |
|  Hierarquia & NUMA | Pirâmide de memória interativa com latências reais e conceito de NUMA |
|  Virtualização | Alocação dinâmica de VMs com monitoramento de recursos do host físico |

---

## 👥 Equipe

| Nome |
|---|
| Gabriel Wolff |
| Vitor Camillo |
| João Victor Alvarez |
| Lucas Ashikaga |
| Wellington Fonseca |

---

## Como executar

O projeto **não requer instalação, servidor local ou conexão com internet**.

**1. Clone o repositório**
```bash
git clone https://github.com/glkwolff/Projeto-Estruturas-de-computadores
```

**2. Acesse a pasta do projeto**
```bash
cd aulaquarta
```

**3. Abra o arquivo no navegador**
```bash
# Linux
xdg-open index.html

# Windows
start index.html

# macOS
open index.html
```

Ou simplesmente arraste o arquivo `index.html` para qualquer navegador moderno (Chrome, Firefox, Edge) ou clique em cima para abrir com o navegador padrão.

---

##  Tecnologias utilizadas

- HTML5
- CSS3 (animations, transitions, CSS variables, clip-path)
- JavaScript ES6+ (manipulação de DOM, lógica de estado, timers)

---

##  Referências Bibliográficas

- MORIMOTO, Carlos E. *Hardware II: o guia definitivo*. Sul Editores, 2013.
- TORRES, Gabriel. *Montagem de Micros*. Novaterra, 2013.
- STALLINGS, William. *Arquitetura e organização de computadores*. 8. ed. Pearson Prentice Hall, 2010.