# Etapa 1 — Estrutura de Tópicos para Slides

---

## 🟦 BLOCO 1 — INTRODUÇÃO

---

**Slide 1 — Capa**
- Título: **Engenharia de Prompts: Como Falar com a IA e Ser Ouvido**
- Subtítulo: Minicurso prático — 4 horas
- Nome do ministrante + instituição
- Data e local

> 📝 *Nota do apresentador:* Deixe a capa visível enquanto os participantes se acomodam. Use esse momento para uma recepção informal antes de começar.

---

**Slide 2 — Agenda do dia**
- Bloco 1: O que é Engenharia de Prompts e por que importa
- Bloco 2: 7 técnicas essenciais com exemplos práticos
- Bloco 3: Boas práticas e comparativo Claude × ChatGPT
- Formato: exposição + demonstrações ao vivo
- Ferramentas usadas: Claude e ChatGPT

> 📝 *Nota do apresentador:* Mencione que demonstrações ao vivo serão feitas durante a apresentação. Encoraje os participantes a acompanhar nos próprios dispositivos.

---

**Slide 3 — O que é um prompt?**
- Prompt é toda instrução ou entrada de texto enviada a uma IA generativa
- É a única interface entre você e o modelo
- A qualidade do prompt determina a qualidade da resposta
- IA não lê mentes — ela processa exatamente o que recebe
- Engenharia de Prompts (*Prompt Engineering*): a prática de escrever prompts de forma intencional e estruturada

> 📝 *Nota do apresentador:* Pergunte ao público: "Quem já usou ChatGPT ou Claude?" Use o levantamento de mãos para calibrar o nível de familiaridade da turma.

---

**Slide 4 — Entra lixo, sai lixo**
- *"Garbage in, garbage out"* — princípio clássico da computação
- A IA é um amplificador: amplifica clareza, mas também amplifica confusão
- Prompt vago → resposta genérica, imprecisa ou inútil
- Prompt bem construído → resposta relevante, aplicável, confiável
- A responsabilidade da qualidade começa em você

> 📝 *Nota do apresentador:* Use a analogia de dar direções a um GPS: quanto mais preciso o endereço, mais certeiro o trajeto.

---

**Slide 5 — Por que prompts vagos falham?**
- Exemplo real: *"Faça um site bonito"*
- Perguntas que ficam sem resposta:
  - Bonito para quem? Qual público?
  - Que tecnologia usar?
  - Qual o objetivo do site?
  - Qual o prazo e escopo esperado?
- A IA vai responder — mas provavelmente não do jeito que você imaginou

> 📝 *Nota do apresentador:* Demonstre ao vivo: envie "faça um site bonito" para o ChatGPT ou Claude e mostre a resposta. Pergunte à turma: "Isso é o que vocês esperavam?"

---

**Slide 6 — O que muda com um bom prompt?**
- ❌ Antes: *"Faça um site bonito"*
- ✅ Depois: *"Crie o HTML de uma landing page para uma cafeteria chamada Moinho. Público: jovens de 18–30 anos. Cores: marrom e bege. Seções: hero, cardápio e contato. Sem frameworks externos."*
- A diferença: intenção clara + contexto + restrições + formato esperado
- Isso é Engenharia de Prompts aplicada

> 📝 *Nota do apresentador:* Mostre os dois prompts lado a lado e, se possível, as duas respostas da IA. O contraste visual é mais didático do que qualquer explicação.

---

## 🟨 BLOCO 2 — TÉCNICAS DE PROMPT

---

**Slide 7 — Visão geral das 7 técnicas**

| # | Técnica | Ideia central |
|---|---------|---------------|
| 1 | Few-Shot Prompting | Ensine pelo exemplo |
| 2 | Chain of Verification | Faça a IA conferir seu próprio trabalho |
| 3 | Memory Injection | Carregue contexto persistente |
| 4 | Reverse Prompting | Deixe a IA perguntar antes de agir |
| 5 | Constrain Cascade | Instrua em camadas progressivas |
| 6 | Verification Loop | Autocrítica antes da resposta final |
| 7 | Técnica KERNEL | Estrutura completa em 6 princípios |

> 📝 *Nota do apresentador:* Este slide funciona como mapa de navegação. Volte a ele entre cada técnica para mostrar onde a turma está na jornada.

---

### TÉCNICA 1

**Slide 8 — Few-Shot Prompting / Exemplos Guiados**
- **O que é:** fornecer exemplos do resultado esperado dentro do próprio prompt
- **Princípio:** modelos de linguagem aprendem padrões — mostrar é mais eficaz do que descrever
- **Quando usar:** tarefas com formato específico, tom ou estilo bem definidos
- **Quantos exemplos:** 2 a 5 costumam ser suficientes
- **Variação:** *Zero-Shot* (sem exemplos) × *Few-Shot* (com exemplos)

> 📝 *Nota do apresentador:* Explique que "shot" significa "exemplo" neste contexto. A analogia útil: é como mostrar um modelo de redação antes de pedir que o aluno escreva.

---

**Slide 9 — Few-Shot: antes × depois**

❌ **Antes (Zero-Shot vago):**
> *"Escreva títulos criativos para artigos de blog."*

✅ **Depois (Few-Shot):**
> *"Escreva títulos para artigos de blog seguindo este padrão:*
> *Exemplo 1: '5 hábitos que destroem sua produtividade (e como eliminá-los)'*
> *Exemplo 2: 'Por que você estuda muito e aprende pouco — e o que fazer'*
> *Agora crie 3 títulos sobre saúde mental universitária."*

- O modelo aprende: tom direto, número no título, subtítulo com solução

> 📝 *Nota do apresentador:* Mostre que o resultado sem exemplos é genérico e previsível. Com exemplos, a IA replica o padrão com precisão surpreendente.

---

### TÉCNICA 2

**Slide 10 — Chain of Verification / Cadeia de Verificação**
- **O que é:** instruir a IA a verificar suas próprias afirmações antes de concluir
- **Problema que resolve:** alucinações — quando a IA afirma coisas erradas com confiança
- **Quando usar:** respostas factuais, resumos, análises que exigem precisão
- **Como funciona:** o modelo gera → lista afirmações → verifica cada uma → corrige se necessário
- Reduz significativamente erros em respostas longas

> 📝 *Nota do apresentador:* "Alucinação" é o termo técnico para quando a IA inventa fatos. Exemplifique com algo simples: pedir a data de nascimento de uma pessoa fictícia.

---

**Slide 11 — Chain of Verification: antes × depois**

❌ **Antes:**
> *"Quais são os principais filósofos iluministas e suas ideias?"*
*(A IA responde com confiança — mas pode errar datas, obras e atribuições)*

✅ **Depois:**
> *"Liste os principais filósofos iluministas e suas ideias centrais.*
> *Em seguida, para cada filósofo citado, verifique se o nome, o período histórico e as obras mencionadas estão corretos.*
> *Se encontrar alguma imprecisão, corrija antes de apresentar a resposta final."*

- Resultado: a própria IA audita o conteúdo que produziu

> 📝 *Nota do apresentador:* Destaque que isso não elimina 100% dos erros, mas reduz drasticamente. Sempre oriente os participantes a conferir informações críticas em fontes primárias.

---

### TÉCNICA 3

**Slide 12 — Memory Injection / Injeção de Memória**
- **O que é:** carregar contexto relevante no início da conversa para que a IA "lembre" durante toda a sessão
- **Problema que resolve:** IAs não têm memória entre sessões por padrão
- **O que pode ser injetado:** seu perfil, estilo de escrita, preferências, restrições recorrentes
- **Quando usar:** fluxos de trabalho repetitivos, projetos longos, consultorias contínuas
- Funciona como um "briefing permanente" antes de cada tarefa

> 📝 *Nota do apresentador:* Analogia útil — é como entregar um currículo e briefing para um assistente novo toda vez que você o contrata. Quanto mais completo, melhor o trabalho.

---

**Slide 13 — Memory Injection: antes × depois**

❌ **Antes (nova sessão, sem contexto):**
> *"Revise este parágrafo do meu artigo."*
*(A IA não sabe: área do conhecimento, tom esperado, público-alvo, nível de formalidade)*

✅ **Depois (com injeção de memória):**
> *"Contexto permanente desta sessão:*
> *— Sou estudante de Psicologia, 4º ano*
> *— Estou escrevendo um artigo acadêmico para uma revista nacional, normas ABNT*
> *— Tom: formal, objetivo, sem jargão clínico excessivo*
> *— Público: professores e pesquisadores da área*
> *Com base nesse contexto, revise o parágrafo abaixo:"*

> 📝 *Nota do apresentador:* Mostre que esse bloco de contexto pode ser salvo em um arquivo de texto e colado no início de qualquer nova sessão. É uma prática simples que economiza muito tempo.

---

### TÉCNICA 4

**Slide 14 — Reverse Prompting / Prompt Reverso**
- **O que é:** em vez de dar todas as instruções, pedir que a IA pergunte o que precisa saber antes de executar
- **Princípio:** forçar o modelo a identificar lacunas antes de agir
- **Quando usar:** tarefas complexas onde você mesmo não sabe exatamente o que quer
- **Efeito colateral positivo:** ajuda o próprio usuário a clarificar seus objetivos
- O modelo atua como consultor, não só como executor

> 📝 *Nota do apresentador:* Este prompt que abre o minicurso é um exemplo real de Reverse Prompting — "Antes de prosseguir, faça perguntas para esclarecer objetivos e restrições."

---

**Slide 15 — Reverse Prompting: antes × depois**

❌ **Antes:**
> *"Me ajude a melhorar minha apresentação de TCC."*
*(A IA dá dicas genéricas que podem não se aplicar ao seu caso)*

✅ **Depois:**
> *"Atue como um orientador acadêmico experiente.*
> *Antes de sugerir melhorias para minha apresentação de TCC, faça as perguntas necessárias para entender: área do curso, público da banca, tempo disponível, pontos que considero fracos e formato atual dos slides.*
> *Só comece a sugerir melhorias depois de ter todas as informações."*

- A IA entrevista você antes de agir — as sugestões ficam muito mais precisas

> 📝 *Nota do apresentador:* Demonstre ao vivo. Envie o prompt e mostre as perguntas que a IA faz. Geralmente são perguntas que o próprio usuário não havia considerado.

---

### TÉCNICA 5

**Slide 16 — Constrain Cascade / Cascata de Restrições**
- **O que é:** fornecer instruções em camadas progressivas, não tudo de uma vez
- **Princípio:** modelos processam melhor instruções incrementais do que blocos densos
- **Quando usar:** tarefas longas e complexas, criação de documentos estruturados, processos em etapas
- **Como funciona:** instrução simples → confirmar compreensão → adicionar restrição → confirmar → avançar
- Evita que erros da primeira instrução se propaguem por toda a tarefa

> 📝 *Nota do apresentador:* Analogia: é como ensinar a receita de um prato — você não despeja todos os ingredientes de uma vez. Cada etapa precisa estar certa antes de avançar.

---

**Slide 17 — Constrain Cascade: antes × depois**

❌ **Antes (tudo de uma vez):**
> *"Crie um plano de estudos para o ENEM cobrindo todas as matérias, com cronograma semanal, técnicas de memorização, simulados, revisão e dicas de redação, considerando que tenho 3 meses e estudo 2 horas por dia."*
*(Resultado: texto longo, genérico, difícil de adaptar)*

✅ **Depois (em cascata):**
> **Mensagem 1:** *"Vou criar um plano de estudos para o ENEM. Primeiro: liste apenas as áreas de conhecimento que precisam ser cobertas."*
> **Mensagem 2:** *"Agora distribua essas áreas em 12 semanas, 2h/dia, priorizando Matemática e Redação."*
> **Mensagem 3:** *"Para a semana 1, detalhe os tópicos diários e sugira um método de estudo para cada um."*

> 📝 *Nota do apresentador:* Mostre que o resultado final da cascata é muito mais utilizável do que um único bloco gerado de uma vez. Cada etapa permite ajuste.

---

### TÉCNICA 6

**Slide 18 — Verification Loop / Laço de Verificação**
- **O que é:** pedir que a IA explique seu raciocínio e depois critique a própria explicação
- **Diferença para Chain of Verification:** aqui o foco é no *processo de raciocínio*, não só nos fatos
- **Quando usar:** análises, recomendações, resoluções de problemas complexos
- **Estrutura:** gerar → explicar → criticar → corrigir → entregar
- Captura erros lógicos que passariam despercebidos em respostas diretas

> 📝 *Nota do apresentador:* Explique que isso simula o que um bom profissional faz antes de entregar um trabalho: reler, questionar as próprias premissas e revisar.

---

**Slide 19 — Verification Loop: antes × depois**

❌ **Antes:**
> *"Qual é a melhor estratégia para engajar alunos desmotivados?"*
*(A IA responde diretamente — sem questionar se as premissas são válidas)*

✅ **Depois:**
> *"Sugira três estratégias para engajar alunos desmotivados no ensino superior.*
> *Para cada estratégia: explique o raciocínio por trás dela.*
> *Em seguida, critique cada estratégia: quais são suas limitações e em que contextos ela pode não funcionar?*
> *Por fim, considerando as críticas, apresente a versão refinada das três estratégias."*

- A resposta final já chegou auditada pelo próprio modelo

> 📝 *Nota do apresentador:* Compare as duas respostas ao vivo. A segunda será notavelmente mais matizada e útil — e o processo de raciocínio fica visível para o usuário.

---

### TÉCNICA 7

**Slide 20 — Técnica KERNEL: visão geral**
- Framework estruturado para construir prompts completos e reproduzíveis
- Cada letra representa um princípio:

| Letra | Princípio | Significado |
|-------|-----------|-------------|
| **K** | *Keep it simple* | Mantenha simples |
| **E** | *Easy to verify* | Fácil de verificar |
| **R** | *Reproducible* | Resultados reproduzíveis |
| **N** | *Narrow scope* | Escopo estreito |
| **E** | *Explicit constraints* | Restrições explícitas |
| **L** | *Logical structure* | Estrutura lógica |

> 📝 *Nota do apresentador:* Apresente o acrônimo de forma pausada. Pergunte à turma qual princípio eles acham mais fácil de ignorar no dia a dia — geralmente é o "N" (escopo estreito).

---

**Slide 21 — KERNEL: os 4 componentes estruturais**

O **L** de *Logical Structure* se desdobra em 4 blocos obrigatórios:

| Componente | Função | Pergunta que responde |
|------------|--------|----------------------|
| **Context** *(Contexto)* | Quem você é e qual é a situação | *"Qual é o cenário?"* |
| **Task** *(Tarefa)* | O que exatamente deve ser feito | *"O que fazer?"* |
| **Constraints** *(Restrições)* | Limites, formatos, restrições | *"O que não fazer / como fazer?"* |
| **Format** *(Formato de saída)* | Como a resposta deve ser entregue | *"Como apresentar?"* |

- Um prompt KERNEL completo responde às quatro perguntas

> 📝 *Nota do apresentador:* Este é o slide mais importante do bloco 2. Sugira que os participantes fotografem ou anotem os 4 componentes — eles formam a base de qualquer prompt avançado.

---

**Slide 22 — KERNEL: antes × depois**

❌ **Antes:**
> *"Me ajude a escrever um e-mail para o meu professor pedindo prazo."*

✅ **Depois (estrutura KERNEL):**
> **Contexto:** Sou aluno de graduação em Letras, 3º semestre. Tive problemas de saúde na última semana.
> **Tarefa:** Escrever um e-mail formal pedindo extensão de 5 dias para entrega de um trabalho escrito.
> **Restrições:** Tom respeitoso e objetivo. Sem exageros dramáticos. Máximo de 3 parágrafos. Não mencionar detalhes médicos.
> **Formato:** E-mail com assunto, saudação, corpo e despedida formais.

- O modelo sabe exatamente o que fazer — e o resultado é utilizável imediatamente

> 📝 *Nota do apresentador:* Gere os dois e-mails ao vivo. O contraste é imediato: o primeiro é genérico; o segundo está pronto para enviar.

---

## 🟩 BLOCO 3 — ENCERRAMENTO

---

**Slide 23 — Boas práticas consolidadas**
- Seja específico: substitua adjetivos vagos por critérios mensuráveis
- Defina o papel da IA: *"Atue como..."* melhora o enquadramento da resposta
- Indique o formato de saída esperado: lista, tabela, texto corrido, tópicos
- Itere: o primeiro prompt raramente é o melhor — refine a conversa
- Desconfie de respostas muito confiantes em temas factuais — sempre verifique

> 📝 *Nota do apresentador:* Peça que cada participante escolha uma dessas práticas e diga em voz alta em qual tarefa do dia a dia ela se aplicaria. Cria engajamento rápido.

---

**Slide 24 — Claude × ChatGPT: como as técnicas se aplicam**

| Técnica | Claude | ChatGPT |
|---------|--------|---------|
| Few-Shot | Excelente adesão a padrões | Bom, mas pode extrapolar |
| Chain of Verification | Responde bem à autocrítica | Funciona melhor com instrução explícita |
| Memory Injection | Projects mantêm contexto nativo | Custom Instructions ou memória automática |
| Reverse Prompting | Comportamento natural | Pode precisar de instrução mais direta |
| Constrain Cascade | Lida bem com instruções longas | Funciona melhor em mensagens curtas |
| Verification Loop | Forte em raciocínio explícito | Bom, especialmente com GPT-4o |
| KERNEL | Segue estrutura com fidelidade | Segue bem, tende a expandir mais |

> 📝 *Nota do apresentador:* Ressalte que ambos os modelos evoluem rapidamente — essas observações refletem o comportamento atual, mas podem mudar com novas versões. O mais importante é experimentar.

---

**Slide 25 — Encerramento**
- Engenharia de Prompts não é programação — é comunicação intencional
- As 7 técnicas são ferramentas: escolha a certa para cada situação
- O melhor prompt é aquele que você itera até funcionar
- Material de consulta: apostila disponível em arquivo `.md`
- Obrigado — dúvidas?

> 📝 *Nota do apresentador:* Reserve 15–20 minutos para perguntas. Sugira que a turma escolha uma técnica e tente aplicar em algo que precisam fazer ainda hoje — a fixação é imediata quando há aplicação prática.