# PWA — EFCsys

## Objetivo
Garantir que projetos EFCsys configurados como PWA sejam instaláveis, responsivos, atualizáveis e seguros, sem comprometer o funcionamento normal na web.

## Quando usar
Use para manifest, ícones, instalação, standalone, splash/launch, service worker, cache, atualização, offline e comportamento específico de PWA.

## Regra central
PWA é uma camada adicional da aplicação. O sistema deve continuar funcionando corretamente como site quando instalação ou recursos PWA não estiverem disponíveis.

Não adicionar complexidade offline sem necessidade real do produto.

## Manifest
Validar, quando aplicável:
- `name`;
- `short_name`;
- `start_url`;
- `scope`;
- `display`;
- `theme_color`;
- `background_color`;
- ícones adequados.

Os valores devem refletir o produto real e não nomes/defaults de template.

## Ícones
- Fornecer tamanhos necessários para os ambientes suportados.
- Evitar texto pequeno dentro do ícone.
- Manter logo/símbolo legível em tamanho reduzido.
- Quando o padrão visual EFCsys for adotado, preferir apresentação circular.
- Considerar ícone `maskable` quando a plataforma suportar.
- Não substituir identidade aprovada do cliente apenas para seguir padrão global.

## Instalação
- Não bloquear o uso do sistema para forçar instalação.
- Mostrar ação de instalar somente quando fizer sentido e o navegador permitir.
- Evitar repetir convite de instalação de forma intrusiva.
- Após instalação, preservar rota inicial e autenticação esperadas.
- Não afirmar que o app está instalado apenas porque o manifest existe.

## Standalone
No modo instalado:
- navegação essencial deve continuar disponível;
- links internos não devem abrir navegador externo sem necessidade;
- áreas seguras/notches devem ser consideradas quando relevantes;
- elementos fixos não devem ser cortados;
- teclado virtual não deve tornar formulários inutilizáveis;
- retorno/fechamento deve seguir comportamento previsível da plataforma.

## Splash / launch
- Usar identidade visual do produto.
- Evitar splash longa que atrase acesso ao sistema.
- Quando houver experiência de splash controlada pelo app, usar aproximadamente até 3 segundos como referência, não como espera obrigatória.
- Não manter splash artificialmente se a aplicação já estiver pronta.
- Loading real deve ser tratado separadamente da animação de entrada.

## Service worker
- Registrar apenas quando necessário e de forma compatível com o ambiente.
- Não duplicar service workers concorrentes.
- Alterações devem considerar usuários que ainda possuem versão anterior ativa.
- Evitar loops de reload.
- Não limpar indiscriminadamente todos os caches/storage do usuário para resolver atualização.
- Mudanças de estratégia devem preservar dados locais necessários.

## Estratégia de cache
Escolher estratégia conforme o tipo de recurso.

### Assets versionados
JS, CSS, fontes e imagens estáticas podem usar cache quando o build/versionamento garantir atualização.

### Conteúdo dinâmico
Dados de usuário, reservas, pagamentos, dashboards e informações que mudam frequentemente não devem receber cache agressivo sem estratégia clara.

### Dados sensíveis
- Não persistir respostas autenticadas/sensíveis em cache público.
- Não tratar cache como mecanismo de autorização.
- Logout deve impedir acesso posterior a conteúdo sensível preservado localmente.

## Atualizações
- Uma nova versão não deve deixar usuários presos indefinidamente na anterior.
- Evitar recarregar durante operação crítica/formulário sem necessidade.
- Quando atualização exigir reload, avisar ou aplicar em momento seguro.
- Remover caches obsoletos de forma controlada.
- Não usar “limpar tudo” como estratégia padrão de atualização.

## Offline
Só implementar experiência offline quando houver necessidade real.

Quando houver:
- distinguir claramente dado local de dado sincronizado;
- não confirmar operação remota antes da sincronização real;
- prever conflito/duplicidade quando ações forem reenviadas;
- informar quando recurso depende de conexão;
- não armazenar segredo desnecessariamente para suportar offline.

Se o produto não exige operações offline, uma página/fallback simples pode ser suficiente.

## Formulários e operações críticas
Para reserva, pagamento, cadastro ou outra gravação:
- evitar reenvio automático que gere duplicidade;
- bloquear submissão repetida enquanto a primeira estiver em andamento;
- usar idempotência no backend quando necessário;
- não exibir sucesso antes da confirmação real da operação.

## Autenticação
- A sessão deve continuar coerente entre modo web e standalone.
- Não criar autenticação paralela específica para PWA sem necessidade.
- Logout deve limpar estado de sessão apropriado.
- Expiração de sessão deve levar o usuário ao fluxo correto, não a tela quebrada/cache antigo.

## Push notifications
Quando usadas:
- pedir permissão em contexto compreensível, não automaticamente na primeira renderização;
- explicar utilidade antes da solicitação quando apropriado;
- respeitar recusa;
- não depender de push como único canal para informação crítica;
- evitar conteúdo sensível excessivo na notificação.

## Responsividade
Aplicar também a Skill UI/UX.

Em PWA, atenção especial a:
- safe areas;
- orientação/tamanho de tela;
- navegação inferior;
- elementos fixos;
- teclado virtual;
- fullscreen/standalone;
- gestos que possam conflitar com a interface.

## Performance
- Não pré-carregar mídia pesada sem necessidade.
- Otimizar imagens e assets relevantes.
- Evitar cache duplicado de grandes recursos.
- Carregar funcionalidades pesadas sob demanda quando fizer sentido.
- PWA não deve piorar significativamente o primeiro carregamento apenas para oferecer instalação.

## Segurança
- Usar HTTPS em produção.
- Não colocar tokens privados/segredos no manifest, service worker ou bundle.
- Não cachear conteúdo sensível de forma insegura.
- Aplicar `../security/SKILL.md` quando houver autenticação, dados pessoais ou operações privilegiadas.

## Validação mínima
Após mudança PWA, validar somente o escopo afetado:
1. aplicação continua funcionando no navegador;
2. manifest permanece válido;
3. modo standalone não perde navegação essencial;
4. atualização não cria loop/cache obsoleto;
5. dados dinâmicos/sensíveis não ficaram cacheados inadequadamente;
6. mobile não apresenta corte/overflow causado pela mudança.

## Validação pré-entrega
Quando o PWA estiver pronto para liberação:
- instalação em ambiente suportado;
- ícone/nome corretos;
- abertura standalone;
- autenticação;
- atualização de versão;
- comportamento com conexão instável/offline conforme escopo;
- operações críticas sem duplicidade;
- responsividade essencial.

## Integração com outras Skills
- UI/UX: `../ui-ux/SKILL.md`
- Security: `../security/SKILL.md`
- Testing: `../testing/SKILL.md`
- Lovable: `../lovable/SKILL.md`
- Padrão global: `../efcsys-standard/SKILL.md`
