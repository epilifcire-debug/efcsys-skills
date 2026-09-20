# Integração EFCsys com Lovable

## Objetivo
Ativar o padrão global EFCsys em projetos Lovable sem copiar todas as Skills para o contexto de cada tarefa.

## Bootstrap recomendado
No projeto Lovable, manter uma instrução curta e permanente equivalente a:

> Este projeto segue o padrão global EFCsys. Antes de executar uma tarefa, use o roteamento definido em `EFCsys.md`, aplique sempre `skills/efcsys-standard/SKILL.md` e carregue somente as Skills especializadas necessárias. Regras específicas deste projeto têm prioridade conforme a hierarquia EFCsys. Não repita contexto já conhecido e faça a menor alteração segura necessária.

## Uso
1. Identificar a tarefa atual.
2. Aplicar o padrão global.
3. Selecionar Skills pelo `EFCsys.md`.
4. Consultar somente referências necessárias.
5. Executar a alteração.
6. Validar proporcionalmente ao risco.

## Economia de créditos
Não copiar o conteúdo completo das Skills para cada prompt.

Preferir:
- referência ao arquivo/regra existente;
- comandos curtos;
- escopo explícito;
- alterações mínimas;
- confirmação final objetiva.

Evitar:
- reenviar histórico do projeto;
- pedir auditoria geral para mudança localizada;
- carregar todas as Skills;
- pedir planejamento para tarefa simples;
- solicitar documentação/relatório não necessários.

## Regras específicas do projeto
Requisitos de cliente, identidade, papéis, regras de negócio, integrações e decisões próprias do sistema permanecem no Knowledge/contexto do projeto.

Não mover regras específicas de um cliente para o repositório global.

## GitHub
Quando o ambiente tiver acesso ao repositório EFCsys, usar os arquivos atuais da branch principal como referência.

Se o ambiente não conseguir acessar esses arquivos diretamente, o bootstrap sozinho não transfere o conteúdo das Skills. Nesse caso, disponibilizar ao projeto apenas as instruções/referências necessárias pelo mecanismo suportado pelo ambiente.

## Atualizações
Quando uma Skill global evoluir, não duplicar manualmente a alteração em todos os projetos se eles estiverem consumindo a referência central.

## Validação
A ativação não deve modificar funcionalidade do projeto. O primeiro teste deve apenas confirmar que:
- o padrão global é reconhecido;
- a Skill correta é selecionada para uma tarefa;
- nenhuma alteração desnecessária é executada.
