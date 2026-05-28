<!--
SYNC IMPACT REPORT
==================
Version change: TEMPLATE (uninitialized) → 1.0.0
Bump rationale: First ratification — populating placeholders with concrete principles.
   MINOR-equivalent (initial baseline), expressed as 1.0.0 by convention.

Modified principles (vs. template placeholders):
   [PRINCIPLE_1] → I. Frictionless by Default (NON-NEGOTIABLE)
   [PRINCIPLE_2] → II. Performance Is Product
   [PRINCIPLE_3] → III. Discovery-Driven Experience
   [PRINCIPLE_4] → IV. Build → Measure → Learn
   [PRINCIPLE_5] → V. Automated Delivery & Marketplace Trust

Added sections:
   - Product & Platform Standards (replaces [SECTION_2])
   - Development Workflow & Quality Gates (replaces [SECTION_3])
   - Governance (filled)

Removed sections: none (only placeholder replacement).

Templates requiring updates:
   ✅ .specify/templates/plan-template.md — Constitution Check rewritten to gate on the 5 principles
   ✅ .specify/templates/spec-template.md — Already enforces measurable Success Criteria (aligns with P-IV); no edit
   ✅ .specify/templates/tasks-template.md — Task structure already supports performance/automation tasks; no edit
   ✅ CLAUDE.md — Existing product doctrine aligned with these principles; no edit
   ✅ .specify/templates/checklist-template.md — Generic checklist; no edit needed

Follow-up TODOs: none.
-->

# Bugou Constitution

Marketplace de produtos digitais ultra acessíveis (até R$1,99) — dopamine commerce,
discovery-first, compra impulsiva instantânea. Esta constituição é a fonte autoritativa
de princípios não-negociáveis para qualquer feature, decisão técnica ou de produto.

## Core Principles

### I. Frictionless by Default (NON-NEGOTIABLE)

Toda interação que precede ou compõe uma compra MUST minimizar fricção cognitiva e
operacional. O preço-âncora elimina o medo de compra; a UX não pode reintroduzi-lo.

Regras invioláveis:
- Checkout MUST completar em < 45 segundos (mediana p50) no fluxo principal mobile.
- Cadastro obrigatório anterior à primeira compra é PROIBIDO; identidade é capturada
  no menor momento possível (preferencialmente pós-pagamento, via Pix).
- Cada campo, clique, modal ou confirmação adicional MUST justificar sua existência
  com hipótese mensurável de conversão. Justificativas baseadas em "boas práticas
  genéricas" ou conforto interno NÃO são aceitas.
- Métodos de pagamento que adicionem mais de 2 toques além do Pix MUST ser
  experimentos opt-in, nunca padrão.

**Rationale**: A tese central do Bugou é que o preço R$1,99 só converte se a
fricção for próxima de zero. Qualquer atrito a mais derrota o modelo de negócio.

### II. Performance Is Product

Latência percebida em feed, mídia e checkout é tratada como feature de produto,
não como concern técnico. Performance ruim É um bug de conversão.

Regras invioláveis:
- Feed inicial MUST renderizar conteúdo útil em ≤ 1.5s (LCP p75) em rede 4G
  comum BR e dispositivos Android de baixo/médio range.
- API crítica (feed, detalhe de produto, criação de pedido, confirmação Pix)
  MUST manter p95 ≤ 300ms em condições nominais.
- Toda PR que altera caminho crítico MUST declarar impacto esperado em latência
  e tamanho de payload. Regressões > 10% MUST ser justificadas ou bloqueadas.
- Mobile-first é literal: layouts, assets, scripts e jornadas são desenhados
  primeiro para mobile (≥ 80% do tráfego) e adaptados a desktop, nunca o inverso.

**Rationale**: 80%+ do tráfego virá de TikTok/Reels em mobile com conexões
heterogêneas. Cada 100ms perdidos no caminho crítico custa conversão real.

### III. Discovery-Driven Experience

A interface primária é o feed algorítmico de descoberta, não a busca. Dopamine
commerce (escassez, urgência, prova social, badges) é UX central — não decoração.

Regras invioláveis:
- Busca é uma feature secundária; nenhuma jornada principal pode assumir que o
  usuário sabe o que procurar.
- Sinais sociais e de escassez ("comprado 324x hoje", "viral", "acabando",
  "bugou de verdade") MUST estar presentes em superfícies de listagem e
  detalhe sempre que houver dados reais que os sustentem.
- Sinais falsos, inflados ou manipulados são PROIBIDOS. Se o dado real não
  existe, o badge não aparece.
- Propostas de UX "clean minimalista" que removem stimuli de engajamento MUST
  ser explicitamente justificadas contra a tese de dopamine commerce e
  testadas com métricas — nunca adotadas por default estético.

**Rationale**: O produto não é "navegar um catálogo"; é "ser puxado para a
próxima compra impulsiva". A UX precisa orquestrar esse loop.

### IV. Build → Measure → Learn

Toda feature MUST declarar hipótese mensurável e métrica de sucesso antes do
merge. Velocidade de aprendizado > velocidade de construção.

Regras invioláveis:
- Toda spec MUST conter Success Criteria mensuráveis e tecnologicamente
  neutros (alinhado ao spec-template).
- Nenhuma POC, MVP ou experimento entra em produção sem (a) métrica primária,
  (b) janela de avaliação definida, (c) critério explícito de
  manutenção/iteração/remoção.
- Features sem evidência de ganho na janela de avaliação MUST ser revisitadas
  para iteração ou remoção; código órfão não é mantido por inércia.
- Métricas norteadoras do produto (conversão visitante→compra, recompra D30,
  checkout < 45s, produtos por carrinho, refund rate) MUST ser referenciadas
  quando aplicável; features que não impactam métrica conhecida MUST declarar
  qual nova métrica passam a observar.

**Rationale**: Marketplace de impulso vive ou morre por iteração rápida sobre
dados. Construir sem medir é desperdício caro.

### V. Automated Delivery & Marketplace Trust

A magia percebida do Bugou — comprar e receber em segundos — depende de
entrega digital 100% automatizada e de salvaguardas de confiança que protejam
ambos os lados do marketplace sem reintroduzir fricção ao comprador.

Regras invioláveis:
- Toda categoria de produto digital ofertada MUST possuir pipeline de entrega
  automática (link/token/arquivo) pós-confirmação de pagamento. Entrega
  manual é PROIBIDA em escala; pilotos manuais são tolerados apenas com
  prazo de automação definido.
- Onboarding de seller MUST permitir publicação do primeiro produto em
  ≤ 10 minutos.
- Anti-fraude (velocity check, fingerprint, regras de gateway) e moderação
  automatizada (detecção de pirataria, score de risco por seller) MUST
  existir como parte do caminho crítico — não como afterthought.
- Processo de DMCA / takedown MUST ser acionável em ≤ 24h úteis; reincidência
  de seller MUST degradar reputação e visibilidade no feed.
- Refund e disputa MUST ter caminho self-service alinhado ao tom do produto;
  fricção em refund corrói confiança e impulso futuro.

**Rationale**: Sem entrega automatizada não há escala; sem confiança não há
recompra. Ambos sustentam a recompra D30, que é o principal indicador de
hábito do produto.

## Product & Platform Standards

Padrões inegociáveis derivados dos princípios acima:

- **Pagamento**: Pix é o método primário e default. Outros métodos são
  experimentos secundários e nunca podem competir por destaque no checkout.
- **Mobile-first literal**: Toda jornada é desenhada, prototipada e validada
  primeiro em viewport mobile, em dispositivo representativo do público
  brasileiro (não apenas em DevTools). Desktop é adaptação, não baseline.
- **Tom de produto**: Comunicação para o usuário final segue o tom Bugou
  (irreverente, coloquial, urgente, oportunístico). Microcopy de erro, vazio
  e confirmação são tratados como superfícies de marca, não strings utilitárias.
- **Catálogo**: O sistema favorece volume e velocidade sobre profundidade.
  Curadoria leve, score de reputação por seller, e moderação automática são
  preferidos a gatekeeping editorial pesado.
- **Bundles e gamificação** (escassez, badges, streaks, "leve 5 por R$6,99")
  são alavancas de primeira classe de produto, não enfeites.
- **Tom interno** (PRDs, specs, análises): técnico, direto, sem corporateês;
  toda feature conecta-se a uma métrica de negócio explícita.

## Development Workflow & Quality Gates

Como a constituição é aplicada no fluxo de trabalho:

- **Spec Gate**: Toda feature começa por `/speckit-specify`. A spec MUST conter
  user stories priorizadas (P1 sendo MVP independente), Success Criteria
  mensuráveis e Assumptions explícitas. Specs que falham essas exigências
  MUST passar por `/speckit-clarify` antes do plano.
- **Plan Gate (Constitution Check)**: `/speckit-plan` MUST avaliar a feature
  contra cada um dos 5 princípios e registrar violações justificadas na seção
  "Complexity Tracking". Violações de P-I (Frictionless) e P-II (Performance)
  exigem aprovação explícita de produto, não apenas justificativa técnica.
- **Tasks Gate**: `/speckit-tasks` MUST incluir, quando aplicável, tarefas
  explícitas de instrumentação (telemetria, dashboards) e de orçamento de
  performance — não como polish, mas como parte da story que as exige.
- **Pre-Merge Quality**: Toda mudança em caminho crítico (feed, detalhe,
  checkout, delivery) MUST declarar impacto esperado em latência e em ao
  menos uma métrica norteadora. Mudanças sem instrumentação correspondente
  MUST ser rejeitadas.
- **Post-Ship Review**: Features são revisitadas dentro da janela de
  avaliação declarada; ausência de revisão é tratada como violação de P-IV.
- **Auto-commit hooks**: Os hooks do Spec Kit (`.specify/extensions.yml`)
  podem auto-commitar artefatos entre etapas; isso é desejado para
  rastreabilidade e NÃO substitui revisão humana antes de merge.

## Governance

Esta constituição supersede convenções informais e preferências individuais.
Em conflito entre uma "boa prática genérica" e um princípio aqui declarado,
o princípio prevalece.

**Amendments**:
- Propostas de emenda MUST ser submetidas como PR alterando este arquivo,
  com (a) motivação explícita, (b) impacto em templates dependentes,
  (c) plano de migração para artefatos existentes que dependam do texto
  antigo, e (d) bump de versão proposto.
- Aprovação requer revisão de pelo menos um responsável de produto e um
  responsável técnico do Bugou.

**Versioning policy** (semantic versioning aplicado a governança):
- **MAJOR**: Remoção ou redefinição incompatível de princípio; mudança de
  governança que invalide artefatos prévios.
- **MINOR**: Novo princípio, nova seção, ou expansão material de regra
  existente.
- **PATCH**: Clarificações, correções de redação, refinamentos
  não-semânticos.

**Compliance review**:
- `/speckit-plan` aplica o Constitution Check como gate de planejamento.
- `/speckit-analyze` (quando executado) MUST sinalizar drift entre artefatos
  da feature e princípios atuais.
- Runtime guidance para colaboradores humanos e agentes vive em `CLAUDE.md`;
  divergência entre `CLAUDE.md` e esta constituição MUST ser resolvida a
  favor da constituição, com `CLAUDE.md` atualizado em seguida.

**Version**: 1.0.0 | **Ratified**: 2026-05-28 | **Last Amended**: 2026-05-28
