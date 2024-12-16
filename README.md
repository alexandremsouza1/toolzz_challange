# Introdução
Aplicativo de chat em tempo real com Laravel, VueJS, Laravel Echo, SocketIO, Redis incluindo Fila, Tarefa Agendada, Laravel Horizon, Laravel Telescope e Laravel Pulse.

## Visão geral

Este aplicativo contém os seguintes recursos:

    Vários quartos de chat
    Chat em tempo real com Canais Privados e de Presença
    Cada sala contém uma área de compartilhamento (onde todos podem conversar) ou um chat privado com um usuário específico na sala
    Mensagem agendada pelo bot
    Reação a mensagens, como no Facebook Messenger (notificação em tempo real para outros sobre a reação)
    Animação de celebração com confetes
    Alteração de cor da mensagem (chat privado)
    phpMyAdmin - gerenciamento de banco de dados


# Rodar com Docker

Primeiro, crie o arquivo .env a partir de .env.docker.

Gere a chave do Laravel:
  ```shell
  docker exec -it <container_name> php artisan key:generate
 ```

<details>
  <summary>Em seguida, precisamos instalar as dependências para o Laravel e Frontend  (VueJS):</summary>
  

  ```shell
  # MacOS + Linux
  docker run --rm -v $(pwd):/app -w /app composer:2.8.3 install

  docker run --rm -v $(pwd):/app -w /app node:22-alpine npm install

  docker run --rm -v $(pwd):/app -w /app node:22-alpine npm run build


  # If Windows see below:

  # Git bash
  docker run --rm -v "/$(pwd)":/app -w //app composer:2.8.3 install

  docker run --rm -v "/$(pwd)":/app -w //app node:22-alpine npm install

  docker run --rm -v "/$(pwd)":/app -w //app node:22-alpine npm run build

  # PowerShell
  docker run --rm -v "$(pwd):/app" -w /app composer:2.8.3 install

  docker run --rm -v "$(pwd):/app" -w /app node:22-alpine npm install

  docker run --rm -v "$(pwd):/app" -w /app node:22-alpine npm run build

  # Command Prompt
  docker run --rm -v "%cd%:/app" -w /app composer:2.8.3 install

  docker run --rm -v "%cd%:/app" -w /app node:22-alpine npm install

  docker run --rm -v "%cd%:/app" -w /app node:22-alpine npm run build

  ```
</details>

<br>


Em seguida, construa e inicie todos os serviços:

```
docker compose up -d --build
```


Agora, migre e faça o seed no banco de dados:
```shell
docker compose exec app php artisan migrate --seed
```

Por fim, você pode acessar o aplicativo em `http://localhost:8000`

O phpMyAdmin (gerenciamento de banco de dados) pode ser acessado em `http://localhost:8001.`

O Laravel Telescope pode ser acessado em `http://localhost:8000/telescope.`

O Laravel Pulse pode ser acessado em `http://localhost:8000/pulse.`

