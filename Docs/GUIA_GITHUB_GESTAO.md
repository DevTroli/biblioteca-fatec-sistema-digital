# 🔧 Guia de Gestão do Projeto no GitHub

> **Propósito:** Ensinar a equipe a usar GitHub não apenas como repositório de código, mas como ferramenta completa de gestão de projeto.

### Repositório
- [ ] Criar repositório com nome descritivo (ex: `biblioteca-fatec` ou `projeto-biblioteca-digital`)
- [ ] Adicionar descrição clara
- [ ] Adicionar todos os 7 membros como colaboradores
- [ ] Tornar privado inicialmente (podem abrir depois se quiserem)

### Branches
- [ ] Criar branch `develop` a partir de `main`
- [ ] Definir `develop` como branch padrão para PRs

### Issues e Projects
- [ ] Criar issues conforme precise
- [ ] Criar projeto Kanban
- [ ] Configurar colunas do board
- [ ] Criar milestones para cada fase

### Automação
- [ ] Configurar auto-link de issues em PRs
- [ ] Configurar delete automático de branches após merge
- [ ] (Opcional) Configurar GitHub Actions básico

### Documentação
- [ ] Adicionar template de Pull Request
- [ ] Adicionar CONTRIBUTING.md (como contribuir)
- [ ] Adicionar LICENSE (se for open source)
- [ ] Adicionar documentos de cada milestone em /docs

---
## 📁 Proposta Estrutura do Repositório

Vocês vão criar um único repositório monorepo que contém tanto o backend quanto o frontend. A estrutura sugerida é:

```
biblioteca-fatec/
├── README.md                       # Documentação principal
├── .gitignore                      # Arquivos a ignorar
├── docs/                           # Toda documentação do projeto
│   ├── MILESTONE_0_PLANEJAMENTO.md
│   ├── MILESTONE_1_FUNDACAO.md
│   ├── ARQUITETURA.md
│   ├── API_DOCUMENTATION.md
│   └── USER_RESEARCH.md
├── backend/                        # Aplicação Java
│   ├── src/
│   ├── pom.xml                    # Dependências Maven
│   └── README.md                  # Instruções de setup do backend
├── frontend/                       # Aplicação FrontEnd
│   ├── src/
│   ├── package.json
│   └── README.md                  # Instruções de setup do frontend
├── database/                       # Scripts SQL
│   ├── migrations/
│   ├── seeds/
│   └── diagrams/
└── .github/                        # Configurações GitHub
    ├── ISSUE_TEMPLATE/            # Templates de issues
    ├── PULL_REQUEST_TEMPLATE.md   # Template de PR
    └── workflows/                 # GitHub Actions (CI/CD)
```

---

## 🎫 Sistema de Issues

Issues são tarefas individuais de trabalho. Uma issue pode ser "Implementar endpoint de login", "Criar tela de cadastro", "Corrigir bug na validação de email", etc.

### Anatomia de uma Boa Issue

Uma issue bem escrita tem cinco componentes:

**1. Título Claro e Específico:**
❌ Ruim: "Fazer login"
✅ Bom: "Implementar endpoint POST /auth/login no backend"

**2. Descrição do Problema/Necessidade:**
Explicar o contexto. Por que essa tarefa existe? Que problema resolve?

**3. Critérios de Aceitação:**
Como você vai saber que a tarefa está completa? Liste checkboxes.

**4. Informações Técnicas (se aplicável):**
Onde no código isso vai? Que arquivos serão afetados? Há alguma consideração especial?

**5. Labels Apropriados:**
Para categorizar e filtrar. Exemplos: `backend`, `frontend`, `bug`, `enhancement`, `documentation`, `priority-high`

### Template de Issue Sugerido

Criem um template em `.github/ISSUE_TEMPLATE/feature.md`:

```markdown
---
name: Nova Funcionalidade
about: Adicionar uma nova funcionalidade ao projeto
title: '[COMPONENTE] Breve descrição'
labels: enhancement
assignees: ''
---

## Descrição
[Explicar o que precisa ser feito e por quê]

## Critérios de Aceitação
- [ ] [O que deve funcionar quando isso estiver pronto]
- [ ] [Outro critério]
- [ ] [Mais um critério]

## Informações Técnicas
**Arquivos afetados:**
- `caminho/para/arquivo.java`
- `caminho/outro/arquivo.tsx`

**Dependências:**
Esta issue depende de #XX estar completa

## Notas Adicionais
[Qualquer informação extra útil]
```

### Como Criar e Atribuir Issues

**Quem cria issues?**
- Product Owner cria a maioria baseado no backlog
- Qualquer membro da equipe pode criar se identificar uma necessidade/bug
- Durante o Planning, a equipe pode discutir e criar issues juntos

**Como atribuir:**
1. Na página da Issue, clicar em "Assignees" do lado direito
2. Selecionar a pessoa responsável
3. Uma pessoa pode se auto-atribuir se a issue está desassignada
4. Evitar ter a mesma pessoa assigned a mais de 3 issues abertas simultaneamente

**Ciclo de vida de uma issue:**
1. Criada (status: Open)
2. Alguém é designado
3. Pessoa cria branch e começa a trabalhar
4. Pessoa abre Pull Request (PR) mencionando a issue (escrever "Closes #XX" no PR)
5. PR é revisado e mergeado
6. Issue automaticamente fecha quando PR é mergeado

---

## 📊 GitHub Projects (Kanban Board)

GitHub Projects permite criar quadros visuais estilo Trello dentro do GitHub.

### Como Configurar

1. Ir em "Projects" no repositório
2. Criar novo projeto: "Biblioteca FATEC - Development Board"
3. Escolher template "Board" (colunas)
4. Criar colunas:
   - **Backlog**: Issues identificadas mas não priorizadas ainda
   - **To Do**: Planejado para a sprint atual
   - **In Progress**: Alguém está trabalhando nisso agora
   - **In Review**: Pull Request aberto, esperando aprovação
   - **Done**: Completado e mergeado

### Como Usar

- Toda issue nova vai automaticamente para **Backlog**
- Durante o Planning, vocês movem issues para **To Do**
- Quando alguém começa a trabalhar, move para **In Progress**
- Quando abre PR, move para **In Review**
- Quando PR é mergeado, move para **Done** (pode ser automático)

### Visualização de Progresso

O board permite ver rapidamente:
- Quantas tarefas estão em cada fase
- Quem está trabalhando no quê (ver pelo avatar)
- Se há tarefas travadas em Review (sinal de bottleneck)
- Progresso geral da sprint

---

## 🌿 Estratégia de Branches

Branches são "linhas paralelas de desenvolvimento". Permitem que múltiplas pessoas trabalhem simultaneamente sem interferir.

### Estrutura de Branches

**main (branch principal):**
- Sempre estável e funcional
- Representa o que está em produção ou pronto para produção
- **Protegida**: Ninguém dá push direto, só merge via Pull Request aprovado
- Deploy automático para produção (eventualmente com GitHub Actions)

**develop (branch de desenvolvimento):**
- Onde features são integradas antes de ir para main
- Pode ter bugs temporários, mas deve ser funcional no geral
- Base para criar novas feature branches

**feature/*** (branches de funcionalidade):**
- Uma branch para cada feature ou issue
- Nomeação: `feature/login-endpoint`, `feature/book-card-component`, `feature/user-profile-page`
- Criada a partir de `develop`
- Vida curta (1-3 dias idealmente, no máximo 1 semana)
- Deletada após merge

**hotfix/*** (branches de correção urgente):**
- Para bugs críticos em produção
- Criada a partir de `main`
- Mergeada de volta para `main` e `develop`

### Workflow Passo a Passo

**Scenario: Você vai implementar o endpoint de login**

1. **Sincronizar develop:**
```bash
git checkout develop
git pull origin develop
```

2. **Criar sua branch:**
```bash
git checkout -b feature/login-endpoint
```

3. **Trabalhar (fazer mudanças, testar):**
```bash
# Editar arquivos
# Testar localmente
```

4. **Commit frequente (a cada mudança lógica):**
```bash
git add .
git commit -m "feat: cria estrutura inicial do LoginController"
# Continuar trabalhando
git commit -m "feat: adiciona validação de email e senha"
# Continuar trabalhando
git commit -m "feat: implementa geração de JWT token"
```

5. **Push da branch para GitHub:**
```bash
git push origin feature/login-endpoint
```

6. **Abrir Pull Request no GitHub** (veja seção seguinte)

7. **Após aprovação e merge, deletar branch local:**
```bash
git checkout develop
git pull origin develop  # Puxar com seu merge incluído
git branch -d feature/login-endpoint  # Deletar branch local
```

---

## 🔀 Pull Requests (PRs)

Um Pull Request é uma proposta de mudança. Você está dizendo "Ei pessoal, fiz essas mudanças na minha branch. Revisem e, se estiver bom, façam merge no develop".

### Anatomia de um Bom Pull Request

**1. Título Descritivo:**
Use o mesmo padrão de commits:
- `feat: implementa endpoint de login com JWT`
- `fix: corrige validação de email que aceitava emails inválidos`
- `docs: atualiza README com instruções de setup do backend`

**2. Descrição Completa:**
```markdown
## O que foi feito
[Resumo das mudanças]

## Por quê
[Explicar o motivo - resolver que issue? Resolver que problema?]

## Como testar
1. Rodar o backend com `mvn spring-boot:run`
2. Fazer POST para http://localhost:8080/auth/login com body:
   ```json
   {
     "email": "teste@exemplo.com",
     "password": "senha123"
   }
   ```
3. Verificar que retorna status 200 e um token JWT

## Closes
Closes #23 [número da issue que este PR resolve]

## Screenshots (se mudança visual)
[Adicionar prints de tela se for frontend]

## Checklist
- [ ] Código compila sem erros
- [ ] Testes passam (quando tivermos testes)
- [ ] Comentários adicionados onde necessário
- [ ] README atualizado se necessário
```

**3. Reviewers Atribuídos:**
Escolher quem vai revisar. Sugestão:
- PRs de backend: Tech Lead ou Backend Lead revisa
- PRs de frontend: Frontend Lead ou UI/UX Designer revisa
- PRs de banco: Database Lead revisa
- Em dúvida: Tech Lead

**4. Labels e Milestone:**
Adicionar labels apropriados (`backend`, `frontend`, etc) e atribuir ao milestone corrente (ex: Milestone 2 - PoC)

### Processo de Code Review
**Checklist de revisão:**
- [ ] O código faz o que a issue pede?
- [ ] O código está claro e legível? (Outro desenvolvedor entenderia?)
- [ ] Há testes? (Quando implementarem testes)
- [ ] Não quebra nada existente?
- [ ] Segue os padrões do projeto? (Nomeação, estrutura de pastas, etc)
- [ ] Sem código comentado ou console.logs esquecidos?
- [ ] Sem segredos (senhas, chaves de API) no código?

**Como dar feedback:**
- Seja construtivo, não crítico
- Pergunte em vez de afirmar: "Poderia explicar por que fez X?" em vez de "Isso está errado"
- Sugira alternativas: "E se fizéssemos Y ao invés de X?"
- Elogie coisas boas: "Gostei de como você estruturou isso, ficou bem claro"

**Tipos de comentário:**
- 🔴 **Blocking (must fix):** Erro crítico que precisa ser corrigido antes de merge
  - Exemplo: "Este endpoint não valida o email, qualquer string passa. Precisa adicionar validação"
- 🟡 **Non-blocking (nice to have):** Sugestão de melhoria mas não bloqueia merge
  - Exemplo: "Este método poderia ser dividido em dois para ficar mais claro, mas funciona assim também"
- 💬 **Question/Discussion:** Pergunta para entender melhor
  - Exemplo: "Por que escolheu usar ArrayList aqui em vez de HashSet?"

**Para quem recebeu review:**
- Não leve para o pessoal - o feedback é sobre o código, não sobre você
- Responda perguntas/comentários explicando seu raciocínio
- Faça as correções solicitadas e dê push
- Marque como "resolved" comentários que você atendeu
- Agradeça o reviewer pelo tempo

### Merging

Após aprovação (normalmente 1-2 approvals), o autor do PR ou o reviewer pode fazer merge:

**Estratégia de Merge:**
- **Squash and Merge**: Junta todos os commits da branch em um único commit no develop
  - Vantagem: Histórico limpo (cada feature = 1 commit)
  - Desvantagem: Perde histórico detalhado de commits
  - **Recomendado para vocês**

**Após merge:**
- GitHub pode automaticamente fechar a issue linkada
- Branch feature é deletada automaticamente (configurar isso)
- Todos devem dar `git pull origin develop` para pegar as mudanças

---

## 🏷️ Sistema de Labels

Labels ajudam a categorizar e filtrar issues e PRs. Criar as seguintes:

### Por Tipo
- `feature`: Nova funcionalidade
- `bug`: Algo quebrado que precisa consertar
- `refactor`: Melhorar código existente sem mudar comportamento
- `documentation`: Mudanças em documentação
- `test`: Adicionar ou corrigir testes
- `chore`: Tarefas de manutenção (configs, dependencies)

### Por Componente
- `backend`: Código Java
- `frontend`: Código React
- `database`: Schemas, migrations, queries SQL
- `devops`: Deploy, CI/CD, configurações
- `design`: UI/UX, Figma

### Por Prioridade
- `priority-critical`: Deve ser feito AGORA (bloqueia outros)
- `priority-high`: Importante para a sprint atual
- `priority-medium`: Bom ter, mas não urgente
- `priority-low`: Pode esperar

### Por Status
- `blocked`: Esperando outra issue ou decisão externa
- `help-wanted`: Pessoa assigned está travada e precisa de ajuda
- `good-first-issue`: Tarefa simples, boa para quem está começando
- `needs-discussion`: Precisa ser discutido em equipe antes de implementar

### Por Milestone
Usar a funcionalidade de Milestones do GitHub ao invés de labels:
- Milestone 0: Planejamento
- Milestone 1: Fundação
- Milestone 2: PoC
- Milestone 3: MVP
- Milestone 4: Documentação
- Milestone 5: Refinamento

---

## 🔒 Proteções de Branch

Para evitar que alguém acidentalmente quebre a branch principal, configurar proteções:

### Para a branch `main`:

1. Ir em Settings → Branches → Add rule
2. Branch name pattern: `main`
3. Habilitar:
   - ✅ Require pull request reviews before merging
     - Required approvals: 2 (ou 1 se equipe for menor)
   - ✅ Dismiss stale reviews when new commits are pushed
   - ✅ Require status checks to pass before merging (quando tiverem CI/CD)
   - ✅ Include administrators (até admin precisa seguir as regras)
   - ✅ Restrict who can push to matching branches
     - Apenas DevOps ou Tech Lead pode forçar push em emergências

### Para a branch `develop`:

1. Mesmas configurações mas mais relaxado
2. Require apenas 1 approval
3. Qualquer membro pode merge

---

## 📈 Milestones e Planejamento

Milestones representam fases/marcos do projeto. Usem para agrupar issues.

### Como Criar

1. Ir em Issues → Milestones → New milestone
2. Título: "Milestone 2: PoC"
3. Descrição: Breve resumo do que esse milestone entrega
4. Data de entrega: Data planejada de conclusão
5. Criar

### Durante Planning

1. Olhar backlog de issues
2. Decidir quais entram na próxima sprint
3. Atribuir essas issues ao milestone corrente
4. Atribuir responsáveis

### Acompanhamento

- GitHub mostra progresso do milestone (X% completo baseado em issues fechadas)
- Permite ver se estão no ritmo para cumprir a data
- Ajuda a identificar se pegaram trabalho demais

---

## 🤖 GitHub Actions (Opcional mas Recomendado)

GitHub Actions permite automatizar tarefas. Mesmo que seja simples, adiciona bastante profissionalismo.

### Exemplo 1: Rodar Testes Automaticamente

Criar arquivo `.github/workflows/backend-tests.yml`:

```yaml
name: Backend Tests

on:
  pull_request:
    branches: [ develop, main ]
    paths:
      - 'backend/**'

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Set up JDK 17
      uses: actions/setup-java@v3
      with:
        java-version: '17'
        distribution: 'temurin'
    
    - name: Build with Maven
      run: |
        cd backend
        mvn clean install
    
    - name: Run tests
      run: |
        cd backend
        mvn test
```

Agora, todo PR que mexe no backend automaticamente roda os testes. Se falharem, o PR não pode ser mergeado.

### Exemplo 2: Deploy Automático

Quando mergearem em `main`, fazer deploy automático:

```yaml
name: Deploy to Production

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - name: Deploy backend to Railway
      run: |
        # Comandos de deploy
        # (depende da plataforma escolhida)
    
    - name: Deploy frontend to Vercel
      run: |
        # Comandos de deploy
```

---

## 🚨 Problemas Comuns e Como Evitar

***Conflito de Merge:***
Acontece quando duas pessoas mexem no mesmo arquivo.

*Como evitar:*
- Comunicação: avisar no grupo "vou mexer no arquivo X"
- Branches pequenas e vida curta (merge rápido)
- Pull do `develop` frequentemente

*Como resolver quando acontece:*
```bash
# Na sua branch
git pull origin develop
# Git mostra conflitos
# Abrir arquivos marcados, resolver conflitos manualmente
git add .
git commit -m "fix: resolve merge conflicts"
git push
```

***Branch desatualizada:***
Sua branch ficou semanas sem merge, `develop` já está muito à frente.

*Como evitar:*
- Não deixar branches vivas por muito tempo
- Quebrar tarefas grandes em menores

*Como resolver:*
```bash
git checkout feature/sua-branch
git pull origin develop
# Resolver conflitos se houver
git push
```

***Commit acidental de arquivo grande ou senha:***
`.gitignore` não estava configurado, subiram arquivo grande ou senha.

*Como evitar:*
- Configurar `.gitignore` logo no início
- Usar .env para credenciais, nunca hardcode
- Revisar `git status` antes de `git add .`

*Como resolver:*
- Se ainda não deu push: `git reset HEAD~1` (desfaz último commit)
- Se já deu push: precisa fazer git filter-branch (complicado, pedir ajuda)

***PR gigante que ninguém vai conseguir revisar revisar:***
Alguém trabalhou 2 semanas e abriu PR de 50 arquivos mudados.

*Como evitar:*
- Quebrar features grandes em pequenas issues
- Fazer PRs incrementais
- Se a task é grande, fazer commits lógicos e abrir PR parcial antes de terminar tudo

---

## 💡 Dicas para Impressionar na Apresentação

**1. Histórico Visual:**
Usar a aba "Insights → Contributors" mostra gráficos de quem contribuiu o quê ao longo do tempo. Demonstra trabalho em equipe.

**2. Processo Maduro:**
Mostrar alguns PRs com reviews construtivos. "Veja como trabalhamos com revisão de código, isso garantiu qualidade"

**3. Rastreabilidade:**
Pegar uma feature e mostrar o caminho completo: Issue → Branch → Commits → PR → Review → Merge → Deploy

**4. Organização:**
Mostrar o project board limpo, bem organizado, com milestones cumpridos

**5. Estatísticas:**
- X issues criadas e resolvidas
- Y pull requests com média de Z reviews
- 100% de commits seguindo padrão semântico
- Zero commits direto em main (tudo via PR)

**6. Automação:**
Se configuraram GitHub Actions, mostrar: "Todo PR automaticamente roda testes. Veja aqui, este passou, este falhou e foi corrigido"

---

**Documento criado:** 19/02/2026
**Última atualização:** 21/02/2026
**Responsável por manter:** DevOps Lead
