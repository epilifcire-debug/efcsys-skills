# Segurança — EFCsys

## Objetivo
Aplicar segurança por padrão nos projetos EFCsys sem transformar correções pontuais em auditorias amplas ou criar complexidade desnecessária.

## Quando usar
Use ao trabalhar com autenticação, autorização, papéis, dados pessoais, APIs, bots, pagamentos, uploads, Supabase, operações administrativas, integrações externas, segredos ou infraestrutura.

## Princípios
1. Menor privilégio.
2. Negar por padrão quando a autorização não puder ser confirmada.
3. Frontend nunca é a única barreira de segurança.
4. Segredos permanecem server-side.
5. Corrigir a causa do problema sem enfraquecer controles existentes.
6. Alterar apenas o escopo necessário.

## Autenticação
- Usar mecanismos reais de autenticação; não simular sessão em produção.
- Validar sessão/token no ambiente responsável pela operação protegida.
- Não confiar em email, user id ou role enviados pelo cliente como prova de identidade.
- Expiração, logout e troca de usuário devem invalidar estado privilegiado quando aplicável.
- Fluxos de recuperação/troca de senha não devem revelar se uma conta existe além do necessário.

## Autorização e papéis
- Separar autenticação de autorização.
- Verificar permissões no backend/banco para ações protegidas.
- Ocultar botão ou rota no frontend melhora UX, mas não substitui autorização.
- Administrador Master e demais papéis devem possuir somente permissões previstas.
- Elevação de privilégio exige operação autorizada e não deve ser controlada pelo próprio cliente.
- Ao alterar roles, revisar cache/sessão/queries que possam manter permissão antiga.

## Segredos e configuração
Nunca colocar em código público, frontend, logs ou documentação:
- senhas;
- tokens privados;
- API secrets;
- service-role keys;
- chaves privadas;
- credenciais de banco.

Usar variáveis de ambiente/secret stores apropriados. Arquivos `.env` reais não devem ser versionados.

## APIs e endpoints
- Validar autenticação e autorização antes de executar ação protegida.
- Validar payload, tipos, limites e campos obrigatórios.
- Não retornar stack trace, segredo ou detalhes internos desnecessários.
- Aplicar rate limiting/controle de abuso quando o endpoint puder ser explorado repetidamente.
- Operações críticas devem ser idempotentes quando repetição puder causar duplicidade.
- Não confiar em CORS como mecanismo de autenticação.

## Supabase
- Manter RLS nas tabelas que exigem isolamento.
- Nunca expor `service_role` no cliente.
- Não criar policy permissiva para resolver rapidamente erro de acesso.
- Evitar `SECURITY DEFINER` sem necessidade e revisão.
- Aplicar também `../supabase/SKILL.md`.

## Bots e WhatsApp
- Endpoints administrativos como conexão/status detalhado devem ter proteção adequada quando expostos.
- Credenciais/sessões do WhatsApp não devem ser publicadas ou registradas em logs.
- Validar origem/autorização de comandos administrativos.
- Mensagens recebidas são entrada não confiável: validar antes de acionar operações internas.
- Falha de envio de mensagem não deve corromper a operação principal quando a notificação for secundária.

## Pagamentos e webhooks
- Nunca confiar apenas no retorno do frontend para confirmar pagamento.
- Confirmar estado por API/webhook confiável do provedor.
- Verificar assinatura/autenticidade do webhook quando disponível.
- Tratar reenvio de webhook de forma idempotente.
- Não registrar dados financeiros sensíveis desnecessários.
- Segredos do provedor permanecem server-side.

## Uploads e arquivos
- Validar tipo e tamanho quando relevante.
- Não confiar somente na extensão do arquivo.
- Separar arquivos públicos e privados.
- Evitar nomes/caminhos controlados livremente pelo usuário quando puderem gerar conflito ou traversal.
- Dados privados devem exigir autorização para acesso.

## Dados pessoais
- Coletar somente o necessário para a finalidade do sistema.
- Evitar exibir CPF, telefone, documentos ou outros dados pessoais sem necessidade.
- Não registrar dados pessoais completos em logs técnicos.
- Aplicar mascaramento na interface quando o contexto exigir exposição parcial.
- Respeitar regras específicas de retenção/exclusão definidas pelo projeto.

## Logs e observabilidade
Logs devem ajudar no diagnóstico sem vazar:
- tokens;
- senhas;
- cookies/sessões;
- chaves;
- payloads sensíveis completos.

Registrar eventos administrativos críticos quando isso for relevante para rastreabilidade.

## Dependências
- Reutilizar dependências existentes quando adequadas.
- Não instalar pacote apenas para tarefa trivial.
- Evitar biblioteca abandonada ou desnecessariamente privilegiada.
- Mudança de dependência de segurança deve ser escopada e validada.

## Infraestrutura
- Serviços administrativos não devem ficar publicamente expostos sem necessidade.
- Usar HTTPS/TLS nas comunicações externas.
- Restringir portas e serviços ao necessário.
- Containers/processos não devem receber privilégios maiores que os exigidos.
- Health checks públicos devem retornar apenas informações operacionais não sensíveis.

## Regra para correções
Nunca resolver bug de permissão por:
- desabilitar RLS;
- tornar bucket privado em público sem necessidade;
- remover autenticação;
- liberar endpoint inteiro;
- colocar segredo no frontend;
- transformar usuário comum em administrador.

Investigue e corrija a autorização específica que está falhando.

## Validação mínima
Após alteração de segurança, validar:
1. acesso permitido funciona;
2. acesso não permitido continua bloqueado;
3. nenhum segredo aparece no cliente/log;
4. dados de outro usuário/papel não ficam acessíveis;
5. erro não revela informação sensível.

Amplie os testes somente se a mudança tiver impacto transversal ou estiver em etapa final de entrega.

## Integração com outras Skills
- Supabase: `../supabase/SKILL.md`
- Lovable: `../lovable/SKILL.md`
- Testing: `../testing/SKILL.md`
- PWA: `../pwa/SKILL.md`
- Padrão global: `../efcsys-standard/SKILL.md`

Consulte `../../shared/security-rules.md` quando precisar das regras resumidas compartilhadas.
