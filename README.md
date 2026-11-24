# aula-ml

Atividade Prática 07 (CK0444, UFC): versionamento de dados e modelos com Git e DVC.

## Pré-requisitos

- Git
- Python 3.10 ou superior
- DVC 3 (`pipx install 'dvc>=3,<4'`)
- No Windows, usar o WSL

## Armazenamento DVC

Os CSVs e o modelo ficam em um remote local, a pasta irmã `dvc-storage`.
O Git guarda apenas os descritores `.dvc`. O remote está configurado em
`.dvc/config` com o caminho `../dvc-storage`, então a restauração funciona
no mesmo computador, com `dvc-storage` ao lado do repositório.

## Restaurando uma versão

Tags: `dados-v1`, `modelo-r1`, `dados-v2`, `modelo-r2`.

    git clone https://github.com/Enilson-jpg/aula-ml.git aula-ml-restauracao
    cd aula-ml-restauracao
    git switch --detach modelo-r1
    dvc pull

Depois do `dvc pull`, os hashes de `data/chamados.csv`, `data/split.csv` e
`models/model.json` devem coincidir com os campos de `reports/modelo.json`.

## Treinamento

    python3 src/train.py chamados-r1

O comando gera `models/model.json`, `reports/metrics.json` e `reports/modelo.json`.

## Relatório

A comparação entre r1 e r2 está em `reports/comparacao.md`.
