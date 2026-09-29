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
vercel.json             URLs limpas (/pagina.html -> /pagina) e cache dos assets
```

## Regras de conteúdo

- Nome, endereço, telefone, horário, serviços e cidades devem ser **idênticos** no HTML
  visível e no JSON-LD. O FAQ visível espelha o `FAQPage` do schema.
- Todos os CTAs usam `https://wa.me/5577991129068` ou `tel:+5577991129068`.
- Só fotos reais do negócio. Nada de banco de imagem.

## Componentes reaproveitáveis

| Classe | Uso |
| --- | --- |
| `.secao`, `.secao-alt`, `.secao-cabeca`, `.sobretitulo`, `.secao-intro` | seção padrão com cabeçalho |
| `.grade .grade-2/-3/-4` | grades responsivas de cartões |
| `.card`, `.card-hover`, `.pastilha` | cartão com ícone |
| `.btn .btn-whats/-linha/-claro/-branco/-lg`, `.acoes` | botões (mín. 48px de toque) |
| `.chips` | lista de cidades/tags |
| `.placa` | placa Mercosul em CSS |
| `.faq` | perguntas com `<details>` |
| `.foto-pendente` | espaço reservado para foto (remover quando a foto entrar) |
| `<svg class="ic"><use href="#i-..."/></svg>` | ícones do sprite no topo do `<body>` |

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
