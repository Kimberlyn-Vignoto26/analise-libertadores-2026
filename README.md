# ⚽ Libertadores 2026: análise de dados e projeção da final

Projeto de portfólio em Python para explorar as finais da CONMEBOL Libertadores de 2023 a 2025 e comparar indicadores das campanhas do Palmeiras e do Estudiantes antes da final de 2026.

> **Aviso:** o índice apresentado é um exercício exploratório, não uma probabilidade real de vitória. A amostra é pequena e não permite conclusões preditivas robustas.

## Pergunta de análise

O que os resultados das últimas três finais mostram sobre gols e decisões? E como os indicadores agregados das quartas de final e semifinais de 2026 comparam Palmeiras e Estudiantes?

## Ferramentas

- Python
- pandas para leitura e tratamento dos dados
- matplotlib para visualizações
- CSV como formato simples e rastreável de armazenamento

## Estrutura do projeto

```text
libertadores-2026-projeto/
├── data/
│   ├── finais_2023_2025.csv
│   └── campanha_2026.csv
├── outputs/
│   ├── gols_finais_2023_2025.png
│   ├── indice_projecao_2026.png
│   └── resumo_analise.txt
├── src/
│   └── analise.py
├── .gitignore
├── README.md
└── requirements.txt
```

## Como executar

Você precisa ter Python 3.10 ou superior instalado.

1. Baixe ou clone este repositório.
2. Abra um terminal na pasta do projeto.
3. (Recomendado) Crie e ative um ambiente virtual:

   **Windows (PowerShell)**
   ```powershell
   py -m venv .venv
   .venv\Scripts\Activate.ps1
   ```

   **macOS/Linux**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

4. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

5. Execute a análise:
   ```bash
   python src/analise.py
   ```

Os gráficos e o resumo serão gerados na pasta `outputs/`.

## Dados utilizados

### Finais de 2023 a 2025

| Ano | Campeão | Vice | Placar final |
|---:|---|---|---:|
| 2023 | Fluminense | Boca Juniors | 2–1 após prorrogação |
| 2024 | Botafogo | Atlético Mineiro | 3–1 |
| 2025 | Flamengo | Palmeiras | 1–0 |

A coluna de gols registra o placar final, incluindo a prorrogação quando houve. Os resultados foram organizados a partir das fontes listadas ao final deste documento.

### Campanha de 2026

A base registra os placares agregados das quartas de final e semifinais: Palmeiras teve agregado de 3–3 contra a LDU e 2–2 contra o Fluminense; Estudiantes venceu o Corinthians por 2–1 no agregado e empatou em 0–0 com o Flamengo. Ambos se classificaram nas semifinais nos pênaltis.

## Metodologia do índice exploratório

O script combina dois componentes com pesos iguais:

1. **Indicador ofensivo:** gols agregados marcados pela equipe divididos pela soma de gols marcados pelas duas equipes nesta base.
2. **Indicador defensivo:** transforma gols agregados sofridos em um valor de referência (`1 / (1 + gols sofridos)`) e normaliza esse valor entre as duas equipes.

A média desses componentes resulta em um índice relativo que soma 100% entre os dois clubes. **Esse percentual não é uma chance estatística de vitória.** É apenas uma forma transparente de comparar dois aspectos simples em uma amostra limitada.

O método não considera desempenho da temporada inteira, qualidade dos adversários, escalações, suspensões, lesões, mando de campo, pênaltis como habilidade separada, odds de mercado ou outras variáveis. Os resultados devem ser interpretados com cautela.

## Resultados e visualizações

### Gols nas finais anteriores

![Gols das finais de 2023 a 2025](outputs/gols_finais_2023_2025.png)

### Índice relativo para a final de 2026

![Índice relativo para 2026](outputs/indice_projecao_2026.png)

Consulte também [`outputs/resumo_analise.txt`](outputs/resumo_analise.txt), gerado pelo script.

## Possíveis melhorias

- Acrescentar estatísticas de toda a campanha de 2026 (gols por jogo, finalizações, xG, posse e desempenho como mandante/visitante).
- Incluir dados de mais temporadas e mais partidas, não somente finais.
- Comparar com odds históricas como uma referência externa, sem tratá-las como certeza.
- Separar treino e teste antes de experimentar um modelo de machine learning.
- Avaliar modelos com métricas apropriadas e evitar vazamento de dados.

## Fontes consultadas

- [Chaveamento da Libertadores 2026 — jogos eliminatórios e finalistas](https://libertadores.com.br/libertadores/chaveamento/) — consultado em 28/10/2026.
- [FIFA — Palmeiras e Estudiantes na final de 2026](https://www.fifa.com/pt/tournaments/mens/intercontinentalcup/2026/articles/estudiantes-palmeiras-copa-libertadores-resumo-semifinais) — consultado em 28/10/2026.
- [FBref — histórico de temporadas da Copa Libertadores](https://fbref.com/en/comps/14/history/Copa-Libertadores-Seasons) — consultado em 28/10/2026.
- [Transfermarkt — histórico de finais da Copa Libertadores](https://www.transfermarkt.com.br/copa-libertadores/alleEndspiele/pokalwettbewerb/CLI) — consultado em 28/10/2026.

Os dados foram transcritos e organizados para fins educacionais; consulte as fontes para contexto e verificação.

## Licença e uso

Material educacional para estudo e portfólio. Resultados esportivos não devem ser tratados como garantia de resultados futuros.
