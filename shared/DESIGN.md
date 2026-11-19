# DESIGN — Base global EFCsys

## O que o padrão EFCsys define
Qualidade: desempenho mobile, responsividade (375px–1280px), acessibilidade AA, PWA, estados (carregando, vazio, erro, sucesso, sem permissão), consistência de componentes e assinatura **by: efcsys**.

## O que o padrão EFCsys NÃO define
Paleta, fontes e estética. Isso sai do **cliente**: logo, materiais, setor, público. Dois clientes EFCsys não devem parecer o mesmo produto com outra cor.

## Ordem de decisão
1. Briefing do assunto e do público (`skills/design-direction`).
2. Identidade do cliente (cores reais do logo, formas, tom).
3. Um elemento memorável ligado ao assunto.
4. Regras de qualidade (`skills/ui-ux`).
5. Perfil visual registrado no projeto (`templates/new-project/ux-profile.md`).

## Sensação desejada
Moderno, profissional, rápido no celular, refinado **sem excesso de efeitos**. Animação é acabamento, não o produto.

## Proibido por padrão (sinais de IA genérica)
Fundo escuro com bolhas/aurora; degradês decorativos; texto em degradê; uma palavra destacada no título; glassmorphism; brilho neon; rótulo em maiúsculas acima de todo título; numeração 01/02/03 sem sequência real; kit de cartões iguais com brilho no canto; faixa de estatísticas no hero; pills em metadado estático; ícone decorativo em input; ilustração cartoon em vazio; fade em toda seção; fundos animados em loop.
Lista completa e exceções: `skills/design-direction/SKILL.md`.

## ColorBends / React Bits
Opcional e pontual. Considerar quando combina com a marca; nunca como fundo padrão de hero/login; cor do cliente; uma tela de destaque por produto; fallback estático e `prefers-reduced-motion`.

Presets disponíveis (adaptar a cor ao cliente):

| Preset | Cor | speed | freq | noise | band | rot | fadeTop | iter | int | Uso |
|---|---|---|---|---|---|---|---|---|---|---|
| Laranja | #F97316 | 0.4 | 1.8 | 0.18 | 0.22 | 115 | 0.70 | 1 | 1.4 | campanhas, eventos |
| Roxo | #A855F7 | 0.2 | 1.0 | 0.15 | 0.14 | 90 | 0.75 | 1 | 1.3 | premium, tecnologia |
| Verde | #10B981 | 0.3 | 1.5 | 0.08 | 0.30 | 60 | 0.80 | 2 | 1.1 | confirmação, financeiro |
| Ciano | #06B6D4 | 0.1 | 1.2 | 0.06 | 0.40 | 45 | 0.95 | 2 | 1.1 | fundos discretos |
| Rose gold | #C89F8A | 0.2 | 1.1 | 0.10 | 0.26 | 80 | 0.82 | 2 | 1.15 | condomínios, estética |
| Dourado | #D4AF37 | 0.18 | 1.25 | 0.08 | 0.32 | 55 | 0.88 | 2 | 1.2 | luxo, eventos |

## Entregáveis de design em todo projeto
- Plano visual curto (cores, fontes, padrão de página, princípio).
- `ux-profile.md` no projeto.
- Preview/mockup navegável para o cliente validar layout e tipografia.
- Screenshots 375px e 1280px conferidos antes da entrega.
