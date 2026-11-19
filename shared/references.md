# Referências globais de design (GitHub)

Repositórios mais bem avaliados por tema (estrelas em 19/11/2026). Fonte de regras e padrões, não de estética: a identidade de cada projeto vem do cliente (`skills/design-direction`). Cada design system de cliente pode ter a sua própria seção de referências com o que aproveitar no produto.
## Gosto e direção para agentes de IA
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 197k | [anthropics/skills](https://github.com/anthropics/skills) | Skills oficiais, incluindo `frontend-design`: lista dos vícios de interface gerada por IA e o processo plano → revisão → construção → crítica. |
| 128k | [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) | DESIGN.md de marcas conhecidas: modelo de como escrever um brand book que agentes conseguem seguir. Não copiar a estética de outra marca. |
| 119k | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | Skills de "gosto" para agentes: direção de arte, imagens de referência e checagem no navegador antes de entregar. |
| 4.6k | [VoltAgent/awesome-claude-design](https://github.com/VoltAgent/awesome-claude-design) | 68 inspirações em formato DESIGN.md; útil para comparar estruturas de documento. |

## Checklists de qualidade
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 75k | [thedaviddias/Front-End-Checklist](https://github.com/thedaviddias/Front-End-Checklist) | Checklist de entrega: meta tags, Open Graph da página pública, performance, acessibilidade. |
| 17k | [thedaviddias/Front-End-Performance-Checklist](https://github.com/thedaviddias/Front-End-Performance-Checklist) | Fontes, imagens e bundle leves para a página pública abrir rápido no 4G. |
| 5.4k | [thedaviddias/Front-End-Design-Checklist](https://github.com/thedaviddias/Front-End-Design-Checklist) | Revisão de tipografia, grid, estados e responsividade antes de mostrar ao cliente. |
| 1.2k | [vercel-labs/web-interface-guidelines](https://github.com/vercel-labs/web-interface-guidelines) | Regras objetivas de interação: foco, teclado, toque, formulários, feedback, animação. |

## Coleções de design systems
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 67k | [bradtraversy/design-resources-for-developers](https://github.com/bradtraversy/design-resources-for-developers) | Índice de fontes, ícones, paletas e ferramentas. |
| 26k | [alexpate/awesome-design-systems](https://github.com/alexpate/awesome-design-systems) | Design systems públicos para estudar documentação e organização de tokens. |
| 1.5k | [alphagov/govuk-frontend](https://github.com/alphagov/govuk-frontend) | Referência em formulários, erros e textos claros, testados com usuários reais. |

## Componentes acessíveis (base da interface)
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 129k | [shadcn-ui/ui](https://github.com/shadcn-ui/ui) | Base de componentes do app (já usada). Sempre restilizar com os tokens deste sistema; o visual padrão do shadcn é o "kit SaaS" que queremos evitar. |
| 29k | [tailwindlabs/headlessui](https://github.com/tailwindlabs/headlessui) | Componentes sem estilo e acessíveis (menus, diálogos, abas). |
| 20k | [radix-ui/primitives](https://github.com/radix-ui/primitives) | Primitivos usados pelo shadcn: foco, teclado e ARIA corretos em diálogos, menus e popovers. |
| 16k | [adobe/react-spectrum](https://github.com/adobe/react-spectrum) | React Aria: referência de acessibilidade para seletor de data, calendário e campos. |
| 13k | [emilkowalski/sonner](https://github.com/emilkowalski/sonner) | Avisos (toasts) já usados no app: "Evento publicado", "Link copiado". |
| 8.8k | [emilkowalski/vaul](https://github.com/emilkowalski/vaul) | Gaveta inferior no celular para editar evento sem sair da agenda. |

## Formulários
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 45k | [react-hook-form/react-hook-form](https://github.com/react-hook-form/react-hook-form) | Já instalado: validação no blur (`mode: "onTouched"`), erros por campo, sem travar o botão de enviar. |

## Tipografia
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 21k | [google/fonts](https://github.com/google/fonts) | Origem das duas fontes do sistema (Big Shoulders Display e Onest), com licença OFL. |
| 7.3k | [ubuwaits/beautiful-web-type](https://github.com/ubuwaits/beautiful-web-type) | Guia de fontes open source bem escolhidas e combinações. |

## Cor e contraste
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 5.6k | [argyleink/open-props](https://github.com/argyleink/open-props) | Exemplo de tokens CSS bem nomeados e escalas consistentes. |
| 2.3k | [color-js/color.js](https://github.com/color-js/color.js) | Gerar e validar variações claro/escuro dos tons do logo (OKLCH) e calcular contraste. |
| 2.0k | [evilmartians/oklch-picker](https://github.com/evilmartians/oklch-picker) | Ajustar os tons `-ink` dos status mantendo a mesma família de cor. |
| 595 | [Myndex/SAPC-APCA](https://github.com/Myndex/SAPC-APCA) | Contraste perceptual (APCA), melhor que WCAG 2 para texto claro sobre fundo escuro, como no cartaz. |

## Acessibilidade (testes)
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 7.9k | [dequelabs/axe-core](https://github.com/dequelabs/axe-core) | Teste automático de acessibilidade em cada tela antes da entrega. |
| 3.9k | [a11yproject/a11yproject.com](https://github.com/a11yproject/a11yproject.com) | Checklist de acessibilidade em linguagem simples. |

## Ícones
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 26k | [lucide-icons/lucide](https://github.com/lucide-icons/lucide) | Biblioteca única de ícones do sistema (já usada), traço 1.75. |

## Movimento
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 35k | [motiondivision/motion](https://github.com/motiondivision/motion) | Só se precisar de transições de layout (ex.: ingresso abrindo para detalhes). Respeitar `useReducedMotion`. Hoje CSS resolve. |

## Agenda e calendário
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 21k | [fullcalendar/fullcalendar](https://github.com/fullcalendar/fullcalendar) | Se a agenda ganhar visão de mês/semana com arrastar e soltar. |
| 6.9k | [gpbl/react-day-picker](https://github.com/gpbl/react-day-picker) | Já instalado: seletor de data dos eventos, com locale pt-BR. |
| 2.6k | [schedule-x/schedule-x](https://github.com/schedule-x/schedule-x) | Alternativa moderna e mais leve ao FullCalendar. |

## PWA
| ★ | Repositório | O que aproveitar |
|---|---|---|
| 31k | [GoogleChrome/lighthouse](https://github.com/GoogleChrome/lighthouse) | Auditoria de PWA, performance e acessibilidade da página pública. |
| 13k | [GoogleChrome/workbox](https://github.com/GoogleChrome/workbox) | Estratégias de cache do service worker (assets versionados; nunca dados do Supabase). |
| 4.3k | [vite-pwa/vite-plugin-pwa](https://github.com/vite-pwa/vite-plugin-pwa) | Alternativa ao service worker escrito à mão, com atualização controlada. |
| 3.0k | [elegantapp/pwa-asset-generator](https://github.com/elegantapp/pwa-asset-generator) | Gerar ícones e splash screens do iOS a partir do selo circular. |

