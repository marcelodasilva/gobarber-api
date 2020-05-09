# GoBarber

Backend do app para agendamento de serviços de barbearia

## Estrutura do projeto

* [src]
  - [@types] Pasta contendo as definições de tipo
  - [config] Pasta contendo as configurações gerais do projeto
  - [modules] Pasta contendo os domínios do projeto
    - [users] Pasta contendo as informações relacionadas ao domínio de usuário
      - [dtos] Pasta contendo os objetos usados na transferência de dados
      - [infra] Pasta contendo as implementações da camada de infra
        - [http] Pasta contendo as implementações que se referem a camada http
          - [controllers] Pasta contendo os arquivos de controle
          - [middlewares] Pasta contendo os middlewares
          - [routes] Pasta contendo as rotas
        - [typeorm] Pasta contendo as implementações ligadas ao typeorm
          - [entities] Pasta contendo as entidades do typeorm
          - [repositories] Pasta contendo os arquivos de implementação dos métodos para acesso ao banco
      - [providers] Pasta contendo os provedores de serviço que são dependências externas do domínio de usuário
        - [HashProvider] Pasta contendo os provedores do serviço de hash de senha
          - [fakes] Pasta contendo o mock das implementações dos provedores
          - [implementations] Pasta contendo as implementaçes dos provedores
          - [models] Pasta contendo a interface em comum entre os provedores
        - index.ts Arquivo que faz a injeção das dependências dos provedores
        - [routes] Pasta contendo as rotas
      - [repositories] Pasta contendo as interfaces dos métodos para acesso ao banco
        - [fakes] Pasta contendo o mock da implementação do repositório
      - [services] Pasta contendo as regras de negócio relacionadas ao domínio de usuário
        - [__tests__] Pasta contendo os testes unitários dos arquivos de serviço
  - [shared] Pasta contendo os arquivos que serão compartilhados entre os domínios do projeto
    - [container] Pasta contendo a implementação de injeção de dependências
      - [providers]
        - [StorageProvider]
          - [fakes]
          - [implementations]
          - [models]
        - index.ts Arquivo que faz a injeção das dependências dos provedores
      - index.ts Arquivo que faz a injeção das dependências de todo o projeto
    - [errors] Pasta contendo os arquivos de erro
    - [infra]
      - [http]
        - [routes] Pasta contendo as configurações de todas as rotas do projeto
        - server.ts Arquivo base onde estão as configuraçes gerais do projeto
      - [typeorm]
        - [migrations] Pasta contendo os arquivos de versionamento do typeorm
        - index.ts Arquivo de conexão do typeorm
  
## Inicialização

Criar banco de dados postgres:
```
docker run --name gobarber -e POSTGRES_PASSWORD=suasenha -p 5432:5432 -d postgres
```
Iniciar banco postgres:
```
docker start gobarber
```
Migrar tabelas para postgres:
```
yarn typeorm migration:run
```
Instalar dependências:
```
yarn
```
Rodar projeto:
```
yarn dev:server
```
