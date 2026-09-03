# Prompt para Claude Code — Site Lugar República

Especificação técnica e de conteúdo para geração de um site institucional em Vite \+ JavaScript puro

## Como usar este documento

O texto abaixo foi escrito para ser copiado e colado diretamente como prompt em uma sessão do Claude Code. Ele está redigido na segunda pessoa, como uma instrução direta ao agente. Revise os dados de negócio na seção 1 antes de enviar, e ajuste qualquer detalhe de estilo que não corresponda ao que você imagina para o espaço.

## 1\. Contexto e papel

Você é um(a) engenheiro(a) front\-end responsável por criar, do zero, um site institucional completo, funcional e visualmente refinado para um café com espaço cultural. O site deve ser construído com **Vite \+ JavaScript puro (vanilla)**, sem frameworks como React, Vue ou Svelte. Entregue um projeto pronto para rodar localmente com `npm install` e `npm run dev`, e pronto para build de produção com `npm run build`.

### Dados do negócio

| Campo | Informação |
| --- | --- |
| Nome / Perfil | Lugar República |
| Instagram | @lugar\_republica |
| Segmento | Café, Gastronomia e Espaço Cultural / Eventos |
| Endereço | Rua Major Sertório, 318 — República, São Paulo – SP |
| Contato | Via DM no Instagram (@lugar\_republica) ou link oficial disponível na bio |

Não existe backend, CMS ou formulário de contato: todo contato acontece fora do site, via Instagram. O site é 100% estático.

## 2\. Stack técnica

- **Build tool:** Vite (última versão estável).
- **Linguagem:** JavaScript ES6\+ puro — sem TypeScript, sem frameworks de UI.
- **Marcação:** HTML5 semântico (`header`, `nav`, `main`, `section`, `footer`, `figure`, etc.).
- **Estilo:** CSS3 puro, organizado em múltiplos arquivos importados via `main.js` ou `style.css` (sem Sass/Less, sem Tailwind).
- **Scroll:** [Lenis](https://lenis.darkroom.engineering/) (`npm install lenis`) para rolagem suave e inercial em toda a página — única dependência externa de JavaScript do projeto.
- **Fontes:** Google Fonts, carregadas via `<link>` no `index.html` com `preconnect`.
- **Ícones:** SVGs inline ou uma biblioteca leve de ícones em linha (ex.: Lucide/Feather), sem dependência de fonte de ícones pesada.
- **Mapa:** iframe do Google Maps incorporado (sem chave de API paga).
- **Sem backend, sem CMS, sem formulário de envio de e\-mail.**

## 3\. Estrutura de pastas

Crie exatamente esta estrutura de projeto:

```
lugar-republica/
├── index.html
├── package.json
├── vite.config.js
├── .gitignore
├── README.md
├── public/
│   ├── favicon.svg
│   └── og-image.jpg
└── src/
    ├── main.js
    ├── style.css
    ├── styles/
    │   ├── variables.css
    │   ├── reset.css
    │   ├── base.css
    │   ├── components.css
    │   ├── sections.css
    │   └── responsive.css
    ├── scripts/
    │   ├── nav.js
    │   ├── lenis.js
    │   ├── scrollReveal.js
    │   └── headerScroll.js
    └── assets/
        ├── images/
        │   └── galeria/
        └── icons/
```

## 4\. Identidade visual

Estilo geral: **rústico\-aconchegante**, remetendo a um café de bairro com alma cultural — madeira, papel kraft, tons quentes, tipografia editorial. Evite qualquer aparência de site corporativo ou genérico.

### Paleta de cores

| Uso | Descrição | Hex |
| --- | --- | --- |
| Fundo principal | Creme quente | `#F5EDE1` |
| Fundo secundário | Bege café\-com\-leite | `#E8DCC8` |
| Texto principal | Marrom café escuro | `#3A2A20` |
| Texto secundário | Marrom médio | `#6B5644` |
| Destaque / CTA | Terracota | `#C1653C` |
| Acento cultural | Verde oliva escuro | `#4A5B3A` |
| Linhas / detalhes | Dourado envelhecido | `#A88B5A` |

Defina todas essas cores como variáveis CSS (`:root`) em `styles/variables.css`, junto com espaçamentos, raios de borda e sombras padronizadas, para reuso consistente em todo o site.

### Tipografia

| Uso | Fonte (Google Fonts) | Peso |
| --- | --- | --- |
| Títulos (`h1`–`h3`) | Fraunces | 600–700, com uso pontual em itálico para destaques |
| Corpo de texto | Nunito Sans | 400 (texto) / 600 (ênfases) |
| Labels / categorias | Nunito Sans | 600, caixa alta, letter\-spacing ampliado |

### Texturas e detalhes

- Fundo com leve textura de papel/grão (pode ser um SVG de ruído sutil ou gradiente suave — nada pesado).
- Linhas divisórias finas em tom dourado envelhecido entre seções.
- Cantos levemente arredondados em cards e botões (não totalmente retos, mas também não excessivamente arredondados).
- Um único elemento de destaque visual forte por seção (nunca mais de um "highlight" competindo por atenção na mesma tela).

## 5\. Estrutura da página

Site **one\-page** (página única), com um menu fixo de navegação por âncoras. Ao clicar em um item do menu, a página deve rolar suavemente (smooth scroll) até a seção correspondente.

### Header / Navegação

- Fixo no topo (`position: fixed` ou `sticky`), com fundo transparente sobre o hero e fundo sólido ao rolar a página (efeito de "encolher" e ganhar sombra sutil no scroll — implementar em `scripts/headerScroll.js`).
- Logotipo em texto (wordmark "Lugar República" em Fraunces), já que não há um arquivo de logo fornecido.
- Menu com âncoras: Início, Sobre, Café, Eventos, Galeria, Localização, Contato.
- Menu hamburguer no mobile, abrindo um painel/overlay de navegação em tela cheia.

### Hero (Início)

- Imagem de fundo em destaque (placeholder — ver seção 7) com overlay escuro semitransparente para legibilidade do texto.
- Título principal: "Lugar República".
- Subtítulo curto reforçando o conceito: café, gastronomia e cultura em um só espaço na República, São Paulo.
- Botão de destaque (CTA) levando à seção de Eventos ou diretamente ao Instagram.

### Sobre

- Texto institucional contando a proposta do espaço: um lugar que une café de qualidade, gastronomia e programação cultural (exposições, música ao vivo, saraus, oficinas) no bairro República.
- Layout em duas colunas no desktop (texto \+ imagem), empilhado no mobile.

### Café & Cardápio

- Seção apresentando o conceito gastronômico (cafés especiais, brunch, petiscos, drinks).
- Grade de cards com categorias ilustrativas (ex.: Cafés especiais, Brunch, Petiscos & Compartilhar, Drinks autorais) — sem preços fixos, apenas categorias e descrições curtas, já que o cardápio completo fica no Instagram/local.
- Texto reforçando que o cardápio completo e atualizado está disponível no local ou por mensagem no Instagram.

### Espaço Cultural & Eventos

- Seção descrevendo a vocação cultural do espaço: shows, exposições, saraus, oficinas, encontros.
- Grade/carrossel de cards de "próximos eventos" com placeholders (título do evento, data, breve descrição) e uma nota explicando que a agenda atualizada é divulgada no Instagram.
- CTA reforçando: "Acompanhe nossa agenda completa no Instagram".

### Galeria

- Grade de imagens (grid responsivo) mostrando o ambiente, pratos e eventos, com efeito hover sutil (zoom leve ou overlay).
- Usar `figure`/`figcaption` para acessibilidade.

### Localização

- Endereço em destaque: Rua Major Sertório, 318 — República, São Paulo – SP.
- Mapa incorporado via iframe do Google Maps, centrado nesse endereço (URL de embed sem necessidade de chave de API: `https://www.google.com/maps?q=Rua+Major+Sert%C3%B3rio,+318+-+Rep%C3%BAblica,+S%C3%A3o+Paulo+-+SP&output=embed`).
- Link "Como chegar" abrindo o Google Maps em nova aba.

### Contato

- Seção final antes do footer, com uma chamada direta: contato apenas via Instagram.
- Botão grande em destaque: "Fale conosco no Instagram" → `https://instagram.com/lugar_republica`.
- Texto curto explicando que reservas, dúvidas e informações sobre eventos são tratadas por DM ou pelo link oficial na bio.

### Footer

- Wordmark repetido, endereço, ícone/link do Instagram, e um link para o topo da página.
- Créditos discretos de ano (`© 2026 Lugar República`).

## 6\. Interações e microanimações

- **Scroll suave (Lenis):** instale a biblioteca [Lenis](https://lenis.darkroom.engineering/) (`npm install lenis`) para controlar a rolagem da página com inércia e suavidade. Inicialize\-a em `scripts/lenis.js`, importado em `main.js`, com uma configuração leve (ex.: `duration` entre 1 e 1.2, `easing` padrão da biblioteca) e um loop de `requestAnimationFrame` chamando `lenis.raf(time)`.
- **Navegação por âncoras via Lenis:** os links do menu devem chamar `lenis.scrollTo(target, { offset: -alturaDoHeader })` em vez de `scrollIntoView` nativo, mantendo a rolagem suave e consistente com o resto da página.
- **Scroll reveal:** elementos de cada seção aparecem com fade\-in \+ leve translação ao entrarem na viewport, usando `IntersectionObserver` (`scripts/scrollReveal.js`). Deve ser sutil e performático, nunca exagerado.
- **Header dinâmico:** transição de estilo do header ao rolar a página (`scripts/headerScroll.js`), usando o evento de scroll emitido pelo próprio Lenis (`lenis.on('scroll', ...)`) em vez do evento nativo do `window`, para manter tudo sincronizado.
- **Hover states:** em botões, cards e imagens da galeria — transições de 200–300ms, sem efeitos bruscos.
- Nada de animações pesadas ou parallax complexo. O Lenis é a única biblioteca externa de JavaScript permitida no projeto, justamente para elevar a qualidade da rolagem; todo o restante das interações continua em CSS/JS nativo.

## 7\. Imagens e placeholders

Nenhuma foto real foi fornecida. Para cada imagem do site (hero, sobre, cardápio, eventos, galeria), crie um placeholder visual usando cores da paleta (ex.: `div` com `background-color` sólido ou gradiente sutil) com um texto centralizado descrevendo o conteúdo esperado (ex.: "Foto: fachada do Lugar República", "Foto: café especial"). Isso evita dependência de serviços externos de imagem e deixa claro onde o cliente deve inserir fotos reais depois. Estruture o HTML/CSS de forma que substituir esses placeholders por arquivos reais em `src/assets/images/` seja trivial (mesma proporção, mesmas classes).

## 8\. Responsividade e acessibilidade

- Abordagem **mobile\-first**\: escreva o CSS base para telas pequenas e use `min-width` media queries para telas maiores.
- Breakpoints sugeridos: 480px, 768px, 1024px, 1280px.
- Use HTML semântico, `alt` descritivo em todas as imagens, contraste adequado de texto sobre fundo (mínimo AA), estados de foco visíveis em elementos interativos (`:focus-visible`), e `aria-label` em botões apenas com ícone (ex.: botão do menu hamburguer, link do Instagram no footer).
- Teste visual em pelo menos três larguras: mobile (375px), tablet (768px) e desktop (1440px).

## 9\. SEO e performance

- `index.html` com `title`, `meta description`, `meta viewport`, favicon e imagem Open Graph (`og:title`, `og:description`, `og:image`, `og:type=website`) apontando para `public/og-image.jpg`.
- Idioma do documento: `<html lang="pt-BR">`.
- Estrutura de headings coerente (um único `h1`, `h2` por seção).
- Carregar imagens com `loading="lazy"` (exceto a do hero).
- Minificação e otimização automática via build padrão do Vite — não adicionar configuração extra desnecessária.

## 10\. Passos de execução esperados

Siga esta ordem ao construir o projeto:

1. Rodar `npm create vite@latest lugar-republica -- --template vanilla`, instalar as dependências com `npm install` e adicionar o Lenis com `npm install lenis`, ajustando a estrutura conforme a seção 3.
2. Criar `index.html` com o esqueleto semântico de todas as seções (sem estilo ainda).
3. Criar `styles/variables.css` com a paleta de cores, tipografia e espaçamentos.
4. Criar `styles/reset.css` e `styles/base.css` com estilos globais (tipografia, `box-sizing`, links, botões base).
5. Estilizar cada seção em `styles/sections.css`, seguindo a ordem: Header, Hero, Sobre, Café, Eventos, Galeria, Localização, Contato, Footer.
6. Criar os componentes reutilizáveis (botões, cards, badges) em `styles/components.css`.
7. Implementar `styles/responsive.css` com os breakpoints da seção 8.
8. Implementar os scripts de interação (`nav.js`, `lenis.js`, `scrollReveal.js`, `headerScroll.js`) e importá\-los em `main.js`, garantindo que o Lenis esteja inicializado antes dos demais scripts que dependem de eventos de scroll.
9. Adicionar meta tags de SEO e favicon.
10. Revisar responsividade e acessibilidade nas três larguras indicadas.
11. Rodar `npm run build` para validar que a build de produção funciona sem erros.
12. Escrever um `README.md` explicando como instalar (`npm install`), rodar em desenvolvimento (`npm run dev`) e gerar build (`npm run build`).

## 11\. Entregáveis finais

- Projeto Vite completo e funcional, seguindo a estrutura de pastas da seção 3.
- Site one\-page com todas as seções da seção 5, com conteúdo de exemplo em português (sem "lorem ipsum") coerente com um café e espaço cultural.
- CSS organizado em arquivos separados por responsabilidade, usando variáveis para cores e tipografia.
- Scroll suave implementado com Lenis, integrado à navegação por âncoras, ao scroll reveal e ao header dinâmico.
- Placeholders de imagem claramente identificados e fáceis de substituir.
- `README.md` com instruções de instalação e execução (incluindo a dependência `lenis`).
- `.gitignore` cobrindo `node_modules`, `dist` e arquivos de ambiente.
