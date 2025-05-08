

Frigate Telegram
Notificações de eventos do Frigate via Telegram.

Exemplo de funcionamento
![image](https://github.com/user-attachments/assets/b890e264-d038-4cf8-813e-5dc24e099fc6)


Como iniciar
Instale o Docker

Baixe o arquivo docker-compose.yml:

bash
Copiar
Editar
https://raw.githubusercontent.com/OldTyT/frigate-telegram/main/docker-compose.yml
Altere as variáveis de ambiente no docker-compose

Faça o deploy:

bash
Copiar
Editar
docker compose up -d
Lucro!

Variáveis de Ambiente
Variável	Valor Padrão	Descrição
TELEGRAM_BOT_TOKEN	""	Token do bot do Telegram.
FRIGATE_URL	http://localhost:5000	Link interno para o Frigate.
FRIGATE_EVENT_LIMIT	20	Limita o número de eventos retornados.
DEBUG	False	Modo debug.
TELEGRAM_CHAT_ID	0	ID do chat do Telegram.
SLEEP_TIME	5	Tempo de espera após o ciclo, em segundos.
FRIGATE_EXTERNAL_URL	http://localhost:5000	Link externo do Frigate (usado para gerar links nas mensagens).
TZ	""	Fuso horário
REDIS_ADDR	localhost:6379	IP e porta do Redis
REDIS_PASSWORD	""	Senha do Redis
REDIS_DB	0	Banco de dados Redis
REDIS_PROTOCOL	3	Protocolo do Redis
REDIS_TTL	1209600	TTL das chaves de eventos no Redis (em segundos)
TIME_WAIT_SAVE	30	Tempo de espera para o vídeo do evento ser totalmente criado (em segundos)
WATCH_DOG_SLEEP_TIME	3	Tempo de espera do watchdog (em segundos)
EVENT_BEFORE_SECONDS	300	Enviar evento ocorridos nos segundos anteriores
SEND_TEXT_EVENT	False	Enviar evento como texto sem mídia
FRIGATE_EXCLUDE_CAMERA	None	Lista de câmeras do Frigate a serem excluídas, separadas por ,
FRIGATE_INCLUDE_CAMERA	All	Lista de câmeras do Frigate a serem incluídas, separadas por ,
FRIGATE_EXCLUDE_LABEL	None	Lista de labels de eventos a serem excluídas, separadas por ,
FRIGATE_INCLUDE_LABEL	All	Lista de labels de eventos a serem incluídas, separadas por ,
FRIGATE_EXCLUDE_ZONE	None	Lista de zonas do Frigate a serem excluídas, separadas por ,
FRIGATE_INCLUDE_ZONE	All	Lista de zonas do Frigate a serem incluídas, separadas por ,
REST_API_ENABLE	False	Habilita a API REST HTTP
REST_API_LISTEN_ADDR	:8080	Endereço onde a API REST irá escutar

Funcionalidades
API REST
Primeiro, a API precisa estar habilitada nas variáveis de ambiente. O arquivo docker-compose.yml já possui a variável, mas está como "False" por padrão.
Para habilitar:
REST_API_ENABLE: True

URL completa:
http://IP-DO-HOST-DO-DOCKER:8080/api/v1/COMANDO

Comandos disponíveis:

/mute

/ping

/resume

/status

/stop

/unmute

Mais detalhes disponíveis no Swagger:
http://localhost:8080/docs/index.html

Silenciar/reativar mensagens de eventos
Você pode ativar ou desativar as notificações de eventos (os dados são armazenados no Redis, garantindo persistência após reinicializações).

Comandos:

/mute

/unmute

⚠️ Atenção: Por motivos de segurança, os comandos só funcionam no chat com o TelegramChatID especificado.

Pausar/retomar envio de mensagens de eventos
Você pode pausar ou retomar o envio das notificações de eventos (os dados são armazenados no Redis, garantindo persistência após reinicializações).

Comandos:

/stop

/resume

⚠️ Atenção: Por motivos de segurança, os comandos só funcionam no chat com o TelegramChatID especificado.
