# Blog da tese de doutorado

Site estático para o GitHub Pages, com três seções: **Reuniões**, **Revisão sistemática** e **Lacunas**. O conteúdo vem de quatro arquivos de texto (JSON), todos na mesma pasta do `index.html`, sem subpastas:

```
index.html      (o site)
site.json       (nomes, tema, resumo, próxima reunião)
reunioes.json   (reuniões de orientação)
rsl.json        (artigos da revisão sistemática)
lacunas.json    (lacunas de pesquisa)
```

Opcionais, também na raiz: `logo-ence.png` (logo no cabeçalho).

## Publicar

1. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`.
2. O site fica em `https://SEU-USUARIO.github.io/NOME-DO-REPO/`.

## Atualizar o conteúdo

Abra o arquivo no GitHub (ícone de lápis), edite e clique em **Commit changes**. O site atualiza em cerca de 1 minuto.

**Nova reunião** (`reunioes.json`): cole o modelo logo abaixo do `[` da primeira linha, com a vírgula no fim:

```json
  {
    "data": "AAAA-MM-DD",
    "titulo": "Reunião #",
    "anotacoes": [
      "Primeiro parágrafo.",
      "Segundo parágrafo. Links começando com https:// ficam clicáveis."
    ],
    "encaminhamentos": [
      { "texto": "Item concluído", "feito": true },
      { "texto": "Item pendente (aparece no quadro vermelho)", "feito": false }
    ],
    "tags": ["rsl"]
  },
```

**Artigo** (`rsl.json`, dentro de `estudos`): `titulo`, `autores`, `ano`, `leitura` (AAAA-MM-DD), `veiculo`, `doi`, `status` (`incluido`, `excluido` ou `analise`), `motivo`, `tags`.

**Lacuna** (`lacunas.json`): `data`, `titulo`, `descricao`, `evidencias` (lista), `proximo`, `tags`, `status` (`identificada`, `em exploração`, `virou questão de pesquisa` ou `descartada`).

**Próxima reunião** (`site.json`): `proximaReuniao` (AAAA-MM-DD) e `frequenciaDias` (14 = quinzenal). Opcionais: `horario`, `local` e `pularReunioes` (datas sem reunião, ex.: `["2026-12-25"]`). Depois da data, o site calcula as seguintes sozinho.

## Regras do JSON

- Cada item de uma lista (bloco ou linha) termina com vírgula, **menos o último**.
- O `[` abre a lista uma vez no início do arquivo e o `]` fecha uma vez no fim. Nunca coloque `]` entre reuniões.
- Use aspas retas (`"`), e datas como AAAA-MM-DD.
- Os nomes dos arquivos devem ser exatamente esses, sem espaços nem “(1)”.

## Se algo der errado

O próprio site avisa. Se um arquivo tiver erro de pontuação, a seção correspondente mostra uma caixa vermelha com o nome do arquivo e a linha do problema. As outras seções continuam funcionando. Confira também o texto em jsonlint.com.

Tudo no repositório é público.
