# Blog da tese de doutorado

Site estático para o GitHub Pages. Todos os arquivos ficam juntos na raiz do repositório, sem pastas:

```
index.html      (o site)
site.json       (nomes, tema, resumo)
reunioes.json   (reuniões de orientação)
rsl.json        (artigos da revisão sistemática)
lacunas.json    (lacunas de pesquisa)
prazos.json     (calendário: prazos e marcos)
```

Opcionais: `logo-ence.png` (logo da ENCE) e `banner.png` (banner da página inicial), também na raiz.

## Publicar pela primeira vez

1. Crie uma conta em github.com e clique em **+ > New repository**.
2. Nome: `tese-blog`. Marque **Public**. Clique em **Create repository**.
3. Clique em **uploading an existing file**, arraste os 5 arquivos acima de uma vez e clique em **Commit changes**.
4. Vá em **Settings > Pages**. Em *Branch*, escolha `main` e `/ (root)`, e clique em **Save**.
5. Espere cerca de 1 minuto. O endereço aparece no topo da página de Pages: `https://SEU-USUARIO.github.io/tese-blog/`.

## Adicionar um novo registro

1. No repositório, clique no arquivo (por exemplo, `reunioes.json`) e no ícone de lápis.
2. Copie um bloco existente, cole logo abaixo, coloque vírgula entre os blocos e troque os textos.
3. Clique em **Commit changes**. O site atualiza em cerca de 1 minuto (recarregue com Ctrl+F5).

Modelo de reunião:

```json
{
  "data": "2026-11-20",
  "titulo": "",
  "anotacoes": ["Primeiro parágrafo (vira o destaque).", "Segundo parágrafo."],
  "encaminhamentos": [
    { "texto": "Item concluído", "feito": true },
    { "texto": "Item pendente (aparece no quadro vermelho)", "feito": false }
  ],
  "tags": ["rsl"]
}
```

Artigo (dentro de `estudos` em `rsl.json`): `titulo`, `autores`, `ano`, `leitura` (AAAA-MM-DD), `veiculo`, `doi`, `status` (`incluido`, `excluido` ou `analise`), `motivo`, `tags`.

Lacuna (`lacunas.json`): `data`, `titulo`, `descricao`, `evidencias` (lista), `proximo`, `tags`, `status` (`identificada`, `em exploração`, `virou questão de pesquisa` ou `descartada`).

Se o site não mostrar o conteúdo depois de salvar, cole o arquivo em jsonlint.com para achar vírgula ou aspa fora do lugar. Tudo que está no repositório é público.

## Calendário e próxima reunião

- **Próxima reunião:** em `site.json`, `proximaReuniao` (AAAA-MM-DD) e `frequenciaDias` (14 = quinzenal) alimentam o card de alerta da página inicial e as reuniões do calendário. Depois da data, o site calcula as seguintes sozinho. Opcionais: `horario`, `local` e `pularReunioes` (lista de datas sem reunião, ex.: `["2026-12-25"]`).
- **Prazos e marcos:** `prazos.json`, uma lista de blocos com `data`, `titulo`, `tipo` (`prazo`, `marco` ou `evento`), `descricao` (opcional) e `concluido` (`true` para dar baixa).

No calendário, as atividades com prazo aparecem em lista, da mais urgente para a menos urgente, com a contagem de dias. As atrasadas (data anterior a hoje e sem `"concluido": true`) ficam em vermelho e negrito, em fonte maior. Eventos (`tipo: evento`) não são marcados como atrasados.

## Modo editor (cadastrar e editar direto no site)

Os botões de cadastro, edição e exclusão ficam ocultos para os visitantes. Para ativá-los:

1. No GitHub: foto de perfil > **Settings > Developer settings > Personal access tokens > Fine-grained tokens > Generate new token**.
2. Dê um nome, defina a validade, em **Repository access** escolha **Only select repositories** e marque o repositório do blog.
3. Em **Permissions > Repository permissions**, ajuste **Contents** para **Read and write**. Gere o token e copie-o (ele só aparece uma vez).
4. No site, clique em **Modo editor** e cole o token. O site confere se ele tem permissão de escrita neste repositório.

Ao salvar, o site grava o arquivo inteiro no GitHub (`reunioes.json`, `rsl.json`, `lacunas.json`, `prazos.json` ou `site.json`), e o blog publicado atualiza em cerca de 1 minuto. O token fica só no seu navegador. **Sair** no cabeçalho o apaga dele.

Cuidados: o token vale como senha, então não o compartilhe nem o coloque em arquivos do repositório. Evite editar o mesmo arquivo pelo GitHub e pelo site ao mesmo tempo, porque o site regrava o arquivo com o que está na tela. Se o GitHub recusar, o aviso oferece o botão **Baixar arquivo** para você não perder o que digitou.

Isso protege a escrita, não a leitura: o site continua público para quem tem o endereço.
