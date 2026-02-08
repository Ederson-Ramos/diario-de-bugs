# Bug: Imagens não foram renderizadas na página html com Angular

**Data:** 08-02-2026  
**Projeto do Bug:** —  Portifólio pessoal  
**Tecnologias Envolvidas:** —  HTML, CSS, TypeScript, Angular  
**Status:** Resolvido

# Antes da Pesquisa:

## Descrição do problema

```txt

As imagens não estavam sendo renderizadas no HTML
mesmo o caminho estando certo. Não adiantava voltar a
pasta com "../".

```

## Mensagem de erro

```txt

Não tinha, pois estava direto no HTML,
apenas aparecia o ALT.

```

# Após Pesquisa:

## Causa do problema

```txt

A partir do Angular 17+, o CLI passou a configurar
o build usando a pasta "public" como assets padrão,
não incluindo automaticamente "src/assets".

```

## Solução

```txt

Tive que ir no arquivo angular.json, onde é feita a
configuração do projeto angular e colocar dentro da 
chave "assets" a string "src/assets" para reconhecer a pasta.

```

## ✅ **O que aprendi**

```txt

Aprendi que uma das primeiras coisas a se verificar em um projeto
angular é em qual maneira ele está usando suas imagens.

Em um projeto sozinho é possível definir isso logo de início.

```
