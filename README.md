# sorteio-premiado
Web App com foco em Android, que tem por objetivo gerar lucro e entretenimento para bares.

#### 1. Apresentação do sistema
#### 2. Como instalar

## 1. Apresentação do sistema

O sistema é dividido em duas partes, sendo que uma delas vai instalada em uma Android TV Box ou SmartTV Android (onde são apresentado os sorteios ao público) e outra vai instalado no celular do dono do bar, que ficará responsável por gerenciar as apostas.

  ### • Televisão
  
![Televisão - Tela](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Televis%C3%A3o%20-%20Tela.png)

  ### • Celular
  
![Celular - Login](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Celular%20-%20Login.jpg) ![Celular - Configuracoes 1](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Celular%20-%20Configuracoes%201.jpg)
![Celular - Configuracoes 2](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Celular%20-%20Configuracoes%202.jpg) ![Celular - Apostas](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Celular%20-%20Apostas.jpg)
![Celular - Sorteios](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Celular%20-%20Sorteios.jpg) ![Celular - Premiacoes](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Celular%20-%20Premiacoes.jpg)
![Celular - Caixa 1](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Celular%20-%20Caixa%201.jpg) ![Celular - Caixa 2](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Celular%20-%20Caixa%202.jpg)

## 2. Como instalar?

### 1. Requisitos

1.1. Servidor WEB VPS linux (que permita utilizar o crontab). É necessário que o apache, php e mysql estejam instalados e configurados corretamente.

### 2. Instalação

2.1. Download dos arquivos:
	2.1.1. >> cd /var/www/html
	2.1.2. >> wget https://github.com/RafaelCecchin/sorteio-premiado/archive/master.zip
	2.1.3. >> unzip master.zip
	2.1.4. >> mv sorteio-premiado-master/* ./
	2.1.5. >> rm -r sorteio-premiado-master
	2.1.6. >> rm master.zip
2.2. Configurar base de dados:
	2.2.1. >> mysql -u root -p
	 2.2.2. [PASSWORD]
	2.2.3. >> CREATE DATABASE sorteios CHARACTER SET utf8 COLLATE utf8_general_ci;
	2.2.4. >> SET time_zone = 'America/Sao Paulo'; SET time_zone = "+03:00"; SET @@session.time_zone = "+03:00";
	2.2.5. >> exit
	2.2.6. >> mysql -u root -p sorteios < /var/www/html/_dump_bd/sorteios.sql
	2.2.7. [PASSWORD]
	2.2.8. >> sudo nano /var/www/html/_bd/conexao_bd.php
	2.2.9. Informe no arquivo as credenciais da base de dados e tecle CTRL + O e CTRL + X para salvar e sair.
2.3. Configuração do crontab:
	2.3.1. >> sudo crontab -e
	2.3.2. Informe no arquivo o seguinte dado (sem aspas): "*/5 * * * * php -f /var/www/html/_iframes/_sorteio/_php/sorteio.php"
	2.3.3. Tecle :wq para salvar e sair
		
### 3. Geração dos APK's

3.1. Baixe e instale o programa WEBSITE 2 APK BUILDER PRO (https://websitetoapk.com/).
3.2. Geração do APK de apostas (celular):
![Web2apk Builder 1](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Web2apk%201.png)
	3.2.1. No campo "APP TITLE", informe o título do aplicativo de apostas. Esse é o nome que vai aparecer em baixo do ícone do aplicativo em seu celular android.
	3.2.2. No campo "APP ORIENTATION", selecione a opção "PORTRAIT" (retrato).
	3.2.3. No campo "URL", informe a URL do seu WEB APP, apontando para o diretório _iframes/_login/login.html. Também informe se a conexão é HTTP ou HTTPS.
	3.2.4. No campo "CACHE MODE", selecione a opção "NO CACHE". Isso permite que atualizações do front-end sejam aplicadas para o cliente de forma mais eficaz.
	3.2.5. Clique no botão "CUSTOMIZE APP PERMISSIONS" e desmarque todas as opções de permissão possíveis. Após isso, clique em "OK".
	![Web2apk Builder 3](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Web2apk%203.png)
	3.2.6. Em extras, deixe selecionado apenas "FULL SCREENS", "JAVASCRIPT API's", "ALLOW EXTERNALS URLs" e "CONFIRM ON EXIT".
	3.2.7. Clique no botão "GENERATE APK" e em "OK" quando a seguinte mensagem aparecer:
	![Web2apk Builder 4](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Web2apk%204.png)
	3.2.8. Clique em "FINISH!" quando a seguinte mensagem aparecer:
	![Web2apk Builder 6](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Web2apk%206.png)
3.3. Para geração do APK de sorteios (televisão), será necessário fazer as seguintes alterações:
![Web2apk Builder 2](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Web2apk%202.png)
	3.3.1. Altere o campo "APP TITLE" para "Sorteios" ou outro nome que desejar.
	3.3.2. Altere o campo "APP ORIENTATION" para opção "LANDSCAPE".
	3.3.3. No campo "URL", altere o diretório para _iframes/_sorteio/sorteio.html
	3.3.4. Clique no botão "GENERATE APK" e em "OK" quando a seguinte mensagem aparecer:
	![Web2apk Builder 4](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Web2apk%204.png)
	3.3.5. Clique em "FINISH!" quando a seguinte mensagem aparecer:
	![Web2apk Builder 6](https://github.com/RafaelCecchin/sorteio-premiado/blob/master/_img/Web2apk%206.png)
	
