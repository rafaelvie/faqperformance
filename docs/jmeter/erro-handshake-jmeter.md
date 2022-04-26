---
layout: default
title: Erro de handshake durante gravação e execução de cenário HTTP(S) no JMeter
parent: JMeter
nav_order: 1
has_toc: false
---

# Erro de handshake durante gravação e execução de cenário HTTP(S) no JMeter
{: .fs-9 }

Para casos específicos em que o sistema a ser gravado apresente erro de SSL ao se comunicar com o JMeter. Constatamos que a situação acontece também com a execução do teste.
{: .fs-6 .fw-300 }

---

- Acessar o arquivo system.properties, localizado na pasta bin do JMeter.

![](img/handshake.png)

- Incluir na última linha do arquivo a seguinte expressão:

```
jsse.enableSNIExtension=false
```
