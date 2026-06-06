# ATIVIDADE - CAIXA CINZA COM SUPABASE E POSTMAN

## Introdução

Este trabalho tem como finalidade a análise e validação de uma API de autenticação utilizando testes de caixa cinza. A API foi implementada no Supabase, uma plataforma Backend as a Service (BaaS) que fornece recursos como autenticação de usuários e gerenciamento de banco de dados.

Durante a atividade, foram realizados testes com o objetivo de compreender o comportamento da API em diferentes cenários, como login válido, credenciais incorretas e falhas de validação. Para execução dos testes, foi utilizada a ferramenta Postman, permitindo o envio de requisições HTTP e análise detalhada das respostas retornadas pelo servidor.

A proposta também envolve o entendimento do fluxo de autenticação baseado em tokens, além da verificação da consistência das respostas da API em situações de sucesso e erro.

## Objetivo da Atividade

Esta atividade tem como objetivo aplicar testes de caixa cinza em uma API de autenticação utilizando o Supabase como backend e o Postman para execução dos testes. Foram realizadas etapas de configuração, criação de requisições HTTP, execução de testes e registro dos resultados.

## Configuração do Supabase

O projeto foi criado na plataforma Supabase, que fornece backend como serviço (BaaS), incluindo autenticação e banco de dados.

### Como o projeto foi criado?
- Foi criada uma conta no Supabase
- Um novo projeto foi iniciado no painel principal
- Foi configurado um nome para o projeto e senha do banco
- O ambiente foi inicializado automaticamente pela plataforma

  <img width="1600" height="761" alt="image" src="https://github.com/user-attachments/assets/bec3c041-8e88-475d-af8e-49e94d75dd56" />

##

  <img width="1600" height="756" alt="image" src="https://github.com/user-attachments/assets/2f2d8be3-7354-453b-b5fc-1aa7fd0ec58d" />

### Tipo de autenticação utilizada
- Foi utilizada a autenticação por e-mail e senha (Email Auth), disponível no módulo de Authentication do Supabase.

### Criação do usuário
- Acessei a aba Authentication → Users
- Adicionei manualmente um usuário de teste
- Defini e-mail e senha para login

  <img width="1600" height="621" alt="image" src="https://github.com/user-attachments/assets/64ddad39-55da-46f7-8c33-4a1e536504b0" />




## Configuração do Postman

### Criação do Workspace

- Foi criado um Workspace no Postman para organizar todas as requisições relacionadas aos testes da API de autenticação.

<img width="1342" height="683" alt="image" src="https://github.com/user-attachments/assets/d877969b-9545-412a-9bc5-4e72f09e320f" />


### Criação do Environment

- Foi criado um Environment para armazenar variáveis utilizadas nos testes.

<img width="1519" height="826" alt="image" src="https://github.com/user-attachments/assets/9e87e460-cefa-498b-a9bc-adaa763f843e" />

- As variáveis foram criadas para facilitar a reutilização dos dados nas requisições, evitando repetição e reduzindo erros manuais.

<img width="1063" height="242" alt="image" src="https://github.com/user-attachments/assets/9481cd70-7454-4520-a0d8-0384ca2566d1" />


### Uso do Postman nos testes

O Postman foi utilizado para enviar requisições HTTP, validar respostas da API, verificar autenticação e analisar tokens retornados.


## Configuração das Requisições

Endpoint utilizado: /auth/v1/token?grant_type=password

### Método HTTP
- POST

### Headers utilizados

| Header        | Valor              |
| ------------- | ------------------ |
| api_key       |  {{api_key}}       |
| Content-Type  | application/json   |
| Authorization | Bearer  {{api_key}}|

### Body JSON utilizado

```json
{
  "email": "{{email}}",
  "password": "{{password}}"
}
```
<img width="977" height="586" alt="image" src="https://github.com/user-attachments/assets/d1123d62-b8c0-4682-88a1-86477a2c046b" />

<img width="1037" height="967" alt="image" src="https://github.com/user-attachments/assets/bff60fc1-d6bd-44fa-aeaf-56e8d5d24c93" />

### Objetivo da requisição
- Essa requisição tem como objetivo autenticar o usuário no Supabase e retornar um token de acesso válido para utilização em outras requisições protegidas.

## Execução dos Testes

### Cenários executados

| Cenário               | Resultado Esperado   | Resultado Obtido | Status |
| --------------------- | -------------------- | ---------------- | ------ |
| Login válido          | Status 200 + token   | Sucesso          | OK     |
| Senha incorreta       | Status 400           | Erro retornado   | OK     |
| Usuário inexistente   | Acesso negado        | Erro 400         | OK     |
| Campos vazios         | Erro de validação    | Erro 400         | OK     |
| Credenciais inválidas | Mensagem de erro     | Erro 400         | OK     |

#### Cenário 1 - ENTRADA DE DADOS:

```json
{
  "email": "{{email}}",
  "password": "{{password}}"
}
```

###### RESULTADO:
  
<img width="1087" height="920" alt="image" src="https://github.com/user-attachments/assets/78b069e0-4eda-4974-85b9-0e70a9cc0bac" />

#### Cenário 2 - ENTRADA DE DADOS:

```json
{
  "email": "{{email}}",
  "password": "{{teste_senha_incorreta}}"
}
```

###### RESULTADO:

<img width="1088" height="675" alt="image" src="https://github.com/user-attachments/assets/c94da6c8-cc71-4bef-b562-d4c9c232156d" />


#### Cenário 3 - ENTRADA DE DADOS:

```json
{
  "email": "duda@gmail.com",
  "password": "{{teste_senha_incorreta}}"
}
```

###### RESULTADO:

  <img width="1077" height="667" alt="image" src="https://github.com/user-attachments/assets/30c93275-948f-4fa3-a419-8c6a566a546a" />
  

#### Cenário 4 - ENTRADA DE DADOS:

```json
{
  "email": "",
  "password": ""
}
```

###### RESULTADO:

  <img width="1073" height="658" alt="image" src="https://github.com/user-attachments/assets/0d71b267-57b9-4ec2-8c4a-e7eb1135dc7f" />

#### Cenário 5 - ENTRADA DE DADOS:

```json
{
  "email": "{{E-mail}}",
  "password": "{{Password}}"
}
```

###### RESULTADO:

  <img width="1080" height="661" alt="image" src="https://github.com/user-attachments/assets/65c66391-6e84-4870-8f33-563c5f961865" />

- Os testes foram registrados em uma planilha estruturada contendo todos os cenários executados, entradas utilizadas e resultados obtidos.

## Registro dos teste 

### Como os testes foram registrados?
- Os testes foram registrados em uma planilha estruturada contendo todos os cenários executados, entradas utilizadas e resultados obtidos.

### Importância da documentação dos testes
- O registro dos testes é fundamental para garantir rastreabilidade, organização e análise de possíveis falhas no sistema.

### Falhas identificadas
- Mensagens de erro genéricas em alguns cenários e variação no formato das respostas dependendo da entrada.

<img width="1408" height="542" alt="image" src="https://github.com/user-attachments/assets/d3919b5f-4695-40b9-8539-53da30bb95ea" />

## Resultados Obtidos
Durante a execução dos testes de caixa cinza na API de autenticação do Supabase, foram observados os seguintes resultados:
- O login com credenciais válidas retornou status 200 (OK) e gerou corretamente o access token, permitindo autenticação com sucesso.
- Ao informar senha incorreta, a API retornou erro de autenticação com status 401, impedindo o acesso.
- Para usuário inexistente, a resposta retornou erro indicando que as credenciais são inválidas, também com status 401.
- Quando os campos foram enviados vazios, a API retornou erro de validação, informando que os dados são obrigatórios.
- Em casos de credenciais inválidas ou mal formatadas, a API retornou mensagens de erro apropriadas, sem geração de token.
De forma geral, a API se comportou conforme o esperado, bloqueando acessos inválidos e permitindo apenas autenticações válidas. O sistema apresentou respostas consistentes em todos os cenários testados.

## Conclusão
Os testes foram executados com sucesso, validando o funcionamento da autenticação da API do Supabase. A autenticação retornou corretamente para credenciais válidas, com geração de tokens, e os cenários negativos também foram tratados de forma adequada.
Um dos principais desafios foi a execução dos testes no Postman, pois eu tinha pouca familiaridade com a ferramenta. A configuração de requisições, headers e endpoints exigiu prática, mas essa experiência ajudou bastante no meu aprendizado.
Como ponto de melhoria, foram identificadas mensagens de erro pouco detalhadas em alguns casos, além da necessidade de melhor padronização dessas mensagens e inclusão de logs mais completos na API.
Por fim, os testes de caixa cinza se mostraram importantes por permitirem validar tanto o comportamento externo quanto aspectos internos da API, aumentando sua confiabilidade e segurança.

##

- Maria Eduarda Souza Santos | 240212 

