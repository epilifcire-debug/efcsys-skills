# UI/UX — EFCsys

## Objetivo
Criar interfaces EFCsys consistentes, responsivas, acessíveis e fáceis de usar, preservando a identidade aprovada de cada projeto e evitando redesigns desnecessários.

## Quando usar
Use para páginas, componentes, formulários, navegação, dashboards, responsividade, acessibilidade, feedback visual, estados da interface e ajustes de experiência.

## Regra central
Antes de criar um novo padrão visual, reutilize o design system, componentes, tokens e comportamento já existentes no projeto.

Não alterar identidade visual aprovada quando a tarefa não exigir isso.

**Interface nova, redesign ou página principal:** aplicar antes `../design-direction/SKILL.md` (briefing, identidade do cliente, plano visual e revisão anti-genérico). Se o projeto tiver `ux-profile.md`, ler antes de mexer em layout, cor ou tipografia.

## Padrão de página
Antes de escrever uma página nova, nomear qual padrão ela é: **lista, detalhe, formulário, dashboard, calendário, configurações, quadro (board), landing/pública**. Uma página é um padrão só; componentes (gráficos, KPIs, vazios) ficam dentro dele. Trocar visualização (lista ↔ calendário) dos mesmos dados é a mesma página com alternância.

## Hierarquia de reutilização
1. componente existente;
2. variante do componente existente;
3. token/padrão já usado no projeto;
4. novo componente somente quando necessário.

Evitar componentes visualmente diferentes para a mesma função.

## Responsividade
A interface deve funcionar em mobile e desktop.

- Priorizar experiência mobile quando o produto for usado principalmente em celular.
- Não apenas reduzir desktop: reorganizar conteúdo quando necessário.
- Evitar overflow horizontal acidental.
- Garantir que modais, tabelas, calendários e menus sejam utilizáveis em telas menores.
- Elementos fixos não devem esconder conteúdo.
- Navegação mobile deve exigir o menor número razoável de ações.
- Validar em **375px e 1280px**: sem rolagem horizontal da página (tabelas podem rolar dentro da própria área).
- Barra lateral fixa não aparece em 375px: vira menu ou navegação inferior.
- Área de toque mínima 44×44px; ícone de 16px não é área de toque.
- Ação que só aparece no hover precisa de caminho visível sem hover.

Quando uma navegação inferior for mais adequada ao uso móvel do que sidebar/hambúrguer, considerar esse padrão sem alterar desktop desnecessariamente.

## Navegação
- Destacar claramente a seção atual.
- Manter ações principais fáceis de encontrar.
- Evitar duplicar caminhos para a mesma ação sem benefício.
- Não esconder função frequente atrás de menus desnecessários.
- Preservar botão voltar/contexto quando a navegação exigir.
- Papéis diferentes devem ver apenas navegação pertinente às suas permissões.

## Formulários
- Label clara para cada campo.
- Placeholder não substitui label quando a identificação do campo for necessária.
- Mostrar campos obrigatórios de forma consistente.
- Validar próximo ao campo e explicar como corrigir.
- Preservar dados digitados após erro sempre que possível.
- Desabilitar envio repetido enquanto a operação estiver processando.
- Aplicar máscaras de CPF, telefone, moeda, CEP ou data quando relevantes ao projeto.
- Validar ao sair do campo (blur), nunca enquanto a pessoa digita pela primeira vez; limpar o erro assim que ela começar a corrigir.
- Botão de enviar nunca fica desabilitado por formulário incompleto: ao clicar, rolar até o primeiro erro e mostrar a mensagem no campo.
- Placeholder só para exemplo de formato (`nome@empresa.com`, `(79) 99999-0000`), nunca no lugar do label.
- Preencher padrões inteligentes (cidade/UF pelo CEP, fuso, última escolha) em vez de select vazio.
- Rascunho de formulário longo não se perde em refresh/navegação acidental.
- Teclado/tipo de input deve combinar com o dado no mobile.
- Não pedir informação que o sistema já possui sem necessidade.

## Botões e ações
- Uma ação primária visualmente dominante por contexto quando possível.
- Diferenciar ações destrutivas das normais.
- Pedir confirmação para exclusões/ações irreversíveis relevantes.
- Evitar botões sem estado de loading quando a ação demora.
- Bloquear clique duplo quando puder gerar duplicidade.
- Ícones sem texto precisam de significado claro e tooltip/label acessível quando necessário.
- Botão só com ícone: quadrado, `aria-label` e tooltip real (não `title`) com o mesmo texto da ação.
- Texto de botão começa com verbo e diz o que acontece: "Salvar artista", "Publicar evento", "Conectar Google". Proibido: "OK", "Enviar", "Prosseguir" genéricos.
- A mesma ação mantém o mesmo nome em todo o fluxo ("Publicar" → aviso "Publicado").
- Confirmação de exclusão nomeia o item ("Excluir o evento 'Festival Luar'?"), botão de confirmação com verbo destrutivo em cor de erro, foco inicial em "Cancelar", Esc fecha sem executar.
- Tarefa curta (menos de ~10s) abre em painel lateral/inline; tarefa longa ganha página própria. Nunca empilhar modal sobre modal.

## Estados obrigatórios
Componentes que carregam dados devem prever, quando aplicável:
- loading;
- vazio;
- sucesso;
- erro;
- sem permissão;
- indisponível/offline.

Nunca usar dados fictícios para esconder estado vazio real.

### Vazio
Todo estado vazio tem: título dizendo o que fica ali, uma frase sobre o valor de preencher e um botão para criar/importar. Busca/filtro sem resultado inclui "Limpar filtros". Sem ilustração cartoon. O esqueleto da página continua (lista mostra cabeçalho, busca e moldura da tabela).

### Carregamento
- Menos de 100ms: nenhum indicador.
- 100ms a 1s: indicador no próprio botão/controle que disparou.
- Mais de 1s em bloco de conteúdo: skeleton com o formato do conteúdo. Nunca spinner gigante centralizado.

### Erro
Mensagem em até duas frases: o que aconteceu, o que isso afeta e como resolver. Nunca culpar o usuário ("E-mail inválido" → "Use um e-mail como nome@dominio.com"). Erro técnico: botão "Copiar detalhes" em vez de stack trace ou código HTTP na tela.

## Feedback
Após ação importante, deixar claro:
- que a ação começou;
- se terminou;
- se teve sucesso ou erro;
- qual é o próximo estado relevante.

Evitar animação que faça o usuário esperar sem necessidade.

## Movimento
Movimento responde a uma ação da pessoa (abrir, expandir, confirmar, mostrar o que mudou) ou marca **um** momento orquestrado da página. Não é decoração.

- Durações apenas: 100, 150, 200 ou 300ms. Entrada com ease-out, saída com ease-in.
- Animar só `transform` e `opacity`; nunca largura, altura, margem, posição.
- Proibido: fade/slide em toda seção ao rolar, hover animado em todo cartão, loop infinito decorativo, bounce/elastic em botões, menus e diálogos.
- Cascata de lista: até 30ms por item, total ~200ms.
- Abrir/fechar não empurra o conteúdo ao lado (reservar espaço).
- `prefers-reduced-motion`: troca instantânea ou só opacidade ≤150ms; sem translate, scale ou parallax.
- Significado nunca depende só de movimento: sempre há texto, ícone ou cor junto.
- Parallax, Ken Burns e fundos animados (ColorBends) só com justificativa em `../design-direction/SKILL.md`.

## Tipografia
- Fonte escolhida pelo assunto e pela marca do cliente, nunca por hábito. Registrar o motivo no plano visual.
- 1 ou 2 famílias; se forem 2, claramente diferentes entre si (ex.: uma condensada para títulos e uma neutra para interface).
- Máximo 3 pesos no app (ex.: 400 / 500 / 600); nada acima de 700. Hierarquia vem de tamanho e espaço, não de peso.
- Tamanhos base: corpo 16px, secundário 14px, meta 12px. Nada abaixo de 12px. Conteúdo principal (linhas de tabela, cartões, valores) é 14–16px; 12px só para data, legal, atalho.
- Títulos por escala modular fixa (1.125 para telas densas, 1.2 para páginas mais editoriais). No máximo 4–5 tamanhos por tela.
- Altura de linha: títulos 1.1–1.25; corpo 1.5–1.6.
- Espaçamento negativo só em títulos ≥32px (−0.01 a −0.02em).
- Linha de texto corrido entre 65 e 75 caracteres.
- Sentence case em botões e rótulos. Evitar rótulos em MAIÚSCULAS espaçadas e rótulo acima de todo título.
- Quando o projeto oferecer escolha de tipografia, manter opções controladas e consistentes, sem alterar layout de forma imprevisível.

## Cores e contraste
- Paleta derivada da marca do cliente (logo/materiais), com 4–6 cores nomeadas.
- Distribuição 60-30-10 conferida em screenshot: 60% fundo, 30% superfícies (cartões, barra lateral), 10% destaque.
- Um destaque principal para ações, links ativos e foco. As outras cores da marca entram como apoio com papel definido (status, categoria, artista), não como decoração.
- Profundidade: borda de 1px sutil primeiro; sombra só suave (alpha < 0.08 no claro). Escuro: realce de borda superior, sem brilho externo.
- Lista/tabela fica sobre uma superfície (borda ou fundo um passo acima) com divisórias finas; texto solto sobre o fundo é falha.
- Sem degradê decorativo em botões, títulos ou fundos de tela; sem glassmorphism.
- Usar tokens/paleta do projeto.
- Não introduzir cores arbitrárias para resolver estados.
- Estados como sucesso, aviso, erro e informação devem ser distinguíveis.
- Não depender somente de cor para transmitir informação importante.
- Garantir contraste adequado para texto e controles.

## Cards, tabelas e dashboards
- Exibir primeiro a informação mais importante.
- Não sobrecarregar cards com métricas secundárias.
- Tabelas no mobile devem adaptar layout, permitir rolagem controlada ou apresentar formato alternativo.
- Filtros devem indicar claramente quando estão ativos.
- KPIs sem dados reais devem mostrar zero/estado vazio apropriado, nunca números simulados.
- Gráficos precisam de contexto, unidade e rótulos suficientes para interpretação.

## Calendários e agendas
- Estado selecionado deve ser evidente.
- Datas indisponíveis/bloqueadas devem ser visualmente distintas.
- Não permitir interação com opção indisponível apenas para exibir erro depois.
- No mobile, preservar área de toque e legibilidade.
- Manter coerência entre calendário e lista quando ambos existirem.

## Modais, drawers e overlays
- Devem possuir forma clara de fechar.
- Não bloquear conteúdo permanentemente por erro.
- Manter foco/teclado acessíveis quando aplicável.
- Em mobile, considerar drawer/bottom sheet quando melhorar a experiência.
- Não empilhar vários modais sem necessidade.

## Imagens e mídia
- Preservar proporção e evitar distorção.
- Usar crop/cover somente quando adequado.
- Prever fallback quando mídia não carregar.
- Não carregar mídia pesada sem necessidade.
- Fotos de perfil/logos devem manter apresentação consistente no sistema.

## Acessibilidade
No mínimo:
- navegação por teclado quando aplicável;
- foco visível;
- labels acessíveis;
- contraste suficiente;
- áreas de toque adequadas;
- texto alternativo para imagens informativas;
- não depender apenas de cor;
- mensagens de erro compreensíveis.

Acessibilidade deve fazer parte do componente, não ser tratada somente no final.

## PWA visual
Quando o projeto for PWA:
- ícone deve permanecer legível nos tamanhos suportados;
- quando o padrão EFCsys for adotado, preferir ícone de apresentação circular;
- splash/launch deve respeitar a identidade do produto;
- evitar splash excessivamente longa; quando houver experiência controlada, referência aproximada de até 3 segundos;
- standalone não deve perder navegação essencial.

Aplicar também `../pwa/SKILL.md` para comportamento técnico.

## Preservação
Uma tarefa de UI não autoriza automaticamente:
- trocar paleta;
- trocar tipografia;
- reorganizar todas as páginas;
- substituir biblioteca de componentes;
- alterar fluxo funcional;
- criar animações em todo o sistema.

Faça somente o necessário para resolver a solicitação.

## Teclado e foco
- Tudo que funciona com mouse funciona com Tab, Shift+Tab, Enter e Espaço.
- Nunca `outline: none` sem substituto visível no claro e no escuro.
- Modal/painel lateral prende o foco dentro e devolve ao botão que abriu ao fechar; Esc fecha.

## Validação mínima
Após mudança visual:
1. testar o componente/fluxo alterado;
2. **screenshot em 375px e 1280px** e avaliar pela imagem (não só pelo código);
3. verificar overflow, corte e sobreposição;
4. testar loading/empty/error se afetados;
5. confirmar que a ação principal continua clara;
6. verificar foco/label/área de toque quando houver interação;
7. em tela nova ou redesign: conferir a lista de sinais genéricos de `../design-direction/SKILL.md`.

Se o plugin VectorLab UI/UX estiver instalado, rodar `ux-audit` antes de declarar a interface pronta.

Não executar auditoria visual completa após ajuste localizado.

## Integração com outras Skills
- Lovable: `../lovable/SKILL.md`
- Design Direction: `../design-direction/SKILL.md`
- Testing: `../testing/SKILL.md`
- PWA: `../pwa/SKILL.md`
- Security: `../security/SKILL.md`
- Padrão global: `../efcsys-standard/SKILL.md`

Consulte `../../shared/DESIGN.md` somente quando precisar do padrão de design compartilhado.
