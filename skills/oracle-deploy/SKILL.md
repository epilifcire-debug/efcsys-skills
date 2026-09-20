# Oracle Deploy — EFCsys

## Objetivo
Padronizar implantação e operação de serviços EFCsys em VMs Oracle Cloud/Linux com Docker, priorizando segurança, estabilidade e diagnóstico simples.

## Quando usar
Use para provisionamento de VM, Ubuntu/Linux, Docker/Compose, containers, portas, firewall, health checks, recursos, logs, atualização e recuperação de serviços.

## Princípios
- Expor publicamente somente o necessário.
- Containers devem ser reproduzíveis.
- Configuração e segredos ficam fora da imagem.
- Health check mede saúde; não deve executar tarefa pesada.
- Antes de reiniciar ou recriar infraestrutura, diagnosticar o problema quando possível.

## Preparação da VM
- Atualizar pacotes de segurança relevantes.
- Instalar somente dependências necessárias.
- Usar usuário não-root para administração quando possível.
- Proteger acesso SSH e chaves.
- Manter horário/timezone coerente com a operação quando tarefas dependem de agenda.

## Docker/Compose
- Definir serviços de forma declarativa.
- Usar restart policy adequada.
- Evitar `latest` quando mudança de versão puder causar regressão.
- Mapear somente portas necessárias.
- Preferir bind local `127.0.0.1` quando o serviço for acessado apenas por proxy/túnel/localmente.
- Persistir volumes necessários a sessões/dados.
- Não copiar `.env` ou credenciais para a imagem.

## Portas e rede
- Abrir somente portas necessárias no sistema e na camada de rede/cloud.
- Serviço interno não precisa ficar diretamente acessível pela internet.
- Quando houver proxy HTTPS, manter aplicação interna restrita sempre que possível.
- Não expor endpoint administrativo sem autenticação.

## Health checks
Um endpoint como `/health` deve:
- responder rapidamente;
- indicar se o processo está operacional;
- evitar segredos/dados sensíveis;
- não depender de chamada externa cara.

Health do container e estado da integração externa podem ser informados separadamente quando isso melhorar diagnóstico.

## Recursos
Para diagnosticar lentidão, observar:
- load average;
- memória disponível;
- swap;
- CPU;
- uso por container;
- reinícios;
- logs.

Swap ajuda a evitar encerramento abrupto por falta de memória, mas uso elevado pode causar lentidão e não substitui RAM adequada.

Não concluir que o notebook/cliente é a causa quando o servidor apresenta carga ou pressão de memória.

## Logs
- Usar logs suficientes para diagnóstico.
- Evitar crescimento ilimitado.
- Não registrar senhas, tokens, sessões ou dados pessoais completos.
- Consultar logs do container antes de recriar serviço quando houver falha.

## Atualização
Fluxo preferencial:
1. confirmar estado atual;
2. preservar configuração/volumes necessários;
3. atualizar código/imagem;
4. reconstruir/reiniciar somente serviços afetados;
5. verificar health;
6. verificar logs;
7. testar apenas o fluxo impactado.

Evitar apagar VM/container/volume como primeira tentativa de correção.

## Backup
Quando houver dados persistidos localmente:
- identificar volumes/diretórios críticos;
- realizar backup antes de operação destrutiva;
- confirmar restauração quando a criticidade justificar.

Dados cujo sistema de origem é externo não devem ser duplicados localmente sem necessidade.

## Segurança
- Segredos em `.env`/secret store com permissões adequadas.
- Não versionar `.env`.
- SSH por chave quando disponível.
- HTTPS para tráfego externo.
- Firewall/regras de rede com menor exposição possível.
- Aplicar `../security/SKILL.md`.

## Diagnóstico mínimo
Antes de mudança destrutiva, quando possível verificar:
- `uptime`;
- memória/swap;
- containers ativos;
- health;
- logs recentes.

A partir disso, alterar apenas o componente necessário.

## Validação pós-deploy
1. container está ativo;
2. health está saudável;
3. porta esperada responde no escopo correto;
4. logs não mostram erro recorrente;
5. integração afetada mantém estado esperado;
6. uso de recursos está razoável para a VM.

## Integração com outras Skills
- WhatsApp Bots: `../whatsapp-bots/SKILL.md`
- Security: `../security/SKILL.md`
- Testing: `../testing/SKILL.md`
- EFCsys Standard: `../efcsys-standard/SKILL.md`
