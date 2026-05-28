# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]

**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit-plan` command. See `.specify/templates/plan-template.md` for the execution workflow.

## Summary

[Extract from feature spec: primary requirement + technical approach from research]

## Technical Context

<!--
  ACTION REQUIRED: Replace the content in this section with the technical details
  for the project. The structure here is presented in advisory capacity to guide
  the iteration process.
-->

**Language/Version**: [e.g., Python 3.11, Swift 5.9, Rust 1.75 or NEEDS CLARIFICATION]

**Primary Dependencies**: [e.g., FastAPI, UIKit, LLVM or NEEDS CLARIFICATION]

**Storage**: [if applicable, e.g., PostgreSQL, CoreData, files or N/A]

**Testing**: [e.g., pytest, XCTest, cargo test or NEEDS CLARIFICATION]

**Target Platform**: [e.g., Linux server, iOS 15+, WASM or NEEDS CLARIFICATION]

**Project Type**: [e.g., library/cli/web-service/mobile-app/compiler/desktop-app or NEEDS CLARIFICATION]

**Performance Goals**: [domain-specific, e.g., 1000 req/s, 10k lines/sec, 60 fps or NEEDS CLARIFICATION]

**Constraints**: [domain-specific, e.g., <200ms p95, <100MB memory, offline-capable or NEEDS CLARIFICATION]

**Scale/Scope**: [domain-specific, e.g., 10k users, 1M LOC, 50 screens or NEEDS CLARIFICATION]

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

Avalie a feature contra cada princípio do Bugou Constitution (`.specify/memory/constitution.md`).
Para cada item, marque PASS / VIOLATION e justifique brevemente. Violações de P-I e P-II
exigem aprovação explícita de produto, não apenas justificativa técnica, e MUST ser
registradas em "Complexity Tracking" abaixo.

- **P-I — Frictionless by Default (NON-NEGOTIABLE)**: A feature mantém checkout < 45s,
  não introduz cadastro pré-compra obrigatório, e cada novo campo/clique/modal tem
  hipótese mensurável de conversão? [PASS/VIOLATION + nota]
- **P-II — Performance Is Product**: Caminho crítico afetado mantém LCP feed ≤ 1.5s
  (p75, 4G BR / Android mid-tier) e APIs críticas p95 ≤ 300ms? Impacto declarado em
  latência e payload? [PASS/VIOLATION + nota]
- **P-III — Discovery-Driven Experience**: A feature reforça (ou ao menos não suprime)
  o feed algorítmico e sinais de dopamine commerce reais? Nenhum sinal social/escassez
  é fabricado? [PASS/VIOLATION + nota]
- **P-IV — Build → Measure → Learn**: Hipótese, métrica primária, janela de avaliação
  e critério de manter/iterar/remover estão declarados na spec? Instrumentação prevista
  em Tasks? [PASS/VIOLATION + nota]
- **P-V — Automated Delivery & Marketplace Trust**: Se a feature toca catálogo,
  pagamento ou entrega, a entrega digital permanece 100% automatizada e as
  salvaguardas (anti-fraude, moderação, DMCA, refund self-service) seguem aplicáveis?
  [PASS/VIOLATION + N/A + nota]

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit-plan command output)
├── research.md          # Phase 0 output (/speckit-plan command)
├── data-model.md        # Phase 1 output (/speckit-plan command)
├── quickstart.md        # Phase 1 output (/speckit-plan command)
├── contracts/           # Phase 1 output (/speckit-plan command)
└── tasks.md             # Phase 2 output (/speckit-tasks command - NOT created by /speckit-plan)
```

### Source Code (repository root)
<!--
  ACTION REQUIRED: Replace the placeholder tree below with the concrete layout
  for this feature. Delete unused options and expand the chosen structure with
  real paths (e.g., apps/admin, packages/something). The delivered plan must
  not include Option labels.
-->

```text
# [REMOVE IF UNUSED] Option 1: Single project (DEFAULT)
src/
├── models/
├── services/
├── cli/
└── lib/

tests/
├── contract/
├── integration/
└── unit/

# [REMOVE IF UNUSED] Option 2: Web application (when "frontend" + "backend" detected)
backend/
├── src/
│   ├── models/
│   ├── services/
│   └── api/
└── tests/

frontend/
├── src/
│   ├── components/
│   ├── pages/
│   └── services/
└── tests/

# [REMOVE IF UNUSED] Option 3: Mobile + API (when "iOS/Android" detected)
api/
└── [same as backend above]

ios/ or android/
└── [platform-specific structure: feature modules, UI flows, platform tests]
```

**Structure Decision**: [Document the selected structure and reference the real
directories captured above]

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., 4th project] | [current need] | [why 3 projects insufficient] |
| [e.g., Repository pattern] | [specific problem] | [why direct DB access insufficient] |
