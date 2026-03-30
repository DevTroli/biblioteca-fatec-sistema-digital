# 📋 Milestone 0 — Planejamento
**Palácio Mental · Projeto Integrador · Engenharia de Software · Fatec Praia Grande**
> Status: ✅ Em andamento · Prof. Marcio Galvão · DSM 2026

---

## Framework CLEAR

### C — Clarificar a Visão

**Nome do Projeto:** Palácio Mental
> *Referência ao "palace of memory" — técnica de organizar informações em um espaço mental estruturado. Traduz a proposta: um lugar onde ideias deixam de ser rascunho e passam a existir.*

**Proposta de valor em uma frase:**
*Para estudantes que veem seus projetos acadêmicos serem esquecidos após a entrega, o Palácio Mental é uma rede de compartilhamento que cria um portfólio vivo ao longo do curso. Diferente do GitHub (focado em código), LinkedIn (genérico) e Behance (design), nossa plataforma é centrada no projeto acadêmico num geral durante seu processo, ideia, evolução.*

**Problema:**
Projetos acadêmicos morrem num ZIP depois da entrega. para outros estudantes compartilharem o que estão construindo, descobrirem o que os colegas fazem e receberem feedback técnico da comunidade.

**Usuários primários:**

| Perfil | Necessidade | Frustração atual |
|---|---|---|
| Estudante de tecnologia | Mostrar o que produziu | Projeto some após a entrega |
| Estudante iniciante | Ver o que colegas avançados fazem | Não há feed acadêmico de tecnologia |
| Professor / orientador | Acompanhar o progresso além da sala | Sem visibilidade extraclasse |
| Recrutador / empresa | Descobrir talentos emergentes | Portfólios acadêmicos dispersos |

**Critérios de sucesso:**
- [ ] `[A definir com o grupo]` — Métrica de adoção
- [ ] `[A definir com o grupo]` — Métrica de uso ativo

---

### L — Listar componentes essenciais (MoSCoW)

**MUST — sem isso o MVP não funciona:**
- Cadastro, login e logout de usuários
- Publicação de projetos (título, descrição, status, categoria, tags)
- Feed público com filtros por categoria e tag
- Perfil do usuário com lista de projetos ("Palácio Mental")
- Curtidas, salvos e comentários em projetos
- Mídia associada via URL

**SHOULD — faremos se der tempo no MVP:**
- Busca por texto, categoria ou tag
- Histórico de versões de projetos
- Notificações básicas (curtidas e comentários)

**COULD — seria legal, não é prioridade:**
- Scroll infinito no feed
- Estatísticas do perfil
- Botão de reportar conteúdo

**WON'T — fora desta versão:**
- App mobile nativo
- Chat em tempo real
- Integração com redes sociais externas
- Sistema de licenciamento de ideias

---

### E — Estabelecer a arquitetura conceitual

```
┌──────────────────────────────────────────────────────┐
│  BANCO DE DADOS   Oracle APEX + campo URL de mídia   │  ← Fase 1 ✅
├──────────────────────────────────────────────────────┤
│                     SQL / REST                        │
├──────────────────────────────────────────────────────┤
│  BACKEND          Auth · API REST · Busca nativa      │  ← Fase 2 🔄 
├──────────────────────────────────────────────────────┤
│                   JSON via browser                    │
├──────────────────────────────────────────────────────┤
│  FRONTEND         Feed · Ideia · Perfil · Editor      │  ← Fase 3
├──────────────────────────────────────────────────────┤
│                   containerizado                      │
├──────────────────────────────────────────────────────┤
│  DEVOPS           Docker · Terraform · CI/CD          │  ← Fase 4
└──────────────────────────────────────────────────────┘
```

**Stack definida até agora:**

| Camada | Decisão | Status |
|---|---|---|
| Banco de Dados | Oracle XE + Oracle APEX | ✅ Confirmado |
| Modelagem | BrModelo + DBDesigner | ✅ Confirmado |
| Backend | PHP/Laravel | 🔲 A validar |
| Frontend | `[A definir na Fase 3]` | 🔄  pensando... |
| DevOps | Docker + Terraform + GitHub Actions | 🔲 A validar |

---

### A — Atribuir responsabilidades

| Papel | Membro |
|---|---|
| `Database Lead` | Pablo Troli |
| `BackEnd` | Felipe Figueiredo |
| `FrontEnd Lead` | Iago Sampaio |
| `DevOps Lead` | Matheus Fernandes |
| `UI/UX Designer` | Yohan Ruiz |
| `BackEnd Lead` | Eduardo Elias |

---

### R — Roadmap de Milestones

| Fase | Entregável principal | Período | Status |
|---|---|---|---|
| 0 — Planejamento | Visão, escopo, CLEAR, equipe | Março/2026 | ✅ |
| 1 — Banco de Dados | Conceitual + Lógico + DDL + Docs | Abril/2026 | ✅ |
| 2 — Backend | API REST + Autenticação | Abr/2026 | 🔄  |
| 3 — Frontend | Interface — 4 telas principais | Mai/2026 | 🔲 |
| 4 — DevOps | Docker + CI/CD + Deploy | Jun/2026 | 🔲 |

---

## ✅ Checklist de conclusão

- [x] Nome do projeto decidido e justificado
- [X] Proposta de valor articulada
- [x] Público-alvo definido
- [X] MoSCoW definido
- [x] Arquitetura conceitual desenhada
- [x] Repositório GitHub criado e workflow de Git definido
- [X] Métricas de sucesso definidas com o grupo
- [X] Stack de Backend confirmada
- [ ] Stack de Frontend confirmada
- [X] Todos os papéis preenchidos
