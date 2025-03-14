# Hospedagem

Definição: processo de disponibilizar uma aplicação ou sistema em um ambiente de produção, onde ele pode ser acessado pelos usuários finais. Esse processo envolve várias etapas, desde a preparação do código até a configuração do ambiente de hospedagem.

## Tipos de Hospedagem

1. Hospedagem Compartilhada: Vários sites ou aplicações compartilham os mesmos recursos de um servidor.
2. Servidores Virtuais Privados (VPS): Um servidor físico é dividido em vários servidores virtuais, cada um com seus próprios recursos.
3. Hospedagem em Nuvem: Recursos de computação são fornecidos sob demanda, permitindo escalabilidade e flexibilidade.
4. Servidores Dedicados: Um servidor físico inteiro é dedicado a uma única aplicação ou site.

Os métodos mais utilizados para Hospedagem para projetos em fase inicial são Hospedagens em Nuvem. Abaixo vão ser detalhados (resumidamente) as plataformas AWS e RailWay.

Lembrando que esse detalhamento é mais teórico do que prático, para subir esses ambientes a documentação das ferramentas DEVEM ser utilizadas.

## AWS

A Amazon Web Services (AWS) é uma das plataformas de computação em nuvem mais populares e oferece uma infraestrutura robusta e flexível para hospedagem de software. O fluxo de hospedagem na AWS envolve várias etapas e serviços que podem ser combinados para atender às necessidades específicas de uma aplicação.

### 1. Planejamento e Configuração Inicial
Antes de hospedar uma aplicação na AWS, é necessário planejar a infraestrutura e configurar os serviços básicos:

- Criação de uma Conta AWS: O primeiro passo é criar uma conta na AWS, que dará acesso a todos os serviços disponíveis.
- IAM (Identity and Access Management): Configurar usuários, grupos e permissões para garantir que apenas pessoas autorizadas possam acessar e gerenciar os recursos da AWS.
- VPC (Virtual Private Cloud): Criar uma VPC para isolar a infraestrutura da aplicação em uma rede virtual privada. Isso inclui a configuração de sub-redes, gateways de internet, e tabelas de rotas.

### 2. Armazenamento e Banco de Dados
A AWS oferece vários serviços para armazenamento e banco de dados:

- Amazon S3 (Simple Storage Service): Para armazenar arquivos estáticos, como imagens, vídeos, e documentos.
- Amazon RDS (Relational Database Service): Para gerenciar bancos de dados relacionais como MySQL, PostgreSQL, Oracle, e SQL Server.
- Amazon DynamoDB: Um banco de dados NoSQL para aplicações que precisam de baixa latência e escalabilidade.

### 3. Computação
A AWS oferece várias opções para execução de código e hospedagem de aplicações:

- Amazon EC2 (Elastic Compute Cloud): Servidores virtuais escaláveis que podem ser configurados para rodar aplicações.
- AWS Lambda: Execução de código sem a necessidade de gerenciar servidores, ideal para funções serverless.
- Elastic Beanstalk: Um serviço que facilita o deploy e o gerenciamento de aplicações, automatizando a configuração de servidores, balanceamento de carga, e escalabilidade.

### 4. Deploy da Aplicação
O deploy de uma aplicação na AWS pode ser feito de várias maneiras, dependendo da complexidade e dos requisitos da aplicação:

- Deploy Manual: Transferir manualmente os arquivos da aplicação para uma instância EC2 via SSH ou FTP.
- Deploy Automatizado: Utilizar serviços como AWS CodeDeploy, que automatiza o processo de deploy para instâncias EC2, Lambda, ou Elastic Beanstalk.
- Contêineres: Utilizar Amazon ECS (Elastic Container Service) ou EKS (Elastic Kubernetes Service) para deploy de aplicações em contêineres Docker.

### 5. Balanceamento de Carga e Escalabilidade
Para garantir alta disponibilidade e desempenho, a AWS oferece serviços de balanceamento de carga e escalabilidade:

- Elastic Load Balancing (ELB): Distribui o tráfego de entrada entre várias instâncias EC2 para garantir que nenhuma instância fique sobrecarregada.
- Auto Scaling: Ajusta automaticamente o número de instâncias EC2 com base na demanda, garantindo que a aplicação possa lidar com picos de tráfego.

### 6. Monitoramento e Gerenciamento
Após o deploy, é crucial monitorar e gerenciar a aplicação para garantir que ela esteja funcionando corretamente:

- Amazon CloudWatch: Monitora métricas e logs, permitindo a identificação e resolução rápida de problemas.
- AWS CloudTrail: Registra todas as chamadas de API feitas na conta AWS, fornecendo um histórico de atividades para auditoria e segurança.

### 7. Segurança
A segurança é uma prioridade na AWS, e vários serviços são oferecidos para proteger a aplicação e os dados:

- AWS IAM: Gerenciamento de acesso e permissões.
- AWS WAF (Web Application Firewall): Protege aplicações web contra ataques comuns.
- Amazon Inspector: Avalia automaticamente a segurança das instâncias EC2.
- AWS Shield: Proteção contra ataques DDoS.

### 8. Backup e Recuperação
Para garantir a continuidade dos negócios, a AWS oferece serviços de backup e recuperação:

- Amazon S3: Armazenamento durável para backups.
- AWS Backup: Serviço centralizado para gerenciar backups de vários serviços AWS.
- Amazon Glacier: Armazenamento de baixo custo para backups de longo prazo.

### 9. Otimização de Custos
A AWS oferece várias ferramentas para ajudar a gerenciar e otimizar os custos:

- AWS Cost Explorer: Analisa e prevê custos.
- AWS Budgets: Define orçamentos e alertas para controlar gastos.
- Reserved Instances: Descontos para compromissos de uso de longo prazo.

## RailWay

O Railway é uma plataforma de hospedagem e deploy que simplifica o processo de implantação de aplicações, especialmente para desenvolvedores que desejam focar no código sem se preocupar tanto com a infraestrutura subjacente. Ele é conhecido por sua facilidade de uso, integração com ferramentas modernas de desenvolvimento e suporte a várias linguagens e frameworks. 

### 1. Preparação do Projeto
Antes de hospedar uma aplicação no Railway, é necessário preparar o projeto para ser implantado. Isso inclui:

- Código-fonte: Ter o código da aplicação pronto em um repositório Git (como GitHub, GitLab ou Bitbucket).
- Dependências: Garantir que todas as dependências do projeto estejam definidas (por exemplo, package.json para Node.js, requirements.txt para Python, etc.).
- Configurações de Ambiente: Definir variáveis de ambiente necessárias para a aplicação funcionar corretamente (como chaves de API, credenciais de banco de dados, etc.).

### 2. Criação de um Projeto no Railway
O próximo passo é criar um projeto no Railway:

- Login/Cadastro: Acessar o Railway (https://railway.app) e criar uma conta ou fazer login.
- Novo Projeto: Clicar em "New Project" para iniciar um novo projeto.
- Escolha do Método de Deploy:
    - Importar de um Repositório Git: Conectar o Railway ao repositório Git onde o código está hospedado.
    - Upload Manual: Fazer upload do código diretamente (menos comum).
    - Template Pronto: Usar um template pré-configurado para frameworks populares (como Next.js, Django, Flask, etc.).

### 3. Configuração do Ambiente
Após criar o projeto, o Railway permite configurar o ambiente de hospedagem:

- Variáveis de Ambiente: Adicionar variáveis de ambiente necessárias para a aplicação (por exemplo, DATABASE_URL, API_KEY, etc.). Isso pode ser feito manualmente ou importando um arquivo .env.
- Plugins e Add-ons: Adicionar serviços complementares, como bancos de dados (PostgreSQL, MySQL, MongoDB), filas (Redis), ou armazenamento (S3-like).

### 4. Deploy Automático
O Railway é conhecido por sua integração contínua e deploy automático:

- Integração com Git: Quando o repositório Git é conectado, o Railway monitora as alterações no branch selecionado (geralmente main ou master). Cada push para o repositório dispara um novo deploy automaticamente.
- Build e Execução: O Railway detecta a linguagem e o framework do projeto e executa os comandos necessários para buildar e rodar a aplicação (por exemplo, npm install e npm start para Node.js).
- Logs em Tempo Real: Durante o deploy, é possível acompanhar os logs em tempo real para verificar se tudo está funcionando corretamente.

### 5. Escalabilidade e Gerenciamento
O Railway gerencia automaticamente a infraestrutura necessária para rodar a aplicação:

- Escalabilidade Automática: O Railway escala a aplicação com base na demanda, sem necessidade de intervenção manual.
- Domínio Personalizado: É possível configurar um domínio personalizado para a aplicação diretamente no painel do Railway.
- Rollback Automático: Se algo der errado durante o deploy, o Railway faz rollback automaticamente para a versão anterior estável.

### 6. Monitoramento e Métricas
O Railway oferece ferramentas básicas para monitorar o desempenho da aplicação:

- Logs: Acesso aos logs da aplicação em tempo real.
- Métricas: Visualização de métricas como uso de CPU, memória e tráfego.
- Health Checks: Verificação automática do status da aplicação.

### 7. Integração com Outros Serviços
O Railway se integra facilmente com outros serviços populares:

- Banco de Dados: Oferece plugins para bancos de dados como PostgreSQL, MySQL, MongoDB e Redis.
- Armazenamento: Integração com serviços de armazenamento como AWS S3 ou similares.
- CI/CD: Pode ser integrado com ferramentas de CI/CD como GitHub Actions para pipelines mais complexos.

### 8. Custos e Planos
O Railway oferece um plano gratuito com limites generosos, ideal para projetos pequenos ou testes. Para projetos maiores, há planos pagos que oferecem mais recursos, como maior capacidade de processamento, armazenamento e suporte prioritário.
