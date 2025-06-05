# Multi-Tenant: Como Funciona e Formas de Implementar

## O que é Multi-Tenant?

**Multi-tenant** é uma arquitetura onde uma única aplicação serve múltiplos clientes (**tenants**), mantendo os dados de cada um isolados. Isso permite:

- Compartilhamento de infraestrutura
- Redução de custos
- Isolamento lógico dos dados

---

## Formas de Implementar Multi-Tenant no Banco de Dados

### 1. Separar por Banco de Dados

Cada tenant possui seu próprio banco.

**Vantagens:**
- Isolamento completo entre os dados
- Backup/restauração individual
- Alta segurança

**Desvantagens:**
- Alta complexidade de manutenção
- Requer mais recursos do servidor
- Escalabilidade mais difícil

---

### 2. Separar por Schema

Um único banco, com schemas diferentes para cada tenant.

**Vantagens:**
- Isolamento lógico dos dados
- Gestão centralizada
- Mais simples que múltiplos bancos

**Desvantagens:**
- Alguns bancos limitam número de schemas
- Gestão de permissões pode ser complexa

---

### 3. Separar por Coluna (Discriminação)

Todas as tabelas compartilham os dados, diferenciando-os por uma coluna `tenant_id`.

**Vantagens:**
- Fácil de implementar
- Escalável com muitos tenants pequenos
- Menor sobrecarga de conexão

**Desvantagens:**
- Risco de acesso indevido se não for bem controlado
- Backups por cliente são mais difíceis
- Tabelas muito grandes podem impactar a performance

---

## Como o Sistema Identifica o Tenant?

A aplicação precisa saber **qual cliente (tenant)** está fazendo a requisição. Isso pode ser feito de várias formas:

### Formas de identificação:

- **Via URL:**  
  Ex: `https://tenant1.testapp.com`
  
- **Via Header:**  
  Ex: `X-Tenant-ID: tenant1`
  
- **Via Token (JWT):**  
  O `tenantId` é incluído no token de autenticação

> **Importante:** É necessário validar se o usuário tem permissão de acessar o tenant informado.

---

## Segurança e Validação de Acesso

- O `tenantId` é incluído no **token JWT** no momento do login.
- Em **todas as requisições**, o backend (ex: **Spring**) valida o token e confere se o usuário pode acessar aquele tenant.
- Isso impede que alguém acesse dados de outro tenant mesmo que saiba o `tenantId`.

---

## Recomendação: Schema por Cliente

Uma abordagem equilibrada é usar **um schema por cliente**:

- Crie schemas como `tenant_1`, `tenant_2`, etc.
- A aplicação identifica o tenant na requisição e conecta no schema correto.
- No **Spring**, isso pode ser feito com:
  - `AbstractRoutingDataSource`
  - Hibernate Multi-Tenancy (com a estratégia SCHEMA)
