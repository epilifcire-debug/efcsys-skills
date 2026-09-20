# Lovable — EFCsys

## Objetivo
Executar criação, correção e evolução de projetos Lovable com **mínimo consumo de créditos/tokens**, menor risco de regressão e sem duplicar trabalho já existente.

## Quando usar
Use em qualquer solicitação destinada ao Lovable: nova funcionalidade, ajuste visual, correção de bug, integração, backend, revisão pontual ou preparação para entrega.

## Fluxo obrigatório

### 1. Entender antes de alterar
- Identifique exatamente o pedido atual.
- Considere o estado já conhecido do projeto.
- Não peça novamente informações já disponíveis no projeto, Knowledge ou etapa atual.
- Se uma etapa anterior está concluída, trate-a como concluída até existir evidência de regressão.

### 2. Definir o menor escopo
- Altere somente arquivos, componentes, funções, tabelas ou policies necessários.
- Não transforme uma correção localizada em revisão geral.
- Não refatore código funcional apenas por preferência.
- Não recrie componente, fluxo, tabela ou regra que já exista.
- Preserve funcionalidades e identidade visual não relacionadas ao pedido.

### 3. Reutilizar antes de criar
Prioridade:
1. componente/função existente;
2. padrão já usado no projeto;
3. dependência já instalada;
4. somente então criar algo novo.

Não instalar biblioteca ou criar arquitetura alternativa se o projeto já possui solução adequada.

### 4. Executar sem etapas desnecessárias
Para tarefas simples, mande implementar diretamente.

Use planejamento/Plan Mode somente quando:
- houver mudança estrutural relevante;
- existir risco real de perda de dados;
- várias áreas dependentes precisarem ser coordenadas;
- planejamento prévio provavelmente evitar retrabalho.

Não pedir análise, plano, relatório, documentação ou explicação antes da implementação quando isso não for necessário.

### 5. Proteger créditos
- Não repetir no prompt requisitos que o Lovable já conhece.
- Referenciar nomes exatos de páginas, componentes, arquivos ou etapas existentes.
- Não solicitar auditoria completa para corrigir problema localizado.
- Não solicitar regressão completa a cada pequena alteração.
- Não pedir para “verificar tudo” sem motivo técnico.
- Agrupar alterações diretamente relacionadas quando isso economizar uma interação.
- Não agrupar tarefas independentes se isso ampliar exploração/contexto.
- Evitar respostas longas do Lovable: pedir confirmação objetiva do que foi alterado quando suficiente.

### 6. Backend e integrações
- Não declarar backend, pagamento, WhatsApp, API ou serviço externo como validado sem teste/evidência real.
- Não criar dados falsos para mascarar integração ausente.
- Preservar segurança, RLS, autenticação e autorização.
- Para Supabase, aplicar também a Skill `../supabase/SKILL.md`.
- Para alterações sensíveis, aplicar `../security/SKILL.md`.

### 7. Testes
Após a alteração:
- validar primeiro o fluxo modificado;
- testar áreas diretamente dependentes;
- ampliar regressão somente quando o risco justificar;
- em preparação final para entrega, aplicar `../testing/SKILL.md`.

## Formato recomendado de comando ao Lovable
Um bom comando deve conter apenas:
1. **ação** — o que deve mudar;
2. **alvo** — onde deve mudar;
3. **regra** — comportamento obrigatório relevante;
4. **preservação** — o que não pode ser alterado, somente quando houver risco;
5. **validação** — teste objetivo necessário.

Não incluir histórico extenso do projeto quando ele já estiver disponível no Lovable.

## Critério de conclusão
A tarefa termina quando o comportamento solicitado estiver implementado e validado no escopo afetado. Não continuar criando melhorias não solicitadas.

## Referências
- `../../shared/lovable-token-economy.md`
- `../../shared/coding-standards.md`
- `../../shared/security-rules.md`

Carregue as referências somente quando forem necessárias para a tarefa.
