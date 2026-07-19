# 🤖 Copiloto de Vendas com IA — Axon Labs

Copiloto de IA que apoia o time comercial da **Axon Labs** (agência de automação
com IA para PMEs e e-commerce) durante e depois das conversas com prospects:
estrutura o pitch, contorna objeções, redige follow-ups e prioriza leads.

> Projeto desenvolvido para o desafio **"Copiloto de Vendas com IA para
> Atendimento ao Cliente"** — DIO. Skills aplicadas: AI Agents, ChatGPT e
> Engenharia de Prompt.

---

## 🎯 Tema escolhido

Em vez da loja gamer de exemplo, o projeto foi ancorado em um negócio real: a
**Axon Labs**, agência de automação com IA para PMEs e e-commerce. Isso deixa a
base de conhecimento concreta (serviços, FAQ e objeções verdadeiras) e transforma
a entrega em uma ferramenta que o próprio time comercial pode usar.

## 👤 Usuário principal

O **time comercial da Axon Labs** — quem faz o primeiro contato, conduz a call de
diagnóstico e negocia. O copiloto **não fala com o cliente final**: ele orienta o
vendedor sobre o que dizer.

## 🧩 Problema que resolve

Vender automação exige responder rápido, com o argumento certo, e não deixar lead
esfriar no follow-up. Na prática, o vendedor:

- trava na hora de montar o pitch para uma dor específica;
- perde a venda em objeções comuns ("tá caro", "IA vai substituir meu time");
- esquece follow-ups e deixa lead morno esfriar;
- gasta energia com lead fora do perfil.

O copiloto ataca exatamente esses quatro pontos.

## 🛠️ Abordagem

**Copiloto (assistente interno) apoiado por base de conhecimento** — não é um
chatbot que fala com o cliente. A solução é composta por:

1. Um **system prompt** que define papel, princípios e formato de resposta.
2. Uma **base de conhecimento** em Markdown com o negócio real.
3. **Prompts de tarefa** para os usos do dia a dia.

Pode ser plugado em um GPT personalizado, num Projeto do Claude ou via API,
anexando os arquivos de `knowledge/`.

## 📚 Base de conhecimento

Fica em [`knowledge/`](./knowledge) e é a fonte de verdade do copiloto:

| Arquivo | Conteúdo |
|---|---|
| `contexto-do-negocio.md` | Quem é a Axon Labs, ICP e tom de voz |
| `produtos.md` | Serviços e para qual dor cada um serve |
| `perguntas-frequentes.md` | Respostas prontas na voz da marca |
| `objecoes.md` | Como contornar cada objeção de venda |

## 💬 Exemplo de resposta gerada

**Vendedor:** *"O cliente disse: 'achei interessante mas tá caro pro meu momento'.
Como respondo sem dar desconto na hora?"*

**Copiloto:**

> 🎯 **Leitura:** ele não está dizendo "não" — está dizendo "não vi o retorno".
> Não baixe o preço; mostre a conta do problema.
>
> 💬 **Resposta sugerida:** "Entendo total. Quantas horas por dia alguém do seu
> time gasta respondendo as mesmas perguntas? E quantos clientes desistem porque
> a resposta demorou? Isso já costuma custar mais por mês do que o investimento —
> a diferença é que um você paga sem perceber..."
>
> ➡️ **Próximo passo:** fechar na call de diagnóstico para levantar esses números
> com ele — não no desconto.

Mais exemplos em [`exemplos/conversas.md`](./exemplos/conversas.md).

## 📁 Estrutura do repositório

```
copiloto-vendas-axon-labs/
├── README.md
├── knowledge/
│   ├── contexto-do-negocio.md
│   ├── produtos.md
│   ├── perguntas-frequentes.md
│   └── objecoes.md
├── prompts/
│   ├── system-prompt.md        ← o "cérebro" do copiloto
│   └── exemplos-de-uso.md      ← prompts de tarefa do dia a dia
└── exemplos/
    └── conversas.md            ← respostas geradas pelo copiloto
```

## ▶️ Como usar

1. Crie um GPT personalizado (ChatGPT) ou um Projeto no Claude.
2. Cole o conteúdo de [`prompts/system-prompt.md`](./prompts/system-prompt.md)
   como instrução/system prompt.
3. Anexe os quatro arquivos de `knowledge/` como base de conhecimento.
4. Mande uma situação de venda (veja `prompts/exemplos-de-uso.md`) e receba a
   sugestão no formato 🎯 Leitura → 💬 Resposta → ➡️ Próximo passo.

## 🚀 Melhorias futuras

- Conectar ao **CRM no Airtable** para o copiloto ler o histórico real do lead.
- Integrar via **Make/n8n** para sugerir e disparar follow-ups automaticamente.
- Adicionar **scoring de leads** automático a partir dos sinais de ICP.
- Registrar quais sugestões foram usadas para medir taxa de conversão.
- Versão multilíngue para os leads internacionais captados na Upwork.

---

*Feito com foco em resultado: menos venda perdida por resposta lenta, mais
follow-up que não esfria.*
