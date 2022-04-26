---
layout: default
title: Erro de handshake em gravação e execução HTTPS no JMeter
parent: JMeter
nav_order: 1
has_toc: false
---

# Erro de handshake em gravação e execução HTTPS no JMeter 
{: .fs-9 }

Para casos específicos em que o sistema a ser gravado apresente erro de SSL ao se comunicar com o JMeter. Constatamos que a situação acontece também com a execução do teste.
{: .fs-6 .fw-300 }

---

- Acessar o arquivo system.properties, localizado na pasta bin do JMeter.

![](https://github.com/rafaelvie/faqperformance/blob/dc4c2c284705fccd4b921fc30e0af65c1c3b89f6/img/handshake.png)

- Incluir na última linha do arquivo a seguinte expressão:

```python
jsse.enableSNIExtension=false
```
