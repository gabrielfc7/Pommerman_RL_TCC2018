# Aplicação de Aprendizado por Reforço no Jogo Pommerman
### Reinforcement Learning in Multi-Agent Adversarial Environments (Pommerman Benchmark)

[![Language](https://img.shields.io/badge/Language-Python_3.6-3776AB.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Domain](https://img.shields.io/badge/Domain-Reinforcement_Learning-blue.svg)](https://en.wikipedia.org/wiki/Reinforcement_learning)
[![Benchmark](https://img.shields.io/badge/Benchmark-Pommerman_(NeurIPS)-critical.svg)](https://www.pommerman.com/)
[![Institution](https://img.shields.io/badge/Institution-UFMS_FACOM-00529B.svg)](https://www.ufms.br/)
[![Degree](https://img.shields.io/badge/Degree-B.S._in_Computer_Science-success.svg)](https://facom.ufms.br/)
[![Monograph](https://img.shields.io/badge/Monograph-PDF_Included-red.svg?logo=adobe-acrobat-reader&logoColor=white)](Aplica__o_de_aprendizado_por_refor_o_no_Jogo_Pommerman.pdf)

Trabalho de Conclusão de Curso (TCC) apresentado à **Faculdade de Computação (FACOM)** da **Universidade Federal de Mato Grosso do Sul (UFMS)** como requisito parcial para obtenção do grau de Bacharel em Ciência da Computação (2018).

---

## 📖 Resumo (Abstract)

### Português
O ambiente Pommerman, inspirado no clássico jogo *Bomberman*, foi desenvolvido como um benchmark para pesquisa em Inteligência Artificial, Aprendizado por Reforço (Reinforcement Learning - RL) e sistemas multiagentes. O jogo apresenta desafios fundamentais como observabilidade parcial, recompensas esparsas e atrasadas, espaço de ações estocástico e ambientes altamente competitivos.

Este trabalho investiga a formulação e o treinamento de agentes baseados em Aprendizado por Reforço na modalidade *Free-For-All* (FFA), onde quatro agentes disputam simultaneamente até restar um único vencedor. São analisadas técnicas de representação de estados, modelagem de funções de recompensa (*reward shaping*) e estabilidade de convergência frente a agentes heurísticos de referência.

### English
The Pommerman environment (accepted as an official AI competition benchmark at NeurIPS) presents critical challenges for multi-agent reinforcement learning: partial observability, delayed and sparse rewards, communication constraints, and high volatility where a single misstep causes agent elimination.

This graduation monograph investigates the modeling and training of reinforcement learning agents operating in the four-player Free-For-All (FFA) setting. We study state representation spaces, reward shaping mechanics, and policy convergence against baseline heuristic adversaries.

📄 **Monografia Completa:** O documento completo está disponível no repositório:  
👉 [`Aplica__o_de_aprendizado_por_refor_o_no_Jogo_Pommerman.pdf`](file:///d:/GitHubOrganizer/Pommerman_RL_TCC2018/Aplica__o_de_aprendizado_por_refor_o_no_Jogo_Pommerman.pdf)

---

## 🕹️ O Ambiente Pommerman

```
+---+---+---+---+---+---+---+---+---+---+---+
| 0 |   |   | W |   |   |   | W |   |   | 1 |
+---+---+---+---+---+---+---+---+---+---+---+
|   | W |   | W |   | W |   | W |   | W |   |
+---+---+---+---+---+---+---+---+---+---+---+
|   |   |   |   | B |   |   |   |   |   |   |
+---+---+---+---+---+---+---+---+---+---+---+
| W | W |   | W |   | W |   | W |   | W | W |
+---+---+---+---+---+---+---+---+---+---+---+
| 3 |   |   | W |   |   |   | W |   |   | 2 |
+---+---+---+---+---+---+---+---+---+---+---+
(0, 1, 2, 3: Jogadores | W: Paredes Rígidas/Madeira | B: Bombas)
```

- **Dinâmica do Jogo:** Tabuleiro 11×11 gerado proceduralmente com paredes destrutíveis (madeira) e indestrutíveis (pedra).
- **Espaço de Ações:** 6 ações discretas: `Stop (0)`, `Up (1)`, `Left (2)`, `Down (3)`, `Right (4)`, `Bomb (5)`.
- **Modos de Jogo:**
  - `FFA (Free-For-All)`: 4 agentes disputando de forma individual.
  - `Team (2v2)`: Cooperação com comunicação restrita.

---

## 📂 Estrutura do Repositório

| Arquivo / Pacote | Descrição |
| :--- | :--- |
| **`Aplica__o_de_aprendizado_por_refor_o_no_Jogo_Pommerman.pdf`** | Monografia completa de TCC (texto integral, fundamentação teórica, gráficos e resultados). |
| **`playground.part01.rar` ... `.part06.rar`** | Arquivos compactados com o código-fonte do ambiente Pommerman, agentes e dependências de dados. |
| **`examples/simple_ffa_run.py`** | Script principal modificado para execução das partidas de teste e coleta de dados experimentais. |
| **`Bingen.py`** | Rotina de geração e conversão de dados de partidas em representações binárias otimizadas. |
| **`printTable.py`** | Utilitário para tabulação, cálculo de taxas de vitória/sobrevivência e formatação de resultados. |

---

## 🚀 Instruções de Instalação e Execução

### 1. Descompactação dos Arquivos
Os arquivos do ambiente estão divididos em um volume RAR de 6 partes para acomodar os limites de armazenamento:
```bash
# No Windows (usando WinRAR ou 7-Zip via terminal):
7z x playground.part01.rar

# No Linux:
unrar x playground.part01.rar
```

### 2. Instalação do Ambiente Pommerman
Recomenda-se o uso de um ambiente virtual Python (Python 3.6 ou 3.7):
```bash
# Criar e ativar o ambiente virtual
python -m venv venv
# Linux / macOS:
source venv/bin/activate
# Windows:
.\venv\Scripts\activate

# Entrar no diretório descompactado do playground
cd playground

# Compilar e instalar o pacote pommerman
python setup.py build
python setup.py install
```

### 3. Executando os Experimentos
Para executar as simulações e avaliar as partidas FFA entre os agentes:
```bash
cd examples
python simple_ffa_run.py
```

Para processar as tabelas de métricas estatísticas:
```bash
python printTable.py
```

---

## 📊 Principais Contribuições e Resultados

1. **Modelagem de Recompensas Intermediárias (*Reward Shaping*):** Demonstração de que recompensas esparsas puras ($\pm 1$ apenas ao final do jogo) resultam em convergência lenta devido à frequência de suicídio por bombas nos primeiros episódios. A inclusão de recompensas intermediárias para sobrevivência, destruição de obstáculos e coleta de *power-ups* reduziu drasticamente o tempo de convergência.
2. **Benchmark Comparativo:** Comparação empírica contra os agentes heuristicamente definidos pela biblioteca Pommerman (`SimpleAgent`), demonstrando a viabilidade do aprendizado autônomo de padrões de esquiva e posicionamento tático.

---

## 📜 Citação Acadêmica

Se você utilizar este trabalho ou dados em sua pesquisa, cite conforme o formato abaixo:

```bibtex
@monography{cacao2018pommerman,
  title     = {Aplicação de Aprendizado por Reforço no Jogo Pommerman},
  author    = {Gabriel Fernandes Cacao},
  year      = {2018},
  school    = {Universidade Federal de Mato Grosso do Sul (UFMS)},
  address   = {Campo Grande, MS, Brasil},
  type      = {Trabalho de Conclusão de Curso (Bacharelado em Ciência da Computação)},
  institution = {Faculdade de Computação (FACOM)}
}
```

---

## 👨‍💻 Autor

**Gabriel F. Cacao**  
Bacharel em Ciência da Computação — Universidade Federal de Mato Grosso do Sul (UFMS)  
GitHub: [@gabrielfc7](https://github.com/gabrielfc7)