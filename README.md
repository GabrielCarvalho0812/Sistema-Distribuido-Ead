# 📚 Sistema Distribuído EAD

> Plataforma educacional baseada em microserviços — projeto em desenvolvimento.

O **Sistema Distribuído EAD** é uma aplicação educacional distribuída, baseada em **microservices**, com serviços independentes para cada domínio de negócio e infraestrutura para configuração, descoberta e roteamento.

O objetivo do projeto é aplicar conceitos reais de arquitetura distribuída, como escalabilidade, modularidade e comunicação entre serviços.

---

## 🔧 Microservices de Negócios

| Serviço         | Descrição                            | Repositório                                              |
|----------------|----------------------------------------|----------------------------------------------------------|
| User Service    | Gerenciamento de usuários             | [authuser-ead](https://github.com/GabrielCarvalho0812/Authuser-ead) |
| Course Service  | Gerenciamento de cursos               | [course-ead](https://github.com/GabrielCarvalho0812/Course-ead) |
| Notification    | Envio de notificações                 | [notification-ead](https://github.com/GabrielCarvalho0812/notification-ead) |
| Payment         | Processamento de pagamentos           | [payment-ead](https://github.com/GabrielCarvalho0812/payment-ead) |

---

## ⚙️ Microservices de Configuração

| Serviço          | Função                             | Repositório                                                |
|------------------|------------------------------------|------------------------------------------------------------|
| Config Server     | Central de configuração            | [config-server](https://github.com/GabrielCarvalho0812/Config-Server) |
| Discovery Server  | Registro e descoberta de serviços  | [service-registry-ead](https://github.com/GabrielCarvalho0812/Service-Registry-ead) |
| API Gateway       | Roteamento de requisições          | [api-gateway](https://github.com/GabrielCarvalho0812/api-gateway) |

---

## 🏗️ Estrutura do Projeto

sistema-distribuido-ead/

├── docker-compose.yml

├── config-server/

├── service-registry-ead/

├── api-gateway/

├── authuser-ead/

├── course-ead/

├── notification-ead/

├── payment-ead/

└── README.md



Cada microserviço é independente e pode ser versionado separadamente. O repositório principal funciona como **hub central**, facilitando o gerenciamento de todos os serviços.

---

## 🐳 Como Rodar o Projeto

O projeto utiliza **Docker** e **Docker Compose** para orquestrar todos os serviços e dependências (PostgreSQL, RabbitMQ).

### Pré-requisitos
- Docker >= 20.x
- Docker Compose >= 1.29
- Java 17 (para rodar localmente sem Docker, opcional)

### Passos

1. Clone o repositório principal com os submodules (ou sub-repositórios separados):
```bash
git clone --recurse-submodules https://github.com/GabrielCarvalho0812/sistema-distribuido-ead.git
cd sistema-distribuido-ead

    Build e start de todos os serviços:

docker-compose up --build

    Acessar serviços:

    Discovery Server (Eureka): http://localhost:8761

Config Server: http://localhost:8888

API Gateway: http://localhost:8085

User Service: http://localhost:8080

Course Service: http://localhost:8081

Notification Service: http://localhost:8082

Payment Service: http://localhost:8083

RabbitMQ Management: http://localhost:15672

    (user: guest, password: guest)

    Parar os serviços:

docker-compose down

🧩 Observações

    Cada microserviço possui Dockerfile próprio, seguindo a estratégia de build em duas etapas: build com Maven e runtime com OpenJDK.

    O banco de dados PostgreSQL é compartilhado para fins de desenvolvimento e testes, mas cada microserviço idealmente teria seu próprio schema ou banco.

    RabbitMQ é utilizado para comunicação assíncrona entre microserviços.

    Para alterações nos sub-repositórios, é necessário dar docker-compose build novamente para atualizar as imagens.

⚡ Comandos Úteis

# Build e start dos containers
docker-compose up --build

# Start sem rebuild
docker-compose up

# Parar todos os containers
docker-compose down

# Ver logs de um serviço específico
docker-compose logs -f user-service

ℹ️ Sobre o projeto

O Sistema Distribuído EAD simula uma plataforma de ensino online com funcionalidades separadas por domínio de negócio e serviços de infraestrutura.

Princípios aplicados:

    Separação de responsabilidades: cada serviço tem sua própria responsabilidade e banco de dados.

    Comunicação entre serviços: REST e mensageria via RabbitMQ.

    Escalabilidade e modularidade: cada serviço pode ser escalado individualmente.

    Infraestrutura baseada em Spring Cloud: Config Server, Eureka e API Gateway.

