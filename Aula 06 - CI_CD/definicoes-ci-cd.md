# Git CI/CD

# Link para Entrega
[Forms Entrega](https://forms.gle/tuMXiSgYnzQkySdw6)

### CI: 
Definição: Prática de automatizar a integração de código de vários desenvolvedores em um repositório compartilhado, com verificações frequentes para detectar erros rapidamente.

- Toda vez que um desenvolvedor faz um git push (ou abre um Pull Request), o GitHub Actions pode executar testes automatizados, verificar a qualidade do código e garantir que a alteração não quebre a build.

### CD: 
Definição: Automatização do processo de liberação do software em ambientes de teste, staging ou produção após a CI.

- Continuous Delivery (Entrega Contínua): O código é automaticamente empacotado e preparado para ser liberado (mas requer aprovação manual para ir para produção).

  - Exemplo: Após os testes, o GitHub gera um artefato pronto para deploy, mas um humano decide quando liberar.

- Continuous Deployment (Implantaçã Contínua): O código vai automaticamente para produção se passar na CI, sem intervenção humana.
  - Exemplo: Um site em React é atualizado automaticamente no GitHub Pages após um push na branch main.

# Exemplo de CI

Nesse exemplo será criado um Fluxo para que os testes unitários rodem ao dar push para a Main ou criar um novo PR.

.github/workflows/ci.yml
```
name: Java CI with Maven

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    
    - name: Set up JDK 17
      uses: actions/setup-java@v3
      with:
        java-version: '17'
        distribution: 'temurin'
        cache: 'maven'
    
    - name: Build with Maven
      run: mvn -B package --file pom.xml
      
    - name: Run Tests
      run: mvn test
```

## Explicação detalhada do ci.yml:

### Estrutura Básica:
```
name: Java CI with Maven
```

- name: Define o nome do workflow que aparecerá na aba "Actions" do GitHub.

### Gatilhos (Triggers)
```
on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]
```

- on: Define quando o workflow será executado.
  - push: Executa quando há push para o branch "main"
  - pull_request: Executa quando há uma pull request direcionada ao branch "main"

### Jobs

```
jobs:
  build:
    runs-on: ubuntu-latest
```

- jobs: Contém os trabalhos que serão executados.
  - build: Nome do job (poderia ser qualquer outro nome).
  - runs-on: Especifica o sistema operacional do runner (neste caso, a última versão do Ubuntu).

### Passos (Steps)
1. Checkout do Código

```
    - uses: actions/checkout@v3
```
- uses: Utiliza uma ação pré-definida do GitHub.
  - actions/checkout@v3: Faz o checkout do seu repositório para o runner, permitindo que o workflow acesse seu código.

2. Configuração do JDK

```
    - name: Set up JDK 17
      uses: actions/setup-java@v3
      with:
        java-version: '17'
        distribution: 'temurin'
        cache: 'maven'
``` 

- name: Nome descritivo do passo.
- uses: Utiliza a ação `setup-java` para configurar o JDK.
- with: Parâmetros para a ação:
  - java-version: '17' - Instala o JDK 17
  - distribution: 'temurin' - Usa a distribuição Eclipse Temurin (antiga AdoptOpenJDK)
  - cache: 'maven' - Habilita cache para dependências Maven, acelerando builds futuros

3. Build com Maven

```
    - name: Build with Maven
      run: mvn -B package --file pom.xml
```
- run: Comando a ser executado no terminal.
  - `mvn -B`: Executa Maven em modo batch (não interativo)
  - `package`: Fase do lifecycle do Maven que compila, testa e empacota o projeto
  - `--file pom.xml`: Especifica o arquivo POM (opcional se estiver na raiz)

4. Execução de Testes

```
    - name: Run Tests
      run: mvn test
```



- Executa os testes do projeto com o comando `mvn test`
- Este passo é separado para melhor visualização no log, embora o `package` já inclua os testes

# Materiais de Apoio:

- [GitHub Actions para Java](https://docs.github.com/pt/actions/automating-builds-and-tests/building-and-testing-java-with-maven)
- [Spring Boot Testing](https://spring.io/guides/gs/testing-web/)
