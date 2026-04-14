# Engenharia de Prompts: comunicação com modelos de IA

> **III InterPET — IFTM (Instituto Federal do Triângulo Mineiro)**
> 📅 15 de abril de 2026 · 📍 Ituiutaba, MG
> 👨‍🏫 Palestrante: Dr. André Luiz França Batista
>
> Ferramentas de referência: Claude e ChatGPT

---

## Sumário

1. [O que é Engenharia de Prompts?](#1-o-que-é-engenharia-de-prompts)
2. [Por que prompts vagos falham?](#2-por-que-prompts-vagos-falham)
3. [Técnica 1 — Few-Shot Prompting / Exemplos Guiados](#3-técnica-1--few-shot-prompting--exemplos-guiados)
4. [Técnica 2 — Chain of Verification / Cadeia de Verificação](#4-técnica-2--chain-of-verification--cadeia-de-verificação)
5. [Técnica 3 — Memory Injection / Injeção de Memória](#5-técnica-3--memory-injection--injeção-de-memória)
6. [Técnica 4 — Reverse Prompting / Prompt Reverso](#6-técnica-4--reverse-prompting--prompt-reverso)
7. [Técnica 5 — Constrain Cascade / Cascata de Restrições](#7-técnica-5--constrain-cascade--cascata-de-restrições)
8. [Técnica 6 — Verification Loop / Laço de Verificação](#8-técnica-6--verification-loop--laço-de-verificação)
9. [Técnica 7 — Técnica KERNEL](#9-técnica-7--técnica-kernel)
10. [Boas Práticas Consolidadas](#10-boas-práticas-consolidadas)
11. [Claude × ChatGPT: como as técnicas se aplicam](#11-claude--chatgpt-como-as-técnicas-se-aplicam)

---

## 1. O que é Engenharia de Prompts?

Um **prompt** é toda instrução ou entrada de texto que você envia a uma inteligência artificial generativa (IA generativa). É a única interface entre você e o modelo — tudo o que a IA produz parte diretamente do que ela recebe.

**Engenharia de Prompts** (*Prompt Engineering*) é a prática de escrever prompts de forma intencional, estruturada e estratégica, com o objetivo de obter respostas mais precisas, úteis e confiáveis.

Um princípio clássico da computação resume bem a ideia central:

> *"Garbage in, garbage out"* — entra lixo, sai lixo.

O inverso também é verdadeiro: quanto mais claro, contextualizado e bem estruturado for o seu prompt, melhor será a resposta gerada. A IA não lê mentes — ela processa exatamente o que recebe. A responsabilidade pela qualidade da resposta começa em quem formula a pergunta.

---

## 2. Por que prompts vagos falham?

Considere o seguinte exemplo:

❌ **Prompt vago:**
> *"Faça um site bonito."*

Este prompt deixa sem resposta perguntas fundamentais:

- Bonito para quem? Qual é o público-alvo?
- Qual é o objetivo do site?
- Que tecnologia deve ser usada?
- Quais seções devem existir?
- Qual é o prazo e o escopo esperado?

A IA vai responder — ela sempre responde. Mas o resultado provavelmente não corresponderá ao que você tinha em mente, porque **o que estava na sua cabeça nunca foi dito**.

✅ **Prompt estruturado:**
> *"Crie o HTML de uma landing page para uma cafeteria chamada Moinho. Público: jovens de 18 a 30 anos. Cores: marrom e bege. Seções obrigatórias: apresentação, cardápio e contato. Sem frameworks externos."*

A diferença está em quatro elementos: **intenção clara**, **contexto**, **restrições** e **formato esperado**. Esses quatro elementos são a base de qualquer bom prompt — e estão detalhados na Técnica 7 (KERNEL).

---

## 3. Técnica 1 — Few-Shot Prompting / Exemplos Guiados

### Definição

*Few-Shot Prompting* (Exemplos Guiados) consiste em fornecer exemplos do resultado esperado dentro do próprio prompt, antes de fazer a solicitação principal. Em vez de apenas descrever o que você quer, você mostra.

O termo "shot" significa "exemplo" neste contexto. A variação *Zero-Shot* é quando nenhum exemplo é fornecido — você apenas descreve a tarefa. O *Few-Shot* inclui de dois a cinco exemplos que demonstram o padrão desejado.

### Quando usar

- Quando a tarefa exige um formato específico e bem definido
- Quando o tom, o estilo ou a estrutura da resposta importam tanto quanto o conteúdo
- Quando respostas genéricas anteriores não atenderam suas expectativas

### Como funciona

Modelos de linguagem aprendem padrões. Ao ver exemplos, o modelo identifica: vocabulário, estrutura, nível de formalidade, comprimento e estilo — e os replica com precisão na resposta solicitada.

---

❌ **Antes — Zero-Shot vago:**
> *"Escreva títulos criativos para artigos de blog."*

O modelo não sabe: qual o tom? Deve incluir números? Há subtítulo? Qual é o assunto?

---

✅ **Depois — Few-Shot:**
> *"Escreva títulos para artigos de blog seguindo este padrão:*
>
> *Exemplo 1: '5 hábitos que destroem sua produtividade (e como eliminá-los)'*
> *Exemplo 2: 'Por que você estuda muito e aprende pouco — e o que fazer'*
> *Exemplo 3: 'O erro que 90% das pessoas cometem ao tomar decisões importantes'*
>
> *Agora crie 3 títulos sobre saúde mental universitária seguindo o mesmo padrão."*

O modelo aprende com os exemplos que os títulos devem ter: tom direto, número ou dado de impacto, e uma promessa de solução ou revelação.

---

## 4. Técnica 2 — Chain of Verification / Cadeia de Verificação

### Definição

*Chain of Verification* (Cadeia de Verificação) é uma técnica que instrui a IA a verificar suas próprias afirmações antes de apresentar a resposta final. O modelo gera uma resposta inicial, lista as principais afirmações contidas nela, verifica cada uma e corrige o que for impreciso.

### Quando usar

- Respostas que envolvem fatos, datas, nomes ou dados que precisam de precisão
- Resumos de textos longos onde erros de interpretação podem passar despercebidos
- Análises e recomendações que serão usadas como base para decisões

### O problema que resolve: alucinações

**Alucinação** (*hallucination*) é o termo técnico para quando uma IA generativa produz informações incorretas com alto grau de confiança. Isso acontece porque o modelo gera texto estatisticamente plausível — não necessariamente verdadeiro. A Cadeia de Verificação reduz significativamente esse problema ao forçar uma etapa de revisão interna antes da entrega.

---

❌ **Antes:**
> *"Quais são os principais filósofos iluministas e suas ideias?"*

A IA responde com confiança, mas pode errar datas, confundir obras entre autores ou atribuir ideias incorretamente.

---

✅ **Depois:**
> *"Liste os principais filósofos iluministas e suas ideias centrais.*
>
> *Em seguida, para cada filósofo citado, verifique se o nome, o período histórico e as obras mencionadas estão corretos.*
>
> *Se encontrar alguma imprecisão, corrija antes de apresentar a resposta final."*

A própria IA audita o conteúdo que produziu. O resultado chega mais confiável — embora a verificação humana em fontes primárias continue sendo recomendada para informações críticas.

---

## 5. Técnica 3 — Memory Injection / Injeção de Memória

### Definição

*Memory Injection* (Injeção de Memória) é a prática de carregar contexto relevante no início de uma conversa para que a IA o utilize durante toda a sessão. Funciona como um "briefing permanente" entregue ao modelo antes de qualquer tarefa.

### O problema que resolve

Por padrão, IAs generativas não têm memória entre sessões distintas. Cada nova conversa começa do zero. Sem contexto injetado, o modelo não sabe quem você é, o que você faz, qual é seu estilo ou quais são suas preferências recorrentes.

### Quando usar

- Fluxos de trabalho repetitivos onde você sempre precisa das mesmas informações de contexto
- Projetos longos que envolvem múltiplas sessões ao longo do tempo
- Quando o tom, o nível de formalidade ou o público-alvo são sempre os mesmos

### O que pode ser injetado

Perfil pessoal ou profissional, estilo de escrita preferido, restrições fixas, público-alvo dos materiais produzidos, nível de detalhamento esperado e qualquer informação que você repetiria no início de cada nova conversa.

---

❌ **Antes — nova sessão, sem contexto:**
> *"Revise este parágrafo do meu artigo."*

A IA não sabe: qual é a área? Qual o tom esperado? É um artigo acadêmico ou jornalístico? Para qual público?

---

✅ **Depois — com injeção de memória:**
> *"Contexto permanente desta sessão:*
> *— Sou estudante de Psicologia, 4º ano*
> *— Estou escrevendo um artigo acadêmico para uma revista nacional, normas ABNT*
> *— Tom: formal, objetivo, sem jargão clínico excessivo*
> *— Público: professores e pesquisadores da área*
>
> *Com base nesse contexto, revise o parágrafo abaixo:"*

O bloco de contexto pode ser salvo em um arquivo de texto e colado no início de qualquer nova sessão. É uma prática simples que elimina repetições e torna as respostas muito mais ajustadas às suas necessidades.

---

## 6. Técnica 4 — Reverse Prompting / Prompt Reverso

### Definição

*Reverse Prompting* (Prompt Reverso) inverte a lógica tradicional: em vez de você dar todas as instruções à IA, você pede que ela identifique o que precisa saber antes de executar a tarefa. O modelo atua como consultor que entrevista o cliente antes de agir.

### Quando usar

- Tarefas complexas onde você mesmo não tem clareza total sobre o que quer
- Quando respostas anteriores foram genéricas demais por falta de especificidade
- Quando quiser usar a IA para ajudar a estruturar seu próprio pensamento antes de executar

### Efeito colateral positivo

Além de melhorar a qualidade da resposta final, o Prompt Reverso frequentemente ajuda o próprio usuário a clarificar seus objetivos. As perguntas que a IA faz revelam lacunas que você não havia percebido — e que, se não preenchidas, levariam a um resultado insatisfatório.

---

❌ **Antes:**
> *"Me ajude a melhorar minha apresentação de TCC."*

A IA dá dicas genéricas sobre apresentações em geral — sem saber nada sobre a área, a banca, o tempo disponível ou os pontos fracos específicos.

---

✅ **Depois:**
> *"Atue como um orientador acadêmico experiente.*
>
> *Antes de sugerir melhorias para minha apresentação de TCC, faça as perguntas necessárias para entender: área do curso, público da banca, tempo disponível para a apresentação, pontos que considero mais fracos e formato atual dos slides.*
>
> *Só comece a sugerir melhorias depois de ter todas as informações."*

A IA entrevista você antes de agir. As sugestões que chegam depois são específicas para o seu caso — não para uma apresentação genérica imaginária.

---

## 7. Técnica 5 — Constrain Cascade / Cascata de Restrições

### Definição

*Constrain Cascade* (Cascata de Restrições) consiste em fornecer instruções em camadas progressivas, uma de cada vez, em vez de entregar todas as instruções em um único bloco denso. Cada camada é confirmada antes da próxima ser adicionada.

### Quando usar

- Tarefas longas e complexas com múltiplas etapas interdependentes
- Criação de documentos estruturados (planos, relatórios, roteiros)
- Quando erros no início de uma tarefa costumam comprometer todo o resultado

### Por que funciona

Modelos de linguagem processam melhor instruções incrementais do que blocos de texto com muitas restrições simultâneas. Ao dividir a tarefa em camadas, você também ganha pontos de controle — pode corrigir o rumo antes que um erro se propague por toda a resposta.

---

❌ **Antes — tudo de uma vez:**
> *"Crie um plano de estudos para o ENEM cobrindo todas as matérias, com cronograma semanal, técnicas de memorização, simulados, revisão e dicas de redação, considerando que tenho 3 meses e estudo 2 horas por dia."*

O resultado tende a ser longo, genérico e difícil de adaptar à realidade de quem perguntou.

---

✅ **Depois — em cascata:**

**Mensagem 1:**
> *"Vou criar um plano de estudos para o ENEM. Primeiro: liste apenas as áreas de conhecimento que precisam ser cobertas e confirme o entendimento."*

**Mensagem 2 (após confirmação):**
> *"Agora distribua essas áreas em 12 semanas, considerando 2 horas de estudo por dia, priorizando Matemática e Redação."*

**Mensagem 3 (após nova confirmação):**
> *"Para a semana 1, detalhe os tópicos diários e sugira um método de estudo adequado para cada um."*

Cada etapa permite ajuste antes de avançar. O resultado final é muito mais preciso e utilizável do que um único bloco gerado de uma vez.

---

## 8. Técnica 6 — Verification Loop / Laço de Verificação

### Definição

*Verification Loop* (Laço de Verificação) instrui a IA a executar um ciclo completo de autocrítica: gerar uma resposta, explicar o raciocínio por trás dela, criticar a própria explicação identificando limitações e inconsistências, e só então entregar a versão final corrigida.

### Diferença em relação à Cadeia de Verificação

Enquanto a *Chain of Verification* foca na verificação de **fatos** (datas, nomes, dados), o *Verification Loop* foca no **processo de raciocínio** — verificando se a lógica da resposta é sólida, se as premissas são válidas e se as conclusões realmente decorrem dos argumentos apresentados.

### Quando usar

- Análises e diagnósticos que envolvem múltiplas variáveis
- Recomendações que serão usadas como base para decisões importantes
- Respostas a perguntas abertas e complexas onde há risco de simplificação excessiva

---

❌ **Antes:**
> *"Qual é a melhor estratégia para engajar alunos desmotivados?"*

A IA responde com confiança e diretamente — sem questionar se as premissas são válidas ou se as estratégias têm limitações contextuais.

---

✅ **Depois:**
> *"Sugira três estratégias para engajar alunos desmotivados no ensino superior.*
>
> *Para cada estratégia:*
> *1. Explique o raciocínio que a sustenta.*
> *2. Critique a estratégia: quais são suas limitações e em que contextos ela pode não funcionar?*
> *3. Considerando as críticas, apresente a versão refinada da estratégia."*

A resposta final chega já auditada pelo próprio modelo. O processo de raciocínio fica visível, o que permite ao usuário identificar onde concorda ou discorda — e refinar ainda mais se necessário.

---

## 9. Técnica 7 — Técnica KERNEL

### Definição

KERNEL é um framework estruturado para construir prompts completos, claros e reproduzíveis. Cada letra representa um princípio que, quando aplicado em conjunto, maximiza a qualidade e a consistência das respostas geradas.

### Os 6 princípios

| Letra | Princípio em inglês | Significado |
|-------|----------------------|-------------|
| **K** | *Keep it simple* | Mantenha simples — evite prompts longos e confusos |
| **E** | *Easy to verify* | Fácil de verificar — o resultado deve ser checável |
| **R** | *Reproducible* | Reproduzível — o mesmo prompt deve gerar resultados consistentes |
| **N** | *Narrow scope* | Escopo estreito — uma tarefa por vez, sem acumular pedidos |
| **E** | *Explicit constraints* | Restrições explícitas — diga o que não deve aparecer na resposta |
| **L** | *Logical structure* | Estrutura lógica — organize o prompt em blocos com função clara |

### Os 4 componentes da estrutura lógica

O princípio **L** (*Logical Structure*) se desdobra em quatro blocos que todo prompt bem construído deve contemplar:

| Componente | Em inglês | Função | Pergunta que responde |
|------------|-----------|--------|----------------------|
| **Contexto** | *Context* | Quem você é e qual é a situação | *"Qual é o cenário?"* |
| **Tarefa** | *Task* | O que exatamente deve ser feito | *"O que fazer?"* |
| **Restrições** | *Constraints* | Limites, exclusões e parâmetros | *"O que não fazer ou como fazer?"* |
| **Formato de saída** | *Format* | Como a resposta deve ser entregue | *"Como apresentar?"* |

Um prompt KERNEL completo responde às quatro perguntas acima de forma explícita.

---

❌ **Antes — sem estrutura KERNEL:**
> *"Me ajude a escrever um e-mail para o meu professor pedindo prazo."*

Sem contexto: a IA não sabe quem você é, qual é a relação com o professor, qual o motivo do pedido.
Sem restrições: a IA pode gerar um texto dramático, informal ou longo demais.
Sem formato: a IA pode entregar um parágrafo solto, sem estrutura de e-mail.

---

✅ **Depois — com estrutura KERNEL:**

> **Contexto:** Sou aluno de graduação em Letras, 3º semestre. Tive problemas de saúde na última semana que me impediram de concluir o trabalho a tempo.
>
> **Tarefa:** Escrever um e-mail formal solicitando uma extensão de 5 dias corridos para a entrega de um trabalho escrito.
>
> **Restrições:** Tom respeitoso e objetivo. Sem exageros dramáticos ou detalhes médicos. Máximo de 3 parágrafos. Não demonstrar que o prazo original foi esquecido.
>
> **Formato:** E-mail completo com linha de assunto, saudação formal, corpo em 3 parágrafos e despedida adequada.

O modelo sabe exatamente o que fazer — e o resultado está pronto para enviar, sem necessidade de edições.

---

### Comparativo visual

| Elemento | Antes | Depois (KERNEL) |
|----------|-------|-----------------|
| Contexto | Ausente | Explícito |
| Escopo | Amplo e vago | Estreito e definido |
| Restrições | Nenhuma | Listadas |
| Formato esperado | Não especificado | Descrito em detalhes |
| Resultado | Genérico | Utilizável imediatamente |

---

## 10. Boas Práticas Consolidadas

As sete técnicas apresentadas neste material compartilham um conjunto de princípios subjacentes. Internalizá-los transforma a relação com qualquer ferramenta de IA generativa:

**Substitua adjetivos vagos por critérios mensuráveis.**
Em vez de "texto criativo", diga "texto com no máximo 3 parágrafos, tom descontraído, sem jargão técnico". Em vez de "resposta completa", diga "resposta em formato de lista com 5 itens".

**Defina o papel da IA antes de fazer o pedido.**
Iniciar o prompt com "Atue como..." ou "Você é um especialista em..." enquadra a resposta de forma muito mais precisa do que começar diretamente com a tarefa.

**Indique sempre o formato de saída esperado.**
Lista, tabela, texto corrido, tópicos numerados, e-mail, roteiro — quanto mais claro o formato, menos ajustes serão necessários depois.

**Itere: o primeiro prompt raramente é o melhor.**
Engenharia de Prompts é um processo, não um ato único. A primeira resposta indica o que faltou no prompt — use isso para refinar a instrução e obter um resultado melhor na próxima tentativa.

**Desconfie de respostas muito confiantes em temas factuais.**
IAs generativas podem afirmar informações incorretas com alto grau de convicção. Para dados, datas, nomes e fatos que importam, sempre verifique em fontes primárias.

**Uma tarefa por vez.**
Prompts que pedem várias coisas ao mesmo tempo tendem a gerar respostas que resolvem mal cada uma delas. Quebre tarefas complexas em etapas menores — isso é o que a Cascata de Restrições formaliza.

---

## 11. Claude × ChatGPT: como as técnicas se aplicam

As sete técnicas funcionam em ambas as ferramentas, mas com nuances de comportamento que vale conhecer:

| Técnica | Claude | ChatGPT |
|---------|--------|---------|
| **Few-Shot Prompting** | Excelente adesão ao padrão fornecido | Bom, mas pode extrapolar além do padrão |
| **Chain of Verification** | Responde bem à instrução de autocrítica | Funciona melhor com instrução explícita e detalhada |
| **Memory Injection** | *Projects* (Projetos) mantêm contexto de forma nativa entre sessões | *Custom Instructions* ou memória automática (quando ativada) |
| **Reverse Prompting** | Comportamento natural — tende a perguntar antes de agir | Pode precisar de instrução mais direta para adotar o comportamento |
| **Constrain Cascade** | Lida bem com instruções longas e incrementais | Funciona melhor quando as mensagens individuais são curtas e diretas |
| **Verification Loop** | Forte em raciocínio explícito e estruturado | Bom desempenho, especialmente com modelos mais recentes |
| **Técnica KERNEL** | Segue a estrutura com fidelidade e precisão | Segue bem, mas tende a expandir mais além do solicitado |

> **Observação:** ambos os modelos evoluem continuamente. As características descritas acima refletem o comportamento observado nos modelos disponíveis à época deste material e podem mudar com novas versões. A melhor forma de aprender é experimentar as técnicas diretamente nas duas ferramentas.

---

*Engenharia de Prompts não é programação — é comunicação intencional. As técnicas apresentadas aqui são ferramentas: a escolha certa depende da tarefa, do contexto e do resultado que você quer alcançar. O melhor prompt é sempre aquele que você itera até funcionar.*
