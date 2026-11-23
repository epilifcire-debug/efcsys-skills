# EFCsys — Skill Router

## Objetivo
Ponto de entrada global para selecionar somente as Skills EFCsys necessárias para cada tarefa.

## Regra principal
Sempre aplicar `skills/efcsys-standard/SKILL.md`.

Depois, carregar apenas as Skills relacionadas ao trabalho atual. Não carregar todo o repositório por padrão.

## Roteamento

| Contexto da tarefa | Skill |
|---|---|
| Projeto/alteração no Lovable | `skills/lovable/SKILL.md` |
| Supabase, banco, Auth, RLS, RPC, Edge Functions, Storage, Realtime | `skills/supabase/SKILL.md` |
| Projeto novo, redesign, nova página principal/pública, "refazer visual/tipografia" | `skills/design-direction/SKILL.md` + `skills/ui-ux/SKILL.md` |
| Tela, layout, formulário, dashboard, navegação, responsividade, acessibilidade | `skills/ui-ux/SKILL.md` |
| Manifest, instalação, service worker, cache, offline, standalone, push | `skills/pwa/SKILL.md` |
| Auth, autorização, API, dados sensíveis, pagamento, segredo ou operação privilegiada | `skills/security/SKILL.md` |
| Validação, regressão ou preparação para entrega | `skills/testing/SKILL.md` |
| WhatsApp, conexão, QR, filas, polling, mensagens ou notificações | `skills/whatsapp-bots/SKILL.md` |
| Oracle/Linux, Docker/Compose, VM, portas, health, logs, memória/swap | `skills/oracle-deploy/SKILL.md` |
| Shard Cloud, Aplicação a partir do GitHub, Dockerfile, plano de memória, bots na Shard | `skills/shardcloud-deploy/SKILL.md` |
| Projeto novo ou migração de app (ex.: sair do Lovable) | `templates/new-project/README.md` + `integrations/lovable.md` + `skills/efcsys-standard/SKILL.md` |
| Hover, transições, cursor, fundos animados, landing page | `shared/DESIGN.md` (seção Animações) + `skills/ui-ux/SKILL.md` |

## Combinação
Uma tarefa pode exigir várias Skills. Carregue somente as necessárias.

Exemplos:
- corrigir RLS no Lovable → standard + lovable + supabase + security;
- ajustar menu mobile → standard + lovable + ui-ux;
- migrar app do Lovable refazendo o layout → standard + design-direction + ui-ux + pwa + supabase;
- implantar bot na Oracle → standard + whatsapp-bots + oracle-deploy + security;
- liberar PWA para cliente → standard + pwa + testing + security.

## Regras de eficiência
- Não repetir conteúdo das Skills no prompt.
- Não carregar referências `shared/` sem necessidade.
- Não transformar roteamento em análise longa.
- Se a tarefa for simples, selecionar as Skills e executar.
- Regras específicas do projeto continuam no próprio projeto.
- Em conflito, seguir a hierarquia definida em `skills/efcsys-standard/SKILL.md`.

## Critério
O roteamento está correto quando fornece contexto suficiente para executar a tarefa sem carregar regras irrelevantes.
