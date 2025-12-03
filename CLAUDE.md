# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## Contexto

Template Slidev profissional com wireframe editorial grayscale. Apresentação do projeto IVE (Integração de Vestíveis ao Check-up Executivo Einstein) — relatório final com 16 slides demonstrando 8 layouts sofisticados.

**Propósito:** Documentar em formato de apresentação executiva os resultados de pesquisa de integração de dados de wearables com serviço médico (n=93 survey, n=8 entrevistas, n=21 workshop).

---

## Arquitetura

**Estrutura principal:**
- `/slides.md` — Arquivo único contendo toda a apresentação (599 linhas, frontmatter YAML + Markdown + HTML inline)
- `/style.css` — Design system Editorial Swiss (34.5 KB, paleta warm grayscale)
- `/styles/global.css` — Estilos adicionais com sistema de variáveis CSS extensível
- `/components/` — Pasta vazia pronta para componentes Vue custom (não utilizados ainda)
- `/public/` — Assets estáticos (vazio)

**Design System:**
- **Tipografia:** Playfair Display (serif, headlines) + DM Sans (sans-serif, body) + JetBrains Mono (código)
- **Paleta:** Warm grayscale (charcoal #1c1917 até paper #fdfcfa)
- **Layout:** 8 padrões CSS reutilizáveis (hero-sidebar, split-asymmetric, metrics-grid, feature-cards, comparison-table, highlight-grid, timeline, process-steps)

**Configuração Slidev:**
- Tema padrão (`@slidev/theme-default`)
- Markdown Components ativo (mdc: true)
- Highlighter: Shiki
- Transição padrão: slide-left

---

## Comandos Comuns

```bash
# Iniciar servidor de desenvolvimento (live reload)
npm run dev
# ou
npx slidev

# Exportar para PDF
npx slidev export

# Exportar para PDF de slides específicos
npx slidev export --range 1-10

# Exportar para PPTX (requer playwright-chromium)
npx slidev export --format pptx

# Exportar para PNG
npx slidev export --format png

# Build para produção (SPA)
npx slidev build
```

---

## Extensão do Template

### Adicionar Novos Slides

Edite `/slides.md`. Cada slide é separado por `---`:

```markdown
---

# Título do Slide

<div class="layout-metrics-grid">
  <!-- conteúdo -->
</div>

---
```

### Criar Componentes Custom

1. Crie arquivo Vue em `/components/YourComponent.vue`
2. Slidev importa automaticamente
3. Use em slides.md:

```markdown
<YourComponent prop="value" />
```

### Customizar Cores

Edite variáveis CSS em `/style.css`:

```css
:root {
  --ink: #000000;           /* cor de texto principal */
  --paper: #ffffff;         /* cor de fundo principal */
  --charcoal: #333333;      /* destaque */
}
```

### Adicionar Fontes Customizadas

No frontmatter de `slides.md`:

```yaml
---
fonts:
  serif: 'Playfair Display'
  sans: 'DM Sans'
  mono: 'JetBrains Mono'
---
```

---

## Layouts Disponíveis

| Classe | Uso | Grid |
|:-------|:----|:-----|
| `.layout-hero-sidebar` | Seção principal com sidebar estatísticas | 1.5fr / 1fr |
| `.layout-split-asymmetric` | Contexto + detalhes lado a lado | 1.2fr / 1fr |
| `.layout-metrics-grid` | 4 métricas em grid 2x2 | 1fr / 1fr |
| `.layout-features` | 3 cards de características | repeat(3, 1fr) |
| `.layout-comparison-table` | Tabela de comparação 3 colunas | 1.5fr / 1fr / 1fr |
| `.layout-highlight-grid` | 4 destaques em grid 2x2 | 1fr / 1fr |
| `.layout-timeline` | Cards de timeline | 1fr / 1fr |
| `.process` | Passos sequenciais numerados | flex com steps |

---

## Padrões CSS

### Componentes Reutilizáveis

**Métrica (para grids):**
```html
<div class="metric-card">
  <div class="metric-value">XX%</div>
  <div class="metric-label">LABEL</div>
  <div class="metric-detail">Contexto</div>
</div>
```

**Info Box:**
```html
<div class="info-box">
  <h3>Título</h3>
  <ul class="list--nested">
    <li><strong>Item</strong> — Descrição</li>
  </ul>
</div>
```

**Quote:**
```html
<div class="quote">
  "Texto da citação"
  <div class="quote__author">— Atribuição</div>
</div>
```

**Card com Acento:**
```html
<div class="card card--accent">
  <h4>Título</h4>
  <p>Descrição</p>
</div>
```

### Sistema de Spacing

Baseado em 4px:
- `var(--space-1)` = 0.25rem
- `var(--space-4)` = 1rem
- `var(--space-5)` = 1.25rem
- `var(--space-6)` = 1.5rem
- `var(--space-7)` = 1.75rem

### Utilitários

```css
.mt-xs, .mt-sm, .mt-md, .mt-lg, .mt-xl  /* margin-top */
.gap-sm, .gap-md, .gap-lg               /* gap em grids/flex */
.flex, .flex-col, .flex-1               /* flexbox utilities */
.h-full, .w-full                        /* dimensões 100% */
```

---

## Workflow de Edição

1. **Editar conteúdo:** Modifique `/slides.md` e veja mudanças em tempo real com `npm run dev`
2. **Ajustar estilos:** Edite `/style.css` ou `/styles/global.css`
3. **Versionamento:** Commit com mensagem clara descrevendo mudanças nos slides
4. **Exportação:** Execute `npx slidev export` para gerar PDF final

---

## Observações

- **Sem playwright:** Exportação para PPTX/PNG requer `npm install -D playwright-chromium`
- **Responsive:** Design system usa `clamp()` para tipografia responsiva — não requer breakpoints manuais
- **Dark mode:** CSS suporta preferências do sistema (media query `prefers-color-scheme`)
- **Impressão:** Todos os slides são otimizados para print via `@media print`

---

**Status:** v1.0 — Template funcional com 16 slides, design system completo, pronto para ser usado como base para novas apresentações.

