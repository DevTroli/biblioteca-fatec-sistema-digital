# 🏗️ Milestone 1: Fundação Conceitual

> **Status:** Não Iniciado
> **Período:** --/--/----
> **Responsável Principal:** Database Lead + Tech Lead  
> **Participantes:** Toda a equipe

---

## 🎯 Objetivo deste Milestone

Este milestone é onde vocês criam todas as fundações conceituais do projeto antes de escrever qualquer linha de código funcional. É a fase de design e planejamento técnico. O objetivo é responder perguntas como: Como os dados vão se estruturar? Como as partes do sistema vão conversar entre si? Onde cada arquivo vai ficar? Quais tecnologias específicas vamos usar e como?

---

## 📊 Parte 1: Modelagem do Banco de Dados

### Por que começar pelo banco de dados?

O banco de dados é a fundação de todo o sistema porque ele define como a informação vai existir e se relacionar. Uma vez que você cria uma estrutura de banco de dados e começa a colocar dados reais nela, é muito trabalhoso mudar. Imaginem que vocês criam a tabela de usuários sem um campo para armazenar a data de nascimento. Depois de mil usuários cadastrados, vocês percebem que precisam desse dado. Agora vocês têm que alterar a estrutura, migrar os dados existentes (que não têm data de nascimento), e atualizar todo o código que interage com essa tabela. É um pesadelo.

Por isso, vocês investem tempo agora pensando profundamente sobre quais entidades existem, quais informações cada uma tem, e como elas se relacionam. Isso se chama modelagem de dados, e é dividida em três níveis crescentes de detalhe: conceitual, lógico e físico.

### Modelo Conceitual (Diagrama ER)

Este é o nível mais abstrato e fácil de entender. Aqui vocês identificam as entidades principais do sistema e como elas se relacionam, sem se preocupar com detalhes técnicos de banco de dados.

**Entidades são "coisas" sobre as quais você precisa guardar informação.** Para o projeto de biblioteca, as entidades óbvias incluem: Usuário, Livro, Empréstimo. Mas podem existir outras dependendo das funcionalidades que vocês decidiram construir: Reserva, Avaliação, Categoria, Autor, etc.

**Relacionamentos descrevem como as entidades se conectam.** Por exemplo, um Usuário pode fazer múltiplos Empréstimos (relacionamento de um para muitos, escrito como 1:N). Um Livro pode ter múltiplos Autores, e um Autor pode ter escrito múltiplos Livros (relacionamento muitos para muitos, escrito como M:N).

Vocês vão criar este diagrama no BrModelo, que é uma ferramenta brasileira gratuita específica para modelagem conceitual. A vantagem do BrModelo é que ele usa notação didática (retângulos para entidades, losangos para relacionamentos) que deixa tudo muito visual e fácil de explicar para os professores.

#### Template de Documentação do Modelo Conceitual

**Entidades Identificadas:**

Para cada entidade principal, documentar:

**ENTIDADE: [Nome da Entidade - ex: USUÁRIO]**

*Descrição:* [O que esta entidade representa? Por exemplo: "Representa um aluno ou funcionário da FATEC que usa a biblioteca"]

*Atributos principais:*
- [Atributo 1 - ex: nome completo]
- [Atributo 2 - ex: email institucional]
- [Atributo 3 - ex: tipo de usuário (aluno, professor, funcionário)]
- [Continue listando...]

*Cardinalidade nos relacionamentos:*
- Com [Outra Entidade]: [1:1, 1:N, ou M:N] - [Explicar: Por exemplo "Um usuário pode ter múltiplos empréstimos (1:N)"]

*Regras de negócio associadas:*
- [Regra 1 - ex: "Alunos podem ter no máximo 3 empréstimos simultâneos"]
- [Regra 2 - ex: "Professores podem ter até 5 empréstimos simultâneos"]

---

**ENTIDADE: [Segunda Entidade - ex: LIVRO]**

[Preencher o mesmo template acima]

---

[Repetir para todas as entidades principais]

---

**Relacionamentos Principais:**

Para cada relacionamento importante, explicar:

**RELACIONAMENTO: [Nome - ex: EMPRESTA]**

*Entre:* [Entidade 1] e [Entidade 2]

*Cardinalidade:* [1:1, 1:N, M:N]

*Descrição:* [Explicar em português claro o que este relacionamento significa. Exemplo: "Um Usuário pode fazer empréstimo de múltiplos Livros ao longo do tempo, e cada Livro pode ser emprestado para múltiplos Usuários (em momentos diferentes). Isso cria um relacionamento M:N que será implementado através de uma tabela de associação chamada EMPRÉSTIMO"]

*Atributos do relacionamento (se houver):* 
[Alguns relacionamentos têm seus próprios atributos. Por exemplo, o relacionamento EMPRÉSTIMO entre Usuário e Livro tem atributos como data_emprestimo, data_devolucao, foi_devolvido, etc]

---

**Arquivo do Diagrama:**
- Caminho: `/database/diagrams/modelo_conceitual_brmodelo.brM3`
- [Anexar imagem exportada do diagrama quando finalizado]
- [Descrever brevemente o que alguém vê no diagrama]

---

### Modelo Lógico (Diagrama no DBDesigner)

O modelo lógico é onde vocês começam a pensar tecnicamente sobre como isso será implementado em um banco de dados relacional real. Aqui as "entidades" viram "tabelas", os "atributos" viram "colunas", e vocês começam a pensar em chaves primárias (Primary Keys), chaves estrangeiras (Foreign Keys), tipos de dados (VARCHAR, INTEGER, DATE), e normalização.

**DBDesigner.net** é uma ferramenta online gratuita que permite desenhar bancos de dados relacionais visualmente. A grande vantagem é que ela já pensa em termos de SQL - quando você cria uma tabela, ela te força a definir tipos de dados, constraints, índices, etc. E no final, ela pode exportar o SQL que cria todas essas tabelas automaticamente.

#### Processo de Transformação do Conceitual para o Lógico

Deixa eu explicar passo a passo como transformar o modelo conceitual em lógico, porque há algumas regras importantes:

**Regra 1 - Entidades viram Tabelas diretamente:**
Cada retângulo (entidade) no modelo conceitual vira uma tabela no modelo lógico. Se você tem entidade USUÁRIO, vai existir tabela `usuarios`. Note que usamos o plural em português (ou inglês, se preferirem padronizar em inglês) para nomes de tabelas.

**Regra 2 - Atributos viram Colunas:**
Cada atributo listado na entidade vira uma coluna na tabela. Mas agora você precisa decidir o tipo de dado. Nome é texto? Então VARCHAR(255). Idade é número? Então INTEGER. Data de cadastro é data e hora? Então TIMESTAMP.

**Regra 3 - Toda tabela precisa de uma Primary Key (PK):**
A Primary Key é uma coluna (ou conjunto de colunas) que identifica unicamente cada linha. Normalmente criamos uma coluna chamada `id` do tipo UUID ou SERIAL (auto-incremento) para ser a PK. Por exemplo, na tabela usuarios, cada usuário tem um `id` único.

**Regra 4 - Relacionamentos 1:N viram Foreign Keys:**
Quando há um relacionamento de "um para muitos" (1:N), a tabela do lado "muitos" recebe uma Foreign Key apontando para a PK da tabela do lado "um". 

Exemplo: Um Usuário pode ter muitos Empréstimos (1:N). Então a tabela `emprestimos` terá uma coluna `usuario_id` que é uma Foreign Key apontando para `usuarios.id`. Isso significa "este empréstimo pertence a este usuário específico".

**Regra 5 - Relacionamentos M:N viram Tabelas de Associação:**
Quando há um relacionamento de "muitos para muitos" (M:N), vocês não podem implementar isso diretamente com Foreign Keys. A solução é criar uma terceira tabela intermediária que conecta as duas entidades.

Exemplo: Se Livros e Categorias têm relacionamento M:N (um livro pode estar em múltiplas categorias, e uma categoria contém múltiplos livros), vocês criam uma tabela `livros_categorias` que tem duas Foreign Keys: `livro_id` e `categoria_id`. Cada linha dessa tabela representa a associação de um livro específico com uma categoria específica.

**Regra 6 - Normalização para evitar redundância:**
Normalização é o processo de organizar os dados para evitar duplicação. Por exemplo, se você tem um campo "nome_do_autor" diretamente na tabela de livros, e múltiplos livros são do mesmo autor, você estaria repetindo o nome dele várias vezes. É melhor criar uma tabela `autores` separada e usar uma Foreign Key. Isso é chamado de Terceira Forma Normal (3NF), que é o padrão que vocês devem buscar.

#### Template de Documentação do Modelo Lógico

**Tabelas Definidas:**

Para cada tabela, documentar detalhadamente:

**TABELA: [nome_da_tabela - ex: usuarios]**

*Descrição:* [O que esta tabela armazena]

*Colunas:*

| Nome da Coluna | Tipo de Dado | Constraints | Descrição |
|----------------|--------------|-------------|-----------|
| id | UUID | PRIMARY KEY, NOT NULL, DEFAULT uuid_generate_v4() | Identificador único do usuário |
| nome_completo | VARCHAR(200) | NOT NULL | Nome completo do usuário |
| email | VARCHAR(255) | NOT NULL, UNIQUE | Email institucional (@fatec.sp.gov.br) |
| cpf | CHAR(11) | NOT NULL, UNIQUE | CPF sem formatação (apenas números) |
| tipo_usuario | VARCHAR(20) | NOT NULL, CHECK (tipo_usuario IN ('aluno', 'professor', 'funcionario')) | Tipo de vínculo com a FATEC |
| data_cadastro | TIMESTAMP | NOT NULL, DEFAULT CURRENT_TIMESTAMP | Quando o usuário se cadastrou |
| ativo | BOOLEAN | NOT NULL, DEFAULT TRUE | Se o usuário está ativo no sistema |

*Índices:*
- `idx_usuarios_email` em (email) - Para login rápido
- `idx_usuarios_cpf` em (cpf) - Para busca por CPF
- `idx_usuarios_tipo` em (tipo_usuario) - Para filtrar por tipo

*Relacionamentos:*
- [Descrever Foreign Keys que esta tabela RECEBE de outras tabelas]
- [Descrever Foreign Keys que outras tabelas têm PARA esta tabela]

*Regras de Integridade:*
- [Exemplo: "Email deve ser do domínio @fatec.sp.gov.br"]
- [Exemplo: "CPF deve ter exatamente 11 dígitos"]
- [Exemplo: "Ao deletar usuário, marcar como inativo ao invés de deletar fisicamente (soft delete)"]

---

[Repetir para cada tabela]

---

**Decisões de Normalização:**

*Escolhas feitas para evitar redundância:*

[Explicar transformações importantes. Por exemplo:]

"Inicialmente, pensamos em colocar os dados do autor (nome, biografia, país de origem) diretamente na tabela de livros. Mas percebemos que isso violaria a 3NF porque teríamos repetição: se dois livros são do mesmo autor, estaríamos duplicando todas as informações dele. Então criamos uma tabela `autores` separada e uma tabela de associação `livros_autores` (M:N) para conectar livros e autores. Isso permite que um livro tenha múltiplos autores e um autor tenha múltiplos livros, sem duplicação de dados."

**Arquivo do Diagrama:**
- Caminho: `/database/diagrams/modelo_logico_dbdesigner.json`
- [Anexar imagem exportada do diagrama]
- [Opcional: Incluir link para o DBDesigner online se salvarem lá]

---

### Modelo Físico (Scripts SQL no PostgreSQL)

O modelo físico é onde o rubber meets the road - é o SQL real que vai ser executado no PostgreSQL para criar o banco de dados. Aqui vocês pegam o modelo lógico e o transformam em comandos CREATE TABLE com todos os detalhes específicos do PostgreSQL.

A grande diferença entre lógico e físico é que agora vocês estão pensando em otimizações específicas do banco que escolheram (PostgreSQL). Por exemplo, PostgreSQL tem suporte nativo a UUIDs, JSON, arrays, e full-text search que outros bancos não têm. Vocês podem aproveitar essas features.

#### Template de Scripts SQL

Vocês vão criar múltiplos arquivos SQL organizados em uma pasta de migrations, numerados sequencialmente:

```
/database/migrations/
├── V001__create_extension_uuid.sql
├── V002__create_table_usuarios.sql
├── V003__create_table_livros.sql
├── V004__create_table_autores.sql
├── V005__create_table_livros_autores.sql
├── V006__create_table_emprestimos.sql
├── V007__create_indexes.sql
├── V008__create_triggers.sql
└── ...
```

Essa numeração (V001, V002...) permite que as migrations sejam executadas em ordem. Ferramentas como Flyway (Java) ou Liquibase leem esses arquivos em ordem e aplicam no banco de dados, mantendo histórico de quais já foram aplicadas.

**Exemplo de conteúdo de um arquivo de migration:**

```sql
-- V002__create_table_usuarios.sql
-- Descrição: Cria tabela de usuários do sistema (alunos, professores, funcionários)
-- Autor: [Nome do Database Lead]
-- Data: [Data de criação]

CREATE TABLE IF NOT EXISTS usuarios (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    
    -- Dados pessoais
    nome_completo VARCHAR(200) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    cpf CHAR(11) NOT NULL UNIQUE,
    
    -- Tipo de usuário
    tipo_usuario VARCHAR(20) NOT NULL 
        CHECK (tipo_usuario IN ('aluno', 'professor', 'funcionario')),
    
    -- Dados de matrícula/registro
    numero_matricula VARCHAR(20) UNIQUE, -- Para alunos
    numero_registro VARCHAR(20) UNIQUE,  -- Para professores/funcionários
    
    -- Dados de contato
    telefone VARCHAR(20),
    
    -- Controle do sistema
    senha_hash VARCHAR(255) NOT NULL, -- Hash bcrypt da senha
    ativo BOOLEAN NOT NULL DEFAULT TRUE,
    data_cadastro TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    ultimo_acesso TIMESTAMP,
    
    -- Constraints de validação
    CONSTRAINT email_formato_fatec CHECK (email LIKE '%@fatec.sp.gov.br'),
    CONSTRAINT cpf_apenas_numeros CHECK (cpf ~ '^\d{11}$')
);

-- Comentários explicativos (aparecem no banco de dados)
COMMENT ON TABLE usuarios IS 'Armazena todos os usuários do sistema (alunos, professores e funcionários da FATEC)';
COMMENT ON COLUMN usuarios.senha_hash IS 'Hash bcrypt da senha (nunca armazenar senha em texto plano)';
COMMENT ON COLUMN usuarios.ativo IS 'Soft delete: ao invés de deletar usuário, marca como inativo';

-- Índices para performance
CREATE INDEX idx_usuarios_email ON usuarios(email);
CREATE INDEX idx_usuarios_cpf ON usuarios(cpf);
CREATE INDEX idx_usuarios_tipo ON usuarios(tipo_usuario) WHERE ativo = TRUE;
```

**Explicação das partes importantes:**

O comentário no topo de cada arquivo documenta o que ele faz, quem criou e quando. Isso ajuda meses depois quando alguém está tentando entender o histórico.

As constraints são regras que o banco de dados vai forçar. Se você tentar inserir um CPF que não tem exatamente onze dígitos numéricos, o banco vai rejeitar. Se você tentar cadastrar dois usuários com o mesmo email, o banco vai rejeitar (UNIQUE). Isso garante integridade de dados mesmo se o código do backend tiver algum bug.

Os comentários via COMMENT ON são documentação que fica no próprio banco de dados. Ferramentas de administração como pgAdmin mostram esses comentários, ajudando outros desenvolvedores a entender o propósito de cada tabela e campo.

Os índices são otimizações. Quando você faz uma busca `WHERE email = 'joao@fatec.sp.gov.br'`, o PostgreSQL pode usar o índice para encontrar rapidamente aquela linha ao invés de percorrer toda a tabela. Sem índice, buscar um usuário entre 10 mil leva segundos. Com índice, leva milissegundos.

#### Documentação das Decisões de Design Físico

**Escolhas Específicas do PostgreSQL:**

[Documentar decisões que são específicas do PostgreSQL e por que vocês fizeram assim]

Exemplo preenchido:

"Decidimos usar UUID para chaves primárias ao invés de SERIAL (auto-incremento) por três razões: (1) UUIDs são globalmente únicos, então se futuramente precisarmos integrar dados de múltiplos bancos, não haverá colisões de IDs; (2) Sequenciais expõem informações (ID 1000 significa que há mil usuários), UUIDs não; (3) Permite gerar IDs no lado do cliente sem consultar o banco. A desvantagem é que UUIDs ocupam mais espaço (16 bytes vs 4-8 bytes), mas considerando o volume esperado (milhares, não milhões de registros), isso não é problema."

[Agora preencher suas decisões]

**Estratégia de Índices:**

[Explicar quais colunas receberam índices e por quê]

Exemplo:

"Criamos índice em `usuarios.email` porque essa coluna é usada em toda operação de login (WHERE email = X). Sem índice, o banco faria table scan (varrer toda a tabela) em cada login, o que é lento. Criamos também em `emprestimos.data_devolucao` porque frequentemente filtraremos empréstimos atrasados (WHERE data_devolucao < CURRENT_DATE AND devolvido = FALSE). Evitamos criar índices em colunas que nunca ou raramente aparecem em WHERE/JOIN."

**Triggers e Stored Procedures (se aplicável):**

[Se vocês decidirem usar triggers ou funções no banco, documentar aqui]

Triggers são "gatilhos" - procedimentos que executam automaticamente quando algo acontece. Por exemplo, você pode criar um trigger que, sempre que um novo empréstimo é criado, verifica se o usuário já não ultrapassou o limite de empréstimos simultâneos.

Exemplo de decisão:

"Criamos um trigger `validate_emprestimo_limite` que executa antes de inserir em `emprestimos`. Ele conta quantos empréstimos ativos o usuário tem e, se já atingiu o limite (3 para alunos, 5 para professores), cancela a inserção e retorna erro. Decidimos fazer isso no banco ao invés do backend para garantir que a regra é respeitada mesmo que múltiplas instâncias do backend tentem criar empréstimos simultaneamente."

**Versionamento e Migrations:**

[Como vocês vão gerenciar mudanças no schema ao longo do tempo]

Exemplo:

"Estamos usando Flyway para gerenciar migrations. Cada mudança no schema é um novo arquivo SQL numerado sequencialmente. Flyway mantém uma tabela `schema_version` no banco que rastreia quais migrations já foram aplicadas. Quando rodamos `mvn flyway:migrate`, ele compara os arquivos existentes com os já aplicados e executa apenas os novos. Isso garante que todos os ambientes (dev, staging, prod) e todos os membros da equipe tenham exatamente o mesmo schema. Nunca alteramos uma migration já aplicada - sempre criamos uma nova."

---

## 🏛️ Parte 2: Arquitetura do Sistema

### Por que definir arquitetura antes de codificar?

Arquitetura de software é sobre decidir como as partes do sistema vão se organizar e se comunicar. É como planejar os cômodos de uma casa - onde fica a cozinha (lógica de negócio), onde fica a sala de estar (interface do usuário), como eles se conectam (portas e corredores = APIs).

Definir isso agora evita que vocês comecem a codificar e descubram, três semanas depois, que misturaram lógica de negócio com código de interface, tornando impossível testar ou reutilizar qualquer coisa. Uma boa arquitetura torna o código organizado, testável, e fácil de entender por qualquer membro da equipe.

### Arquitetura em Três Camadas (Recomendada para o Projeto)

Para um projeto do escopo de vocês, a arquitetura clássica em três camadas (Three-Tier Architecture) é ideal. Ela é simples, bem compreendida, e fácil de explicar para os professores. As três camadas são:

**Camada de Apresentação (Frontend):**
É tudo que o usuário vê e interage. No caso de vocês, a aplicação React. Esta camada só sabe exibir informações e coletar inputs do usuário. Ela NÃO contém lógica de negócio. Por exemplo, quando o usuário preenche um formulário de login, a camada de apresentação valida se o email está no formato correto (validação cosmética), mas NÃO verifica se o email e senha estão corretos - isso é responsabilidade da camada de negócio.

**Camada de Negócio/Aplicação (Backend):**
É onde mora toda a lógica do sistema. As regras como "um aluno pode ter no máximo três empréstimos simultâneos" ou "livros atrasados mais de sete dias geram multa" vivem aqui. Esta camada recebe requisições da camada de apresentação, processa (consultando/modificando o banco de dados conforme necessário), e retorna respostas. No Java com Spring Boot, vocês vão implementar isso usando Controllers (recebem requisições HTTP), Services (lógica de negócio), e Repositories (acesso ao banco).

**Camada de Dados/Persistência (Banco de Dados):**
É onde os dados são armazenados permanentemente. No caso de vocês, o PostgreSQL. Esta camada só sabe guardar e recuperar dados conforme solicitado pela camada de negócio. Ela NÃO toma decisões de negócio (não deve ter lógica como "se usuário é aluno, limite a três empréstimos" - isso é responsabilidade da camada de negócio). A exceção são triggers e constraints que garantem integridade de dados.

**Como essas camadas conversam:**
Frontend faz requisições HTTP (GET, POST, PUT, DELETE) para o Backend. Backend processa e faz queries SQL para o Banco de Dados. Banco retorna dados para Backend. Backend formata esses dados em JSON e retorna para Frontend. Frontend exibe para o usuário. É sempre um fluxo unidirecional: Frontend → Backend → Banco → Backend → Frontend. O Frontend nunca acessa o Banco diretamente.

#### Template de Documentação da Arquitetura

**Decisão de Arquitetura: [Escolhida]**

Arquitetura: [PREENCHER - ex: Three-Tier Architecture / Microservices / Monolito em Camadas]

*Justificativa:*
[Por que escolhemos esta arquitetura? Que alternativas consideramos?]

Exemplo preenchido:

"Escolhemos Three-Tier Architecture (Frontend separado / Backend API / Banco de Dados) porque: (1) É apropriada para o escopo do projeto - não é nem tão simples que precisamos de um monólito tudo-em-um, nem tão complexo que justifique microservices; (2) Permite desenvolvimento paralelo - a equipe de frontend pode trabalhar simultaneamente com a de backend definindo apenas o contrato da API; (3) É fácil de escalar - se precisarmos, podemos rodar múltiplas instâncias do backend atrás de um load balancer; (4) É padrão da indústria e fácil de explicar na apresentação."

**Diagrama de Arquitetura:**

[Criar um diagrama visual mostrando as camadas e como elas se comunicam. Pode ser feito em ferramentas como Draw.io, Lucidchart, ou mesmo PowerPoint]

Caminho: `/docs/diagrams/arquitetura_sistema.png`

[Descrever o que está representado no diagrama]

**Detalhamento por Camada:**

**FRONTEND (React):**

*Responsabilidades:*
- [PREENCHER - ex: Renderizar interface do usuário]
- [PREENCHER - ex: Validar inputs do lado do cliente]
- [PREENCHER - ex: Fazer requisições HTTP para o backend]
- [PREENCHER - ex: Gerenciar estado da aplicação do lado do cliente]

*Tecnologias específicas:*
- Framework: [PREENCHER - React? Next.js? Vue?]
- Roteamento: [PREENCHER - React Router?]
- Estilização: [PREENCHER - Tailwind CSS? Material-UI? CSS Modules?]
- Estado Global: [PREENCHER - Context API? Redux? Zustand?]
- Requisições HTTP: [PREENCHER - Axios? Fetch? React Query?]
- Build Tool: [PREENCHER - Vite? Create React App? Next.js built-in?]

*Estrutura de Pastas:* (Documentar após decidir na próxima seção)

**BACKEND (Java + Spring Boot):**

*Responsabilidades:*
- [PREENCHER - ex: Implementar regras de negócio]
- [PREENCHER - ex: Validar dados do lado do servidor]
- [PREENCHER - ex: Autenticar e autorizar usuários]
- [PREENCHER - ex: Intermediar acesso ao banco de dados]
- [PREENCHER - ex: Expor API REST para o frontend]

*Tecnologias específicas:*
- Framework: Spring Boot
- Versão Java: [PREENCHER - Java 11? 17? 21?]
- Gerenciador de Dependências: [PREENCHER - Maven ou Gradle?]
- ORM: [PREENCHER - Spring Data JPA? Hibernate direto?]
- Autenticação: [PREENCHER - Spring Security + JWT? OAuth?]
- Validação: [PREENCHER - Bean Validation? Hibernate Validator?]
- Documentação da API: [PREENCHER - Springdoc OpenAPI? Swagger?]
- Testes: [PREENCHER - JUnit 5? Mockito?]

*Padrões Arquiteturais Aplicados:*
[Explicar padrões que vocês vão seguir no backend]

Exemplo:

"Controller-Service-Repository Pattern: Controllers recebem requisições HTTP e delegam para Services. Services contêm a lógica de negócio e chamam Repositories quando precisam acessar dados. Repositories abstraem o acesso ao banco usando Spring Data JPA. Isso cria separação clara de responsabilidades e facilita testes unitários (podemos mockar repositories para testar services sem precisar de banco de dados real)."

*Estrutura de Pastas:* (Documentar após decidir na próxima seção)

**BANCO DE DADOS (PostgreSQL):**

*Responsabilidades:*
- [PREENCHER - ex: Armazenar dados de forma persistente e confiável]
- [PREENCHER - ex: Garantir integridade referencial via constraints e FKs]
- [PREENCHER - ex: Otimizar queries via índices]
- [PREENCHER - ex: Executar lógica de validação via triggers quando apropriado]

*Versão:* PostgreSQL [PREENCHER - 14? 15? 16?]

*Extensões Utilizadas:*
- uuid-ossp (para gerar UUIDs)
- [PREENCHER - pgcrypto? Para criptografia?]
- [PREENCHER - pg_trgm? Para busca textual?]

*Estratégias de Otimização:*
[Como vão garantir que o banco é rápido?]

Exemplo:

"Índices criados em todas as colunas usadas em WHERE, JOIN, e ORDER BY frequentemente. Queries complexas serão analisadas com EXPLAIN para identificar bottlenecks. Se necessário, views materializadas para relatórios complexos que não precisam ser em tempo real."

---

## 📁 Parte 3: Estrutura de Pastas e Organização de Código

### Por que isso importa?

Imagine entrar em um projeto novo pela primeira vez. Se os arquivos estão jogados aleatoriamente, você vai gastar horas tentando entender onde está cada coisa. Mas se há uma estrutura lógica e consistente, você rapidamente identifica "Ah, os controllers ficam em `src/controllers`, os models em `src/models`, entendi!". Isso acelera muito o desenvolvimento em equipe.

Além disso, na apresentação, vocês podem mostrar a estrutura do projeto no VS Code e os professores vão ver que vocês organizaram tudo profissionalmente, não apenas "fizeram funcionar de qualquer jeito".

#### Template de Estrutura de Pastas

Preencher a estrutura que vocês decidirem seguir. Abaixo estão sugestões baseadas em convenções do Java/Spring Boot e React, mas vocês devem adaptá-las às necessidades do projeto:

**Backend (Java + Spring Boot):**

```
backend/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── br/edu/fatec/biblioteca/        # Pacote raiz
│   │   │       ├── BibliotecaApplication.java  # Classe principal
│   │   │       │
│   │   │       ├── controllers/                # Endpoints da API REST
│   │   │       │   ├── UsuarioController.java
│   │   │       │   ├── LivroController.java
│   │   │       │   └── EmprestimoController.java
│   │   │       │
│   │   │       ├── services/                   # Lógica de negócio
│   │   │       │   ├── UsuarioService.java
│   │   │       │   ├── LivroService.java
│   │   │       │   └── EmprestimoService.java
│   │   │       │
│   │   │       ├── repositories/               # Acesso ao banco (JPA)
│   │   │       │   ├── UsuarioRepository.java
│   │   │       │   ├── LivroRepository.java
│   │   │       │   └── EmprestimoRepository.java
│   │   │       │
│   │   │       ├── models/                     # Entidades (mapeiam tabelas)
│   │   │       │   ├── Usuario.java
│   │   │       │   ├── Livro.java
│   │   │       │   └── Emprestimo.java
│   │   │       │
│   │   │       ├── dto/                        # Data Transfer Objects
│   │   │       │   ├── UsuarioDTO.java
│   │   │       │   ├── LoginDTO.java
│   │   │       │   └── EmprestimoDTO.java
│   │   │       │
│   │   │       ├── security/                   # Configurações de segurança
│   │   │       │   ├── JwtUtils.java
│   │   │       │   ├── SecurityConfig.java
│   │   │       │   └── UserDetailsServiceImpl.java
│   │   │       │
│   │   │       ├── exceptions/                 # Exceções customizadas
│   │   │       │   ├── ResourceNotFoundException.java
│   │   │       │   └── GlobalExceptionHandler.java
│   │   │       │
│   │   │       └── config/                     # Configurações gerais
│   │   │           └── DatabaseConfig.java
│   │   │
│   │   └── resources/
│   │       ├── application.properties          # Configurações da app
│   │       ├── application-dev.properties      # Configs de dev
│   │       ├── application-prod.properties     # Configs de produção
│   │       └── db/
│   │           └── migration/                  # Scripts Flyway
│   │               ├── V001__create_tables.sql
│   │               └── V002__insert_seed_data.sql
│   │
│   └── test/                                   # Testes
│       └── java/
│           └── br/edu/fatec/biblioteca/
│               ├── services/
│               └── controllers/
│
├── pom.xml                                     # Dependências Maven
└── README.md                                   # Documentação do backend
```

**Frontend (React):**

```
frontend/
├── public/
│   ├── index.html
│   └── favicon.ico
│
├── src/
│   ├── components/                             # Componentes reutilizáveis
│   │   ├── common/                             # Genéricos
│   │   │   ├── Button/
│   │   │   │   ├── Button.jsx
│   │   │   │   └── Button.css
│   │   │   ├── Input/
│   │   │   └── Modal/
│   │   │
│   │   ├── layout/                             # Layout
│   │   │   ├── Navbar/
│   │   │   ├── Sidebar/
│   │   │   └── Footer/
│   │   │
│   │   └── features/                           # Específicos de domínio
│   │       ├── livros/
│   │       │   ├── LivroCard/
│   │       │   └── LivroDetalhes/
│   │       └── usuarios/
│   │           └── PerfilUsuario/
│   │
│   ├── pages/                                  # Páginas/Rotas
│   │   ├── Home.jsx
│   │   ├── Login.jsx
│   │   ├── Cadastro.jsx
│   │   ├── Catalogo.jsx
│   │   ├── MeusEmprestimos.jsx
│   │   └── Perfil.jsx
│   │
│   ├── services/                               # Chamadas à API
│   │   ├── api.js                              # Configuração Axios
│   │   ├── authService.js
│   │   ├── livrosService.js
│   │   └── emprestimosService.js
│   │
│   ├── contexts/                               # Context API
│   │   ├── AuthContext.jsx
│   │   └── ThemeContext.jsx
│   │
│   ├── hooks/                                  # Custom hooks
│   │   ├── useAuth.js
│   │   └── useLocalStorage.js
│   │
│   ├── utils/                                  # Utilitários
│   │   ├── formatters.js
│   │   └── validators.js
│   │
│   ├── styles/                                 # Estilos globais
│   │   └── global.css
│   │
│   ├── App.jsx                                 # Componente raiz
│   ├── routes.jsx                              # Configuração de rotas
│   └── index.jsx                               # Entry point
│
├── package.json
├── vite.config.js                              # Config do Vite
└── README.md
```

**Documentação das Decisões de Organização:**

[Explicar por que organizaram dessa forma. Quais padrões seguiram?]

Exemplo:

"No backend, seguimos a organização por camadas recomendada pelo Spring Boot: Controllers expõem a API, Services contêm lógica, Repositories acessam o banco. DTOs (Data Transfer Objects) são usados para transferir dados entre camadas sem expor as entidades JPA diretamente, o que dá mais controle sobre o que é serializado para JSON.

No frontend, organizamos componentes em três categorias: common (componentes genéricos reutilizáveis como Button, Input), layout (componentes de estrutura da página), e features (componentes específicos de cada funcionalidade). Pages representam rotas completas. Services abstraem toda comunicação com o backend, centralizando a lógica de requisições HTTP."

---

## 🎨 Parte 4: Design e Identidade Visual

### Conexão com a FATEC

Como este projeto é para a biblioteca da FATEC, o design precisa comunicar profissionalismo e alinhamento com a instituição. Isso significa usar elementos da identidade visual da FATEC onde apropriado (cores oficiais, logos), mas sem copiar o site da FATEC completamente - vocês estão criando algo novo que complementa, não replica.

#### Template de Guia de Design

**Paleta de Cores:**

[Definir cores primárias e secundárias]

- Cor Primária: [PREENCHER - ex: #C1272D (vermelho FATEC)] - Usada em botões principais, headers
- Cor Secundária: [PREENCHER - ex: #003366 (azul escuro)] - Usada em elementos de destaque secundários
- Cor de Fundo: [PREENCHER - ex: #F5F5F5 (cinza claro)]
- Cor de Texto: [PREENCHER - ex: #333333 (cinza escuro)]
- Cor de Erro: [PREENCHER - ex: #D32F2F (vermelho erro)]
- Cor de Sucesso: [PREENCHER - ex: #388E3C (verde)]

*Justificativa:*
[Por que essas cores? Como se conectam com a FATEC?]

**Tipografia:**

- Fonte Principal (Headings): [PREENCHER - ex: Roboto Bold]
- Fonte Secundária (Body): [PREENCHER - ex: Roboto Regular]
- Fonte Monospace (Código): [PREENCHER - ex: Fira Code]

*Justificativa:*
[Por que essas fontes? São legíveis? Modernas? Alinhadas com a FATEC?]

**Componentes Principais (a serem desenhados no Figma):**

Lista de telas/componentes que precisam ser desenhados:

- [ ] Tela de Login
- [ ] Tela de Cadastro
- [ ] Dashboard/Home
- [ ] Catálogo de Livros (grid view)
- [ ] Detalhes de um Livro
- [ ] Meus Empréstimos
- [ ] Perfil do Usuário
- [ ] [Adicionar outras conforme necessário]

**Arquivo do Figma:**

Link: [PREENCHER - link compartilhável do Figma]

Organização: [Descrever como o arquivo está organizado - ex: "Uma página para cada tela principal, componentes reutilizáveis em uma página separada de 'Design System'"]

---

## 🔐 Parte 5: Decisões de Segurança

Mesmo sendo um projeto acadêmico, vocês devem implementar segurança básica. Não apenas porque é importante na vida real, mas porque mostra para os professores que vocês pensaram além do "funcionar".

#### Template de Documentação de Segurança

**Autenticação:**

Método escolhido: [PREENCHER - ex: JWT (JSON Web Tokens)]

*Como funciona:*
[Explicar passo a passo o fluxo de autenticação]

Exemplo:

"Quando o usuário faz login, o backend valida o email e senha comparando com o hash armazenado no banco. Se correto, gera um JWT token assinado com uma chave secreta. Este token contém informações básicas do usuário (id, tipo de usuário) e tem validade de 7 dias. O frontend armazena este token no localStorage e o envia no header `Authorization: Bearer <token>` em toda requisição subsequente. O backend valida o token em cada requisição antes de processar."

**Senhas:**

Armazenamento: [PREENCHER - ex: Hash bcrypt com salt]

*Por quê:*
[Explicar por que nunca armazenar senhas em texto plano]

"Nunca armazenamos senhas em texto plano porque se o banco de dados vazar, todas as senhas estariam expostas. Usamos bcrypt para gerar um hash unidirecional - é impossível reverter o hash para obter a senha original. Bcrypt também adiciona um 'salt' (valor aleatório) antes de fazer hash, então duas pessoas com a mesma senha terão hashes diferentes."

**Proteção contra Ataques Comuns:**

[Listar e explicar proteções implementadas]

- SQL Injection: [ex: "Uso de prepared statements via JPA - nunca concatenar strings para montar queries"]
- XSS (Cross-Site Scripting): [ex: "React escapa automaticamente valores, previne injeção de código malicioso"]
- CSRF (Cross-Site Request Forgery): [ex: "Tokens CSRF em formulários sensíveis"]
- Brute Force: [ex: "Rate limiting de 5 tentativas de login por IP a cada 15 minutos"]

**CORS (Cross-Origin Resource Sharing):**

Configuração: [PREENCHER - quais origens são permitidas?]

Exemplo:

"Configuramos CORS para aceitar requisições apenas de `https://biblioteca-fatec.vercel.app` (frontend em produção) e `http://localhost:3000` (frontend em desenvolvimento). Isso previne que sites maliciosos façam requisições ao nosso backend fingindo ser o usuário."

---

## ✅ Checklist de Conclusão do Milestone 1

### Banco de Dados
- [ ] Modelo conceitual criado no BrModelo e exportado
- [ ] Modelo lógico criado no DBDesigner e exportado
- [ ] Scripts SQL de criação de tabelas escritos e testados localmente
- [ ] Migrations organizadas e numeradas sequencialmente
- [ ] Todas as tabelas têm comentários explicativos
- [ ] Índices criados em colunas apropriadas
- [ ] Constraints de integridade definidas
- [ ] Relacionamentos (FKs) todos documentados

### Arquitetura
- [ ] Arquitetura escolhida e justificada
- [ ] Diagrama de arquitetura criado e documentado
- [ ] Responsabilidades de cada camada claras
- [ ] Stack tecnológico de cada camada definido
- [ ] Padrões arquiteturais documentados

### Estrutura de Código
- [ ] Estrutura de pastas do backend definida
- [ ] Estrutura de pastas do frontend definida
- [ ] Convenções de nomenclatura acordadas
- [ ] Todos da equipe entendem onde cada tipo de código fica

### Design
- [ ] Paleta de cores definida e documentada
- [ ] Tipografia escolhida
- [ ] Componentes principais listados
- [ ] Pelo menos 3-5 telas principais desenhadas no Figma

### Segurança
- [ ] Método de autenticação escolhido e documentado
- [ ] Estratégia de armazenamento de senhas definida
- [ ] Proteções contra ataques comuns planejadas
- [ ] Configuração de CORS definida

### Documentação
- [ ] Este documento completamente preenchido
- [ ] Todos os diagramas criados e incluídos
- [ ] Decisões justificadas (não apenas listadas)
- [ ] README atualizado com informações deste milestone

### Validação em Equipe
- [ ] Reunião de revisão realizada (todos revisaram o documento)
- [ ] Tech Lead aprovou as decisões técnicas
- [ ] Database Lead aprovou a modelagem
- [ ] Não há dúvidas pendentes sobre a fundação
- [ ] Equipe está confiante para começar a codificar

---

## 🎯 Entregável Final do Milestone 1

**Documento Consolidado:** "Fundação Técnica - Projeto [Nome]"

**Conteúdo:**
- Todas as seções acima preenchidas com decisões da equipe
- Todos os diagramas (ER conceitual, lógico, arquitetura)
- Screenshots do Figma
- Scripts SQL organizados na pasta de migrations

**Apresentação Interna (para a equipe):**
Fazer uma reunião onde cada responsável apresenta sua parte:
- Database Lead mostra e explica os diagramas de banco
- Tech Lead mostra e explica a arquitetura
- Frontend/UI Lead mostra e explica os designs do Figma

Isso garante que todos entenderam a fundação antes de começar a construir.

---

**Data de Conclusão Planejada:** [PREENCHER]  
**Data Real de Conclusão:** [PREENCHER]  
**Próximo Milestone:** Milestone 2 - PoC
