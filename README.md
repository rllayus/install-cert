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


