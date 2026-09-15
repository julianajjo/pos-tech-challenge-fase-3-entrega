# Tech Challenge Fase 3 — Assistente Médico com PubMedQA

Este projeto foi desenvolvido como parte do **Tech Challenge da Fase 3** e tem como objetivo aplicar conceitos estudados como **fine-tuning de LLMs, LangChain, LangGraph, segurança e rastreabilidade**.

A proposta foi criar um protótipo de assistente para o contexto biomédico utilizando o **PubMedQA**, um dataset público de perguntas e respostas baseadas em artigos científicos da área da saúde.

> **Importante:** este é um projeto exclusivamente acadêmico e não deve ser utilizado para diagnóstico, prescrição ou qualquer tipo de decisão clínica.

## Sobre os dados

Para o desenvolvimento foi utilizado o **PubMedQA PQA-L**, que possui 1.000 exemplos anotados com as classes `yes`, `no` e `maybe`.

O dataset é baixado diretamente do Hugging Face durante a execução do notebook:

```python
load_dataset(
    "qiaojin/PubMedQA",
    "pqa_labeled",
    split="train"
)
```

O PubMedQA contém informações provenientes de literatura biomédica. Portanto, ele **não representa prontuários eletrônicos, dados reais de pacientes ou protocolos internos de hospitais**.

Neste projeto, ele foi utilizado como uma base pública para simular e demonstrar a arquitetura proposta no desafio.

## Estrutura do projeto

O projeto contém os seguintes arquivos:

- `tech_challenge_fase3_pubmedqa.ipynb` — notebook principal com todo o desenvolvimento do projeto;
- `requirements.txt` — dependências utilizadas;
- `.gitignore` — configuração dos arquivos que não devem ser enviados para o Git.

Os artefatos gerados durante o treinamento, como o adapter LoRA e os logs de auditoria, são armazenados na pasta `artifacts`.

## Como executar

A execução foi realizada utilizando o **Google Colab com GPU**.

Para reproduzir o projeto:

1. Abra o notebook no Google Colab.
2. Ative a GPU no ambiente de execução.
3. Execute a instalação das dependências.
4. Utilize `SMOKE_MODE=True` caso queira fazer primeiro uma execução reduzida para validar o pipeline.
5. Utilize `RUN_FINE_TUNING=True` para executar o treinamento.
6. Para reproduzir o experimento final, utilize `SMOKE_MODE=False`.

O treinamento final deste projeto foi executado utilizando uma GPU **Tesla T4**.

## Desenvolvimento

O projeto foi dividido nas seguintes etapas:

1. Carregamento do PubMedQA PQA-L;
2. Limpeza e preparação dos dados;
3. Separação dos conjuntos de treino, validação e teste;
4. Preparação dos exemplos para instruction tuning;