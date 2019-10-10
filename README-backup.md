# Desafio 04 | Grupo Boticário

[![](https://img.shields.io/badge/IBM%20Cloud-powered-blue.svg)](https://cloud.ibm.com)
[![Platform](https://img.shields.io/badge/platform-nodejs-lightgrey.svg?style=flat)](https://developer.ibm.com/node/)

* [1. Introdução](#1-introdução)
* [2. Desafio](#2-desafio)
* [3. Pré-requisitos](#3-pré-requisitos)
* [6. Avaliação](#6-avaliação)
* [7. Aplicação na nuvem](#7-aplicação-na-nuvem)
    * [7.1. Veja como configurar o IBM Continuous Delivery](#7-1-veja-como-configurar-o-ibm-continuous-delivery)
    * [7.2. Credenciais do IBM Cloud Object Storage](#72-credenciais-do-ibm-cloud-object-storage)
    * [7.3. Configuração do IBM Continuous Delivery](#73-configuração-do-ibm-continuous-delivery)
* [8. Submissão](#8-submissão)
* [9. Dicas](#9-dicas)

## Para te ajudar

* [Material de Apoio](#material-de-apoio)
* [Troubleshooting](#troubleshooting)
* [Dúvidas](#dúvidas)
* [PDF do Desafio](#pdf-do-desafio)
* [License](#license)

## 1. Introdução

## 2. Desafio

## 3. Avaliação

## 4. Pré-requisitos

## 6. Treinamento do modelo

🚨 **É POSSÍVEL USAR A MESMA INSTÂNCIA DO WATSON STUDIO NESTE DESAFIO** 🚨

Veja o vídeo abaixo de como treinar o seu modelo de Machine Learning, usando Watson Studio.

<div align="center">
    <a href="https://youtu.be/o_VP7-gbLSs">
        <img width="375" src="doc/source/images/Thumbnail.png">
    </a>
</div>

* Crie uma instância de [Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio), em `Dallas` e acesse a plataforma, clicando no botão "Get Started".
* Faça o treinamento, com o [dataset.csv](doc/source/dataset/dataset.csv), em um Modelo de Machine Learning, usando `Modeler Flow`, e espere até concluir o treinamento.

## 7. Usando IBM Cloud Functions

Acesse o [IBM Cloud Functions](https://cloud.ibm.com/openwhisk/actions) e crie uma nova `função` com `Node.js 10` (**pode ser qualquer nome sem espaço. Ex:** `grupo_boticario`). Copie o conteúdo do arquivo `action.js` que se encontra neste projeto ([link aqui](doc/source/action/action.js)). Cole o código dentro do espaço onde já existe um código (auto gerado pela plataforma), substituindo o código existente.

Clique em "Salvar". Substitua as credenciais do serviço de `Machine Learning` nas linhas `20`, `21` e `44` ([Veja mais abaixo](#usando-ibm-cloud-functions)). Acesse a aba `Endpoints`.

A linha `44` deve ser preenchida com o `Scoring End-point` apresentado no meio e final do [vídeo de treinamento do modelo](#6-treinamento-do-modelo).

<div align="center">
    <img width="750" src="doc/source/images/Cloud%20Config%2001.png">
</div>

Clique sobre o botão `API-KEY` para acessar a `API-KEY` do seu IBM Cloud Function (dúvidas sobre onde está as credenciais, assista novamente o [vídeo sobre treinamento](#6-treinamento-do-modelo)).

<div align="center">
    <img width="750" src="doc/source/images/Cloud%20Config%2002.png">
</div>

Clique sobre o ícone para copiar o `API-KEY` para a área de transferência.

<div align="center">
    <img width="750" src="doc/source/images/Watson%20Assistant%2002.png">
</div>

Crie uma instância do [Watson Assistant](https://cloud.ibm.com/catalog/services/watson-assistant), em `Dallas`, e acesse a ferramenta de treinamento, clicando no `Launch Watson Assistant`.

Importe a Skill do [Lojista virtual](doc/source/dataset/skill-Lojista-virtual.json) e coloque as credenciais da `Function` na aba `Dialog`, no nó `@Hobby`.

<div align="center">
    <img width="750" src="doc/source/images/Import%2001.png">
</div>

<div align="center">
    <img width="750" src="doc/source/images/Import%2002.png">
</div>

No Watson Assistant, após importar o [Skill de Lojista virtual](doc/source/dataset/skill-Lojista-virtual.json), acesse a aba `Dialog` para alterar as credenciais da `Function` dentro do nó `@Hobby`.

Clique na seta `>` para abrir o nó filho (*child node*). Vai clicando, seguindo a ordem abaixo, até chegar no nó `@Hobby` onde está pré-configurado a conexão com o IBM Cloud Functions.

`Bem-vindo` > `getViagem` > `getGenero` > `getBebida` > `getHobby` > `@Hobby`

Altere as linhas `6` e `25` do `JSON editor` dentro do nó do `@Hobby`.

<div align="center">
    <img width="375" src="doc/source/images/Cloud%20Functions%2001.png">
    <img width="375" src="doc/source/images/Cloud%20Functions%2002.png">
</div>

### 7.1. Credenciais do Machine Learning e Watson Assistant

🚨 **SALVE AS CREDENCIAIS. VOCÊ IRÁ PRECISAR PARA SUBIR A APLICAÇÃO** 🚨

Para pegar o `IAM_APIKEY` (ou, em alguns casos, `API Key` apenas), acesse o https://cloud.ibm.com/resources e veja na lista de `Service`, você encontrará todos os serviços provisionados na sua conta (incluindo o Watson Assistant, Discovery, Watso Studio e Visual Recognition, serviços dos desafios 1, 2 e 3 respectivamente).

<div align="center">
    <br>
    <h2><b>Lista de recursos na conta</b></h2>
    <img width="750" src="doc/source/images/Resource%2001.png">
</div>

<div align="center">
    <br>
    <br>
    <h2><b>Watson Assistant</b></h2>
    <h2><b>IAM_APIKEY na IBM Cloud</b></h2>
    <img width="750" src="doc/source/images/Watson%20Assistant%2001.png">
    <h2><b>WORKSPACE_ID dentro do Watson Assistant</b></h2>
    <img width="750" src="doc/source/images/Watson%20Assistant%20Skill%2001.png">
    <img width="750" src="doc/source/images/Watson%20Assistant%20Skill%2002.png">
</div>

<div align="center">
    <br>
    <br>
    <h2><b>Machine Learning</b></h2>
    <img width="750" src="doc/source/images/Watson%20Studio%2001.png">
</div>

## 9. Aplicação na nuvem

Para subir a aplicação na IBM Cloud, você deve `clicar no botão` abaixo para subir usando o IBM Continuous Delivery (também conhecido como Delivery Pipeline). **Você deve subir a sua aplicação em Dallas**.

🚨 **CLIQUE PARA SUBIR A APLICAÇÃO NA IBM CLOUD** 🚨

[![Deploy to IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https://github.com/maratonadev/desafio-4)

### 9.1. Veja como configurar o IBM Continuous Delivery

1. Configure o `Toolchain Name` com `<maratona-id>-desafio4-behindthecode`, substituindo o `<maratona-id>` pelo seu ID da Maratona (Ex: 100001). Se você não souber, verifique no seu e-mail, usado no registro da Maratona, para pegar o seu ID.

2. Configure o `App name` com a mesmo valor usado no item 1.

3. Crie uma chave (de uso interno). Basta clicar em "Create" e depois clique em "Create" novamente. Espere um instante até carregar todas os dados. Se demorar muito (mais de 5 minutos), recarregue a página e faça novamente o passo 1 e 2. **Na parte superior, você pode deixar em Washington DC ou Dallas. Já na parte inferior (abaixo do item 2), é mandatório configurar a Região de Dallas**. 

<div align="center">
    <img width="750" src="doc/source/images/Pipeline%2001.png">
</div>

### 9.2. Credenciais na aplicação

Clique em `Eclipse Orion Web IDE` para configurar a aplicação.

<div align="center">
    <img width="750" src="doc/source/images/Pipeline%2002.png">
</div>

Abaixo estão o passo-a-passo, **obrigatório**, para configurar a sua aplicação no Eclipse Orion Web IDE.

1. Abra o arquivo `.env` para colocar as credenciais do `Watson Assistant`, `Machine Learning` e da `Maratona` (lembre-se de que é o mesmo código usado para indicar novos participantes na Maratona). Preencha com os dados, após o `=` (símbolo de igual). Lembre-se: **As credenciais do `Watson Machine Learning` estão localizados nos pontos do [vídeo de treinamento do modelo](#6-treinamento-do-modelo)**.

```
# Credenciais para o Desafio 4
DESAFIO=4
MARATONA_ID=

# Watson Assistant
IAM_APIKEY=
WORKSPACE_ID=

# Watson Machine Learning
USERNAME=
PASSWORD=
INSTANCE_ID=
SCORING_ENDPOINT=
```

<div align="center">
    <img width="750" src="doc/source/images/Pipeline%2003.png">
</div>

2. Abra o arquivo `manifest.yml` e altere o `<maratona-id>` com o seu ID da Maratona, o mesmo usado acima. Lembre-se: é mandatório ter a URL com o formato do `name`, apresentado abaixo.

```
applications:
- name: <seu-id>-desafio4-behindthecode
  memory: 256M
  instances: 1
  buildpack: sdk-for-nodejs
```

<div align="center">
    <img width="750" src="doc/source/images/Pipeline%2004.png">
</div>

Clique em `Create new launch configuration` e crie a configuração para a sua aplicação (que está sendo criada em *background*). `Launch Config Name`, `Application Name` e `Host` devem ter o mesmo nome, com o formato `<maratona-id>-desafio4-behindthecode`, igual nos itens anteriores. Clique em `SAVE` para salvar as configurações.

<div align="center">
    <img width="750" src="doc/source/images/Pipeline%2005.png">
    <img width="750" src="doc/source/images/Pipeline%2006.png">
</div>

Clique em `PLAY` (primeiro botão na imagem). Espere até ficar `verde` (com o status: `running`). Depois, clique em `Open` (terceiro botão na imagem). Vai abrir a sua aplicação, com as configurações implementadas.

<div align="center">
    <img width="375" src="doc/source/images/Pipeline%2007.png">
    <img width="375" src="doc/source/images/Pipeline%2008.png">
</div>

## 10. Submissão

🚨 **TESTE BASTANTE O SEU MODELO DE TREINAMENTO** 🚨

Mande várias mensagens, com variações das opções disponíveis, para ver o resultado no chat. Faça quantos testes forem necessários e, se precisar, treine e re-treine o seu modelo para melhorar cada vez mais. Quando se sentir confortável, faça a submissão do seu desafio. Lembre-se: **NÃO é possível submeter mais de uma vez**. Fique atento!

Através da aplicação na IBM Cloud (`https://<maratona-id>-desafio4-behindthecode.mybluemix.net`), você irá clicar no botão **SUBMETER DESAFIO**, preencher com o seu CPF e enviar para a avaliação final.

<div align="center">
    <img width="750" src="doc/source/images/App%2001.png">
</div>

FIQUEM LIGADOS NO [SITE DA MARATONA](ibm.biz/maratona) PARA ACOMPANHAR O RANKING GERAL E O RANKING DO DESAFIO! FIQUE NA TORCIDA PARA ESTAR ENTRE OS MELHORES!

## Material de apoio

- [O que é a IBM Cloud e como subir a sua primeira aplicação na nuvem](https://medium.com/ibmdeveloperbr/o-que-%C3%A9-a-ibm-cloud-e-como-subir-a-sua-primeira-aplica%C3%A7%C3%A3o-na-nuvem-41bfd260a2b7?source=friends_link&sk=7944d2fe14aa940e9bade68ce0731ba0)
- [Making programmatic calls from a dialog node](https://cloud.ibm.com/docs/services/assistant?topic=assistant-dialog-actions)

## Troubleshooting

1. No `Logs` da aplicação, apresentou um erro (em vermelho). O que pode ser? 

    Resposta: **Veja se você colocou as credenciais da Maratona, Watson Assistant e Machine Learning no arquivo `.env` e se o arquivo `manifest.yml` está correto, conforme [descrito acima](#credenciais-na-aplicação). Veja se a sua aplicação está rodando na URL correta conforme [descrito acima](#submissão).**

## Dúvidas

Acesse o slack e mande a sua dúvida: [ibm.biz/convite-slack](https://ibm.biz/convite-slack).

## PDF do Desafio

> Baixe o PDF do desafio [aqui](doc/source/pdf/Storytelling.pdf).

## License

Copyright 2019 Maratona Behind the Code

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
