# 🧠 Mind Palace: Plataforma de Ideias Criativas

> **Trabalho Semestral - Fevereiro a Junho de 2025**
> **Objetivo:** Desenvolver uma plataforma online para armazenar, organizar e compartilhar ideias criativas.

---

## 🎯 Visão Geral

O **Mind Palace** é uma plataforma online inovadora projetada para ser um refúgio digital para a criatividade. Ele funciona como uma fusão de portfólio pessoal, rede social criativa e biblioteca de ideias, permitindo que usuários postem e explorem uma vasta gama de conteúdos criativos, como textos, imagens, músicas, vídeos, ideias de projetos, roteiros, histórias e conceitos experimentais.

Cada usuário terá seu próprio "palácio mental" (perfil), um espaço personalizado para organizar e exibir suas criações. O projeto visa fomentar uma comunidade vibrante onde a troca de ideias e a colaboração são incentivadas, ao mesmo tempo em que oferece ferramentas para a organização eficiente do pensamento criativo.

---

## 💡 Ideia Central: O Mind Palace

O conceito central do Mind Palace é fornecer um ambiente digital onde a criatividade possa florescer. A plataforma permitirá que os usuários:

*   **Armazenem e organizem** suas ideias de forma estruturada.
*   **Compartilhem** suas criações com uma comunidade engajada.
*   **Explorem** o trabalho de outros criadores, buscando inspiração e colaboração.

---

## 🚀 Escopo do MVP (Produto Mínimo Viável)

O objetivo do MVP é validar três premissas fundamentais:

1.  **As pessoas querem postar ideias publicamente?**
2.  **As pessoas querem explorar ideias de outros criadores?**
3.  **As ideias precisam de organização e conexão?**

Se estas premissas forem validadas, o projeto terá um potencial real para crescimento, incluindo a possibilidade de funcionalidades futuras como um "cartório e licenciamento de ideias" para proteger a autoria.

### Estrutura Mínima do Site para o MVP

#### Página Inicial (Feed de Ideias)

Exibirá ideias recentes da comunidade, com os seguintes elementos para cada ideia:

*   **Título da Ideia**
*   **Autor**
*   **Categoria**
*   **Tags**
*   **Botão para abrir** (visualizar detalhes)

**Exemplos:**

*   **Ideia:** Cidade onde ninguém pode mentir
    *   **Data de Criação e Modificação:** 19/03/2026
    *   **Autor:** Maria
    *   **Categoria:** Ficção
*   **Ideia:** Sistema de energia baseado em emoções
    *   **Autor:** João
    *   **Categoria:** Tecnologia

#### Página da Ideia

Ao clicar em uma ideia, o usuário será direcionado para uma página detalhada contendo:

*   **Título**
*   **Descrição** completa da ideia
*   **Autor**
*   **Data** de criação e última modificação
*   **Tags** relacionadas
*   **Seção de Comentários** para interação da comunidade

**Exemplo:**

*   **Título:** Trem da Hipnose
*   **Descrição:** Um trem luxuoso que faz passageiros esquecerem da realidade e viverem numa ilusão perfeita.
*   **Tags:** fantasia, psicológico, ficção

### Desafios e Soluções do MVP

#### Problema da Rede Social Vazia (Cold Start)

Redes sociais novas frequentemente enfrentam o desafio de atrair e reter usuários iniciais. Para o Mind Palace, a solução será:

*   **Foco em Comunidades Nichadas:** Começar atraindo grupos específicos de criadores, como escritores, criadores de jogos e artistas, em vez de tentar alcançar um público amplo desde o início. Isso garantirá um conteúdo inicial de qualidade e engajamento.

#### Problema de Moderação

Conteúdo inadequado (spam, pornografia, propaganda, ilegal) é um risco para qualquer plataforma de conteúdo gerado por usuários. Para mitigar isso, o Mind Palace implementará:

*   **Botão de Reportar:** Ferramenta para que os próprios usuários sinalizem conteúdo impróprio.
*   **Sistema de Moderação:** Equipe ou algoritmos dedicados à revisão e remoção de conteúdo que viole as diretrizes da plataforma.
*   **Filtros Automáticos:** Implementação de tecnologias para identificar e bloquear proativamente conteúdo indesejado.

---

## 📅 Cronograma do Projeto (Adaptado para Mind Palace)

O cronograma será reestruturado para alinhar-se com os objetivos do Mind Palace, mantendo a estrutura de Milestones para organização:

*   **Milestone 0: Planejamento e Visão (2 semanas)**
    *   Definição completa da visão do Mind Palace, pesquisa de mercado para validação das premissas do MVP, e refinamento da stack tecnológica.
*   **Milestone 1: Fundação Conceitual e Design (2-3 semanas)**
    *   Modelagem do banco de dados para `IDEIAS`, `CRIADORES`, `COMENTARIOS` e `TAGS`. Definição da arquitetura do sistema e criação dos primeiros designs de telas (Feed de Ideias, Página da Ideia, Perfil) no Figma.
*   **Milestone 2: Prova de Conceito (PoC) (3-4 semanas)**
    *   Implementação de um fluxo básico de postagem de ideias e visualização no feed. Desenvolvimento de uma API de saúde do sistema e configuração inicial do banco de dados com as novas entidades.
*   **Milestone 3: MVP - Minimum Viable Product (4-5 semanas)**
    *   Implementação de todas as funcionalidades "MUST HAVE": Feed de Ideias funcional, Página da Ideia completa, Perfil do Criador (Palácio Mental), e um sistema básico de moderação (botão de reportar). Deploy em ambiente de produção para testes beta com usuários nichados.
*   **Milestone 4: Documentação e Métricas (2-3 semanas)**
    *   Elaboração da documentação técnica e de usuário. Coleta e análise de métricas de engajamento e feedback dos usuários beta para validar as premissas do MVP.
*   **Milestone 5: Refinamento e Lançamento (1-2 semanas)**
    *   Correção de bugs, otimização de performance e segurança. Preparação para a apresentação final e possível lançamento para a comunidade inicial.

---

## 🛠️ Stack Tecnológica

A stack tecnológica será mantida, pois é robusta e flexível para o novo escopo do projeto:

### Backend
*   **Java + Spring Boot:** Para construir uma API RESTful escalável e performática.

### Frontend
*   **React (com Vite):** Para uma interface de usuário dinâmica e responsiva.

### Banco de Dados
*   **PostgreSQL:** Um banco de dados relacional poderoso e confiável para armazenar as ideias e dados dos usuários.

### Deploy e DevOps
*   A ser definido, com foco em automação e escalabilidade para suportar o crescimento da plataforma.

---

## 👥 Organização da Equipe

A organização da equipe e os rituais ágeis (planejamentos, sincronizações, reviews, retrospectivas) serão mantidos, adaptando as responsabilidades para o novo foco do projeto. O GitHub continuará sendo a ferramenta central para gerenciamento de código e tarefas.

---

## 📚 Documentação do Projeto

Toda a documentação será atualizada e organizada na pasta `/docs` do repositório, refletindo a transição para o Mind Palace. Documentos específicos para cada Milestone guiarão a equipe nas decisões e entregas.

---

## 🔧 Setup do Ambiente de Desenvolvimento

Os pré-requisitos e os primeiros passos para configurar o ambiente de desenvolvimento (Java Development Kit, Maven/Gradle, Node.js, PostgreSQL, Git) permanecem os mesmos, garantindo uma transição suave para os desenvolvedores.

---

## 🤝 Como Contribuir

O workflow de desenvolvimento via Issues, Pull Requests e Code Reviews será mantido, incentivando a colaboração e a qualidade do código.

---

## 📊 Métricas de Sucesso

As métricas de sucesso serão redefinidas para o contexto do Mind Palace, focando em:

*   **Engajamento da Comunidade:** Número de ideias postadas, comentários, interações.
*   **Retenção de Usuários:** Percentual de usuários que retornam à plataforma.
*   **Qualidade do Conteúdo:** Feedback positivo sobre a relevância e originalidade das ideias.
*   **Aprendizado da Equipe:** Desenvolvimento de novas habilidades e contribuição para o portfólio profissional.

---

## 🚀 Status Atual

**Fase Atual:** Milestone 0 - Planejamento e Visão do Mind Palace

**Progresso Geral:**
*   Planejamento da nova visão: [30%]
*   Modelagem de Dados (Mind Palace): [0%]
*   Backend (Mind Palace): [0%]
*   Frontend (Mind Palace): [0%]
*   Testes com Usuários: [0%]
*   Documentação: [0%]

---

## 📞 Contatos

*   **Coordenador do Projeto:** Marci Galvão
*   **Tech Lead:** @DevTroli
*   **Contato da Equipe:** [Adicionar contatos relevantes]

---

## 📝 Licença e Uso Futuro

[DECIDIR EM EQUIPE: Este projeto será open source? Permanecerá privado? Como será o licenciamento das ideias postadas?]
