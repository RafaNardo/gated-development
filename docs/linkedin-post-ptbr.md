# Rascunho de post para LinkedIn

## Versão longa

Nos últimos dias eu estava usando agentes de código para acelerar o desenvolvimento de um produto real.

A velocidade era impressionante, mas comecei a perceber um padrão: quanto maior e mais ambicioso o prompt, maior a chance do agente entender o objetivo e ainda assim "bater na trave" na execução.

Ele implementava coisas futuras antes da hora, criava infraestrutura que ainda não era necessária, refatorava áreas fora do escopo ou tomava decisões arquiteturais cedo demais.

O problema não parecia ser capacidade do modelo.

Era liberdade de execução demais de uma vez.

Então mudei a forma de trabalhar.

Passei a dividir o projeto em milestones pequenas e, dentro delas, tasks extremamente restritivas.

O agente continuava tendo acesso ao contexto completo do produto, à arquitetura e ao roadmap, mas cada execução recebia autoridade para alterar apenas uma parte.

As tasks passaram a declarar explicitamente:

- objetivo;
- contexto atual;
- mudanças permitidas;
- mudanças proibidas;
- non-goals;
- critérios de aceite;
- comandos de validação;
- formato do relatório final.

E uma instrução simples fez uma diferença enorme:

**"Não implemente as próximas milestones."**

O resultado foi muito melhor.

Os diffs ficaram menores, o comportamento do agente mais previsível, os reviews mais fáceis e o drift arquitetural caiu bastante.

Ao mesmo tempo, eu não queria deixar o agente "cego" para o futuro.

Se eu já sei, por exemplo, que um app será dividido em dois futuramente, essa informação deve influenciar a arquitetura de hoje — mas não significa que o agente tenha permissão para fazer essa separação agora.

Daí surgiu uma ideia que estou chamando de **Gated Development**.

A frase que melhor resume é:

> **Global context. Local authority. Explicit gates.**

Ou, de forma mais simples:

> **Dê ao agente o mapa inteiro, mas apenas uma chave por vez.**

O processo é mais ou menos:

```text
Visão
  ↓
Restrições arquiteturais
  ↓
Roadmap
  ↓
Milestone atual
  ↓
Task atual
  ↓
Build / Test / Review
  ↓
Próximo gate
```

Outra coisa que funcionou bem foi reavaliar o repositório depois de milestones importantes.

O roadmap não vira uma verdade imutável. O código real pode mostrar que uma decisão futura faz mais sentido agora — ou que uma task que parecia necessária já não é.

Estou documentando a metodologia e alguns templates em um repo público:

`github.com/RafaNardo/gated-development`

Ainda é uma primeira versão, extraída de uso real, mas achei interessante compartilhar porque vejo muita discussão sobre qual modelo ou agente usar e relativamente pouca sobre **como limitar e organizar a execução desses agentes dentro de um projeto real**.

Minha impressão até agora é que, conforme os agentes ficam mais capazes, o desafio deixa de ser apenas "escrever um prompt melhor" e passa a ser também **gerenciar autoridade, escopo e checkpoints**.

## Versão curta

Uma coisa mudou bastante a forma como estou usando agentes de código:

**parar de dar uma missão grande e começar a abrir gates pequenos.**

O agente recebe o contexto completo do projeto e conhece o roadmap, mas só tem autorização para implementar a task atual.

Cada task define objetivo, mudanças permitidas, mudanças proibidas, non-goals, critérios de aceite e validação.

A regra central virou:

> Global context. Local authority. Explicit gates.

Isso reduziu scope creep, refactors prematuros e decisões arquiteturais fora de hora, além de deixar os reviews muito mais fáceis.

Estou documentando o padrão como **Gated Development**:

`github.com/RafaNardo/gated-development`

A ideia não é dar menos contexto para a IA. É dar **menos autoridade por execução**.
