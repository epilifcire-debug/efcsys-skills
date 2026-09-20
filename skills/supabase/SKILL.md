# Supabase — EFCsys

## Objetivo
Implementar e corrigir backend Supabase com segurança, alterações mínimas e sem quebrar dados, autenticação ou regras já funcionais.

## Quando usar
Use para Database/Postgres, Auth, RLS, policies, RPC, migrations, Storage, Edge Functions, Realtime e integrações server-side ligadas ao Supabase.

## Princípios
- Corrigir a causa do problema, não contornar segurança.
- Alterar somente schema, policies, funções e serviços relacionados à tarefa.
- Preservar dados e compatibilidade sempre que possível.
- Separar autenticação, autorização e regra de negócio.
- Nunca usar o frontend como única barreira de permissão.

## Banco e migrations
- Inspecionar a estrutura existente antes de criar tabela, coluna, enum, função ou trigger.
- Não duplicar estruturas existentes com nomes diferentes.
- Preferir migrations controladas e reversíveis quando aplicável.
- Evitar operações destrutivas sem necessidade explícita.
- Antes de remover/renomear coluna, tabela ou função, verificar dependências.
- Definir constraints, defaults e índices somente quando necessários ao comportamento ou integridade.
- Não inserir dados fictícios em produção para fazer telas parecerem funcionais.

## Auth e usuários
- `auth.users` identifica autenticação; perfil, papel e dados de negócio devem seguir a arquitetura do projeto.
- Nunca confiar em user id, email ou role enviados pelo cliente para autorizar operação.
- Usar a identidade autenticada no servidor/banco como fonte de verdade.
- Cadastro novo deve receber somente o papel padrão previsto pelo projeto.
- Elevação de privilégio deve exigir fluxo autorizado.
- Troca de role deve refletir corretamente em queries/cache/estado da aplicação.

## RLS
Para tabelas expostas pela API:
- manter RLS habilitada quando houver dados protegidos;
- criar policies específicas para SELECT/INSERT/UPDATE/DELETE conforme necessidade;
- aplicar menor privilégio;
- usar `auth.uid()` ou mecanismo equivalente coerente com a arquitetura;
- não usar policy permissiva apenas para “fazer funcionar”;
- validar isolamento entre usuários e papéis;
- revisar policies existentes antes de adicionar outra que possa ampliar acesso involuntariamente.

Problemas de listagem devem ser investigados na origem: query, sessão, role, policy e relacionamento. Não desabilitar RLS como correção.

## Client x server
### Cliente
Pode usar apenas credenciais públicas previstas pelo Supabase e executar operações permitidas por RLS.

### Servidor
Operações administrativas ou privilegiadas devem ocorrer em ambiente server-side protegido.

- Nunca expor `service_role` no bundle, variáveis públicas, logs ou repositório.
- Nunca confiar em esconder botão/tela como controle de acesso.
- Validar autorização novamente no servidor para ações privilegiadas.

## RPC e funções Postgres
- Usar RPC quando centralizar atomicidade, regra crítica ou operação que não deve depender do cliente.
- Validar entradas e identidade dentro da operação.
- Evitar `SECURITY DEFINER` por padrão.
- Se `SECURITY DEFINER` for indispensável, limitar privilégios, definir `search_path` seguro e revisar exposição da função.
- Não criar RPC duplicando operação simples já protegida adequadamente por RLS.

## Edge Functions
- Guardar segredos em variáveis server-side.
- Validar autenticação/autorização antes de operações protegidas.
- Validar payloads e tratar erros previsíveis.
- Não retornar stack traces, tokens ou segredos.
- Tornar callbacks/webhooks idempotentes quando o provedor puder reenviar eventos.
- Verificar assinatura/autenticidade de webhooks quando o provedor oferecer esse mecanismo.

## Storage
- Separar buckets públicos e privados conforme finalidade.
- Aplicar policies de Storage compatíveis com os papéis.
- Não tornar bucket público apenas para contornar erro de acesso.
- Validar tipo/tamanho de upload quando relevante.
- Para arquivos privados, usar acesso autenticado ou URLs assinadas conforme necessidade.

## Realtime
- Ativar somente onde houver benefício real.
- Não usar Realtime para substituir persistência ou regras de autorização.
- Garantir que RLS continue protegendo os dados acessados.

## Alterações de alto risco
Exigem cuidado adicional:
- exclusão/renomeação de tabelas ou colunas;
- mudança ampla de policies;
- alteração de roles/permissões;
- funções `SECURITY DEFINER`;
- operações em massa;
- mudanças em autenticação;
- migrations que transformem dados existentes.

Nesses casos, planejar somente o necessário para evitar perda de dados ou indisponibilidade.

## Validação mínima
Após uma alteração, validar somente o que foi afetado:
1. usuário/papel autorizado consegue executar a ação;
2. usuário/papel não autorizado continua bloqueado;
3. dados existentes permanecem íntegros;
4. frontend recebe o resultado esperado;
5. nenhum segredo foi exposto.

Não executar regressão completa do sistema para uma alteração isolada, salvo risco técnico real ou etapa final de entrega.

## Integração com outras Skills
- Lovable: `../lovable/SKILL.md`
- Segurança: `../security/SKILL.md`
- Testes: `../testing/SKILL.md`
- Regras globais: `../efcsys-standard/SKILL.md`

Consulte também `../../shared/security-rules.md` quando a tarefa envolver dados sensíveis, autorização ou operações privilegiadas.
