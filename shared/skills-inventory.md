# Inventário de skills e plugins — conta EFCsys

Referência de quais skills e plugins ficam ativos na conta e por quê. Atualizar quando algo for adicionado ou removido.

## Mantidos

### Padrão EFCsys (repositório efcsys-skills)
- `efcsys-standard`: regra-base dos projetos
- `pwa`: apps instaláveis
- `shardcloud-deploy`: publicação na Shard Cloud

### Design e interface
- VectorLab UX (`motion`, `transitions`, `reduced-motion`, `page-patterns`, `anti-slop`, `keyboard`, `labels`, demais): transições, movimento e padrões de página
- `frontend-design` (Anthropic): direção visual sem cara de template
- `web-animation-design` (audit-suite): hover, easing, duração, `prefers-reduced-motion`
- `emil-design-engineering` (audit-suite): estados de botão, formulários, toque, landing pages
- `landing-page` (Website Design): construção de landing com direção visual definida
- `web-review` (Website Design): lista de correções por prioridade
- `vercel-react-best-practices` (audit-suite): opcional, para projetos React

### Dados e banco
- `supabase`
- `supabase-postgres-best-practices`

### Documentos e arquivos
- `docs`, `docx`, `xlsx`, `pdf`, `pptx`

### Uso geral
- `import-memory`, `skill-creator`, `deep-research`, `google-workspace`
- `chrome-browser`, `built-in-browser`, `computer-use`

### Economia de tokens
- `claude-context-optimizer`
- `code-parser` (quando aceito)
- `token-saver` (quando aceito)

## Removidos (ou a remover)

- Todas as `databricks:*`, `cartographer:*`, `claude-for-manufacturing:*`, `equity-research:*`, `engineering:*`
- `feature-dev`, `dataviz`, `claude-code-setup`, `explain-usage`, `setup-claude`, `cowork-plugin`, `plugin-authoring`, `video-making`, `morning`, `structured-memory`, `file-reading`, `pdf-reading`, `product-self-knowledge`, uma das duas cópias de `frontend-design`
- `audit-as-*` (10 lentes) e `full-audit`
- `make-interfaces-feel-better` (repetido por `emil-design-engineering`)
- `web-design-guidelines` (repetido por `ui-ux` e `web-review`)
- `design-system`, `web-design-system` (use o `DESIGN.md` do padrão EFCsys)
- `review-page` (use `web-review`)
- `context-bench` (ativado por engano)

## Motivo
Skills com descrições longas são injetadas em toda sessão. Manter só o que é usado reduz o custo fixo de cada conversa.
