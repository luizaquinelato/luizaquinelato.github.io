Esse é um site para uma Terapeuta Ocupacional, a ideia é que seja um dos principais pontos em que clientes possam encontrar os contatos.
As informaçoes que gostariamos de apresentar são:
- Contato(instagram, whatsapp, email, telefone e endereço)
- Descriçao do tipo de serviço prestado

## Referências

Nome: Luiza Quinelato - Terapia Ocupacional
Instagram: @luizaquinelato
Whatsapp: 11996218086
Email: contato@luizaquinelato.com.br
Endereço: Vila Prudente - São Paulo

## Cores

| Nome   | HEX     |
|--------|---------|
| Rose   | #9C446E |
| Blush  | #D09E97 |
| Dark   | #3F1F1F |
| Sky    | #AFCCD2 |
| Sage   | #909A76 |
| Cream  | #FAEAD3 |

## Fontes

- Principal: Lemone (não disponível como web font; substituto atual: Cormorant Garamond via Google Fonts)
- Secundário: Coolvetica (substituto atual: Raleway via Google Fonts)
- Secundário: Badge

## Assets (`assets/`)

- `Logotipo SVG/` — 72 variações do logotipo em SVG (1.svg … 72.svg)
  - Arquivos ~49KB = logotipo completo (ícone + texto "Luiza Quinelato" + "terapia ocupacional")
  - Arquivos ~21KB = versão intermediária (ícone + texto menor)
  - Arquivos ~7KB (41–72.svg) = apenas o ícone/monograma LQ, sem texto
  - Todos têm `viewBox="0 0 810 810"` com muito espaço em branco ao redor
- `Mascote/mascote.svg` — ilustração da mascote (personagem feminino com cabelo roxo)
- `Destaques/` — imagens para as seções da landing page:
  - `integraçãosensorial.png`, `saúdemental.png`, `sobre.png`, `espaço.png`, `contato.png`, `depoimentos.png`

## Estrutura do site (`index.html`)

Landing page em HTML/CSS/JS puro, arquivo único. Seções:
1. **Nav** — logo (1.svg), links âncora, botão WhatsApp; hambúrguer no mobile
2. **Hero** — título, subtítulo, CTAs (WhatsApp + âncora serviços), mascote SVG
3. **Serviços** — 3 cards com imagens dos Destaques
4. **Sobre** — texto de apresentação + badges de especialidade
5. **Espaço** — descrição do consultório + imagem
6. **Contato** — links clicáveis (WhatsApp, Instagram, e-mail, endereço)
7. **Footer** — ícone LQ (45.svg, sem texto) + copyright

## Decisões técnicas

### Logo na navbar
O SVG `1.svg` tem `viewBox="0 0 810 810"` mas o conteúdo real fica em `x=78, y=257, w=654, h=297`.
Para cortar o espaço em branco usa-se CSS crop:
```css
.nav__logo { overflow: hidden; height: 60px; width: 132px; }
.nav__logo img { height: 164px; margin-top: -52px; margin-left: -16px; }
```
Fórmula: `height_render = desired_height × (810 / content_height)`

### Ícone no footer
Usa `45.svg` (ícone LQ sem texto, ~7KB). Conteúdo em `x=178, y=164, w=454, h=482`.
```css
.footer__logo { overflow: hidden; height: 44px; width: 42px; }
.footer__logo img { height: 74px; margin-top: -15px; margin-left: -16px; opacity: .9; }
```
Sem filtro de cor — o SVG mantém suas cores originais sobre o fundo escuro.

### Seções removidas
- Depoimentos foi removida a pedido do cliente (seção e CSS).
