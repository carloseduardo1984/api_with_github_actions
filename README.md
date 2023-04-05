# API_com_GitHub_Actions 
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=%20CONCLUIDO&color=GREEN&style=for-the-badge)

Nossa api com with github actions__ 

![api](https://user-images.githubusercontent.com/33332202/174480260-f97d8667-463a-4041-862f-0fd2fadbfb95.jpg)

### O que são GitHub Actions?
As GitHub Actions (ações do GitHub) são os fluxos de trabalho, mais conhecidos na área de projetos de software como pipelines, que permitem o uso de um conjunto de ações ao serem identificados determinados eventos  no repositório. Um evento no repositório pode ser tão simples, por exemplo "quando um push é feito para o branch master" ou "Uma solicitação de pull é levantada no branch master". O GitHub Actions nos permite automatizar certas respostas a esses eventos usando fluxos de trabalho (workflows) automatizados chamados de GitHub Actions. Essas ações reagem a um ou vários eventos e executam determinadas tarefas, por exemplo. "Construir e executar os testes", "Implantar o código", "Mesclar o código de uma ramificação para outra".

Podemos construir nossa integração contínua (CI) e implantação (CD) de ponta a ponta para o código no repositório diretamente no GitHub.
Configurando o  GitHub Actions

### 1 - Adicionando uma AÇÃO
As ações do Github Actions são definidas em um arquivo no formato yaml (YAML é uma linguagem de serialização de dados legível por humanos. É comumente usada para arquivos de configuração e em aplicativos onde os dados estão sendo armazenados ou transmitidos) e estão localizadas na pasta do GitHub > .github/workflows
 
### 2 - Para começar crie o repositório com nossos arquivos exportados de Coleção e Ambiente, e logo após clique em Actions: 
 
### 3 - Na sequencia clique em fluxo simples, na opção configurar:
 
### 4- Criando o arquivo de Workflow (Fluxo de trabalho)
Começamos adicionando o gatilho (trigger) no qual nosso fluxo de trabalho GitHub Action será executado. Isso é feito no arquivo yaml, conforme mostrado abaixo. As linhas de código abaixo definem o nome do fluxo de trabalho e o que ele será executado quando ocorrer um evento de push no branch main/principal do repositório.
 
### 5 - Agora criamos o trabalho que realmente executará a coleção POSTMAN.
 
Agora começamos a definir as etapas individuais que serão executadas dentro do trabalho.
Instalando o Node e o Newman no arquivo de fluxo de trabalho - Wokflow GitHub Action 
O Postman pode ser executado dentro dos agentes CI/CD usando o utilitário de prompt de comando chamado newman. Para instalar o newman, primeiro precisamos instalar o node.js no runner. É feito como mostrado abaixo.
Observação: o newman-reporter-htmlextra instala um repórter personalizado que gerará relatórios visualmente atraentes para nós.
 
### 6- Diretório para resultados de teste
Como um processo personalizado em CI/CD, precisamos de um espaço de trabalho para fazer upload dos artefatos gerados durante a execução, esses artefatos podem ser os logs gerados pelo agente, logs personalizados escritos em etapas, resultados de testes etc. GitHub Actions fornece uma maneira de fazer upload os arquivos do trabalho para o espaço de trabalho. O truque é criar um diretório e enviar os resultados para ele. O diretório pode ser criado usando a etapa a seguir.
 

### 7- Configurando a execução da coleção Postman no Wokflow do GitHub Actions
Nossa próxima tarefa é executar os testes definidos na coleção do Postman. O arquivo de coleção do Postman (.json) está disponível no repositório conforme mostrado abaixo.  
A etapa SEGUINTE executa a coleção do Postman e cria o relatório html como resultado da execução do teste.
 
### 8 - Fazendo upload de artefatos (relatórios, coleções e ambientes)
Como última etapa, fazemos upload dos artefatos para o espaço de trabalho, isso pode ser feito usando o actions/upload-artifact@v2 conforme mostrado abaixo. Estamos carregando todo o conteúdo do diretório testResults que criamos anteriormente.
 

## O Teste em si
Quando um push é feito para o repositório main/principal, o fluxo de trabalho é acionado. A saída de cada compilação está disponível no painel Ações do repositório e podemos detalhar cada fluxo para ver por que ele falhou.
 
`Ao clicar na execução (Update postman-pull-request.yml) vemos os detalhes E LOGO ABAIXO PODEMOS VER O LINK DO RELATORIO EM FORMATO ZIP, CONTENTO O RELATORIO HTML DA EXECUÇÃO`
 

 

