# CloudFTP
Configuring a Cloud FTP server using AWS EC2 and CrushFTP

# Como fazer...

- Iniciar uma instancia com amazon linux
   - Configurações mínimas para a máquina:
      Máquina t2.micro;
      1GB Memoria
      1 vCPU (2.5GHz)

- Fazer login como root
```shell
sudo -i
```

- Ir ate a pasta /var/opt/
```shell
cd /var/opt/
```
 
- Fazer o download do CrushFTP
```shell
wget https://www.crushftp.com/early7/CrushFTP7_PC.zip
```

- Descompactar 
```shell
sudo unzip CrushFTP7_PC.zip
```

- Deletar o arquivo zip
```shell
sudo rm CrushFTP7_PC.zip
```

- Entrar na pasta do CrushFTP
```shell
cd CrushFTP7_PC
```

- Dar permissões de execução para o script de instalação
```shell
sudo chmod +x crushftp_init.sh
```

- Criar um usuario administrador, executando o comando:
```shell
java -jar CrushFTP.jar -a "login-do-usuario" "senha-do-usuario"
```

- Adicionar um sym link para iniciar o serviço do CrushFTP automaticamente
```shell
ln -s /var/opt/CrushFTP7_PC/crushftp_init.sh /etc/init.d/crushftp
```

- Adicionar o CrushFTP como um serviço
```shell
/sbin/chkconfig --add crushftp
```

- Iniciar o Serviço do CrushFTP
```shell
/sbin/service crushftp start
/sbin/chkconfig crushftp on
```
- 


- TroubleShooting

Ao instalar o serviço em um EC2 com linux na Primeira vez, não conseguia acessa a interface grafica pelas portas 8080, 9090 e 443,
mesmo o processo do CrushFTP estar escutando nas portas Certas (vide Imagem 01.)

Link da Imagem 01: http://imgur.com/HhQNHIh

Ainda não sei como resolver...
