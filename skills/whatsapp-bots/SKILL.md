# WhatsApp Bots — EFCsys

## Objetivo
Padronizar criação, implantação e manutenção de bots WhatsApp EFCsys com foco em estabilidade, segurança, baixo consumo de recursos e diagnóstico simples.

## Quando usar
Use para bots WhatsApp, sessões/conexão, filas, polling, lembretes, notificações, endpoints de conexão/status/health e integração do bot com sistemas EFCsys.

## Princípios
- A operação principal do sistema não deve falhar apenas porque uma notificação WhatsApp falhou.
- Mensagens recebidas são entrada não confiável.
- Sessões, credenciais e tokens nunca devem ser versionados ou expostos em logs.
- Evitar duplicidade de mensagens e processamento.
- Reutilizar infraestrutura e padrões existentes antes de criar novos serviços.

## Conexão
- Manter estado explícito: conectado, desconectado, conectando ou aguardando pareamento.
- Não criar múltiplas conexões concorrentes para a mesma sessão.
- Reconexão deve possuir controle para evitar loop agressivo.
- QR/pairing code deve ser exposto somente pelo tempo e contexto necessários.
- Não registrar conteúdo sensível da sessão.

## Endpoints
Quando aplicável:
- `/health`: saúde mínima do serviço;
- `/status`: estado operacional do bot;
- endpoint de conexão/pareamento somente com proteção adequada.

Health check deve ser leve e não depender de operação externa cara.

Não retornar credenciais, tokens, sessão completa ou dados pessoais nos endpoints.

## Processamento
- Bloquear processamento concorrente quando puder gerar duplicidade.
- Usar idempotência/chave de evento quando necessário.
- Polling deve impedir nova execução se a anterior ainda estiver ativa.
- Intervalos devem ser configuráveis quando fizer sentido.
- Falha em um item não deve interromper toda a fila sem necessidade.
- Registrar tentativa/erro suficiente para reprocessamento seguro.

## Notificações
- Respeitar preferências do usuário/projeto.
- Não enviar mensagem duplicada para o mesmo evento.
- Diferenciar evento criado, enviado, entregue e falho quando o projeto exigir.
- Reprocessamento deve ter limite/backoff apropriado.
- Uma falha de WhatsApp não deve reverter reserva/pagamento/operação principal já confirmada, salvo regra explícita do produto.

## Integração com backend
- O backend do produto continua sendo fonte de verdade.
- Bot não deve inventar estado de reserva, pagamento ou cadastro.
- Validar payloads e respostas da API.
- Não marcar operação como concluída apenas porque a mensagem foi enviada.
- Proteger endpoints usados pelo bot com autenticação adequada.

## Recursos
- Monitorar memória, CPU, uptime e reinícios quando houver suspeita de lentidão.
- Evitar polling excessivo.
- Não manter objetos/mensagens indefinidamente em memória.
- Em servidor pequeno, limitar serviços concorrentes e investigar swap/pressão de memória antes de culpar o cliente.
- Reiniciar container não substitui correção da causa de vazamento ou loop.

## Logs
Registrar de forma objetiva:
- conexão/desconexão;
- falha de autenticação;
- início/fim de ciclos relevantes;
- erros de API;
- reprocessamentos.

Não registrar:
- credenciais;
- conteúdo integral de sessão;
- tokens;
- senhas;
- dados pessoais completos sem necessidade.

## Docker
- Executar como serviço/container independente quando essa for a arquitetura do projeto.
- Definir restart policy adequada.
- Usar healthcheck.
- Persistir apenas os volumes realmente necessários.
- Não embutir segredos na imagem.
- Fixar versões relevantes quando atualização inesperada puder quebrar conexão.

## Validação mínima
1. serviço inicia sem erro;
2. health responde;
3. estado de conexão é coerente;
4. uma mensagem/evento de teste percorre o fluxo previsto quando teste real for necessário;
5. falha externa não corrompe operação principal;
6. não há duplicidade;
7. logs não expõem segredos.

Não repetir testes de pareamento/envio quando a integração já estiver validada e a mudança não afetar esse fluxo.

## Integração com outras Skills
- Security: `../security/SKILL.md`
- Testing: `../testing/SKILL.md`
- Oracle Deploy: `../oracle-deploy/SKILL.md`
- EFCsys Standard: `../efcsys-standard/SKILL.md`
