---
layout: default
title: Tratamento de arquivo CSV contendo vários dados em uma única linha
parent: Diversos
nav_order: 1
has_toc: false
---

# Tratamento de arquivo CSV contendo vários dados em uma única linha 
{: .fs-9 }

Para casos em que seja necessário tratar arquivos CSV contendo vários dados (como matrículas de funcionários), porém todos estão inseridos em uma única linha. Exemplificaremos como tratar estes arquivos, separando facilmente cada dado em sua respectiva linha.
{: .fs-6 .fw-300 }

---

1) Em uma injetora e com o arquivo a ser tratado selecionado, execute o comando:

```bash
tr ',' '\n' < empregados_caixa.csv >> novoArquivo.txt

Onde:

tr = comando principal
',' '\n' = substituir de -> para 

Exemplo: ',' para '\n' (quebra de linha) ou poderia ser ',' para '#'

< empregados_caixa.csv = arquivo a ser alterado
>> novoArquivo.txt = arquivo que deve ser gerado após o tratamento
```

2) Caso deseje visualizar quantas linhas possui o arquivo tratado ou quaisquer outros, basta executar o comando:

```bash
cat novoArquivo.txt | wc -l
```
