# Shard Cloud Deploy — EFCsys

## Objetivo
Padronizar a publicação de apps e bots EFCsys na Shard Cloud a partir do GitHub, com imagem Docker, segredos fora do código e diagnóstico simples.

## Quando usar
Use para criar, publicar, atualizar, reiniciar ou diagnosticar uma Aplicação na Shard Cloud, incluindo Dockerfile, variáveis de ambiente, plano de memória e ligação com o repositório GitHub.

## Não usar
- Servidores Oracle/VM com Docker Compose: use `oracle-deploy`.
- Banco, Auth e RLS: use `supabase`.
- Lógica do bot WhatsApp: use `whatsapp-bots`.

## Modelo adotado
- Cada app ou bot é uma **Aplicação** da Shard Cloud, construída a partir de um `Dockerfile` do repositório GitHub.
- Código no GitHub; banco no Supabase; segredos apenas no painel da Shard Cloud.
- A VPS é plano B. Não usar IP fixo ou VPS sem motivo registrado no projeto.

## Princípios
- Não copiar `.env`, tokens ou sessões de WhatsApp para a imagem.
- Imagem enxuta: instalar só dependências de produção; usar `.dockerignore` para `node_modules`, `.git`, `.env` e arquivos de sessão locais.
- Versão do Node fixada na imagem (ex.: `node:<versão LTS>-slim`), sem `latest`.
- Processo principal escuta na porta definida por variável de ambiente (`PORT`), não em porta fixa.
- Health check leve (`/health`), sem chamadas externas caras.
- Um processo por Aplicação. Bots que usam navegador consomem muita RAM; planejar a memória antes.

## Planejamento de memória
- Plano atual de referência: Core com 6 GB, dividido entre os bots.
- Bot com navegador (Puppeteer/Playwright): estimar cerca de 2 GB por instância; verificar antes de subir mais de um.
- Se a soma das Aplicações passar do limite do plano, escolher entre subir de plano (8 GB ou Pro) ou reduzir instâncias. Não reduzir a estabilidade do bot para caber.

## Variáveis de ambiente
- Cadastrar no painel da Shard Cloud, nunca no repositório.
- Documentar no README do projeto apenas os **nomes** das variáveis e para que servem.
- Trocar qualquer segredo que tenha sido exposto em chat, commit ou log.

## Passo a passo de publicação
1. Confirmar que o repositório tem `Dockerfile`, `.dockerignore` e `/health`.
2. Criar a Aplicação na Shard Cloud ligada ao repositório GitHub e à branch de produção.
3. Cadastrar as variáveis de ambiente no painel.
4. Definir o plano de memória conforme o planejamento acima.
5. Publicar e aguardar o build; conferir os logs de build e de execução.
6. Testar `/health` e o fluxo crítico do app ou do bot.
7. Registrar na memória do projeto a URL, o plano usado e a data.

## Diagnóstico
Ordem de verificação:
1. Logs de build: falha de dependência ou de Dockerfile.
2. Logs de execução: erro de variável ausente ou porta errada.
3. Uso de memória da Aplicação: reinícios por falta de RAM indicam plano insuficiente ou instância a mais.
4. Conexão externa (Supabase, WhatsApp, APIs): só depois de descartar os itens anteriores.

## Atualização e rollback
- Atualizar pelo push na branch de produção, com testes locais antes.
- Manter a versão anterior disponível para voltar caso o health check falhe.
- Mudança de schema no Supabase deve ser aplicada antes ou junto com a versão do código que a usa.

## Limites
- Não afirmar que a Aplicação está no ar sem health check e teste real.
- Os nomes de campos e menus do painel da Shard Cloud devem ser conferidos na própria interface, porque podem mudar.
- Não expor endpoints administrativos sem autenticação.
