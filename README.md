
## Chatbot de Clima no Telegram com N8N
Este projeto consiste em um chatbot de clima no Telegram, desenvolvido no N8N, que informa a temperatura atual de uma cidade do Brasil por meio de uma consulta à OpenWeather API. 
O bot recebe o nome da cidade e UF informados pelo usuário, faz a validação e formatação da entrada, consulta a API do OpenWeather e retorna uma mensagem informando a temperatura. 

## Funcionalidades
-Integração com Telegram Bot
-Consulta em tempo real à API do OpenWeather
-Recebimento de mensagens via Telegram
-Validação e formatação da entrada (Cidade, UF)
-Validação da resposta e tratamento de erro
-Respostas automáticas (sucesso e erro)

## Estrutura do Workflow
**1. **Telegram Trigger****
     Recebe mensagens enviadas ao bot no Telegram.
**2. Set (Captura e formatação de entrada)**
    Captura e formata o texto recebido.
**3. If (Cidade e UF)**
    Verifica se o texto segue o padrão de (Cidade, UF).
    TRUE → HTTP Request (Chamada à OpenWeather)
    FALSE → Telegram Send Message (Mensagem de erro)
**4. HTTP Request (Chamada à OpenWeather)**
    Consulta à OpenWeather API.
**5. Set (Extração e formatação dos dados)**
    Formata a resposta enviada ao usuário.
**6. IF (validação da resposta)**
    Valida se a resposta indica sucesso ou erro.
    TRUE -> Envia mensagem de sucesso para o usuário.
    FALSE -> Envia mensagem de erro para o usuário.

## Importar o workflow no N8N 
1. Acesse o painel do N8N 
2. Em **"Workflows"**, clique em **"Import from file"**
3. Selecione o **"arquivo JSON do workflow"**
4. Salve o workflow

## Inserir as credenciais 
**Telegram 
-Criar o bot no Telegram**
1. Abra o aplicativo Telegram e procure por **@BotFather** no campo de busca
2. Para criar um novo bot, envie **/newbot** no campo de mensagem 
3. Escolha um nome e um nome de usuário para o bot (nome de usuário deve terminar em **“bot”**)
4. Copie o token de acesso fornecido pelo BotFather

**-Configurar no N8N**
1. Clique em **"Credentials"** e selecione **"Create credential"**
2. Selecione **"Telegram API"** e clique em **"Continue"**
3. Em **"Access Token"**, cole o token copiado *(TELEGRAM_BOT_TOKEN)*
4. Salve a credencial
5. Associe a credencial com os nós **"Telegram Trigger"** e **"Telegram - Send Message"**

**OpenWeather API
-Obter API Key**
1. Crie uma conta em https://home.openweathermap.org/users/sign_up
2. Clique em **"API Keys",** digite um nome e clique em **"Gerar"**

**-Configurar no N8N**
1. Clique em **"Credentials"** e selecione **"New"**
2. Selecione **"OpenWeather API"**
3. Em **"Access Token"**, insira a API Key *(OPENWEATHER_API_KEY)*
4. Salve a credencial
5. Associe a credencial com o nó **"Chamada à OpenWeather"**

## Configurar credencial no workflow 
Após colocar o nó **"Chamada à OpenWeather",** nos parâmetros em **"Credential to connect with"** associe com a credencial 

## Variáveis Esperadas
-Token do Bot do Telegram ***(TELEGRAM_BOT_TOKEN)***
-API Key da OpenWeather API ***(OPENWEATHER_API_KEY)***

## Executar o Chatbot
-No Telegram, envie a mensagem no formato padrão *(Cidade,UF)* 

## Respostas
### Mensagem de sucesso
🌤️ A temperatura em São Paulo é de 26°C.

### Mensagem de erro
❌ Cidade não encontrada. Use o formato Cidade,UF (ex.: São Paulo,SP).

### Link do Bot
[enter link description here](t.me/clima_cidades_bot)
