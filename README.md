# UniJuntos - integração real com OneDrive

## Estrutura
- `index.html`: interface.
- `css/style.css`: estilos.
- `js/config.js`: configurações e permissões.
- `js/auth.js`: login Microsoft com MSAL.
- `js/graph.js`: chamadas autenticadas ao Microsoft Graph.
- `js/storage.js`: leitura e gravação do JSON no OneDrive.
- `js/app.js`: interface, cadastro, edição, exclusão, pesquisa e histórico.
- `assets/logo-unijuntos.png`: coloque aqui o arquivo PNG oficial do logo UniJuntos. O pacote mantém este caminho pronto para uso.

## Registro do aplicativo
1. No Microsoft Entra, crie um registro de aplicativo.
2. Em tipos de conta, habilite contas Microsoft pessoais.
3. Em Autenticação, adicione uma plataforma `Single-page application (SPA)`.
4. Cadastre exatamente a URL em que esta aplicação será executada, por exemplo `http://localhost:5500/index.html`.
5. Em permissões delegadas do Microsoft Graph, adicione `User.Read` e `Files.ReadWrite.AppFolder`.
6. Copie o `Application (client) ID` e informe na tela inicial.
7. Não crie nem coloque Client Secret no JavaScript.

## Executar localmente
Na pasta do projeto:

```bash
python -m http.server 5500
```

Abra `http://localhost:5500/index.html`.

## Dados
O aplicativo grava `unijuntos_dados.json` na pasta de aplicativo do OneDrive da conta autenticada. O código usa ETag/If-Match para evitar sobrescrever silenciosamente alterações concorrentes.

## Limitação arquitetural
Cada conta Microsoft pessoal usa a própria pasta de aplicativo. Para membros diferentes gravarem em uma base central administrável, use SharePoint/Microsoft Lists, Dataverse, Firebase ou um backend próprio.
