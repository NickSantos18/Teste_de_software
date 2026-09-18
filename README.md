# Teste Carrinho

Projeto JavaScript para validar a lógica de cálculo de um carrinho de compras, incluindo subtotal, desconto, frete e tratamento de entradas inválidas.

## Visão geral

Este projeto simulou um cenário de regras de negócio para um carrinho de compras, com foco em:

- validação do carrinho;
- cálculo do subtotal dos itens;
- aplicação de cupom de desconto;
- cálculo do valor do frete;
- arredondamento do valor final;
- testes de comportamento esperados em cenários específicos.

A lógica principal está na função `calcularTotal`, localizada em [carrinho.js](carrinho.js), e a validação dos requisitos está em [carrinh.test.js](carrinh.test.js).

## Objetivo do projeto

O objetivo é garantir que a função de cálculo do carrinho respeite as regras de negócio e que o comportamento esperado seja validado por testes automatizados.

## Regras de negócio

A lógica do carrinho deve seguir estas regras:

1. Carrinho vazio é inválido.
2. Itens com quantidade menor ou igual a zero são inválidos.
3. Preços negativos também tornam o carrinho inválido.
4. O cupom `PROMO10` aplica desconto de 10% sobre o subtotal.
5. Frete grátis para compras com subtotal igual ou superior a R$ 100,00.
6. Compras com subtotal abaixo de R$ 100,00 pagam frete de R$ 15,00.
7. O valor final deve ser arredondado para duas casas decimais.
8. Quando a entrada for inválida, a função deve lançar erro com a mensagem `Carrinho inválido`.

## Estrutura do projeto

- [carrinho.js](carrinho.js): contém a lógica principal do cálculo do total;
- [carrinh.test.js](carrinh.test.js): testes automatizados com cenários esperados;
- [index.js](index.js): execução manual dos testes de caixa-preta;
- [package.json](package.json): configuração do projeto e dependências;
- [README.md](README.md): documentação do projeto.

## Pré-requisitos

Antes de executar o projeto, certifique-se de ter instalado:

- Node.js
- npm

## Como executar

### 1. Instalar dependências

```bash
npm install
```

### 2. Executar os testes automatizados

O projeto utiliza Jest para validar os requisitos.

```bash
npx jest
```

### 3. Executar a verificação manual

```bash
node index.js
```

Esse arquivo executa uma bateria de testes manuais, mostrando se cada cenário passou ou falhou.

## Exemplos de uso

```javascript
const { calcularTotal } = require('./carrinho');

const itens = [
  { preco: 50, quantidade: 1 },
  { preco: 30, quantidade: 2 }
];

const total = calcularTotal(itens, 'PROMO10');
console.log(total);
```

### Cenário com frete grátis

```javascript
const itens = [{ preco: 100, quantidade: 1 }];
console.log(calcularTotal(itens, null));
// Resultado esperado: 100
```

### Cenário com cupom de desconto

```javascript
const itens = [{ preco: 50, quantidade: 1 }];
console.log(calcularTotal(itens, 'PROMO10'));
// Resultado esperado: 60
```

## Casos de teste cobertos

Os testes do arquivo [carrinh.test.js](carrinh.test.js) validam:

- CT-01: frete grátis em compras de exatamente R$ 100,00;
- CT-02: desconto de 10% com cupom `PROMO10`;
- CT-03: rejeição de quantidade negativa ou zero;
- CT-04: arredondamento para duas casas decimais;
- CT-05: rejeição de carrinho vazio;
- CT-06: cobrança de frete de R$ 15,00 para subtotal abaixo de R$ 100,00.

## Observações importantes

- A função `calcularTotal` deve sempre validar a entrada antes do cálculo.
- Valores monetários devem ser tratados com cuidado para evitar problemas de precisão.
- O uso de arredondamento em centavos é essencial para manter o resultado consistente.

## Status do projeto

Este projeto está estruturado como um exercício de lógica e testes de regras de negócio em JavaScript, com foco em validação de comportamento e garantia de qualidade.

