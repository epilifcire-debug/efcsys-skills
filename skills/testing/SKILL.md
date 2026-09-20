# Testing — EFCsys

## Objetivo
Validar mudanças com o menor custo necessário, encontrando regressões reais sem gastar créditos/tempo repetindo testes que não foram impactados.

## Quando usar
Use após implementação, correção de bug, alteração de banco/permissão, integração ou antes de liberar uma versão.

## Regra central
O tamanho do teste deve acompanhar o risco da mudança.

Não executar regressão completa após cada alteração pequena. Durante desenvolvimento, testar o que mudou e suas dependências diretas. Reservar validação ampla para mudanças transversais, alto risco ou preparação final para entrega.

## Níveis de validação

### Nível 1 — alteração localizada
Para texto, estilo, componente isolado ou correção simples:
- testar o comportamento alterado;
- conferir desktop/mobile se a mudança for visual;
- verificar erro de console somente se relacionado;
- não revisar o sistema inteiro.

### Nível 2 — fluxo funcional
Para formulário, agendamento, CRUD, filtros, navegação ou regra de negócio:
- caminho principal;
- validações relevantes;
- estado de erro;
- persistência/resultado;
- dependências diretamente conectadas.

### Nível 3 — segurança/backend
Para Auth, roles, RLS, RPC, Edge Functions, APIs ou dados sensíveis:
- usuário autorizado funciona;
- usuário não autorizado é bloqueado;
- isolamento entre usuários/papéis;
- falhas não expõem segredos;
- dados permanecem íntegros.

Aplicar também Security/Supabase quando relevante.

### Nível 4 — integração externa
Para WhatsApp, pagamentos, webhooks, email ou API externa:
- diferenciar implementação de validação real;
- testar sucesso e falha quando o ambiente permitir;
- confirmar idempotência quando eventos puderem repetir;
- não declarar integração validada apenas por mock, frontend ou código compilando;
- registrar claramente dependência externa ainda pendente.

### Nível 5 — pré-entrega
Somente quando o projeto estiver efetivamente pronto para liberação:
- fluxos críticos ponta a ponta;
- autenticação e papéis;
- operações principais de cada perfil;
- responsividade das telas essenciais;
- persistência de dados;
- integrações disponíveis;
- estados loading/empty/error/success;
- segurança básica;
- PWA quando aplicável;
- ausência de dados fictícios/credenciais de teste indevidas.

## Teste orientado pela mudança
Antes de testar, responder:
1. O que foi alterado?
2. Que fluxo usa diretamente isso?
3. O que depende desse fluxo?
4. Qual falha seria crítica?

Teste primeiro essas respostas. Não ampliar escopo sem evidência ou risco que justifique.

## Correção de bug
Ao corrigir bug:
1. reproduzir quando necessário;
2. corrigir a causa;
3. validar o cenário que falhava;
4. validar o cenário normal relacionado;
5. verificar permissão/dados se o bug envolver backend;
6. encerrar quando o escopo estiver estável.

Não usar a correção de um bug como justificativa automática para auditoria completa.

## UI/UX
Quando a mudança for visual, validar somente os breakpoints e estados afetados:
- largura móvel relevante;
- desktop relevante;
- overflow/corte;
- interação por toque;
- loading/empty/error quando o componente possuir esses estados;
- acessibilidade básica da interação alterada.

## Banco de dados
Se houver mudança de schema/policy/função:
- confirmar que migration/operação foi aplicada;
- preservar dados existentes;
- testar leitura/escrita conforme papéis;
- testar bloqueio indevido ou acesso excessivo;
- evitar testes destrutivos em produção.

## Dados de teste
- Preferir ambiente/contas de teste quando disponíveis.
- Não poluir produção com registros fictícios desnecessários.
- Remover dados temporários quando o teste exigir criação e a remoção for segura.
- Nunca usar credenciais reais em documentação ou commits.

## Evidência
Só considerar algo validado quando houver evidência compatível:
- execução real;
- resposta da API;
- resultado persistido;
- comportamento observado;
- teste automatizado relevante aprovado.

Código existente, mock ou mensagem de “sucesso” não prova sozinho que serviço externo está funcionando.

## Quando parar
Pare os testes quando:
- o comportamento alterado funciona;
- dependências diretas relevantes continuam funcionando;
- não há regressão observada no escopo;
- requisitos de segurança relacionados foram verificados.

Não continuar explorando áreas sem relação com a mudança apenas para “garantir tudo”.

## Relato final
Manter curto:
- o que foi testado;
- resultado;
- pendência real, se houver.

Não gerar relatório extenso salvo solicitação.

## Integração com outras Skills
- Lovable: `../lovable/SKILL.md`
- Supabase: `../supabase/SKILL.md`
- Security: `../security/SKILL.md`
- UI/UX: `../ui-ux/SKILL.md`
- PWA: `../pwa/SKILL.md`
