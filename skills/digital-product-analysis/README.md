# Digital Product Analysis

Skill para [Claude Code](https://docs.anthropic.com/en/docs/claude-code) que realiza análise completa de produto digital — da validação de ideia até a tese de investimento — gerando documentação estruturada, pronta para compartilhar com sócios, investidores e stakeholders.

## O que faz

A skill atua como um **analista sênior de produto, estratégia e negócios**. A partir de uma ideia de produto digital, ela:

1. Coleta e organiza informações sobre o projeto (ou lê um `REFERENCES.md` existente)
2. Pesquisa na internet: concorrentes, tamanho de mercado, legislação, tendências, benchmarks
3. Gera **14 documentos estruturados** cobrindo todas as dimensões da análise
4. Entrega um veredicto claro: **vale apostar ou não**, e por quê

### Diferenciais

- **Crítica, não genérica.** Usa dados reais, nomes de concorrentes, números concretos. Se a ideia tem problemas, diz claramente.
- **Pragmática.** O foco é: "existe uma forma rápida e viável de ganhar dinheiro com isso?" — não teoria abstrata.
- **Completa.** De overview a pitch deck de investidor, tudo em um único fluxo.
- **Pesquisa ativa.** Busca concorrentes, legislação, dados de mercado e cases na internet automaticamente.

## Instalação

Copie a pasta `digital-product-analysis/` para o diretório de skills do Claude Code:

```bash
cp -r digital-product-analysis/ ~/.claude/skills/digital-product-analysis/
```

A skill será detectada automaticamente na próxima sessão.

## Como usar

### Opção 1 — Prompt direto (sem REFERENCES.md)

Descreva sua ideia diretamente. A skill vai fazer perguntas complementares e criar o `REFERENCES.md` automaticamente.

```
Quero analisar uma ideia de produto: um SaaS de gestão para clínicas 
odontológicas no Brasil. O público são dentistas donos de clínicas 
pequenas e médias (1-10 cadeiras). Tenho R$ 30 mil pra começar e sei 
programar. Me ajuda a decidir se sigo ou não com isso.
```

### Opção 2 — Com REFERENCES.md (recomendado)

Crie um arquivo `REFERENCES.md` na raiz do seu projeto com todas as informações sobre a ideia. Um template completo é fornecido em `references/references_template.md`.

```
Preciso de uma análise completa sobre minha plataforma. 
Já existe o REFERENCES.md no projeto com as informações.
```

### Informações mínimas necessárias

Para iniciar a análise, a skill precisa de pelo menos:

- **Ideia/produto** — o que faz e qual problema resolve
- **Público-alvo** — quem é o cliente
- **Mercado** — segmento ou setor

Quanto mais contexto (orçamento, time, concorrentes conhecidos, materiais de apoio), melhor a análise.

## Arquivos gerados

A skill gera **14 arquivos** organizados em 4 categorias:

```
REFERENCES.md                          # Informações coletadas e fontes
docs/
├── 01_overview.md                     # Visão geral, proposta de valor, modelo de negócio
├── 02_market_analysis.md              # TAM/SAM/SOM, tendências, timing, contexto competitivo
├── 03_product_strategy.md             # MVP, roadmap, diferenciação, stack tecnológico
├── 04_go_to_market.md                 # Lançamento 30-60-90 dias, canais, aquisição
├── 05_monetization.md                 # Modelos de receita, preços, projeções em 3 cenários
├── 06_risks.md                        # Riscos mapeados com probabilidade, impacto e mitigação
├── 07_benchmarks.md                   # Concorrentes, alternativas, cases de sucesso/fracasso
├── analysis/
│   ├── viability_score.md             # Score 0-10 em 6 dimensões + veredicto final
│   ├── strengths_weaknesses.md        # Forças e fraquezas reais
│   └── opportunities_threats.md       # Oportunidades, ameaças e cenários
├── investor/
│   ├── investor_thesis.md             # Tese de investimento: por que sim e por que NÃO
│   └── investor_deck.md               # Deck de investidor (15 slides em markdown)
└── presentation/
    └── pitch_deck.md                  # Pitch resumido (8 slides, 5 minutos)
```

### Detalhes de cada arquivo

| Arquivo | Propósito | Conteúdo principal |
|---------|-----------|-------------------|
| `01_overview.md` | Resumo executivo | Problema, proposta de valor, modelo de negócio, conclusão inicial |
| `02_market_analysis.md` | Dimensionamento | TAM/SAM/SOM com fontes, tendências, oportunidade real vs hype |
| `03_product_strategy.md` | O que construir | MVP ideal, roadmap (MVP→V1→Escala), stack tecnológico |
| `04_go_to_market.md` | Como lançar | Plano 30-60-90 dias, primeiros 100 clientes, canais prioritários |
| `05_monetization.md` | Como ganhar dinheiro | Modelos de receita, pricing, projeções mensais em 3 cenários |
| `06_risks.md` | O que pode dar errado | Riscos categorizados com probabilidade/impacto/mitigação |
| `07_benchmarks.md` | Concorrência | Concorrentes diretos/indiretos, tabela comparativa, cases |
| `viability_score.md` | Nota final | Score ponderado 0-10 em 6 dimensões + veredicto |
| `strengths_weaknesses.md` | Forças/fraquezas | Análise SWOT focada em pontos internos |
| `opportunities_threats.md` | Oportunidades/ameaças | Análise SWOT focada em pontos externos + cenários |
| `investor_thesis.md` | Para investidores | Tese, argumentos pró/contra, perfil de investidor ideal |
| `investor_deck.md` | Apresentação completa | 15 slides estruturados para pitch de investimento |
| `pitch_deck.md` | Apresentação rápida | 8 slides para pitch de 5 minutos |

## Score de viabilidade

A skill avalia cada produto em **6 dimensões** com nota de 0 a 10:

| Dimensão | O que avalia |
|----------|-------------|
| **Dor do problema** | A dor é real? Quantas pessoas sentem? Quanto pagam pra resolver? |
| **Facilidade de venda** | É fácil convencer alguém a comprar? Os canais estão acessíveis? |
| **Potencial de monetização** | Tem modelo de receita viável? O mercado paga quanto? |
| **Velocidade de execução** | Dá pra lançar rápido com os recursos disponíveis? |
| **Diferenciação** | O que torna difícil de copiar? Existe moat? |
| **Escalabilidade** | Cresce sem custo marginal proporcional? |

O veredicto final é binário: **Vale apostar** ou **Não vale apostar**, sempre com justificativa.

### Exemplo de resultado

```markdown
| Dimensão                  | Score | Justificativa                                           |
|---------------------------|-------|---------------------------------------------------------|
| Dor do problema           | 8/10  | Inadimplência condominial de 11,95% — recorde histórico |
| Facilidade de venda       | 5/10  | Setor conservador, ciclo de decisão longo               |
| Potencial de monetização  | 7/10  | LTV/CAC de 20x+, modelo de assinatura comprovado        |
| Velocidade de execução    | 6/10  | MVP em 4 meses é agressivo mas factível                 |
| Diferenciação             | 5/10  | PIX-first é temporal, IA ainda não existe no MVP        |
| Escalabilidade            | 7/10  | SaaS escala bem, mas onboarding exige esforço humano    |
| **Média geral**           | **6,3/10** |                                                    |

### **Vale apostar — com condições.**
```

## Exemplos de uso reais

A skill foi testada com 3 cenários distintos. Abaixo os resultados:

### Cenário 1 — SaaS para clínicas odontológicas

**Prompt:** *"SaaS de gestão para clínicas odontológicas, R$ 30k de orçamento, dev solo"*

**Resultado:**
- **Score:** 4,7/10 — **Não vale apostar**
- Identificou 8+ concorrentes reais (Simples Dental, Clinicorp, Codental, Capim, BlueDental)
- Apontou mercado em fase de consolidação (Capim captou US$ 27M, Henry Schein adquiriu players)
- Sugeriu alternativas: nichar em ortodontia, construir ferramenta complementar, ou aplicar IA em prontuários

### Cenário 2 — Marketplace de cabos eleitorais

**Prompt:** *"App pra conectar cabos eleitorais com candidatos. Orçamento zero, dev fullstack."*

**Resultado:**
- **Score:** 3,7/10 — **Não vale apostar**
- Identificou 3 riscos FATAIS: sazonalidade extrema (3 meses a cada 2 anos), cold start impossível, desintermediação via WhatsApp
- Pesquisou legislação eleitoral (Lei 9.504/97, Lei 13.877/2019, resoluções do TSE)
- Sugeriu pivôs concretos: ferramenta de compliance eleitoral, infoproduto, ou SaaS de gestão de mandato

### Cenário 3 — Plataforma de gestão de condomínios

**Prompt:** *"Análise completa da plataforma CondoGestor"* (com REFERENCES.md preenchido)

**Resultado:**
- **Score:** 6,3/10 — **Vale apostar, com condições**
- Identificou 5+ concorrentes (Superlógica, TownSq, CondoConta, uCondo, Condomínio21)
- Pesquisou dados de mercado (327 mil condomínios, inadimplência de 11,95%)
- Projeções de receita em 3 cenários com tabelas mensais para 12 meses
- Condições claras: contratar advisor do setor, manter MVP enxuto, dedicar 50% do tempo a vendas

## Princípios da análise

A skill segue 8 princípios que garantem qualidade:

1. **Não seja genérico.** Dados específicos, concorrentes reais, números concretos.
2. **Não valide à força.** Se a ideia tem problemas, diz claramente.
3. **Questione premissas.** "Todo mundo precisa" não é validação.
4. **Priorize pragmatismo.** Foco em ganhar dinheiro, não em teoria.
5. **Use benchmarks.** Números, referências, comparações reais.
6. **Pense como operador.** Ações concretas, não apenas análise.
7. **Seja honesto sobre formato.** Se não é SaaS, recomenda o que for melhor.
8. **Conclusões em cada seção.** Toda seção termina com veredicto acionável.

## REFERENCES.md — Template

O arquivo `REFERENCES.md` é o ponto de entrada da análise. Ele centraliza todas as informações do projeto. A skill inclui um template completo em `references/references_template.md` com as seguintes seções:

- **Ideia / Produto** — nome, descrição, estágio atual
- **Público-Alvo** — cliente ideal, dor principal, como resolve hoje
- **Mercado** — segmento, região, regulamentação
- **Objetivo** — validar, monetizar, captar investimento
- **Recursos Disponíveis** — orçamento, time, habilidades
- **Concorrentes Conhecidos** — tabela com nome, URL, modelo, preço
- **Materiais de Apoio** — arquivos locais, links externos
- **Contexto Adicional** — insights, hipóteses, restrições

Se o `REFERENCES.md` não existir, a skill coleta as informações via conversa e cria o arquivo automaticamente.

## Benchmarks

A skill foi avaliada em testes comparativos (com skill vs sem skill):

| Métrica | Com Skill | Sem Skill |
|---------|-----------|-----------|
| Arquivos gerados | 14 (estrutura padronizada) | 8-10 (ad-hoc) |
| Subpastas organizadas | analysis/, investor/, presentation/ | Nenhuma |
| Conclusão por seção | 100% (7/7) | 14% (1/7) |
| Concorrentes encontrados | 5-8 por análise | 5-8 por análise |
| Score de viabilidade | Tabela padronizada 6 dimensões | Formato variável |
| Acentuação pt-BR | Correta | Inconsistente |
| Tempo médio | ~13 minutos | ~10 minutos |

A principal vantagem da skill é **consistência e completude** — toda análise sai no mesmo formato, com a mesma profundidade, com conclusões acionáveis.

## Estrutura da skill

```
digital-product-analysis/
├── SKILL.md                           # Instruções da skill (o "cérebro")
├── README.md                          # Este arquivo
└── references/
    └── references_template.md         # Template do REFERENCES.md
```

## Requisitos

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (CLI ou IDE)
- Acesso à internet (para pesquisa de mercado)
- Ferramentas WebSearch e WebFetch disponíveis (para buscar concorrentes, legislação, dados)

## Idioma

Toda a saída é gerada em **pt-BR** com acentuação e ortografia corretas.

## Licença

MIT
