# Painel de Contratacoes DECOF

Painel publico de consulta do cronograma de contratacoes da DECOF/LIC. Esta versao foi preparada para GitHub Pages e usa o Google Apps Script apenas como backend de leitura da planilha.

## Arquitetura

```text
Google Sheets (banco de dados)
         |
         | leitura
         v
Apps Script da DECOF (backend somente leitura)
         |
         | JSONP publico
         v
Painel de Contratacoes (GitHub Pages)
```

## Arquivos

```text
.
|-- index.html
|-- config.js
|-- .gitignore
|-- README.md
`-- apps-script/
    `-- Code.gs
```

## Como Publicar no GitHub Pages

1. Crie um repositorio separado para o painel.
2. Copie estes arquivos para o repositorio.
3. No Apps Script da conta DECOF, cole o conteudo de `apps-script/Code.gs`.
4. Implante o Apps Script como Web App.
5. Copie a URL `/exec` da implantacao.
6. Cole essa URL em `config.js`, no campo `apiUrl`.
7. Ative o GitHub Pages no repositorio do painel.

## Rotas do Backend

O painel usa apenas rotas publicas de leitura:

- `?route=painel.dados`
- `?route=painel.capacidade`

Para funcionar em GitHub Pages, o painel usa JSONP:

```text
?route=painel.dados&callback=nomeDaFuncao
```

## Cuidados Antes de Publicar

- Nao inclua planilha real, PDF assinado, dados pessoais, e-mails pessoais ou links internos sensiveis.
- Use a conta da DECOF como dona/implantadora do Apps Script.
- Mantenha o AppSEL em projeto separado; ele exige login e sera migrado depois, com outra estrategia.
