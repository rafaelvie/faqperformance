---
layout: default
title: Configuração do BackEnd Listener (Grafana)
parent: Grafana
nav_order: 1
has_toc: false
---

# Configuração do BackEnd Listener (Grafana)
{: .fs-9 }

---

**Observação:** Conforme reunião de equipe, para os campos _testName_ e _nodeName_, foram fixadas parametrizações de preenchimento, para sempre serem escritas em _MAIÚSCULA_ e, caso possuam espaços entre palavras, separar por "underline" e sem a presença de acentuações.

- **Exemplos:** SISTEMA, EXEMPLO_COM_SEPARACAO.

| Nome                       | Valor                                                                                                   |
|:---------------------------|:--------------------------------------------------------------------------------------------------------|
| testName                   | _Nome do sistema testado, que será exibido no campo_ **Sistema** _do Grafana._ **Ex.: SIACI, SIAPD, SIMTX, etc.**                                                                                                                          |
| nodeName                   | _Nome da comunidade a que pertence o sistema testado, que será exibido no campo_ **Comunidade** _do Grafana._ **Ex.: HABITACAO, MEIOS_DE_PAGAMENTO, etc.**                                                                                                                                 |
| runId                      | R001                                                                                                    |
| influxDBHttpScheme         | http                                                                                                    |
| influxDBHost               | 10.116.172.47                                                                                           |
| influxDBPort               | 8086                                                                                                    |
| influxDBToken              | _kmF8hG81kggJSTv309CC2aCROhAdtmtLpoNsMvfWEXW0VbJj2wAMApRZVhoef3RqYZkJYiHVudX5cT5mhuaXQ==                |
| influxDBOrganization       | 7d7a0a1bae8de667                                                                                        |
| influxDBBucket             | db_performance                                                                                          |
| influxDBFlushInterval      | 4000                                                                                                    |
| influxDBMaxBatchSize       | 2000                                                                                                    |
| samplersList               | .*                                                                                                      |
| useRegexForSamplerList     | true                                                                                                    |
| recordSubSamples           | true                                                                                                    |
| saveResponseBodyOfFailures | true                                                                                                    |
