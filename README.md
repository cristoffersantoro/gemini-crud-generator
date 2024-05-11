
# Gemini CRUD GENERATOR

Este projeto tem por finalidade gerar telas de aplicações com base em um projeto de sua escolha, por meio de Inteligência Generativa, que vai estudar toda a arquitetura do projeto e com isso, dado os inputs que deseja, no caso os atributos da tela, a IA vai gerar uma tela do zero, com todas as operações de cadastro, edição e atualização. Neste projeto você terá a chance de explorar como conectar e varrer dados com Python, e como manter suas credenciais seguras no Google Drive, o que torna esse projeto uma ótima fonte de aprendizado para quem está iniciando. Vale a pena conferir..


## Características

- Leitura de arquivos de repositório GITHUB
- Armazenamento de arquivos e histórico de chat no banco de dados Firebase
- Treinamento de modelo
- Geração de telas baseadas em modelo
- Conexão com o Google Drive


## Como obter a Google API Key

1. Acesse o Google Cloud Console: [Google Cloud Console](https://console.cloud.google.com/)
2. Se necessário, crie um novo projeto clicando em "Criar Projeto".
3. No menu de navegação, vá para "APIs e Serviços" e selecione "Credenciais".
4. Clique em "+ Criar Credenciais" e selecione "Chave de API".
5. Sua nova chave de API será criada e exibida. Copie e guarde em um local seguro.

## Como Obter um GitHub Token

 Um GitHub Token é uma forma de autenticar-se na API do GitHub sem precisar usar sua senha pessoal. Ele oferece um controle mais granular de permissões e pode ser revogado a qualquer momento. Siga os passos abaixo para gerar um token:

1. Acesse as Configurações:

    - Faça login na sua conta do GitHub.
    - Clique na sua foto de perfil no canto superior direito e selecione "Settings" (Configurações).
2. Vá para Developer Settings:

    - No menu lateral esquerdo, clique em "Developer settings" (Configurações do desenvolvedor).
3. Gere um novo token:

    - Selecione a opção "Personal access tokens" (Tokens de acesso pessoal) no menu lateral.
    - Clique em "Generate new token" (Gerar novo token).
    - Escolha um nome descritivo para o token (por exemplo, "Colab Token").
    - Defina uma data de expiração para o token (opcional).
    - Selecione os escopos (permissões) que você precisa para o token. Para a maioria dos casos, o escopo "repo" (repositório) é suficiente para ler e escrever em repositórios.
4. Clique em "Generate token" (Gerar token):

    - O GitHub irá exibir o token gerado. Copie-o imediatamente, pois ele será mostrado apenas uma vez.
5. Armazene o token em um local seguro:

    - Salve o token em um local seguro, como um gerenciador de senhas. Nunca compartilhe seu token publicamente.
 Observações:

- Escolhendo os escopos: Seja cuidadoso ao selecionar os escopos do seu token. Conceda apenas as permissões necessárias para evitar o risco de acesso não autorizado à sua conta.
- Revogando tokens: Se você não precisar mais de um token, revogue-o nas configurações do desenvolvedor do GitHub.
- Tokens de aplicativo do GitHub: Para fins de automação e integração, considere usar GitHub Apps em vez de tokens de acesso pessoal, pois eles oferecem mais segurança e controle.
 Com o seu GitHub Token em mãos, você poderá usá-lo para autenticar suas requisições à API do GitHub em seus projetos e scripts.

## Adicionar a Google API Key e o GITHUB Token no aplicativo

1. Preencha os valores dos campos abaixo entre "aspas" com as chaves correspondentes. 

```json
{
    "generative-api-key": "",
    "github-token": ""
}
```
2. Carregue o Arquivo JSON no Colab:

    - No Colab, clique no ícone de pasta à esquerda para abrir o painel lateral.
    - Clique nos três pontos ao lado de "drive" e selecione "Montar Drive".
    - Faça o upload do arquivo JSON de credenciais para o seu Drive.
    - Faça o upload do arquivo tokens.json para sua pasta MyDrive

## Passo a Passo para Criar um Banco de Dados no Firebase (Firestore)

1. Crie um projeto Firebase: 
- Acesse o console do Firebase: https://console.firebase.google.com/
- Clique em "Adicionar projeto".
- Dê um nome ao seu projeto e clique em "Continuar".
- (Opcional) Habilite o Google Analytics para seu projeto e clique em "Criar projeto".
2. Acesse o Firestore: 
- No menu lateral esquerdo, clique em "Build" (Construir) e selecione "Firestore Database".
- Clique em "Criar banco de dados".
3. Escolha o modo e a localização: 
- Selecione o modo de segurança para iniciar:
    - Modo de produção: Mais seguro, mas exige autenticação para acessar os dados.
    - Modo de teste: Permite acesso livre aos dados por um período limitado (30 dias). Ideal para testes e desenvolvimento inicial.
- Escolha a localização do seu banco de dados. Essa escolha pode afetar a latência e a disponibilidade, dependendo da região dos seus usuários.
4. Crie sua primeira collection: 
- Após criar o banco de dados, você será direcionado para a interface do Firestore.
- Clique em "Iniciar collection".
- Dê um nome para sua collection (por exemplo, "usuarios").
- Adicione um documento à sua collection:
    - Defina um ID para o documento (opcional, o Firestore pode gerar um automaticamente).
    - Adicione campos e seus valores (por exemplo, "nome": "João", "idade": 30).
    - Clique em "Salvar".
Pronto! Você criou seu primeiro banco de dados no Firebase (Firestore) e adicionou um documento a uma collection.

Observações:

O Firestore é um banco de dados NoSQL, ou seja, não possui um esquema rígido. Você pode adicionar campos dinamicamente aos documentos.
O Firestore oferece recursos em tempo real, permitindo que seus aplicativos recebam atualizações instantâneas quando os dados mudam.
Consulte a documentação oficial do Firestore para aprender mais sobre como modelar seus dados, realizar consultas complexas e usar os recursos avançados do Firestore: https://firebase.google.com/docs/firestore.

## Para obter as credenciais do Firebase para usar no seu projeto do Colab, siga estes passos:

 1. Acesse o Console do Firebase: Vá para o Console do Firebase e faça login com sua conta Google.

 2. Selecione seu Projeto: Escolha o projeto Firebase para o qual você deseja obter as credenciais. Se você ainda não tiver um projeto, crie um novo.

 3. Vá para as Configurações do Projeto: Clique no ícone de engrenagem (⚙️) no canto superior esquerdo da tela e selecione "Configurações do projeto".

 4. Acesse a seção "Contas de Serviço": Na página de configurações do projeto, clique na aba "Contas de serviço".

 5. Gere uma Nova Chave Privada: Role a página para baixo até a seção "SDKs de Admin do Firebase". Clique em "Gerar nova chave privada".

 6. Faça o Download do Arquivo JSON: O Firebase irá gerar um arquivo JSON contendo suas credenciais. Faça o download deste arquivo e salve-o em um local seguro.

 ### Usando as Credenciais no Colab:

 1. Carregue o Arquivo JSON no Colab:

2. No Colab, clique no ícone de pasta à esquerda para abrir o painel lateral.
3. Clique nos três pontos ao lado de "drive" e selecione "Montar Drive".
4. Faça o upload do arquivo JSON de credenciais para o seu Drive (no caso deste projeto, o nome do arquivo é 'chat-gemini-firebase.json').

## Suporte

Se você encontrar problemas ou tiver dúvidas sobre o Gemini CRUD Generator, abra uma issue no GitHub ou envie uma mensagem diretamente para os mantenedores do projeto.

