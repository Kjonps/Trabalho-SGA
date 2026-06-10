# 🏋️ GymFlow 💪

> Sistema de Treinos Personalizados e Acompanhamento Físico

O **GymFlow** é uma plataforma web voltada para academias que desejam oferecer aos seus alunos um sistema completo de montagem e execução de treinos personalizados, com acompanhamento da evolução física ao longo do tempo.

---

## 🚧 Status do Projeto

![Versão](https://img.shields.io/badge/Versão-v1.0.0-blue)
![Java](https://img.shields.io/badge/Java-17-007ec6?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.3.5-007ec6?logo=springboot&logoColor=white)
![React](https://img.shields.io/badge/React-18.2.0-007ec6?logo=react&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-007ec6?logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Compose-007ec6?logo=docker&logoColor=white)
![Licença](https://img.shields.io/badge/Licença-MIT-green)

---

## 📚 Índice

- [Links Úteis](#-links-úteis)
- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Tecnologias Utilizadas](#️-tecnologias-utilizadas)
- [Arquitetura](#-arquitetura)
- [Instalação e Execução](#-instalação-e-execução)
- [Estrutura de Pastas](#-estrutura-de-pastas)
- [Documentações utilizadas](#-documentações-utilizadas)
- [Autores](#-autores)
- [Licença](#-licença)

---

## 🔗 Links Úteis

- 📖 **Documentação:** [Documentação de Projeto (PDF/DOCX)](./docs/GymFlow_Documentacao_Projeto.docx.pdf)
- 🗂️ **Diagramas PlantUML:** [Ver pasta /PlantUML](./PlantUML/)

---

## 📝 Sobre o Projeto

O **GymFlow** surgiu da necessidade de academias modernas oferecerem uma experiência digital integrada aos seus alunos. O sistema permite que alunos visualizem fichas de treino personalizadas, registrem a execução de cada sessão e acompanhem métricas de evolução física ao longo do tempo — tudo em uma única plataforma.

Do lado operacional, recepcionistas realizam cadastros e gerenciam planos de treino, enquanto administradores têm visibilidade gerencial completa. A arquitetura de microsserviços garante escalabilidade e independência entre os módulos do sistema.

---

## ✨ Funcionalidades Principais

- 🔐 **Autenticação Segura:** Login com JWT e controle de acesso por perfil (Aluno, Recepcionista, Administrador).
- 🏋️ **Fichas de Treino:** Criação e gerenciamento de fichas personalizadas com exercícios, séries, repetições e carga.
- ✅ **Registro de Sessões:** Alunos registram cada sessão de treino, anotando cargas e repetições realizadas.
- 📈 **Evolução Física:** Dashboard com histórico de medidas corporais, peso e comparativos por período.
- 👤 **Gestão de Alunos:** Cadastro completo com histórico de treinos e medidas.
- 📊 **Relatórios de Desempenho:** Geração de relatórios para acompanhamento de frequência e evolução.
- ⚙️ **Configuração de Exercícios:** Cadastro de exercícios com grupo muscular, equipamento e vídeo demonstrativo.
- 📨 **Notificações:** Envio de e-mails automáticos para novos cadastros e lembretes de treino.

---

## 🛠️ Tecnologias Utilizadas

### 💻 Front-end

- **Framework:** React 18.2.0
- **Linguagem:** TypeScript 5.x
- **Estilização:** Tailwind CSS 3.x
- **Gerenciamento de Estado:** Zustand
- **Build Tool:** Vite 5.x
- **Cliente HTTP:** Axios

### 🖥️ Back-end

- **Linguagem/Runtime:** Java 17 (JDK)
- **Framework:** Spring Boot 3.3.5
- **Microsserviços:** Spring Cloud Gateway, Spring Cloud Netflix Eureka
- **Banco de Dados:** PostgreSQL 16
- **ORM:** Hibernate / Spring Data JPA
- **Autenticação:** JWT (jjwt 0.11.5) + Spring Security

### ⚙️ Infraestrutura & DevOps

- **Containerização:** Docker, Docker Compose
- **Cloud:** AWS EC2 + AWS RDS + AWS SES
- **CI/CD:** GitHub Actions
- **Documentação de API:** Swagger / OpenAPI 3

---

## 🏗️ Arquitetura

O GymFlow adota **arquitetura de microsserviços**, com cada domínio de negócio implementado como um serviço Spring Boot independente, com banco de dados próprio (Database per Service). A comunicação é feita via HTTP REST, roteada por um **API Gateway (Spring Cloud Gateway)**.

**Microsserviços:**

| Serviço | Porta | Responsabilidade |
|---|---|---|
| Auth Service | 8081 | Autenticação e tokens JWT |
| Aluno Service | 8082 | Cadastro e perfil de alunos |
| Treino Service | 8083 | Fichas, exercícios e sessões |
| Evolução Service | 8084 | Medidas corporais e relatórios |
| Notificação Service | 8085 | E-mails e notificações |

Os diagramas de arquitetura, componentes, classes, sequência, comunicação e estados estão disponíveis na pasta [`/plantuml`](./plantuml/) em formato PlantUML (`.puml`).

---

## 🔧 Instalação e Execução

### Pré-requisitos

- **Java JDK 17** ou superior
- **Node.js** v18.x ou superior
- **Docker** e **Docker Compose**

### Variáveis de Ambiente

Crie um arquivo `.env` na raiz de cada serviço:

**Back-end (cada microsserviço):**

| Variável | Exemplo |
|---|---|
| `SERVER_PORT` | `8082` |
| `SPRING_DATASOURCE_URL` | `jdbc:postgresql://localhost:5432/gymflow_aluno` |
| `SPRING_DATASOURCE_USERNAME` | `postgres` |
| `SPRING_DATASOURCE_PASSWORD` | `senha123` |
| `JWT_SECRET` | `chave_super_secreta_base64` |

**Front-end:**

```
VITE_API_URL=http://localhost:8080/api
```

### Como Executar com Docker Compose

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/gymflow.git
cd gymflow

# Suba todos os serviços
docker-compose up --build -d

# Verifique os containers
docker ps
```

🚀 A aplicação estará disponível em **http://localhost:5173**

---

## 📂 Estrutura de Pastas

```
.
├── docker-compose.yml
├── README.md
├── /plantuml                        # 📐 Diagramas PlantUML (.puml)
├── /docs                            # 📚 Documentação de projeto
│
├── /frontend                        # 💻 React + TypeScript
│   ├── /src
│   │   ├── /components
│   │   ├── /pages
│   │   ├── /services
│   │   └── /hooks
│   └── package.json
│
├── /api-gateway                     # 🚪 Spring Cloud Gateway (:8080)
├── /auth-service                    # 🔐 Autenticação (:8081)
├── /aluno-service                   # 👤 Alunos (:8082)
├── /treino-service                  # 🏋️ Treinos (:8083)
├── /evolucao-service                # 📈 Evolução (:8084)
└── /notificacao-service             # 📨 Notificações (:8085)
```

Cada microsserviço segue a estrutura:
```
/src/main/java/br/com/gymflow/<servico>/
  ├── /controller
  ├── /service
  ├── /repository
  ├── /domain
  ├── /dto
  ├── /config
  └── /security
```

---

## 🔗 Documentações utilizadas

- 📖 [Documentação Oficial do Spring Boot](https://docs.spring.io/spring-boot/docs/current/reference/html/)
- 📖 [Spring Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/)
- 📖 [Documentação do React](https://react.dev/reference/react)
- 📖 [PlantUML Language Reference](https://plantuml.com/guide)
- 📖 [Docker Documentation](https://docs.docker.com/)
- 📖 [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

---

## 👥 Autores

| Nome | GitHub |
|---|---|
| Jonas | [@seu-usuario](https://github.com/seu-usuario) |

---

## 🙏 Agradecimentos

- [**Engenharia de Software PUC Minas**](https://www.instagram.com/engsoftwarepucminas/) — Pelo apoio institucional e fomento às boas práticas de engenharia.
- [**Prof. Dr. João Paulo Aramuni**](https://github.com/joaopauloaramuni) — Pelos ensinamentos sobre Arquitetura de Software e Padrões de Projeto.

---

## 📄 Licença

Este projeto é distribuído sob a **Licença MIT**.
