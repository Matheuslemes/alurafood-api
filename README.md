# Projeto de Integração de Microsserviços com Java e Spring

## Descrição

Este projeto visa demonstrar a criação, integração e deploy de microsserviços utilizando Java e Spring. O projeto inclui as seguintes funcionalidades e tecnologias:

- Conexão com banco de dados
- Migrations
- Service Discovery e Registry
- Load Balancer
- Integração de Microsserviços
- Deploy de um microsserviço na nuvem com containers Docker
- Utilização de recursos AWS como CDK, ECS, ECR, Fargate e RDS

## Pré-requisitos

Antes de iniciar, certifique-se de ter os seguintes itens instalados:

- Java 11+
- Spring Boot
- Docker
- AWS CLI
- AWS CDK

## Configuração do Banco de Dados

O projeto utiliza o banco de dados PostgreSQL. Para configurar a conexão, ajuste as propriedades no arquivo application.properties:

properties

spring.datasource.url=jdbc:postgresql://localhost:5432/nome_do_banco
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect

Migrations

Para gerenciar as migrations do banco de dados, utilizamos o Flyway. As migrations estão localizadas no diretório src/main/resources/db/migration.

Service Discovery e Registry

Para o Service Discovery e Registry, utilizamos o Eureka. Certifique-se de incluir a dependência no pom.xml:

<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
</dependency>

Configure o Eureka no arquivo application.yml:

eureka:
  client:
    register-with-eureka: false
    fetch-registry: false
  server:
    enable-self-preservation: false

Load Balancer

Utilizamos o Spring Cloud LoadBalancer para balanceamento de carga. Adicione a seguinte dependência ao pom.xml:

<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-loadbalancer</artifactId>
</dependency>

Integração de Microsserviços

Os microsserviços comunicam-se entre si utilizando o RestTemplate ou Feign Client. Adicione a dependência do Feign no pom.xml:

<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
</dependency>

Deploy na Nuvem com Docker e AWS

Docker

Crie um arquivo Dockerfile para construir a imagem Docker do microsserviço:

FROM openjdk:11-jre-slim
VOLUME /tmp
COPY target/nome-do-jar.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]

AWS

CDK

Utilizamos o AWS CDK para definir a infraestrutura como código. Acesse o diretório infra e execute:

cdk deploy

ECS, ECR e Fargate

Implemente a infraestrutura ECS com Fargate e armazene as imagens no ECR. Certifique-se de ter configurado as permissões adequadas no AWS IAM.

RDS

Configure uma instância do RDS para o banco de dados PostgreSQL e ajuste as configurações de conexão no application.properties.

Contribuição

Para contribuir com o projeto, siga as etapas abaixo:

	1.	Fork o repositório
	2.	Crie uma nova branch (git checkout -b feature/nova-funcionalidade)
	3.	Faça commit das suas alterações (git commit -am 'Adiciona nova funcionalidade')
	4.	Faça push para a branch (git push origin feature/nova-funcionalidade)
	5.	Abra um Pull Request

Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo LICENSE para mais detalhes.

Contato

Para dúvidas e sugestões, entre em contato através do email: matheuslemesmsl@gmail.com
