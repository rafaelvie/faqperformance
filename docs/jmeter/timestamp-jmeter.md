---
layout: default
title: Timestamp no JMeter
parent: JMeter
nav_order: 4
---

# Timestamp no JMeter
{: .no_toc }

## Índice
{: .no_toc .text-delta }

1. TOC
{:toc}

---

A geração do **timestamp atual** é um requisito comum em testes de desempenho. Ou você precisa passar o timestamp atual no formato de **época** ou no formato **ISO**. O **JMeter** possui algumas funções relacionadas ao tempo na biblioteca de funções que atendem ao requisito de gerar o timestamp atual, passado ou futuro usando deslocamentos.

## Função `<__time()>`

Esta função é usada para gerar o timestamp atual em diferentes formatos, possuindo dois argumentos, ou seja, formato de hora e nome da variável e ambos são opcionais. A função `<__time()>` sem nenhum argumento retorna a hora atual no formato de época.

| Função | Exemplo | Descrição |
|:-------|:--------|:----------|
| `${__time()}` | 1603188484750 | Hora atual no formato de época em milissegundos |
| `${__time(/1000)}` | 1603188484 | Hora atual no formato de época em segundos |
| `${__time(yyyy)}` | 2020 | Ano atual |
| `${__time(MM)}` | 10 | Mês atual em 2 dígitos |
| `${__time(MMM)}` | Out | Mês atual em 3 dígitos |
| `${__time(MMMM)}` | Outubro | Nome completo do mês atual |
| `${__time(d)} / ${__time(dd)}` | 1 / 01 **ou** 21 / 21 | Dia atual em um ou dois dígitos |
| `${__time(h)} / ${__time(hh)}` | 1 / 01 **ou** 11 / 23 | Hora atual em um ou dois dígitos no formato de 12 horas (1-12) |
| `${__time(H)} / ${__time(HH)}` | 1 / 01 **ou** 11 / 23 | Hora atual em um ou dois dígitos no formato de 24 horas (0-23) |
| `${__time(k)} / ${__time(kk)}` | 1 / 01 **ou** 11 / 23 | Hora atual em um ou dois dígitos no formato de 24 horas (1-24) |
| `${__time(K)} / ${__time(KK)}` | 1 / 01 **ou** 11 / 23 | Hora atual em um ou dois dígitos no formato de 12 horas (0-11) |
| `${__time(m)} / ${__time(mm)}` | 5/ 05 **ou** 15 / 15 | Minuto atual em um ou dois dígitos |
| `${__time(s)} / ${__time(ss)}` | 2/ 02 **ou** 19 / 19 | Segundo atual em um ou dois dígitos |
| `${__time(S)} / ${__time(SS)} / ${__time(SSS)}` | 3/ 03 / 003 **ou** 13 / 13 / 013 **ou** 310 / 310 / 310 | Milissegundo atual em um, dois ou três dígitos |	
| `${__time(a)}` | AM **ou** PM | Meridiano atual |
| `${__time(z)}` | IST | Fuso horário |
| `${__time(Z)}` | +0530 | Deslocamento de fuso horário em horas (padrão RFC) |
| `${__time(XXX)}` | +05:30 | Deslocamento de fuso horário no formato ISO |
| `${__time(u)}` | 3 | Número do dia atual (1 – segunda, 2 – terça, 3 – quarta, 4 – quinta, 5 – sexta, 6 – sábado, 7 – domingo) |
| `${__time(E)} / ${__time(EEEE)}` | Qua / Quarta-feira | Hora atual no formato de época em milissegundos |
| `${__time(D)}` | 295 | Contagem de dias atuais no ano |
| `${__time(W)}` | 4 | Semana em um mês (1 – Primeira semana, 2 – Segunda semana) |
| `${__time(w)}` | 43 | Semana em um ano |
| `${__time(G)}` | AD | Era atual |

Se você quiser inserir o timestamp atual (no formato de época) na solicitação, então você pode usar diretamente `<${__time()}>`, ou então você pode usar o argumento mencionado acima e gerar o valor no formato de hora desejado.

```js
Exemplo: ${__time(yyyy-MM-dd-HH:mm:ss:SSS a XXX)} gerará 2020-10-21-11:16:38:966 AM +05:30
```

Caso você queira salvar o valor em uma variável, adicione um nome de variável ao lado do formato separado por uma vírgula.

```js
{__time(yy-MM-dd-HH:mm:ss:SSS, cTime)}	
```

Use a variável `<${cTime}>` onde queira inserir o valor gerado.

## Função `<__timeShift()>`

A função `<__timeShift()>` é usada para gerar a data passada ou futura durante o teste de desempenho. Possui cinco argumentos de entrada, entre eles 2 são opcionais.

- **Time Format**: Consulte a tabela acima e use o argumento para criar a string de formato de hora. Por exemplo: `<aa-MM-dd>`;
- **Date to Shift**: Por padrão, usa o timestamp atual. Caso você queira mudar a data/hora de uma data/hora específica, especifique-a. Por exemplo: `<20-10-2020>`;
- **How much shift**: Especifique a quantidade de dia/hora para mudança:
   - **P** indica interpretação para uma data futura;
   - **-P** indica interpretação para uma data passada;
   - **PT** indica interpretação para um tempo futuro;
   - **-PT** indica interpretação para um tempo passado;
   - **D** indica Dia;
   - **H** indica hora;
   - **M** indica Minuto;
   - **S** indica o segundo.
- **String Format** (Opcional);
- **Name of variable** (Opcional).

![](https://github.com/rafaelvie/faqperformance/blob/main/img/timestamp.png?raw=true)

**Exemplos**:
   - `<${__timeShift(yyyy-MM-dd HH:mm:ss,,P2D,,)}>` gerará uma data futura adicionando 2 dias no dia atual;
   - `<${__timeShift(yyyy-MM-dd HH:mm:ss,,PT2H,,)}>` gerará um horário futuro adicionando 2 horas no horário atual;
   - `<${__timeShift(yyyy-MM-dd HH:mm:ss,,PT2M,,)}>` gerará um horário futuro adicionando 2 minutos no horário atual;
   - `<${__timeShift(yyyy-MM-dd HH:mm:ss,,P2DT2H,,)}>` gerará uma data e hora futuras adicionando 2 dias e 2 horas na data/hora atual;
   - `<${__timeShift(yyyy-MM-dd HH:mm:ss,,-PT2M,,)}>` gerará um tempo passado reduzindo 2 minutos no tempo atual;
   - `<${__timeShift(yyyy-MM-dd HH:mm:ss,,-P2DT2H,,)}>` gerará uma data e hora anteriores reduzindo 2 dias e 2 horas na data/hora atual;
   - `<${__timeShift(yyyy-MM-dd HH:mm:ss,2020-10-20,P2D,,)}>` gerará `<2020-10-22>`, que é o próximo segundo dia a partir da data especificada.
