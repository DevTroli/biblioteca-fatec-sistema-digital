# 📚 Projeto de Sistema Digital para Biblioteca FATEC

> **Trabalho Semestral - Fevereiro a Junho de 2025**  
> **Objetivo:** Criar uma plataforma digital para melhorar a experiência dos usuários da biblioteca da FATEC

---

## 🎯 Visão Geral

Este projeto nasceu da oportunidade de resolver problemas reais da biblioteca da FATEC enquanto aprendemos tecnologias importantes para nossa formação acadêmica e carreira profissional. Estamos construindo uma plataforma web que tornará mais fácil e agradável para alunos, professores e funcionários descobrirem livros, acompanharem suas leituras e interagirem com a comunidade acadêmica em torno da literatura.

O projeto serve simultaneamente três propósitos. Primeiro, resolve necessidades concretas identificadas através de pesquisa com a biblioteca e seus usuários. Segundo, permite que demonstremos domínio de Java e PostgreSQL para os professores da banca, que são especialistas nessas tecnologias. Terceiro, nos dá experiência prática trabalhando em equipe em um projeto de software real do começo ao fim, incluindo levantamento de requisitos, modelagem, desenvolvimento, testes e apresentação.

---

## 📅 Cronograma do projeto

**Milestone 0: Planejamento e CLEAR Framework (2 semanas)**  
Nesta fase inicial, definimos a visão completa do projeto. Realizamos pesquisa com a biblioteca para entender necessidades reais, decidimos o nome final do projeto, definimos funcionalidades essenciais versus desejáveis, escolhemos a stack tecnológica, e estabelecemos processos de trabalho em equipe. O entregável é um documento de planejamento completo que serve como norte para todo o desenvolvimento.

**Milestone 1: Fundação Conceitual (2-3 semanas)**  
Aqui criamos todas as bases técnicas sem ainda escrever código funcional. Fazemos a modelagem completa do banco de dados em três níveis (conceitual no BrModelo, lógico no DBDesigner, físico em scripts SQL), definimos a arquitetura do sistema explicando como as camadas vão se comunicar, decidimos a estrutura de pastas de backend e frontend, e criamos os primeiros designs das telas no Figma alinhados com a identidade visual da FATEC.

**Milestone 2: Proof of Concept (3-4 semanas)**  
Neste marco, construímos uma versão mínima mas funcional para validar que nossas decisões técnicas estão corretas. Colocamos no ar um site simples de "Em Construção", criamos uma health check API que mostra o status do sistema, implementamos o banco de dados com as tabelas principais, desenvolvemos um fluxo completo de ponta a ponta (por exemplo, cadastro e login funcionando), e finalizamos os designs das telas principais no Figma. O objetivo não é ter todas as funcionalidades, mas provar que conseguimos integrar backend Java com banco PostgreSQL com frontend React.

**Milestone 3: MVP - Minimum Viable Product (4-5 semanas)**  
Aqui implementamos todas as funcionalidades classificadas como essenciais (Must Have). O produto se torna utilizável de verdade por usuários reais. Fazemos deploy em produção de forma estável, recrutamos vinte a trinta alunos da FATEC para testarem como usuários beta, coletamos feedback sistematicamente, e iteramos baseado no que aprendemos. Ao final desta fase, temos um produto que funciona e gera valor real para os usuários.

**Milestone 4: Documentação e Métricas (2-3 semanas)**  
Com o MVP validado, focamos em documentar tudo formalmente. Escrevemos a documentação completa em formato ABNT que será entregue aos professores, preparamos a apresentação de slides para a defesa, compilamos métricas de uso do período beta (quantos usuários, quais funcionalidades mais usadas, feedback recebido), organizamos depoimentos de usuários que demonstrem o valor gerado, e criamos materiais que comprovem impacto real na biblioteca.

**Milestone 5: Refinamento e Lançamento (1-2 semanas)**  
Na fase final, polimos o produto para a apresentação. Corrigimos bugs críticos identificados no beta, implementamos melhorias de segurança básicas para proteger contra ataques comuns, otimizamos performance onde necessário, ensaiamos a apresentação múltiplas vezes até todos estarem confortáveis, e garantimos que o sistema esteja absolutamente estável para funcionar perfeitamente no dia da defesa.

---

## 🛠️ Stack Tecnológica

### Backend
-------

### Frontend
-------

### Banco de Dados
-------

### Deploy e DevOps
-------

---

## 👥 Organização da Equipe

Com sete pessoas trabalhando simultaneamente, organização é crítica. Cada membro tem uma área de responsabilidade principal, mas todos contribuem para todas as partes do projeto para garantir aprendizado completo. A sugestão de papéis inclui Tech Lead que define arquitetura e resolve conflitos técnicos, Backend Lead que implementa a lógica de negócio em Java, Database Lead que modela e otimiza o PostgreSQL, Frontend Lead que traduz designs em código React, UI/UX Designer que cria a experiência visual no Figma, DevOps que cuida de deploy e configurações de ambiente, e Product Owner que faz pesquisa com usuários e mantém a documentação.

Usamos rituais ágeis adaptados para contexto acadêmico. Planejamentos semanais ou quinzenais onde decidimos o que cada pessoa fará, sincronizações rápidas para desbloquear quem está travado, reviews para demonstrar o que foi feito, e retrospectivas para melhorar continuamente nosso processo. Tudo gerenciado através do GitHub para manter histórico completo que será valioso na apresentação.

---

## 📚 Documentação do Projeto

Toda a documentação está organizada na pasta `/docs` do repositório. Cada milestone tem seu próprio documento que guia a equipe através das decisões e entregas necessárias.

---

## 🔧 Setup do Ambiente de Desenvolvimento

### Pré-requisitos

Antes de começar a trabalhar no projeto, cada membro da equipe precisa ter instalado em sua máquina Java Development Kit versão 17 ou superior, Maven ou Gradle para gerenciar dependências Java, Node.js versão 18 ou superior para rodar o frontend, PostgreSQL 14 ou superior (pode ser local ou via Docker), Git para controle de versão, e um editor de código como VS Code ou IntelliJ IDEA. Também é necessário ter conta no GitHub e ser adicionado como colaborador do repositório.

### Primeiros Passos

O primeiro passo é clonar o repositório usando git clone seguido da URL do projeto. Depois de clonar, navegue até a pasta do backend e execute o comando para instalar dependências (mvn install se usando Maven). Configure o arquivo application.properties com as credenciais do seu banco de dados PostgreSQL local. Execute as migrations para criar a estrutura do banco de dados. Inicie o servidor backend que por padrão rodará na porta 8080.

Em paralelo, em outra janela do terminal, navegue até a pasta do frontend e execute o comando para instalar dependências do Node (npm install). Configure o arquivo de ambiente apontando para o backend local. Inicie o servidor de desenvolvimento do frontend que rodará tipicamente na porta 3000 ou 5173. Acesse no navegador para ver a aplicação funcionando.

---

## 🤝 Como Contribuir

### Workflow de Desenvolvimento

Quando for implementar uma nova funcionalidade ou corrigir um bug, primeiro verifique se existe uma issue no GitHub para aquela tarefa. Se não existir, crie uma com descrição clara do que precisa ser feito, por que é importante, e critérios de como saberemos que está completo. Se alguém já criou a issue, você pode se auto-atribuir para indicar que está trabalhando nela.

Quando terminar, faça push da sua branch para o GitHub e abra um Pull Request. No PR, descreva o que foi feito, por que, e como testar. Adicione screenshots se for mudança visual. Marque revisores apropriados (Tech Lead, Backend Lead, ou Frontend Lead dependendo da área). Responda aos comentários do code review fazendo ajustes conforme necessário. Após aprovação, pode fazer merge em develop. A branch de feature será automaticamente deletada após o merge.

---

## 📊 Métricas de Sucesso

### Como Saberemos que Fomos Bem-sucedidos?

Definimos sucesso em três dimensões. Na dimensão acadêmica, buscamos nota mínima de oito vírgula cinco na apresentação final, demonstração clara de domínio de Java e PostgreSQL paraos professores, e feedback positivo sobre o processo de desenvolvimento documentado. Na dimensão de usuários reais, queremos pelo menos cinquenta alunos da FATEC usando ativamente durante o período beta, taxa de retenção de trinta por cento após sete dias (usuários que voltam uma semana depois), e feedback qualitativo positivo de setenta por cento dos usuários beta.

Na dimensão de aprendizado da equipe, medimos sucesso se cada membro conseguir explicar todas as partes do projeto (não apenas sua área), se publicarmos o projeto como portfolio profissional de código aberto, e se a experiência preparar a equipe para estágios e trabalhos na área de desenvolvimento de software.

---

## 🚀 Status Atual

**Fase Atual:** Milestone 0 

**Progresso Geral:**
- Planejamento: [30%]
- Modelagem de Dados: [0%]
- Backend: [0%]
- Frontend: [0%]
- Testes com Usuários: [0%]
- Documentação: [0%]

---

## 📞 Contatos

**Coordenador do Projeto:** Marci Galvão 
**Tech Lead:** @DevTroli 
**Contato da Biblioteca FATEC:** -----------  

---

## 📝 Licença e Uso Futuro

[DECIDIR EM EQUIPE: Este projeto será open source? Permanecerá privado? A biblioteca da FATEC terá direitos de uso?]
