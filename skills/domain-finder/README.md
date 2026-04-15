# Domain Finder

Skill que analisa a descrição de um projeto e gera uma lista das 10 melhores opções de domínios disponíveis para registro, validando cada um via WHOIS em tempo real.

## O que faz

A skill atua como um **especialista em branding, naming e estratégia digital**. A partir de uma descrição de projeto, ela:

1. Coleta informações sobre o projeto, público-alvo e mercado
2. Gera 20+ candidatos de domínio em 5 estilos diferentes
3. Valida cada candidato via WHOIS real em até 3 TLDs (.com, .com.br e TLD estratégico)
4. Retorna exatamente 10 domínios disponíveis, ordenados por qualidade
5. Inclui recomendação com Top 3, sugestão de registro prioritário e dica estratégica

### Diferenciais

- **Validação real.** Cada domínio é verificado via `whois` — nada é assumido.
- **Multi-TLD.** Verifica .com, .com.br e o TLD mais estratégico para o projeto (.ai, .dev, .io, .app, .me).
- **Diversidade criativa.** Gera nomes em 5 estilos: descritivo, brandável, híbrido, composto e neologismo.
- **Pronta para registro.** A lista final contém apenas domínios que você pode registrar agora.

## Como usar

Descreva seu projeto e a skill cuidará do resto. As informações mínimas necessárias são:

- **Descrição do projeto** — o que é, o que faz
- **Público-alvo** — para quem é

Contexto de mercado e palavras-chave são opcionais (a skill deduz quando não fornecidos).

### Exemplos de prompts

**SaaS B2B:**
```
Estou criando um SaaS de gestão financeira para pequenas e médias 
empresas brasileiras. O foco é simplificar o fluxo de caixa, contas 
a pagar/receber e conciliação bancária. Público-alvo: empreendedores 
e contadores.
```

**App com IA:**
```
Quero lançar um app que usa inteligência artificial pra criar planos 
alimentares personalizados. O público são pessoas que querem emagrecer 
ou ganhar massa muscular mas não têm grana pra nutricionista. 
Mercado brasileiro.
```

**Plataforma para devs:**
```
Preciso de um nome pro meu projeto: uma plataforma de cursos práticos 
de programação, tipo hands-on com projetos reais. Público são devs 
junior e pleno que querem subir de nível. Palavras-chave: código, 
prática, carreira, evolução.
```

## Formato de saída

A skill retorna uma tabela com exatamente 10 domínios validados:

| # | Nome Base | TLD Principal | Status TLD | .com | .com.br |
|---|-----------|---------------|------------|------|---------|
| 1 | caixaly   | caixaly.com   | Disponível | Disponível | Disponível |
| 2 | kontfy    | kontfy.com    | Disponível | Disponível | Disponível |
| 3 | banqfy    | banqfy.com    | Indisponível | Indisponível | Disponível |

Onde:
- **Nome Base** — nome do domínio sem extensão
- **TLD Principal** — extensão mais estratégica para o projeto
- **Status TLD** — disponibilidade do TLD principal
- **.com / .com.br** — disponibilidade em cada extensão

Após a tabela, uma seção **Recomendação** com:
- Top 3 favoritos com justificativa
- Sugestão de qual registrar primeiro
- Dica estratégica de proteção de marca

## Regras de geração

### Critérios de qualidade dos nomes

- Até 12 caracteres (sem TLD)
- Fácil pronúncia e memorização
- Sem hífens nem números
- Sem conflito com marcas conhecidas

### Estilos explorados

| Estilo | Descrição | Exemplo |
|--------|-----------|---------|
| Descritivo | Comunica o que o produto faz | `taskboard`, `codeflow` |
| Brandável | Inventado, sonoro, com personalidade | `votely`, `campaigo` |
| Híbrido | Palavra real + sufixo/prefixo criativo | `campaignhub`, `votestack` |
| Composto | Duas palavras curtas juntas | `quickpoll`, `smartvote` |
| Neologismo | Palavra nova inspirada no conceito | `appify`, `launchly` |

### Estratégia de TLDs

| TLD | Quando é escolhido como principal |
|-----|-----------------------------------|
| `.com` | Padrão universal — sempre considerado |
| `.com.br` | Mercado brasileiro — sempre considerado |
| `.io` | SaaS, ferramentas para devs, tecnologia |
| `.ai` | Produtos com inteligência artificial |
| `.dev` | Ferramentas para desenvolvedores |
| `.app` | Aplicativos e produtos digitais |
| `.me` | Engajamento pessoal, portfólios |

### Regras de filtragem

- Um domínio só entra na lista se pelo menos **.com** ou **.com.br** estiver disponível
- Domínios onde apenas o TLD alternativo (.ai, .io, .dev) está livre são descartados
- Domínios com todas as variações registradas são rejeitados
- Prioridade de ordenação: disponibilidade do .com > qualidade de marca > simplicidade

## Benchmarks

A skill foi avaliada em 3 cenários distintos (SaaS financeiro, app de IA, plataforma para devs):

| Métrica | Com Skill | Sem Skill |
|---------|-----------|-----------|
| Pass rate das assertions | 100% | 68% |
| Verificação multi-TLD | Sempre (3 TLDs) | Parcial (1 TLD) |
| Coluna Status TLD | Presente | Ausente |
| TLD estratégico correto | 100% (.ai para IA, .dev para devs) | 0% |
| Limite de 12 caracteres | Respeitado | Violado (13 chars) |
| Acentuação pt-BR | Correta | Inconsistente |
| Formato da tabela | Padronizado | Variável |

## Estrutura da skill

```
domain-finder/
├── SKILL.md                # Instruções da skill
├── README.md               # Este arquivo
```

## Requisitos

- Comando `whois` disponível no terminal

## Idioma

Toda a saída é gerada em **pt-BR** com acentuação e ortografia corretas.

## Licença

MIT
