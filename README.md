# EFCsys Skills

Repositório central das **Skills globais da EFCsys**, criado para reutilizar padrões entre projetos sem misturar regras específicas de clientes.

## Entrada global
Use `EFCsys.md` como roteador. Ele aplica o padrão global e seleciona somente as Skills necessárias para a tarefa.

## Princípios
- Skills pequenas, especializadas e reutilizáveis.
- Alterações mínimas e escopadas.
- Reutilização de componentes, padrões e dependências existentes.
- Segurança por padrão.
- Economia de créditos/tokens no Lovable.
- Referências detalhadas carregadas somente quando necessárias.
- Regras específicas permanecem no projeto correspondente.

## Skills
- `efcsys-standard` — padrão global EFCsys.
- `lovable` — execução eficiente no Lovable.
- `supabase` — banco, Auth, RLS e backend.
- `ui-ux` — interface, responsividade e acessibilidade.
- `pwa` — instalação, cache e experiência standalone.
- `security` — autenticação, autorização e dados sensíveis.
- `testing` — validação focada e prevenção de regressões.
- `whatsapp-bots` — conexão, filas, notificações e operação dos bots.
- `oracle-deploy` — deploy e diagnóstico de serviços Docker em VMs Oracle/Linux.

## Estrutura
- `skills/` — instruções reutilizáveis.
- `shared/` — padrões globais consultados pelas Skills.
- `templates/` — base para novas Skills e novos projetos.
- `integrations/` — instruções de ativação em plataformas como Lovable.

## Regra de uso
Carregue somente a Skill relevante para a tarefa. Consulte arquivos de `shared/` apenas quando a Skill ou a mudança realmente exigir contexto adicional.

Desenvolvido por EFCsys • Todos os direitos reservados.
