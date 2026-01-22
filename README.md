# 🤖 Telegram Weather Bot | n8n Workflow

Este projeto automatiza um chatbot de previsão do tempo integrado ao **Telegram** via **n8n**. O sistema processa entradas de usuários, consulta a **OpenWeather API** e retorna dados meteorológicos em tempo real.

---

### ⚙️ Configurações Necessárias (Variáveis de Ambiente)

Antes de iniciar, certifique-se de que seu ambiente (Docker ou `.env`) possui as chaves abaixo:

> | Variável | Função |
> | --- | --- |
> | `TELEGRAM_BOT_TOKEN` | Token gerado pelo @BotFather. |
> | `OPENWEATHER_API_KEY` | Chave de acesso da OpenWeather. |
> 
> 

---

### 🚀 Fluxo de Instalação

#### 1. Importação do Projeto

1. Obtenha o arquivo `workflow-chatbot-telegram.json`.
2. No painel do n8n, acesse **Add Workflow** > **Import from File**.
3. Selecione o arquivo e carregue o fluxo.

#### 2. Vinculação das Credenciais (Telegram)

Para que o gatilho funcione, você deve mapear a variável de ambiente para uma credencial interna:

* Vá em **Credentials** > **Create New** > **Telegram API**.
* No campo **Access Token**, ative o modo **Expression** (ícone `f(x)`).
* Cole o código: `{{ $env.TELEGRAM_BOT_TOKEN }}`.
* **Checklist:** Certifique-se de que os nós de *Trigger* e *Send Message* estão apontando para esta credencial criada.

#### 3. Conexão OpenWeather

* **Configuração Zero:** O nó **HTTP Request** já está pré-configurado.
* Ele busca automaticamente a variável `{{ $env.OPENWEATHER_API_KEY }}` sem necessidade de intervenção manual nas credenciais do n8n.

---

### 💬 Exemplos de Resposta

* **Sucesso:** `🌤️ A temperatura em [Cidade] é de [X]°C.`
* **Erro:** `❌ Cidade não encontrada. Use o formato Cidade,UF...`

---
