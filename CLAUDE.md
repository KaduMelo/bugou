# CLAUDE.md — Bugou

Marketplace de produtos digitais ultra acessíveis (até R$1,99) · Dopamine Commerce · Discovery-first · Compra impulsiva instantânea

---

## O que é o Bugou

Plataforma marketplace inspirada nas antigas "lojas de 1,99", aplicada ao ambiente digital. Não é um marketplace racional — é um mecanismo de descoberta, impulso e compra instantânea de micro utilidades digitais.

**Posicionamento:** "A Shopee dos produtos digitais baratos."

O diferencial não é profundidade de produto. É:
- volume de catálogo
- preço que elimina fricção de decisão
- entrega instantânea
- feed de descoberta contínua
- sensação de oportunidade ("bugou de tão barato")

**Produtos vendidos:** templates, packs de IA, prompts, ebooks, automações, assets, planilhas, presets, kits digitais, micro ferramentas

---

## Hipótese Central

O usuário não quer pensar, comparar ou arriscar. O preço extremamente baixo:
- elimina medo de compra
- reduz tempo de decisão para segundos
- dispensa necessidade de confiança profunda
- transforma curiosidade em conversão

---

## Personas Principais

### Pedro — O Caçador de Oportunidades
- 23 anos, estudante/trabalha remoto
- consome TikTok/Instagram compulsivamente
- compra por curiosidade, ama "achados"
- zero tolerância para checkout longo
- **JTBD:** "Quando vejo algo barato e útil, quero comprar instantaneamente antes de perder."

### Ana — A Micro Empreendedora
- 31 anos, vende no Instagram/WhatsApp
- precisa de packs, templates e artes para produção rápida
- **JTBD:** "Quando preciso postar rápido, quero assets baratos sem contratar designer."

### Rafael — O Heavy User de IA
- 26 anos, usa ChatGPT diariamente
- compra prompts, packs e automações
- **JTBD:** "Quando encontro algo que economiza meu tempo, quero testar sem investir muito."

---

## Loop de Crescimento Principal

```
TikTok/Reels
→ "olha isso por R$1,99"
→ curiosidade
→ compra instantânea (< 45s)
→ exploração do feed
→ mais produtos
→ compartilhamento
→ novos usuários
```

---

## Features Estratégicas (por prioridade)

### 1. Compra ultra rápida
- Pix 1-click
- checkout invisível
- sem cadastro obrigatório inicial

### 2. Feed infinito de descoberta
- modelo TikTok/Shopee/AliExpress
- discovery > busca
- algoritmo de impulso

### 3. Sensação de escassez/oportunidade
- "acabando", "comprado 324x hoje", "viral", "bugou de verdade"
- timers, trending badges

### 4. Entrega instantânea
- a experiência precisa parecer mágica
- automação end-to-end no delivery

### 5. Bundle automático
- "prompt pack + template + automação"
- "leve 5 por R$6,99"

---

## Métricas Norteadoras

| Métrica | Objetivo |
|---|---|
| GMV mensal | crescimento do marketplace |
| Taxa de recompra D30 | principal indicador de hábito |
| Produtos por pedido | medir impulso |
| Tempo até primeira compra | ativação |
| Conversão visitante → compra | eficiência da vitrine |
| % compras em < 5 min | força da proposta impulsiva |
| CAC | eficiência viral/social |
| Uploads por semana | expansão do catálogo |
| Refund rate | confiança e qualidade |

**Metas de referência:**
- Conversão visitante → compra: 6%
- Recompra D30: 35%
- Checkout < 45 segundos
- Produtos por carrinho: 3+
- Ticket médio: R$4–R$9

---

## OKRs Fase Inicial

| Objetivo | KRs-chave |
|---|---|
| Validar compra impulsiva | 25k compras/mês, conversão 6%, checkout < 45s |
| Criar hábito de descoberta | Recompra D30 35%, 4+ sessões/semana |
| Escalar catálogo | 50k produtos ativos, onboarding seller < 10min |
| Construir marca cultural | 100k seguidores TikTok, 15% tráfego via sharing |

---

## Competidores e Posicionamento

| Competidor | Relação | O que aprender | O que superar |
|---|---|---|---|
| DFG Games | mais direto | volume, SEO, cauda longa | UX, discovery, branding |
| GhostDigital | modelo similar | cultura "barato", percepção oportunidade | confiança, reputação |
| Shopee | referência de UX | dopamine commerce, feed infinito | foco digital-first |
| Hotmart | mercado adjacente | confiança, pagamentos | ticket alto, cursos longos |
| Etsy | referência assets | curadoria, creators | preço acessível, impulso |

---

## Riscos Críticos

| Risco | Tipo | Mitigação |
|---|---|---|
| Catálogo virar spam/lixo digital | Qualidade | curadoria leve + score de reputação + moderação automática |
| Direitos autorais / conteúdo pirateado | Regulatório | DMCA simplificado + detecção automática + score de risco por seller |
| Commoditização extrema comprime margem | Negócio | bundles, gamificação, assinatura, sellers premium |
| Fraude no checkout | Segurança | velocity check, fingerprint, regras anti-fraude no gateway |

---

## Stack e Decisões Técnicas (Diretrizes)

**Princípios inegociáveis:**
- Performance é produto: latência de feed e checkout impacta diretamente conversão
- Mobile-first: 80%+ do tráfego virá de mobile via TikTok/Reels
- Entrega automatizada: delivery manual não escala
- Checkout sem atrito: cada campo a mais é conversão perdida

**Decisões já tomadas:**
- Pix como método principal de pagamento
- Entrega digital automática via link/token pós-pagamento
- Feed algorítmico como interface principal (não busca)
- Onboarding seller < 10 minutos

---

## Padrões de Comunicação para este Contexto

**Tom do produto:** irreverente, coloquial, urgente, oportunístico
- "Bugou de tão barato"
- "Corre que tá acabando"
- "R$1,99 e você ainda tá pensando?"

**Tom interno (specs, PRDs, análises):**
- Técnico, direto, sem corporateês
- Sempre conectar feature com métrica de negócio
- Priorizar velocidade de aprendizado (Build → Measure → Learn)

---

## Comandos Rápidos

- `/prd [feature]` → PRD estruturado com 10 seções
- `/arch [componente]` → Arquitetura com trade-offs
- `/analise [métrica]` → Análise técnica/negócio profunda
- `/copy [contexto]` → Copy para produto/social no tom Bugou
- `/okr` → Review e diagnóstico de OKRs
- `/benchmark [competidor]` → Análise competitiva
- `/exec` → Executive summary para liderança

---

## O que NÃO fazer

- Não propor features complexas sem validar impulso primeiro
- Não adicionar fricção no checkout sob nenhuma justificativa
- Não tratar o Bugou como marketplace educacional (não é Hotmart)
- Não priorizar profundidade de produto sobre volume e velocidade
- Não ignorar mobile ao desenhar qualquer fluxo
- Não construir POC de feature sem métricas de sucesso definidas
- Não sugerir UX "clean minimalista" sem considerar o engajamento de dopamine commerce

---

## Próximos Horizontes Estratégicos

- [ ] Assinatura mensal ("Bugou Club") para compradores frequentes
- [ ] Programa de afiliados/creators
- [ ] Sellers premium com visibilidade ampliada
- [ ] Gamificação: badges, streaks, colecionáveis digitais
- [ ] Bundles automáticos por IA (cross-sell inteligente)
- [ ] Expansão para LATAM (Argentina, México)