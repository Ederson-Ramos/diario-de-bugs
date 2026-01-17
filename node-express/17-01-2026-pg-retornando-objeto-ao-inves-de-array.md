# Bug: pg retornando objeto ao invés do array de rows

**Data:** 17-01-2026  
**Projeto do Bug:** Calculadora Carbono (Atividade Extensionista Faculdade)   
**Tecnologias Envolvidas:** Node.js, Express, PostgreSQL, Módulo pg  
**Status:** Resolvido  

# Antes da Pesquisa:

## Descrição do problema

```txt

Ao fazer uma query SELECT usando o módulo pg, eu esperava receber diretamente um array com os dados do banco, pois tinha colocado o retorno em uma variável fazendo destructuring.

Porém, ao acessar o retorno da variável, o resultado vinha como um objeto, e não como um array, o que quebrou a lógica da aplicação.

```

## Mensagem de erro

```txt

TypeError: rows.map is not a function

```

# Após Pesquisa:

## Causa do problema

```txt

O método client.query() do pg sempre retorna um objeto.

Esse objeto contém várias propriedades, como:
- rows
- rowCount
- fields

Mesmo tendo feito destructuring em { rows }, no return eu acabei retornando { rows } também, o que criou um novo objeto contendo a propriedade rows, ao invés de retornar o array diretamente.

```

## Solução

```txt

Troquei o que antes estava:
return { rows }

Para:
return rows

Como o destructuring já havia sido feito, bastava retornar a variável rows, que já era o array esperado.

```

## ✅ O que aprendi

```txt

Quando se faz destructuring de um objeto, é importante prestar atenção no que está sendo retornado.

Retornar { rows } cria um novo objeto. Retornar rows retorna diretamente o valor esperado.

```
