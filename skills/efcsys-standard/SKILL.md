# EFCsys Standard

## Objetivo
Ser a Skill-base dos projetos EFCsys, definindo como criar, alterar, validar e entregar sistemas com consistência, segurança e mínimo retrabalho.

## Quando usar
Use como regra global em qualquer projeto EFCsys. Combine com Skills especializadas somente quando o escopo exigir.

## Princípios
1. Preservar o que já funciona.
2. Alterar somente o necessário.
3. Reutilizar antes de criar.
4. Segurança por padrão.
5. Interface consistente e responsiva.
6. Dados reais ou estados vazios — nunca simulação enganosa.
7. Validar proporcionalmente ao risco.
8. Separar padrão global de regra específica do cliente.
9. Economizar créditos/contexto sem sacrificar precisão.
10. Não declarar concluído aquilo que ainda depende de backend, integração ou teste real.

## Hierarquia de contexto
Ao executar uma tarefa, considerar nesta ordem:
1. solicitação atual do usuário;
2. requisitos específicos já aprovados no projeto;
3. estado/código existente do projeto;
4. Skill especializada aplicável;
5. padrão global EFCsys.

Uma regra global não deve sobrescrever requisito específico aprovado do projeto, salvo conflito de segurança ou instrução explícita.

## Escopo de mudanças
- Fazer a menor alteração capaz de atender ao pedido.
- Não refatorar áreas não relacionadas.
- Não trocar arquitetura, biblioteca ou padrão visual sem necessidade.
- Não recriar funcionalidade existente.
- Não alterar fluxos aprovados apenas por preferência técnica.
- Antes de adicionar algo, verificar se já existe solução equivalente no projeto.

## Reutilização
Prioridade:
1. componente/função existente;
2. padrão existente;
3. dependência instalada;
4. extensão mínima da solução atual;
5. novo componente/dependência somente quando necessário.

## Dados e estados
- Produção deve usar dados reais.
- Sem dados: mostrar zero ou estado vazio adequado.
- Não preencher dashboards, gráficos, listas ou perfis com dados fictícios para aparentar funcionamento.
- Dados de demonstração só quando explicitamente necessários e claramente separados de produção.
- Não manter credenciais de teste em versão destinada ao cliente.

## Backend
Quando houver backend:
- persistência real deve ser a fonte de verdade;
- frontend não deve simular autorização;
- erros devem ser tratados sem mascarar falhas;
- mudanças de schema/permissão devem seguir a Skill Supabase quando aplicável;
- operações críticas devem evitar duplicidade.

## Papéis e permissões
- Cada papel vê e executa somente o que lhe compete.
- Esconder elemento de UI não substitui autorização.
- Administrador Master pode possuir controles globais definidos pelo produto, mas isso não autoriza criar privilégios não solicitados.
- Mudança de papel deve atualizar corretamente acesso e estado da aplicação.

## UI/UX
- Preservar identidade visual aprovada.
- Reutilizar design system/componentes.
- Manter mobile e desktop funcionais.
- Prever loading, vazio, erro e sucesso quando aplicável.
- Evitar navegação desnecessariamente complexa.
- Aplicar a Skill UI/UX para mudanças relevantes de interface.

## PWA
Quando o projeto for PWA:
- manter manifest/ícones coerentes com o produto;
- preservar uso web;
- evitar cache inseguro ou desatualizado;
- garantir navegação standalone;
- aplicar a Skill PWA para mudanças técnicas relacionadas.

## Assinatura EFCsys
Quando o projeto adotar a assinatura global EFCsys:
- preferência gráfica: **by: efcsys**;
- fallback textual: **Desenvolvido por EFCsys • Todos os direitos reservados.**
- quando existir tela/configuração de assinatura, upload, visibilidade e link ficam sob controle exclusivo do Administrador Master;
- a assinatura não deve prejudicar legibilidade ou identidade principal do cliente.

Consulte `../../shared/efcsys-brand.md` quando necessário.

## Segurança
- Nunca expor segredos.
- Aplicar menor privilégio.
- Validar operações protegidas no backend/banco.
- Não reduzir segurança para contornar bug.
- Aplicar a Skill Security em autenticação, autorização, APIs, pagamentos, bots ou dados sensíveis.

## Integrações
Para WhatsApp, pagamentos, APIs, email ou outros serviços:
- diferenciar “implementado” de “validado em ambiente real”;
- não simular sucesso de integração ausente;
- tratar falhas externas sem corromper a operação principal quando possível;
- proteger credenciais server-side;
- tornar operações idempotentes quando repetição puder causar duplicidade.

## Lovable
Quando o projeto estiver no Lovable:
- usar prompts curtos e escopados;
- não repetir contexto já conhecido;
- não solicitar auditorias/refatorações desnecessárias;
- executar diretamente tarefas simples;
- usar planejamento apenas quando reduzir risco/retrabalho;
- aplicar `../lovable/SKILL.md`.

## Testes
Durante desenvolvimento:
- testar alteração e dependências diretas;
- ampliar somente conforme risco.

Antes da entrega:
- validar fluxos críticos, papéis, persistência, responsividade, integrações disponíveis e segurança básica;
- remover dados fictícios e credenciais indevidas;
- não afirmar que dependência externa está funcionando sem evidência.

Aplicar `../testing/SKILL.md`.

## Documentação
- Documentar regras permanentes, decisões arquiteturais ou instruções realmente reutilizáveis.
- Não gerar documentação extensa automaticamente para toda alteração.
- Evitar duplicar a mesma regra em vários arquivos.
- Detalhes específicos do cliente permanecem no projeto, não nesta Skill global.

## Critério de conclusão
Uma tarefa está concluída quando:
1. comportamento solicitado foi implementado;
2. escopo diretamente afetado foi validado;
3. não foi criada regressão conhecida;
4. segurança/permissões relacionadas permanecem corretas;
5. pendências externas são explicitamente identificadas.

Não continuar adicionando melhorias fora do pedido.

## Skills especializadas
Use apenas quando necessárias:
- Lovable: `../lovable/SKILL.md`
- Supabase: `../supabase/SKILL.md`
- UI/UX: `../ui-ux/SKILL.md`
- PWA: `../pwa/SKILL.md`
- Security: `../security/SKILL.md`
- Testing: `../testing/SKILL.md`

## Referências compartilhadas
Carregar somente quando relevantes:
- `../../shared/lovable-token-economy.md`
- `../../shared/coding-standards.md`
- `../../shared/security-rules.md`
- `../../shared/efcsys-brand.md`
- `../../shared/DESIGN.md`
