---
layout: default
title: Gerar Token Global
parent: JMeter
nav_order: 3
has_toc: false
---

# Gerar Token Global
{: .fs-9 }

Utilizado para trabalhar com token do SSO (SISET) com mais de um Thread Group.
{: .fs-6 .fw-300 }

---

1) Criar na requisição do Token do primeiro Thread Group:

- Criar um extrator de JSON;

```js
Valor da expressão: $.access_token
```

- Criar um BeanShell PostProcessor com o código abaixo:

```js
String token = bsh.args[0];

${__setProperty(globaltoken,${token})}
```

_Obs.: Este código está definindo a variável token como global através de propriedade do JMeter._
{: .fs-4 }

2) Adicionar no "HTTP Header Manager" a variável como "global":

| Nome             | Valor                        |
|:-----------------|:-----------------------------|
| _Authorization_  | _Bearer ${__P(globaltoken)}_ |
