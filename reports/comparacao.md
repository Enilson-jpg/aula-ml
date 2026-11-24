# Comparação entre os modelos r1 e r2

## Alteração feita

O rótulo do chamado `006` ("bloqueio de acesso") foi corrigido de `comum` para
`urgente` (dataset `chamados-v1` para `chamados-v2`). A partição `split.csv`
não mudou.

## Versões comparadas

| | r1 | r2 |
|---|---|---|
| Tag do modelo | `modelo-r1` | `modelo-r2` |
| Tag dos dados | `dados-v1` | `dados-v2` |
| Dataset | chamados-v1 | chamados-v2 |

## Métricas (mesma partição de teste, 4 exemplos)

| Métrica | r1 | r2 |
|---|---|---|
| Acurácia | 0.75 | 1.0 |
| Recall de urgentes | 0.5 | 1.0 |
| Recall de comuns | 1.0 | 1.0 |

O hash da partição é o mesmo nas duas rodadas:
`2ef820171c1a4625fe216e6da67c7c8dcf9d97a08288c0239cd23f1a6961d981`.

## Hashes verificados no clone limpo (r1)

Restauração em `aula-ml-restauracao` com `git switch --detach modelo-r1` e
`dvc pull`. Commit: `b003fbdf342d9f3c56c76b2e25d0708b7208bd32`.

- `data/chamados.csv`: `bc3fd86a3a5f598841a58839a9726d901fa7e8361ffe79c5b43873ad8a1328ac`
- `data/split.csv`: `2ef820171c1a4625fe216e6da67c7c8dcf9d97a08288c0239cd23f1a6961d981`
- `models/model.json`: `09d965544c9298c5586af0a1becbf07fb3f3c7b7c228a803ab91179f8b458a09`

Os três coincidem com os valores registrados em `reports/modelo.json` do r1.

## Hashes do r2

- `data/chamados.csv`: `4ca2e29cb930a9161c2a851b3c71f5529dbb812db607ee4a5ea95d2223baa14d`
- `models/model.json`: `3bcddff15fe272fe16e092dfb76dab30fa3786cd8c2ce4849ccf5ace002c6ee6`

## Decisão

**Aceitar r2.** O critério era melhorar o recall de urgentes sem reduzir o
recall de comuns, com a mesma partição de teste. O recall de urgentes passou de
0.5 para 1.0 e o de comuns permaneceu em 1.0. Ressalva: o teste tem apenas
quatro exemplos, então a comparação demonstra o efeito da correção neste
exercício e não é uma estimativa estatística de desempenho.
