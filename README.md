# Teste Carrinho

Este projeto implementa a lógica de cálculo do total de um carrinho de compras em JavaScript. A função principal valida itens, aplica descontos e calcula frete conforme regras de negócio.

## Objetivo

O sistema deve:

- calcular o subtotal dos itens do carrinho;
- rejeitar carrinhos inválidos;
- aplicar desconto com cupom `PROMO10`;
- conceder frete grátis para compras iguais ou acima de R$ 100;
- cobrar frete de R$ 15 quando o subtotal for menor que R$ 100;
- arredondar o valor final para duas casas decimais.

## Estrutura da pasta

- `carrinho.js` — lógica principal do cálculo do total;
- `carrinh.test.js` — testes automatizados do comportamento esperado;
- `index.js` — execução manual de testes de caixa-preta;
- `package.json` — configuração do projeto e dependências.

## Regras de negócio

1. Carrinho vazio é inválido.
2. Qualquer item com quantidade menor ou igual a zero é inválido.
3. Preço negativo também torna o carrinho inválido.
4. O cupom `PROMO10` aplica 10% de desconto sobre o subtotal.
5. Frete grátis para subtotal igual ou acima de R$ 100.
6. Caso o subtotal seja menor que R$ 100, o frete é R$ 15.
7. O total final deve ser arredondado para 2 casas decimais.

## Como executar

### 1. Instalar dependências

```bash
npm install
```

### 2. Rodar os testes

Este projeto usa Jest para validação dos cenários.

```bash
npx jest
```

### 3. Executar a verificação manual

```bash
node index.js
```

## Exemplo de uso

```javascript
const { calcularTotal } = require('./carrinho');

const itens = [
  { preco: 50, quantidade: 1 },
  { preco: 30, quantidade: 2 }
];

const total = calcularTotal(itens, 'PROMO10');
console.log(total);
```

## Observação

A função `calcularTotal` lança erro com a mensagem `Carrinho inválido` quando a entrada não atende às regras do negócio.
