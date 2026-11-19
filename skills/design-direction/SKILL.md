# Design Direction — EFCsys

## Objetivo
Evitar interfaces com "cara de IA genérica". Toda interface EFCsys deve parecer feita **para aquele cliente e aquele assunto**, e não sair de um template reaproveitado.

## Quando usar
Sempre que houver:
- projeto novo ou migração com redesign (ex.: sair do Lovable e refazer layout);
- nova página pública, landing ou tela principal;
- pedido de "refazer o visual", "melhorar o layout", "mudar a tipografia";
- primeira tela de um módulo novo.

Não usar para ajuste localizado (botão, espaçamento, um campo). Nesses casos basta `../ui-ux/SKILL.md`.

## Regra central
**A identidade do cliente vem antes do padrão EFCsys.** O padrão EFCsys define qualidade (desempenho, acessibilidade, responsividade, PWA, estados). Ele **não** define paleta, fonte nem estética. Isso sai do logo, do assunto e do público do cliente.

## Processo obrigatório (antes de escrever código)

### 1. Briefing do assunto
Responder em 3 linhas:
- **O que é o produto** e qual o trabalho principal da tela (ex.: "gerenciar eventos dos artistas; a página pública é o extra para o fã").
- **Quem usa** cada parte (admin no dia a dia, público no celular, portaria, cliente final).
- **De onde vem a identidade**: logo, materiais e vocabulário do setor (ingresso, palco, cartaz, obra, condomínio, barbearia).

Se faltar informação, propor o briefing e confirmar com o usuário.

### 2. Extrair a identidade
- Ler o logo e os materiais do cliente: cores reais (hex), formas (arredondado, reto, recortado), tom (alegre, sóbrio, luxuoso, técnico).
- Listar **1 a 3 elementos próprios do assunto** que podem virar linguagem visual. Exemplos: canhoto picotado de ingresso, faixa de cartaz, carimbo, planta baixa, régua técnica, recibo.
- Escolher **um** elemento memorável. O resto da interface fica quieto.

### 3. Plano visual (curto, no chat ou no projeto)
- **Cores:** 4 a 6 hex nomeados, com papel definido (fundo, superfície, texto, destaque único, apoio). Regra 60-30-10: 60% fundo, 30% superfícies estruturais, 10% destaque.
- **Tipografia:** 1 ou 2 famílias, com papel claro (títulos / interface). Dizer **por que** combinam com o assunto. Escala definida (veja `../ui-ux/SKILL.md`).
- **Layout:** padrão de página nomeado (lista, detalhe, formulário, dashboard, calendário, configurações, landing) e um esboço ASCII das telas principais.
- **Princípio único:** uma frase que diga o que torna esta interface diferente.

### 4. Revisão anti-genérico (antes de construir)
Comparar o plano com a lista abaixo. Se algum item aparece **sem um motivo específico do cliente**, trocar e registrar o que mudou.

### 5. Construir, fotografar, cortar
- Construir seguindo o plano.
- Tirar screenshots em **375px e 1280px** de cada tela alterada (navegador headless/preview).
- Avaliar pela imagem, não pelo código: hierarquia, 60-30-10, legibilidade, se lembra o assunto do cliente.
- "Tirar um acessório": remover pelo menos um enfeite antes de entregar.
- Gerar o preview/mockup navegável para o cliente validar.

## Sinais de interface genérica (proibidos por padrão)
Só usar quando o briefing do cliente justificar explicitamente.

**Cor e fundo**
- Fundo roxo/azul escuro com bolhas ou manchas borradas, mesh gradient ou "aurora" atrás do conteúdo.
- Degradê violeta → magenta → laranja em botões, títulos ou fundos.
- Texto em degradê (`background-clip: text`) em títulos.
- Uma única palavra do título destacada em outra cor, itálico ou degradê.
- Glassmorphism (`backdrop-filter`) sem borda de alto contraste; barra lateral translúcida.
- Brilho neon em bordas/cartões; sombra pesada; sombra + degradê + blur no mesmo componente.
- Fundo creme com serifa e destaque terracota; preto com um único verde-ácido — estéticas "padrão IA".

**Tipografia e rótulos**
- Rótulo pequeno em MAIÚSCULAS espaçadas acima de todo título (eyebrow em toda seção).
- Mais de 3 pesos de fonte; pesos acima de 700.
- Textos de interface abaixo de 12px; tabela inteira em 12px.
- Fontes "padrão" escolhidas por hábito (Inter, Poppins, Sora, Outfit...) sem justificativa ligada ao assunto.
- Metadados unidos por "·" em toda linha; "→" no fim de todo link/botão.

**Estrutura**
- Numeração "01 / 02 / 03" quando o conteúdo não é uma sequência real.
- Kit de cartões SaaS: tudo cortado em cartões iguais, mesmo raio, mesma sombra, brilho no canto.
- Bento grid de recursos genérico; faixa de "estatísticas" no hero (número grande + rótulo).
- Pills/etiquetas arredondadas em metadado estático (data, autor, cidade).
- Ícone decorativo dentro de todo input (permitido só: busca, limpar, mostrar senha).
- Ilustração de pessoas cartoon em estado vazio; spinner gigante centralizado como estado vazio.

**Movimento**
- Fade + slide em toda seção ao rolar; hover animado em todo cartão.
- Fundos animados em loop infinito (inclui ColorBends usado como "hero padrão").
- Bounce, elastic, spring em botões, menus e diálogos.

## ColorBends / React Bits
- É **opcional**. Usar só quando o efeito combina com a marca do cliente e adiciona algo que uma imagem/cor sólida não daria.
- Nunca como fundo automático de hero ou login.
- Cor sempre derivada do cliente, nunca o roxo do preset por padrão.
- Máximo **um** uso por produto, em uma tela de destaque, com fallback estático e `prefers-reduced-motion`.

## Critério de aprovação
A interface passa quando:
1. alguém que conhece o cliente reconhece a marca sem ver o logo;
2. nenhum sinal da lista aparece sem justificativa registrada;
3. existe um elemento memorável ligado ao assunto, e só um;
4. screenshots em 375px e 1280px estão legíveis e sem overflow;
5. `../ui-ux/SKILL.md` (validação) passou.

## Integração
- Regras de qualidade de UI: `../ui-ux/SKILL.md`
- Perfil visual por projeto: `../../templates/new-project/ux-profile.md`
- Padrão compartilhado: `../../shared/DESIGN.md`
- Plugin opcional recomendado: **VectorLab UI/UX Skills** (`anti-slop`, `typography`, `colour-palette`, `ux-audit`). Quando instalado, rodar `ux-audit` antes de entregar.
