# Lugar República

Site institucional one-page para o Lugar República — café, gastronomia e espaço cultural na República, São Paulo. Construído com **Vite + JavaScript puro (vanilla)**, sem frameworks de UI, usando [Lenis](https://lenis.darkroom.engineering/) como única dependência externa, para rolagem suave.

## Instalação

```bash
npm install
```

## Ambiente de desenvolvimento

```bash
npm run dev
```

Abre o site em `http://localhost:5173` com hot reload.

## Build de produção

```bash
npm run build
```

Gera os arquivos otimizados na pasta `dist/`. Para pré-visualizar o build localmente:

```bash
npm run preview
```

## Estrutura do projeto

```
lugar-republica/
├── index.html              # marcação semântica de todas as seções
├── public/                 # favicon e imagem Open Graph
└── src/
    ├── main.js              # ponto de entrada: inicializa Lenis, nav, scroll reveal e header
    ├── style.css            # agrega todos os arquivos de estilo
    ├── styles/               # CSS organizado por responsabilidade
    │   ├── variables.css     # paleta de cores, tipografia, espaçamentos
    │   ├── reset.css
    │   ├── base.css
    │   ├── components.css    # botões, cards, header, footer
    │   ├── sections.css      # hero, sobre, localização, contato
    │   └── responsive.css    # breakpoints mobile-first
    ├── scripts/
    │   ├── lenis.js          # inicialização do scroll suave
    │   ├── nav.js             # menu mobile + navegação por âncoras via Lenis
    │   ├── scrollReveal.js    # fade-in dos elementos ao entrar na viewport
    │   └── headerScroll.js    # header dinâmico ao rolar a página
    └── assets/
        ├── images/galeria/    # onde entram as fotos reais da galeria
        └── icons/
```

## Substituindo os placeholders por fotos reais

Nenhuma foto real foi fornecida no momento da criação do site. Todos os espaços de imagem (hero, seção Sobre, cardápio, galeria) usam `div`s com a classe `.placeholder-img`, identificando textualmente o que deve entrar em cada um (ex.: "Foto: fachada do Lugar República").

Para trocar por fotos reais:

1. Coloque os arquivos em `src/assets/images/` (ou `src/assets/images/galeria/` para a galeria).
2. No `index.html`, substitua o `div.placeholder-img` correspondente por uma tag `<img>` (ou `<img>` dentro do `<figure>`, no caso da galeria), apontando para o arquivo importado, mantendo a mesma classe do contêiner para preservar as proporções e o border-radius já definidos.
3. Adicione `loading="lazy"` em todas as imagens, exceto a do hero.

A imagem `public/og-image.svg` (usada nas meta tags Open Graph) também é um placeholder — troque por uma imagem real de 1200×630px (idealmente `.jpg`) antes de publicar, e atualize a tag `<meta property="og:image">` no `index.html` de acordo.

## Conteúdo e contato

O site não possui backend, CMS ou formulário de contato — todo contato acontece via Instagram [@lugar\_republica](https://instagram.com/lugar_republica). Cardápio completo e agenda de eventos atualizados são divulgados por lá.

**Endereço:** Rua Major Sertório, 318 — República, São Paulo – SP.
