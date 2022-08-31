# install-cert
Instalar certificado firmado por una entidad certificador en un servidor JAVA

## URL DE REFERENCIA
https://www.sslshopper.com/ssl-converter.html

En el servidor se debe tener la llave privada.

## Primero se obtiene o descarga de la pagina de digicert el archivo p7b.

## Luego se convierte el p7b en .cert

      openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer

## Luego se crea pkcs12 con la llave privada el archivo .cer

      openssl pkcs12 -export -in certificate.cer -inkey privateKey.key -out certificate.p12
      
## El archivo p12 se creará y el certificado estará con el ALIAS 1


Listo para instalar el certificado



## Crear Certificado autofirmado

    keytool -genkey -alias MLD1001 -keyalg rsa -keysize 2048 -sigalg sha256withrsa -validity 730 -keystore MLD1001.jks
    
#Comando para obtener el certificado publico
 
    keytool -export -alias UNI50001 -rfc -file UNI50001.cer -keystore UNI50001.jk
    
#Obtener certificado privado

Primero se debe convertir el JKS a p12 con el siguiente comando

     keytool -importkeystore -srckeystore UNI50001.jks -srcstorepass changeit -srckeypass changeit -srcalias UNI50001 -destalias UNI50001 -destkeystore  UNI50001.p12 -deststoretype PKCS12 -deststorepass changeit -destkeypass changeit

Luego obtener la llamave privada con el siguiente comando

     openssl pkcs12 -in UNI50001.p12 -nodes -nocerts -out UNI50001.pem
