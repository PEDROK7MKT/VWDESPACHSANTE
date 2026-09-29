# VW Despachante — site institucional

Site estático (HTML + CSS + SVG, sem build) publicado na Vercel em
[vwdespachante.com.br](https://vwdespachante.com.br). Objetivo: SEO local, visibilidade em IAs (GEO)
e conversão para WhatsApp.

## Estrutura

```
index.html              página única (conteúdo + JSON-LD LocalBusiness/FAQPage)
assets/css/site.css     estilos: tokens de tema -> base -> layout -> componentes -> blocos
assets/img/             logos e ícones do site
assets/img/fotos/       fotos reais (atendimento, equipe, escritório, placas)
vercel.json             URLs limpas, redirect do alias .vercel.app para o www e cache dos assets
robots.txt, sitemap.xml rastreamento (Google, Bing e robôs de IA liberados)
llms.txt                resumo factual do negócio para assistentes de IA
404.html                página de erro com CTA
<chave>.txt             chave do IndexNow (Bing) — não apagar
```

Domínio canônico: **https://www.vwdespachante.com.br/** (o apex redireciona para o www na Vercel).
Todo canonical, og:url, JSON-LD e sitemap usam o www. Ao editar o conteúdo, atualize
`dateModified` no JSON-LD, `lastmod` no sitemap e a data "Atualizado em" do rodapé.

## Regras de conteúdo

- Nome, endereço, telefone, horário, serviços e cidades devem ser **idênticos** no HTML
  visível e no JSON-LD. O FAQ visível espelha o `FAQPage` do schema.
- Todos os CTAs usam `https://wa.me/5577991129068` ou `tel:+5577991129068`.
- Só fotos reais do negócio. Nada de banco de imagem.

## Componentes reaproveitáveis

| Classe | Uso |
| --- | --- |
| `.secao`, `.secao-intro` | seção padrão |
| `.linhas`, `.linhas-2` | lista em linhas com régua vermelha (serviços) |
| `.motivo` | bloco com régua vermelha à esquerda |
| `.foto` | foto com legenda (serviços realizados) |
| `.btn .btn-whats/-linha/-claro/-branco/-lg`, `.acoes` | botões (mín. 48px de toque) |
| `.chips` | lista de cidades/tags |
| `.placa` | placa Mercosul em CSS |
| `.faq` | perguntas com `<details>` |
| `.foto-pendente` | espaço reservado para foto (remover quando a foto entrar) |
| `<svg class="ic"><use href="#i-..."/></svg>` | ícones do sprite (só em botões/contato) |

Para outro despachante: troque os tokens em `:root` (bloco 1 do CSS), o logo em `assets/img/`
e os dados do negócio no HTML + JSON-LD.

## Próximos passos (terreno já preparado)

- Páginas por serviço/cidade: criar `transferencia-de-veiculo-barreiras.html` etc. na raiz.
  Com `cleanUrls` elas abrem em `/transferencia-de-veiculo-barreiras`. Usar os mesmos
  `site.css`, sprite de ícones, cabeçalho e rodapé, e referenciar a empresa no schema pelo
  `@id` `https://vwdespachante.com.br/#vw-despachante`.
- Blog: pasta `blog/` com o mesmo padrão.

## Fotos

Busque `SUBSTITUIR` no `index.html`: cada comentário traz o nome do arquivo, a proporção e o
`alt` já escrito. Formato: `.webp` (800 e 1200 px de largura) + `.jpg` de fallback, até ~200 KB
cada.

Placas e documentos de clientes devem ser desfocados antes de publicar (dados pessoais).
Remova metadados (EXIF/GPS) das fotos.
