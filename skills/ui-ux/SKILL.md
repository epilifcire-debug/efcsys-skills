# UI/UX — EFCsys

## Objetivo
Criar interfaces EFCsys consistentes, responsivas, acessíveis e fáceis de usar, preservando a identidade aprovada de cada projeto e evitando redesigns desnecessários.

## Quando usar
Use para páginas, componentes, formulários, navegação, dashboards, responsividade, acessibilidade, feedback visual, estados da interface e ajustes de experiência.

## Regra central
Antes de criar um novo padrão visual, reutilize o design system, componentes, tokens e comportamento já existentes no projeto.

Não alterar identidade visual aprovada quando a tarefa não exigir isso.

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
- Teclado/tipo de input deve combinar com o dado no mobile.
- Não pedir informação que o sistema já possui sem necessidade.

## Botões e ações
- Uma ação primária visualmente dominante por contexto quando possível.
- Diferenciar ações destrutivas das normais.
- Pedir confirmação para exclusões/ações irreversíveis relevantes.
- Evitar botões sem estado de loading quando a ação demora.
- Bloquear clique duplo quando puder gerar duplicidade.
- Ícones sem texto precisam de significado claro e tooltip/label acessível quando necessário.

## Estados obrigatórios
Componentes que carregam dados devem prever, quando aplicável:
- loading;
- vazio;
- sucesso;
- erro;
- sem permissão;
- indisponível/offline.

Nunca usar dados fictícios para esconder estado vazio real.

## Feedback
Após ação importante, deixar claro:
- que a ação começou;
- se terminou;
- se teve sucesso ou erro;
- qual é o próximo estado relevante.

Evitar animação que faça o usuário esperar sem necessidade.

## Microinterações
Podem ser usadas com moderação:
- fade;
- slide;
- scale;
- transições suaves;
- cards progressivos;
- parallax leve;
- Ken Burns em imagens apropriadas.

A animação deve apoiar hierarquia/feedback, não prejudicar desempenho ou legibilidade. Respeitar preferência por redução de movimento quando aplicável.

## Tipografia
- Manter escala consistente de títulos, corpo, labels e auxiliares.
- Priorizar legibilidade.
- Evitar excesso de pesos/tamanhos.
- Quando o projeto oferecer escolha de tipografia, manter opções controladas e consistentes, sem alterar layout de forma imprevisível.

## Cores e contraste
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

## Validação mínima
Após mudança visual:
1. testar o componente/fluxo alterado;
2. conferir mobile e desktop relevantes;
3. verificar overflow, corte e sobreposição;
4. testar loading/empty/error se afetados;
5. confirmar que a ação principal continua clara;
6. verificar foco/label/área de toque quando houver interação.

Não executar auditoria visual completa após ajuste localizado.

## Integração com outras Skills
- Lovable: `../lovable/SKILL.md`
- Testing: `../testing/SKILL.md`
- PWA: `../pwa/SKILL.md`
- Security: `../security/SKILL.md`
- Padrão global: `../efcsys-standard/SKILL.md`

Consulte `../../shared/DESIGN.md` somente quando precisar do padrão de design compartilhado.
