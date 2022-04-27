---
layout: default
title: Trabalhando com “multipart/form-data” para POST de certificados no JMeter
parent: JMeter
nav_order: 2
has_toc: false
---

# Trabalhando com “multipart/form-data” para POST de certificados no JMeter 
{: .fs-9 }

Para casos em que é preciso trabalhar com envio de múltiplos arquivos em cada endpoint, como uma cadeia de certificados, por exemplo.
{: .fs-6 .fw-300 }

---

1) Na requisição HTTP criada, após configurar os parâmetros conforme documentação do sistema ou _collection_, marque a caixa de seleção **Usar multipart/form-data para HTTP Post**. Em seguida, adicionar todos os parâmetros conforme documentação da API testada. Para o **Content-Type**, deixar todos como **text/plain**.

![](https://github.com/rafaelvie/faqperformance/blob/main/img/multipart-1.png?raw=true)

2) Na aba **Files Upload**, primeiramente, clique no botão **Adicionar** para incluir uma linha. Em seguida, clique no botão **Procurar**. Localize o arquivo de certificado e clique no botão **Abrir**. Automaticamente, o JMeter exibirá o caminho completo da localização do arquivo recém-inserido. Para que a requisição funcione corretamente, insira em **Nome do Parâmetro** o parâmetro configurado na documentação ou na collection da API (para nosso exemplo, o parâmetro é _certificates[0][content])_. Em **MIME Type**, insira o tipo correto para o arquivo. No exemplo abaixo, como o arquivo de certificado .cer inserido foi criado como **BASE 64**, configuramos o MIME Type correspondente _(application/x-x509-ca-cert)_.

![](https://github.com/rafaelvie/faqperformance/blob/main/img/multipart-2.png?raw=true)

- _Para uma lista com todos os MIME types existentes, clique [aqui](https://www.hostmysite.com/support/dedicated/iis/mimetypes)_

3) Caso a requisição não funcione, mesmo com a inserção dos parâmetros de forma correta como exemplificado até aqui, clique na aba **Advanced** e no item **Implementação**, selecione **Java**. A resposta da requisição deverá funcionar corretamente.

![](https://github.com/rafaelvie/faqperformance/blob/main/img/multipart-3.pngraw=true)
