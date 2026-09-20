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
| Tela, layout, formulário, dashboard, navegação, responsividade, acessibilidade | `skills/ui-ux/SKILL.md` |
| Manifest, instalação, service worker, cache, offline, standalone, push | `skills/pwa/SKILL.md` |
| Auth, autorização, API, dados sensíveis, pagamento, segredo ou operação privilegiada | `skills/security/SKILL.md` |
| Validação, regressão ou preparação para entrega | `skills/testing/SKILL.md` |
| WhatsApp, conexão, QR, filas, polling, mensagens ou notificações | `skills/whatsapp-bots/SKILL.md` |
| Oracle/Linux, Docker/Compose, VM, portas, health, logs, memória/swap | `skills/oracle-deploy/SKILL.md` |

## Combinação
Uma tarefa pode exigir várias Skills. Carregue somente as necessárias.

Exemplos:
- corrigir RLS no Lovable → standard + lovable + supabase + security;
- ajustar menu mobile → standard + lovable + ui-ux;
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
