# sorteio-premiado
Web App com foco em Android, que tem por objetivo gerar lucro e entretenimento para bares.

#### 1. Apresentação do sistema
#### 2. Como instalar

## 1. Apresentação do sistema

São gerados dois APK's, sendo que um vai instalado em uma Android TV Box ou SmartTV Android (onde são apresentado os sorteios ao público) e outro vai instalado no celular do dono do bar, que ficará responsável por gerenciar as apostas.

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
