# AIMED OS · Release pré-curso (16/05/2026)

Pacote de revisão antes do lançamento de 22/05. Trocas mínimas, conservando intacta a estrutura, o conteúdo dos módulos, a metodologia e a identidade visual.

## Arquivos novos

```
manifest.json
og-image.png            (1200×630, identidade AIMED)
og-image.jpg            (mesma OG em JPEG, fallback)
icons/
  favicon.ico
  icon-192.png          (PWA Android)
  icon-512.png          (PWA Android)
  icon-maskable-192.png (Android adaptive)
  icon-maskable-512.png (Android adaptive)
  apple-touch-icon.png      (iOS, 180)
  apple-touch-icon-167.png  (iPad Pro)
  apple-touch-icon-152.png  (iPad)
```

## Mudanças no `index.html`

### Conteúdo
1. **Frase de abertura (módulo `abertura-go`):** "Uma residente com IA bem treinada **supera um especialista sem ela**" → "Uma residente com IA bem treinada **decide melhor do que decidiria sem ela**." Preserva a tese, elimina a comparação vulnerável a screenshot.
2. **Alegação de "primeiro curso" (meta description e og:description):** "O primeiro curso de IA especificamente para residentes de GO no Brasil" → "Primeira aplicação integral da metodologia AIMED em GO no Brasil." Verdadeira, defensável, recentra a marca na sua autoria.
3. **Callout de segurança no topo do módulo `calculos-mdv`:** novo bloco `alert-box danger` (vermelho proeminente, com borda lateral grossa e glow) antes do conteúdo de Zuspan/Pritchard. Reafirma checagem dupla institucional como pré-condição do módulo. A "Regra zero" original continua onde estava.
4. **Meta description duplicada:** removida (havia duas).

### PWA — versão 1.0 (instalação na tela inicial, sem service worker)
5. **`<head>` ganhou bloco PWA completo:**
   - `<link rel="manifest" href="manifest.json">`
   - `apple-touch-icon` em 3 tamanhos (180/167/152)
   - `<meta name="apple-mobile-web-app-capable">` + status bar + title
   - `application-name`, `mobile-web-app-capable`
6. **OG image local:** trocou a imagem do WordPress por `og-image.png` no próprio repo. Não depende mais do `inovamed.pro` estar de pé na hora do compartilhamento.
7. **Twitter / X Card:** adicionado bloco `twitter:card summary_large_image` para previews bonitos no X, LinkedIn etc.

### CSS
8. Nova classe `.alert-box.danger` — variante mais forte da `.alert-box.warning`, com borda lateral grossa, fundo vermelho mais opaco e box-shadow. Usada apenas no callout do módulo de cálculos.

## O que NÃO foi tocado (deliberadamente)

- Estrutura de módulos (`PROGRAMA`), níveis N1/N2/N3, prompts.
- Glossário, Biblioteca AIMED GO, Logística, Sobre.
- Avaliação T0/T1/T2 (instrumento de pesquisa intacto).
- Lógica de countdown (já era viva via JS).
- Módulo de Ética e citações da Resolução CFM 2.454/2026 (confirmada como real).
- Sidebar, topbar, overlays, navegação.

## PWA v2.0 — depois do curso

Service worker com estratégia `network-first` + fallback para cache. Não foi incluído agora porque um service worker mal configurado pode entregar versão stale enquanto você corrige erros nos dias finais. A v2.0 entra como anúncio separado às residentes ("agora funciona offline no plantão") na semana seguinte ao curso.

## Como testar antes de publicar

1. Subir tudo para o repo `aimed-residentes-go` no GitHub.
2. Acessar `https://mbulabarros.github.io/aimed-residentes-go/` no celular.
3. iOS Safari: "Compartilhar → Adicionar à Tela de Início" — deve aparecer ícone dourado "A" com nome "AIMED GO".
4. Android Chrome: deve oferecer "Instalar app" automaticamente; ícone idem.
5. Compartilhar o link no WhatsApp / LinkedIn / X — preview deve mostrar `og-image.png` com identidade AIMED.
6. Validador OG: https://www.opengraph.xyz/ ou https://cards-dev.twitter.com/validator
7. Validador PWA: DevTools → Lighthouse → categoria "PWA" — deve passar instalabilidade (offline ainda vai falhar — é esperado, fica para v2.0).
