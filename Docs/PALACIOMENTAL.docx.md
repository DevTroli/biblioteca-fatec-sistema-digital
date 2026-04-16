  
**FACULDADE DE TECNOLOGIA DE PRAIA GRANDE \- CENTRO PAULA SOUZA**  
**Curso de Tecnologia em Desenvolvimento de Software Multiplataforma**

PABLO TROLI · FELIPE FIGUEIREDO · YOHAN RUIZ  
EDUARDO ELIAS · MATHEUS FERNANDES · IAGO SAMPAIO

**PALÁCIO MENTAL:**  
**REDE ACADÊMICA DE COMPARTILHAMENTO DE PROJETOS ACADÊMICOS**

Projeto Integrador — Engenharia de Software

Praia Grande  
2026

**PRAIA GRANDE**  
**2025**

PABLO TROLI · FELIPE FIGUEIREDO · YOHAN RUIZ  
EDUARDO ELIAS · MATHEUS FERNANDES · IAGO SAMPAIO

**PALÁCIO MENTAL:**  
**REDE ACADÊMICA DE COMPARTILHAMENTO DE PROJETOS E IDEIAS ACADÊMICAS**

| *Documentação parcial apresentada à disciplina de Engenharia de Software do Curso Superior de Tecnologia em Desenvolvimento de Software Multiplataforma da Faculdade de Tecnologia de Praia Grande, como requisito parcial do Projeto Integrador Orientador: Prof. Marcio Galvão* |
| :---- |

Praia Grande  
2026

**SUMÁRIO**

1  INTRODUÇÃO ..........................................................................  2  
2  SITUAÇÃO-PROBLEMA ....................................................................  2  
3  OBJETIVOS .............................................................................  3  
4  PROPOSTA DE VALOR E JUSTIFICATIVA ....................................................  3  
5  ARQUITETURA GERAL DO PROJETO .........................................................  4  
6  REQUISITOS FUNCIONAIS E NÃO FUNCIONAIS ..............................................  5  
7  IDENTIFICAÇÃO DE ENTIDADES E ATRIBUTOS ..............................................  6  
8  RELACIONAMENTOS .......................................................................  9  
9  REGRAS DE NEGÓCIO ....................................................................  9  
10  NORMALIZAÇÃO .........................................................................  10  
11  STACK TECNOLÓGICA ....................................................................  11  
12  DIAGRAMAS UML ........................................................................  12  
13  BACKEND — API REST ...................................................................  12  
14  FRONTEND .............................................................................  13  
15  DEVOPS ................................................................................  13  
16  CONSIDERAÇÕES FINAIS .................................................................  14  
    REFERÊNCIAS ..........................................................................  15

# **1 INTRODUÇÃO**

O presente documento constitui a documentação do Projeto Integrador Palácio Mental, desenvolvido como parte da disciplina de Engenharia de Software do Curso Superior de Tecnologia em Desenvolvimento de Software Multiplataforma da Fatec Praia Grande, sob orientação do Prof. Marcio Galvão.  
O Palácio Mental é uma plataforma web de compartilhamento de projetos e ideias acadêmicas. A denominação remete ao conceito de palace of memory — técnica mnemônica que consiste em organizar informações em um espaço mental estruturado —, metáfora que traduz a proposta da plataforma: um espaço onde ideias deixam de ser rascunho e passam a existir de forma organizada, visível e compartilhável.  
Este documento cobre a fase inicial do projeto, com foco na fundação de Banco de Dados Relacional, e apresenta o planejamento das fases subsequentes (Backend, Frontend e DevOps) de forma estrutural, a serem detalhadas e implementadas nas etapas seguintes do Projeto Integrador.

# 

# **2 SITUAÇÃO-PROBLEMA**

A maioria dos projetos desenvolvidos em cursos de universitários cumpre um ciclo curto: são elaborados ao longo de semanas ou meses, entregues ao professor para avaliação e, em seguida, arquivados. Esse fluxo resulta na perda de trabalhos que poderiam demonstrar habilidades técnicas relevantes, documentar soluções para problemas reais ou servir de referência para outros estudantes.  
Plataformas existentes não atendem plenamente às necessidades dos estudantes de certos nichos de cursos. O GitHub é orientado ao versionamento de código-fonte; o LinkedIn é uma rede profissional de propósito genérico; o Behance é voltado ao design gráfico. Nenhuma dessas ferramentas é pensada para o projeto acadêmico no geral em sua totalidade — compreendendo o processo criativo, as versões intermediárias, a documentação e o feedback da comunidade.  
Diante desse cenário, identificou-se a necessidade de uma plataforma específica que permita ao estudante publicar projetos e ideias em qualquer estágio de desenvolvimento, organizá-los por categoria e palavras-chave, receber comentários da comunidade e construir um portfólio acadêmico progressivo ao longo do curso.

# 

# **3 OBJETIVOS**

## **3.1 Objetivo Geral**

Desenvolver o Palácio Mental — plataforma web de compartilhamento de projetos e ideias acadêmicas —, cobrindo desde a modelagem de banco de dados até a implantação em produção, ao longo das fases do Projeto Integrador de Engenharia de Software.

## **3.2 Objetivos Específicos — Fase 1 (Banco de Dados)**

- Identificar as entidades, atributos e relacionamentos do domínio do problema;  
- Elaborar o modelo conceitual por meio do Diagrama de Entidade-Relacionamento (DER);  
- Desenvolver o modelo lógico com tipos de dados, chaves primárias e estrangeiras;  
- Documentar as regras de negócio que governam as operações sobre os dados;  
- Implementar o modelo físico por meio de scripts DDL no Oracle Database.

## **3.3 Objetivos Específicos — Fases Subsequentes**

- Fase 2 — Backend: desenvolver API REST com autenticação e endpoints para todas as entidades;  
- Fase 3 — Frontend: implementar interface web responsiva com as quatro telas principais do sistema;  
- Fase 4 — DevOps: containerizar a aplicação, configurar CI/CD e realizar deploy em produção.

# 

# **4 PROPOSTA DE VALOR E JUSTIFICATIVA**

O Palácio Mental se posiciona como uma rede acadêmica vertical — especializada em projetos, com proposta de valor distinta para diferentes perfis de usuário.

**Quadro 1 — Proposta de valor por perfil de usuário**

| Perfil | Problema atual | Benefício oferecido |
| :---- | :---- | :---- |
| Estudante de tecnologia | Projetos ficam arquivados após a entrega | Portfólio vivo, construído progressivamente ao longo do curso |
| Estudante iniciante | Desconhece o que colegas mais avançados produzem | Feed de projetos por categoria e nível |
| Professor / orientador | Sem visibilidade do progresso extraclasse | Projetos públicos com histórico de atualizações |
| Recrutador / empresa | Difícil identificar talentos acadêmicos emergentes | Perfis com projetos reais, comentados pela comunidade |

*Fonte: Elaborado pelos autores (2026).*

A justificativa acadêmica reside no alinhamento com as competências esperadas das disciplinas de Engenharia de Software, Banco de Dados Relacional entre outras: modelagem de domínio, aplicação de padrões arquiteturais, normalização e implementação em Oracle. O projeto também serve de base para as disciplinas subsequentes de Desenvolvimento Web, Estrutura de Dados, Sistemas Operacional.

# 

# **5 ARQUITETURA GERAL DO PROJETO**

O Palácio Mental adota uma arquitetura em quatro camadas, organizadas de forma hierárquica e com comunicação definida entre cada nível. A arquitetura foi planejada para o MVP (Minimum Viable Product), contemplando as principais funcionalidades da plataforma de forma coesa e funcional.

**Quadro 2 — Camadas da arquitetura do Palácio Mental**

| Camada | Componentes | Comunicação com a camada acima | Status |
| :---- | :---- | :---- | :---- |
| Banco de Dados | Oracle APEX · Servidor de Mídia | — | 🔲 Fase atual |
| Backend | Auth simples · API REST · Busca básica por SQL nativo | SQL / REST | 🔲 Fase 2 |
| Frontend | Feed de Ideias · Página da Ideia · Palácio Mental · Editor | talvez JSON via browser | 🔲 Fase 3 |
| DevOps | Docker · Terraform · CI/CD (GitHub Actions) | containerizado | 🔲 Fase 4 |

*Fonte: Elaborado pelos autores (2026).*

## **5.1 Banco de Dados**

Camada de persistência implementada no Oracle APEX. Armazena usuários, projetos, tags e comentários. A mídia é gerenciada via campo de URL que referencia um servidor de mídia externo — decisão que simplifica a camada de banco e delega o armazenamento de arquivos binários a um serviço dedicado.

## **5.2 Backend**

Camada de lógica de negócio e exposição de API. Responsável pela autenticação simples (login/senha com cookies), pelos endpoints REST das entidades principais e pela busca utilizando SQL nativo do Oracle. A comunicação com o banco se dá por SQL direto e chamadas REST do APEX.

## **5.3 Frontend**

Interface web composta por quatro telas principais: Feed de Ideias (home com filtros), Página da Ideia (exibição completa com mídia via URL), Palácio Mental (perfil e gestão dos projetos do usuário) e Editor (criação e edição de projetos). O frontend consome a API via JSON no navegador.

## **5.4 DevOps**

Toda a aplicação é containerizada com Docker Compose. A infraestrutura é provisionada via Terraform (IaC básico). O pipeline de CI/CD utiliza GitHub Actions para executar testes automáticos em Pull Requests e realizar deploy automático na branch principal. Testes automatizados mais abrangentes estão planejados para após a estabilização do MVP.

# 

# **6 REQUISITOS FUNCIONAIS E NÃO FUNCIONAIS**

## **6.1 Requisitos Funcionais (RF)**

Os requisitos funcionais descrevem as funcionalidades que o sistema deve oferecer ao usuário.

**Quadro 3 — Requisitos funcionais do sistema**

| Código | Requisito | Descrição |
| :---- | :---- | :---- |
| RF01 | Cadastro e autenticação | Usuário pode criar conta, fazer login e logout com segurança. |
| RF02 | Publicação de projetos | Usuário pode criar, editar e excluir projetos com título, descrição, status e mídia. |
| RF03 | Feed de projetos | Sistema exibe feed público de projetos publicados, com filtros por categoria e tag. |
| RF04 | Perfil — Palácio Mental | Cada usuário tem um perfil público com lista de seus projetos. |
| RF05 | Curtidas e salvos | Usuário pode curtir e salvar projetos de outros criadores. |
| RF06 | Comentários | Usuário pode comentar em projetos publicados. |
| RF07 | Categorias e tags | Sistema permite classificar projetos por categoria e palavras-chave livres. |
| RF08 | Busca | Usuário pode buscar projetos por texto, categoria ou tag. |

*Fonte: Elaborado pelos autores (2026).*

## 

## **6.2 Requisitos Não Funcionais (RNF)**

Os requisitos não funcionais estabelecem critérios de qualidade, desempenho e restrições do sistema.

**Quadro 4 — Requisitos não funcionais do sistema**

| Código | Atributo | Descrição |
| :---- | :---- | :---- |
| RNF01 | Desempenho | Páginas carregam em menos de 3 segundos na maioria dos cenários de uso. |
| RNF02 | Segurança | Autenticação com JWT, proteção contra XSS, CSRF e SQL Injection. |
| RNF03 | Usabilidade | Interface intuitiva — novo usuário conclui cadastro sem assistência. |
| RNF04 | Escalabilidade | Arquitetura containerizada suporta crescimento sem refatoração estrutural. |
| RNF05 | Disponibilidade | Sistema disponível 99,5% do tempo em ambiente de produção. |
| RNF06 | Manutenibilidade | Código documentado, testado e organizado por camadas bem definidas. |

*Fonte: Elaborado pelos autores (2026).*

# 

# **7 IDENTIFICAÇÃO DE ENTIDADES E ATRIBUTOS**

## **7.1 Entidade Central**

### ***7.1.1 PROJETO***

Entidade pivot do sistema. Representa qualquer ideia ou projeto publicado por um usuário, em qualquer estágio de desenvolvimento.

**Quadro 5 — Atributos da entidade PROJETO**

| Atributo | Tipo | Constraint | Descrição |
| :---- | :---- | :---- | :---- |
| id | NUMBER | PK, NOT NULL, IDENTITY | Identificador único |
| usuario\_id | NUMBER | FK → USUARIO, NOT NULL | Autor do projeto |
| categoria\_id | NUMBER | FK → CATEGORIA | Categoria principal |
| titulo | VARCHAR2(200) | NOT NULL | Título do projeto |
| descricao | CLOB | — | Descrição completa |
| status | VARCHAR2(20) | CHECK IN ('rascunho','publicado','arquivado') | Estado de publicação |
| criado\_em | DATE | DEFAULT SYSDATE | Data de criação |
| atualizado\_em | DATE | DEFAULT SYSDATE | Última atualização |

*Fonte: Elaborado pelos autores (2026).*

## **7.2 Entidades Fortes**

### ***7.2.1 USUÁRIO***

Representa qualquer criador cadastrado na plataforma. Entidade independente — não depende de nenhuma outra para existir.

**Quadro 6 — Atributos da entidade USUÁRIO**

| Atributo | Tipo | Constraint |
| :---- | :---- | :---- |
| id | NUMBER | PK, NOT NULL, IDENTITY |
| username | VARCHAR2(50) | NOT NULL, UNIQUE |
| email | VARCHAR2(150) | NOT NULL, UNIQUE |
| senha\_hash | VARCHAR2(255) | NOT NULL |
| nome\_exibicao | VARCHAR2(100) | — |
| bio | VARCHAR2(500) | — |
| avatar\_url | VARCHAR2(300) | — |
| criado\_em | DATE | DEFAULT SYSDATE |

*Fonte: Elaborado pelos autores (2026).*

### ***7.2.2 CATEGORIA e TAG***

CATEGORIA: classificação principal dos projetos (ex: Web, Mobile, IA, IoT). Atributos: id (PK, IDENTITY), nome (VARCHAR2(80), NOT NULL, UNIQUE).  
TAG: palavras-chave livres para indexação e descoberta (ex: oracle, python, docker). Atributos: id (PK, IDENTITY), nome (VARCHAR2(50), NOT NULL, UNIQUE).

## **7.3 Entidades Fracas**

### ***7.3.1 COMENTARIO***

Depende simultaneamente de PROJETO e de USUARIO. Atributos: id (PK, IDENTITY), projeto\_id (FK → PROJETO, NOT NULL), usuario\_id (FK → USUARIO, NOT NULL), conteudo (VARCHAR2(2000), NOT NULL), criado\_em (DATE, DEFAULT SYSDATE).

### 

### ***7.3.2 MIDIA***

Depende de PROJETO. Representa arquivos e links associados ao projeto. Atributos: id (PK, IDENTITY), projeto\_id (FK → PROJETO, NOT NULL), tipo (VARCHAR2(20), CHECK IN ('imagem','video','link')), url (VARCHAR2(500), NOT NULL), criado\_em (DATE, DEFAULT SYSDATE).

## **7.4 Tabelas Associativas**

As tabelas associativas resolvem os relacionamentos N:M que não podem ser implementados diretamente por chaves estrangeiras simples.

**Quadro 7 — Tabelas associativas**

| Tabela | Relacionamento resolvido | Atributos adicionais |
| :---- | :---- | :---- |
| PROJETO\_TAG | PROJETO ↔ TAG (N:M) | Nenhum — PK composta (projeto\_id, tag\_id) |
| CURTIDA | USUARIO ↔ PROJETO — curte (N:M) | criado\_em (registro temporal); UNIQUE(projeto\_id, usuario\_id) |
| SALVO | USUARIO ↔ PROJETO — salva (N:M) | criado\_em (registro temporal); UNIQUE(projeto\_id, usuario\_id) |

*Fonte: Elaborado pelos autores (2026).*

# 

# **8 RELACIONAMENTOS**

**Quadro 8 — Relacionamentos entre entidades**

| Relacionamento | Entidades | Cardinalidade | Descrição |
| :---- | :---- | :---- | :---- |
| publica | USUARIO → PROJETO | 1:N | Um usuário publica vários projetos |
| classifica | CATEGORIA → PROJETO | 1:N | Uma categoria classifica vários projetos |
| agrupa | PROJETO ↔ TAG | N:M | Resolvido por PROJETO\_TAG |
| escreve | USUARIO → COMENTARIO | 1:N | Um usuário escreve vários comentários |
| tem | PROJETO → COMENTARIO | 1:N | Um projeto recebe vários comentários |
| contém | PROJETO → MIDIA | 1:N | Um projeto contém vários arquivos de mídia |
| curte | USUARIO ↔ PROJETO | N:M | Resolvido por CURTIDA |
| salva | USUARIO ↔ PROJETO | N:M | Resolvido por SALVO |

*Fonte: Elaborado pelos autores (2026).*

# 

# **9 REGRAS DE NEGÓCIO**

**Quadro 9 — Regras de negócio**

| Código | Regra | Implementação Oracle |
| :---- | :---- | :---- |
| RN01 | Autoria única — projeto pertence a um único usuário | NOT NULL na FK usuario\_id de PROJETO |
| RN02 | Username e e-mail únicos | UNIQUE em USUARIO.username e USUARIO.email |
| RN03 | Status controlado — apenas três estados | CHECK (status IN ('rascunho','publicado','arquivado')) |
| RN04 | Curtida única por usuário/projeto | UNIQUE(projeto\_id, usuario\_id) em CURTIDA |
| RN05 | Salvo único por usuário/projeto | UNIQUE(projeto\_id, usuario\_id) em SALVO |
| RN06 | Tag não duplicada por projeto | PK composta em PROJETO\_TAG |
| RN07 | Tipo de mídia restrito | CHECK (tipo IN ('imagem','video','link')) |
| RN08 | Comentário não pode ser vazio | NOT NULL em COMENTARIO.conteudo |
| RN09 | Cascata na exclusão de projeto | ON DELETE CASCADE nas FKs dependentes |
| RN10 | Senha protegida | Hash armazenado; responsabilidade da camada de aplicação |

*Fonte: Elaborado pelos autores (2026).*

# 

# **10 NORMALIZAÇÃO**

O modelo lógico foi construído respeitando as três primeiras formas normais da teoria relacional.

## **10.1 Primeira Forma Normal (1FN)**

Todos os atributos são atômicos. Atributos multivalorados, como tags de um projeto, foram separados em tabela própria (PROJETO\_TAG), eliminando grupos repetidos.

## **10.2 Segunda Forma Normal (2FN)**

Nas tabelas com chave primária composta (PROJETO\_TAG), todos os atributos dependem da chave inteira. A tabela não possui atributos além das chaves que a compõem, garantindo conformidade com a 2FN.

## **10.3 Terceira Forma Normal (3FN)**

Não há dependências transitivas. Cada atributo depende diretamente da chave primária de sua tabela. Dados do usuário autor, por exemplo, não são replicados em PROJETO — apenas a chave estrangeira usuario\_id é mantida.

# 

# **11 STACK TECNOLÓGICA**

A stack tecnológica foi parcialmente definida nesta fase inicial. As tecnologias da camada de banco de dados foram confirmadas; as demais serão detalhadas e validadas nas fases correspondentes do projeto.

**Quadro 10 — Stack tecnológica do Palácio Mental**

| Camada | Tecnologia | Status | Justificativa |
| :---- | :---- | :---- | :---- |
| Banco de Dados | Oracle Database XE / Oracle APEX | ✅ Confirmado | Disciplina de BD \+ mercado enterprise |
| Backend | Java \+ Spring Boot (previsto) | 🔲 A confirmar — Fase 2 | Conteúdo do curso \+ banca de professores |
| Frontend | React \+ Vite (previsto) | 🔲 A confirmar — Fase 3 | Componentização \+ ecossistema moderno |
| DevOps | Docker \+ Terraform \+ GitHub Actions | 🔲 A confirmar — Fase 4 | Containerização e automação de CI/CD |
| Design | Figma | 🔲 A confirmar — Fase 3 | Prototipação colaborativa de interfaces |

*Fonte: Elaborado pelos autores (2026).*

# 

# **12 DIAGRAMAS UML**

Os diagramas UML serão elaborados ao longo das fases do projeto, conforme as responsabilidades de cada camada forem sendo implementadas.

*\[ DIAGRAMA DE CASO DE USO — A COMPLETAR NA FASE CORRESPONDENTE \]*

*A ser elaborado na Fase 2 — Backend. Identificação de atores (Usuário Visitante, Usuário Criador, Administrador) e funcionalidades do sistema.*

*\[ DIAGRAMA DE SEQUÊNCIA — A COMPLETAR NA FASE CORRESPONDENTE \]*

*A ser elaborado na Fase 2 — Backend. Fluxos de autenticação, publicação de projeto e interação com comentários.*

*\[ DIAGRAMA DE CLASSES — A COMPLETAR NA FASE CORRESPONDENTE \]*

*A ser elaborado na Fase 2 — Backend. Estrutura das entidades, métodos dos services e relacionamentos entre classes Java.*

*\[ DIAGRAMA DE IMPLANTAÇÃO — A COMPLETAR NA FASE CORRESPONDENTE \]*

*A ser elaborado na Fase 4 — DevOps. Infraestrutura de produção, containers Docker e serviços em nuvem.*

# 

# **13 BACKEND — API REST**

Esta seção será completada na Fase 2 do Projeto Integrador, após a validação do modelo de banco de dados.

*\[ AUTENTICAÇÃO — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Auth simples com login/senha \+ cookies. JWT token para gerenciamento de sessão.*

*\[ ENDPOINTS DA API REST — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Recursos: /usuarios, /projetos, /categorias, /tags, /comentarios, /curtidas, /salvos. Métodos: GET, POST, PUT, DELETE.*

*\[ BUSCA E FILTROS — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Busca por texto, categoria e tag implementada via SQL nativo no Oracle através do APEX.*

*\[ DOCUMENTAÇÃO DA API — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Swagger / OpenAPI spec para todos os endpoints. A ser gerada automaticamente com SpringDoc.*

# 

# **14 FRONTEND**

Esta seção será completada na Fase 3 do Projeto Integrador.

*\[ FEED DE IDEIAS — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Página inicial com lista de projetos publicados. Filtros por categoria e tag. Scroll infinito (lazy loading).*

*\[ PÁGINA DA IDEIA — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Exibição completa do projeto: título, descrição, mídia via URL, autor, tags, comentários e botões de interação.*

*\[ PALÁCIO MENTAL (PERFIL) — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Perfil público do usuário com lista de seus projetos. Gestão de criação, edição e exclusão de projetos próprios.*

*\[ EDITOR — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Formulário de criação e edição de projetos. Campos: título, descrição, status, categoria, tags e URL de mídia.*

# 

# **15 DEVOPS**

Esta seção será completada na Fase 4 do Projeto Integrador. A infraestrutura planejada compreende containerização completa da aplicação e automação do pipeline de entrega.

*\[ DOCKER — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Docker Compose local com serviços separados para banco, backend e frontend. Imagens publicadas no Docker Hub.*

*\[ TERRAFORM — A COMPLETAR NA FASE CORRESPONDENTE \]*

*IaC (Infrastructure as Code) básico para provisionamento dos ambientes de staging e produção em nuvem.*

*\[ CI/CD COM GITHUB ACTIONS — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Pipeline automático: testes em todo Pull Request \+ deploy automático na branch main para produção.*

*\[ TESTES AUTOMATIZADOS (FUTURO) — A COMPLETAR NA FASE CORRESPONDENTE \]*

*Camada de testes de integração e end-to-end planejada para após a estabilização do MVP.*

# 

# **16 CONSIDERAÇÕES FINAIS**

Este documento apresentou a primeira fase do Projeto Integrador Palácio Mental, cobrindo desde a análise do problema e a proposta de valor até a modelagem completa do banco de dados relacional no Oracle, incluindo entidades, relacionamentos, regras de negócio e normalização.  
A arquitetura em quatro camadas definida nesta fase — Banco de Dados, Backend, Frontend e DevOps — fornece uma estrutura clara e progressiva para o desenvolvimento do produto ao longo das próximas etapas do Projeto Integrador. As seções relativas às fases 2, 3 e 4 foram intencionalmente deixadas em aberto, com estrutura e diretrizes definidas, aguardando a implementação nas disciplinas e semestres correspondentes.  
A escolha do Oracle Database como SGBD ancora o projeto ao conteúdo da disciplina de Banco de Dados Relacional e ao mercado enterprise, permitindo a aplicação prática de constraints de integridade, índices, sequences e, futuramente, procedimentos armazenados e triggers.

# 

# **REFERÊNCIAS**

DATE, C. J. Introdução a sistemas de bancos de dados. 8\. ed. Rio de Janeiro: Elsevier, 2004\.

ELMASRI, R.; NAVATHE, S. B. Sistemas de banco de dados. 7\. ed. São Paulo: Pearson, 2019\.

ORACLE CORPORATION. Oracle Database SQL Language Reference. Disponível em: https://docs.oracle.com. Acesso em: mar. 2026\.

PRESSMAN, R. S.; MAXIM, B. R. Engenharia de software: uma abordagem profissional. 8\. ed. Porto Alegre: AMGH, 2016\.

SOMMERVILLE, I. Engenharia de software. 10\. ed. São Paulo: Pearson, 2018\.

SILBERSCHATZ, A.; KORTH, H. F.; SUDARSHAN, S. Sistema de banco de dados. 6\. ed. Rio de Janeiro: Elsevier, 2012\.