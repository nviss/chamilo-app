Chamilo LMS Mobile app
================================

Instalación
-----------------------------

En primer lugar instalar NPM en caso de no tenerlo instalado, a continuación Apache Cordova en tu equipo #npm install -g cordova

Clonar este repositorio:
```
git clone git@github.com:nviss/chamilo-mobile.git
cd chamilo-mobile
```

Añadir el SDK Android y los plugins necesarios

#cordova platform add android
#cordova plugin add cordova-plugin-device
#cordova plugin add cordova-plugin-dialogs
#cordova plugin add cordova-plugin-file
#cordova plugin add cordova-plugin-file-transfer
#cordova plugin add cordova-plugin-inappbrowser
#cordova plugin add cordova-plugin-network-information
#cordova plugin add cordova-plugin-screen-orientation
#cordova plugin add cordova-plugin-spinner
#cordova plugin add cordova-plugin-splashscreen
#cordova plugin add cordova-plugin-whitelist
#cordova plugin add cordova-plugin-zip
#cordova plugin add cordova-plugin-cache-clear
#cordova plugin add cordova-plugin-android-permissions
#cordova plugin add cordova-plugin-filechooser
#cordova plugin add cordova-plugin-filepath
#cordova plugin add cordova-plugin-pdialog
#cordova plugin add cordova-plugin-file-opener2

Si se desea utilizar el sistema de notificaciones escriba el comando #cordova plugin add phonegap-plugin-push
Es necesario tener en la raíz del proyecto el fichero google-services.json
Para generarlo debes crear un proyecto en https://console.firebase.google.com/u/0/?pli=1 
En Firebase, una vez creado el proyecto para descargare el archivo google-services.json hay que seguir las instrucciones indicadas aquí:
Cómo descargar un archivo de configuración --> https://support.google.com/firebase/answer/7015592?hl=es#zippy=%2Cen-este-art%C3%ADculo
En el fichero config.xml está añadida la linea necesaria para las notificaciones --><resource-file src="google-services.json" target="app/google-services.json" />
En caso de no usar notificaciones deberá eliminarla.

Nota:
Se debe editar la cadena org.chamilo.app que aparece en el fichero config.xml y sustituirlo por el que se haya creado en google-services.json
Si no se hace dará un error Apache Cordova.

El fichero google-services.json debe copiarse a la ruta ../platforms/android/app/google-services.json para que no muestre error Cordova al compilar.

Construir el APK de Android mediante #cordova build android
Finalmente ejecutar sobre un dispositivo Android o en un entorno de pruebas con el comando #cordova run android

En tu Chamilo:
* Debes copiar el contenido de la carpeta "chamilo_app" debe ser copiada en el directorio plugin de la plataforma (plugins/chamilo_app).
* Para poder visualizar las imágenes de las secciones de mensajes, descripción, anuncios y foros, debes modificar el fichero .htaccess de la carpeta "courses".
```
RewriteCond %{HTTP_USER_AGENT} !android [NC]
RewriteRule ([^/]+)/document/(.*)$ /main/document/download.php?doc_url=/$2&cDir=$1 [QSA,L]
```
Fin
