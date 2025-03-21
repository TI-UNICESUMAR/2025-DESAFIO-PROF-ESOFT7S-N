# Git Básico

## Sumário
1. Conceitos básicos e Fluxo
2. Comandos Úteis
3. Conflitos

## 1. Conceitos Básicos e Fluxo

### 1.1. Conceitos Básicos de Git

Definição de Git: Sistema de controle de versão distribuído amplamente utilizado para rastrear mudanças em arquivos e coordenar o trabalho entre várias pessoas. Ele é essencial para o desenvolvimento de software, mas também pode ser usado em outros contextos onde o controle de versão é necessário.

- Repository: Um repositório Git é um local onde todos os arquivos de um projeto são armazenados, junto com o histórico de alterações desses arquivos;
- Commit: Um commit é um ponto na história do seu projeto onde você salva o estado atual dos arquivos. Cada commit tem um identificador único (hash) e uma mensagem que descreve as mudanças feitas;
- Staged (Área de Preparação): A área de staged é um local temporário onde você coloca as mudanças que deseja incluir no próximo commit;
- Working Directory (Diretório de Trabalho): O diretório de trabalho é a pasta onde você está editando os arquivos do seu projeto. Ele reflete o estado atual dos arquivos, incluindo todas as mudanças que ainda não foram commitadas;
- Branch (Ramificação): Um branch é uma linha de desenvolvimento separada que permite que você trabalhe em novas funcionalidades ou correções sem afetar a linha principal (geralmente chamada de main ou master);
- Merge (Mesclagem): Merge é o processo de combinar as mudanças de dois branches diferentes. Isso é comum quando você termina de trabalhar em uma funcionalidade em um branch e deseja integrar essas mudanças ao branch principal;
- Remote (Repositório Remoto): Um repositório remoto é uma versão do seu projeto que está hospedada em um servidor, como GitHub, GitLab ou Bitbucket. Ele permite que várias pessoas colaborem no mesmo projeto;
- Pull: O comando pull é usado para trazer as mudanças mais recentes do repositório remoto para o seu repositório local;
- Push: O comando push é usado para enviar as mudanças do seu repositório local para o repositório remoto;
- Clone: Clonar um repositório significa criar uma cópia completa de um repositório remoto no seu computador local;
- Fork: Um fork é uma cópia de um repositório que pertence a outra pessoa, permitindo que você faça alterações sem afetar o projeto original;
- Tag: Uma tag no Git é uma referência estática a um ponto específico na história do seu projeto. Geralmente, as tags são usadas para marcar versões específicas do seu software, como lançamentos (releases), por exemplo, "v1.0.0" ou "v2.3.1";

### 1.2. Git Flow (Fluxo)
Modelo de Organização ou estratégia de trabalho para auxiliar no versionamento de códigos. Facilitando assim o desenvolvimento de novas funcionalidades, correções de Bugs e versionamentos.

O Git Flow trabalha com 5 tipos de Branchs: Master/Main, Fix/Hotfix, Develop, Feature. Cada qual com sua função e suas regras de uso.
- Master/Main: Branch principal, contém o código em sua totalidade da aplicação. Não é aberta para interação direta, a adição de novos arquivos ou alterações nessa branch, serão feitos por meio das branchs de Fix/Hotfix e Releases
- Develop: Branch que está em desenvolvimento durante a sprint ou até o Deploy. Nessa branch ficarão as funcionalidades que ainda não foram jogadas para a Master/Main.
- Feature: Branchs de desenvolvimento. Devem seguir um padrão de Desenvolvimento, em âmbito de Escola de TI, seguindo o exemplo de código dos cards, elas começariam com o prefixo ETI-001-nome-branch. Essas branchs são criadas com base na branch Develop e somente com a Develop, as branchs de Feature não devem ter uma interação direta com a Main/Master.
- Fix/Hotfix: Branchs destinadas a correção de BUGS urgentes, ou correções imediatas. A Fix/Hotfix é criada com base na Main/Master, após finalização é realizado o Merge na Main/Master e na Develop. Quando uma Fix/Hotfix é mergeada na Main/Master, é necessário criar uma Tag, cada alteração na Main/Master deve ter uma Tag correspondente.
- Release: Após finalizado o período proposto de Desenvolvimento, será criada uma branch Release com base na Develop para mergear essas alterações na Main/Master. A Homologação costuma ser feita em branchs de Release. Após validação essa branch vai ser mergeada na Main/Master e uma Tag será criada para sinalizar essa movimentação.

![image](https://github.com/user-attachments/assets/891857df-5ecf-4941-9a35-f4459ecfb3f5)

[Artigo de Apoio - Alura](https://www.alura.com.br/artigos/git-flow-o-que-e-como-quando-utilizar)

## 2. Comandos Úteis

### 2.1. STATUS:
- Função: Demonstrar o estado atual do Repositório/Branch. Demonstra arquivos modificados, Staged, etc.
- Comando Bash:
```
git status
```

### 2.2. ADD:
- Função: Adicionar um arquivo especifico ao Staging Area. Podendo ser usado para adicionar todos os arquivos também.
- Comando Bash:
```
git add <nome_arquivo>

git add .
```

### 2.3. COMMIT:
- Função: Cria um Commit com as alterações que estão em Staging Area. SEMPRE realizar o commit com uma Mensagem descritiva.
- Comando Bash:
```
git commit -m "Mensagem Descritiva"
```

### 2.4. PUSH
- Função: Envia os commits locais para o repositório remoto.
- Comando Bash: 
```
git push
```

### 2.5. PULL
- Função: Atualiza o repositório local com as alterações do repositório remoto.
- Comando Bash:
```
git pull origin <nome_branch_remota>
```

### 2.6. CLONE
- Função: Clona um repositório remoto para o seu ambiente local.
- Comando Bash:
```
git clone <URL_DO_REPOSITÓRIO>
```

### 2.7. LOG
- Função: Mostra o histórico de commits.
- Comando Bash:
```
git log
```

### 2.8. DIFF
- Função: Mostra as diferenças entre o working directory e o staging area.
- Comando Bash:
```
git diff
```

### 2.9. MERGE
- Função: Combina as alterações de uma branch com a branch atual.
- Comando Bash:
```
git merge <nome_da_branch>
```

### 2.10. REBASE
- Função: Reaplica os commits da branch atual em cima de outra branch.
- Comando Bash:
```
git rebase <nome_da_branch>
```
