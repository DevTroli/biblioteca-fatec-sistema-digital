# 👥 Estrutura da Equipe - Projeto Biblioteca FATEC

> **Propósito deste documento:** Ajudar a equipe de 7 pessoas a se organizar de forma que todos possam trabalhar em paralelo sem conflitos.

---

## 🏗️ Proposta de Atribuições (7 pessoas)

### 1. Tech Lead (Troli) 

**Responsabilidades principais:**
- Define e documenta a arquitetura do sistema (camadas, fluxo de dados, padrões)
- Resolve conflitos técnicos quando duas pessoas têm abordagens diferentes
- Faz code review das partes críticas (autenticação, integração banco-backend)
- Garante que há documentação técnica suficiente para os outros seguirem
- É o "desempacador" - quando alguém está travado em um problema técnico, ajuda a destrancar

**Habilidades importantes:**
- Curiosidade técnica (gosta de pesquisar soluções)
- Capacidade de abstrair problemas (ver o "big picture")
- Boa comunicação (precisa explicar decisões técnicas para o resto da equipe)
- Experiência prévia com Java é um plus, mas não obrigatório - pode aprender junto

---

### 2. Backend Lead (Felipe)

**Responsabilidades principais:**
- Desenvolve os controllers (endpoints da API)
- Implementa os services (lógica de negócio)
- Define os DTOs (Data Transfer Objects - estruturas de dados que trafegam pela API)
- Integra com o banco de dados (usando JPA/Hibernate)
- Escreve testes unitários das funções críticas
- Documenta a API (quais endpoints existem, o que cada um faz, exemplos de requisição/resposta)

**Habilidades importantes:**
- Confortável com orientação a objetos
- Entendimento de arquitetura em camadas (controller → service → repository)
- Familiaridade com Spring Boot (ou disposição para aprender rápido)
- Atenção a edge cases (o que acontece se o usuário enviar dados inválidos?)

---

### 3. Database Lead(Pedro)

**Responsabilidades principais:**
- Cria os diagramas conceituais, lógicos e físicos do banco de dados
- Escreve os scripts DDL (CREATE TABLE) com todas as constraints
- Desenvolve triggers e stored procedures para lógica complexa
- Define índices estratégicos para performance
- Cria views úteis para queries comuns
- Documenta o schema (dicionário de dados explicando cada tabela e campo)
- Popula dados de seed para desenvolvimento e testes

**Habilidades importantes:**
- Entendimento de normalização (1NF, 2NF, 3NF)
- Familiaridade com PostgreSQL (ou disposição para aprender)
- Pensamento analítico (consegue modelar relacionamentos complexos)
- Atenção a integridade referencial (foreign keys, cascades)

---

### 4. Frontend Lead (Mathues??)

**Responsabilidades principais:**
- Traduz designs do Figma em FronEnd
- Define a estrutura de pastas e organização de componentes
- Implementa navegação dos paths
- Integra com a API do backend
- Gerencia estado da aplicação
- Garante responsividade (funciona em mobile e desktop)
- Implementa validações de formulário
- Cria tratamento de erros e loading states

**Habilidades importantes:**
- HTML, CSS, JavaScript sólidos
- Outra tecnologia não decidida
- Noção de UX (experiência do usuário)
- Atenção a detalhes visuais

---

### 5. UI/UX Designer (Cicera)

**Responsabilidades principais:**
- Cria wireframes (esboços de baixa fidelidade das telas)
- Desenvolve protótipos no Figma com todas as telas principais
- Define a identidade visual alinhada com a FATEC (cores, tipografia, logo)
- Cria guia de estilo (design system) para consistência
- Pensa nos estados das interfaces (vazio, carregando, erro, sucesso)
- Pode ajudar com iconografia e ilustrações
- Testa usabilidade com usuários beta e coleta feedback

**Habilidades importantes:**
- Familiaridade com Figma
- Senso estético (noção de cores, espaçamentos, proporções)
- Empatia com usuário (consegue se colocar no lugar de quem vai usar)
- Comunicação visual

---

### 6. DevOps (Leonardo)

**Responsabilidades principais:**
- Configura o repositório GitHub (branches, proteções, CI/CD)
- Define e documenta o fluxo de trabalho (como criar branches, como fazer PRs)
- Configura ambientes (desenvolvimento, staging, produção)
- Faz deploy do backend (pode ser Heroku, Railway, Render)
- Faz deploy do frontend (Vercel é ideal para React)
- Configura banco de dados em produção (NeonDB como vocês mencionaram)
- Implementa health check e status page
- Configura ferramentas de monitoramento e logs
- Pode configurar GitHub Actions para testes automáticos

**Habilidades importantes:**
- Confortável com terminal/linha de comando
- Entendimento de Git (branches, merges, rebases)
- Noção de redes e deploy (o que é um servidor, como funciona DNS, etc)
- Capacidade de debugar problemas de ambiente

---

### 7. Product Owner / Documentação Lead (Troli)

**Responsabilidades principais:**
- Faz pesquisa com a biblioteca (entrevistas, questionários) para entender necessidades
- Define e prioriza funcionalidades (o que entra no PoC vs MVP vs futuro)
- Escreve user stories e critérios de aceitação
- Mantém o backlog organizado (issues do GitHub)
- Documenta decisões importantes da equipe
- Escreve a documentação ABNT do projeto
- Prepara slides para apresentação final
- Coordena testes com usuários beta e coleta feedback
- Calcula e apresenta métricas de uso
- Cria relatórios de progresso para os professores (se necessário)

**Habilidades importantes:**
- Excelente comunicação escrita
- Organização (mantém muitos documentos e informações organizados)
- Empatia (entende necessidades dos usuários)
- Capacidade de priorização (o que é mais importante agora?)

**Colabora principalmente com:**
Todos (essa pessoa interage com toda a equipe regularmente), especialmente UI/UX Designer (para validar designs com usuários) e Tech Lead (para entender viabilidade técnica de features)

**Volume de trabalho esperado:**
Constante durante todo o projeto, com pico no Milestone 0 (pesquisa inicial) e Milestone 4 (documentação final)

---

### Acordos de Colaboração

**Como vamos trabalhar juntos:**
- Frequência de 1 ou 2 vezes por semana.
- Por via do Discord & WhatsApp
- Usaremos PR para averiguar a qualidade do código e as decisões em geral provem da escolha da maioria 
- [PREENCHER: O que fazemos se alguém não estiver entregando sua parte?]

### Rituais da Equipe

**Reuniões/Eventos regulares:**
- As sprints estão organizadas em milestone no GitHub além do auxilio da tabela de kanban para visualização de oq/quando precisa ser feito
- Em caso de duvida abrir uma issue no GitHub ou enviar mensagem
- Meta de Apresentar a cada semana apresentar uma parte do software finalizado para conseguirmos entregar no prazo o projeto

---

**Data da última atualização:** 19/02/2026
**Revisão necessária:** 26/02/2026
