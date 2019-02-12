---
title: Configuración de dispositivo iOS en Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Agregue, configure o cree valores en dispositivos iOS para restringir características, lo que incluye establecer requisitos de contraseña, controlar la pantalla de bloqueo, usar aplicaciones integradas, agregar aplicaciones restringidas o aprobadas, controlar dispositivos Bluetooth, conectarse a la nube para realizar copias de seguridad y almacenar, habilitar la pantalla completa, agregar dominios y controlar la manera en que los usuarios interactúan con el explorador web Safari en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune; seodec18
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 94e09f413ea0e6b3811c7c19a93d188ac15ee04c
ms.sourcegitcommit: 0142020a7cd75348c6367facf072ed94238e667f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2019
ms.locfileid: "55230093"
---
# <a name="ios-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos iOS para permitir o restringir características mediante Intune

En este artículo se enumeran y describen los diferentes valores de configuración que se pueden controlar en los dispositivos iOS. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, permitir o restringir determinadas aplicaciones, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos iOS.

## <a name="before-you-begin"></a>Antes de comenzar
[Cree un perfil de configuración de dispositivo](device-restrictions-configure.md).

## <a name="general"></a>General

- **Compartir los datos de uso**: Elija **Bloquear** para evitar que el dispositivo envíe a Apple datos de diagnóstico y uso. **No configurado** permite que se envíen estos datos.
  - **Envío de datos de diagnóstico**: **Bloquear** evita que el usuario cambie la configuración de análisis de aplicación y envío de diagnóstico en **Datos de diagnóstico y uso** (configuración del dispositivo). Para usar esta configuración, el dispositivo debe estar en modo de supervisión (iOS 9.3.2 y posteriores). **No configurado** permite que el usuario cambie esta configuración del dispositivo.
- **Captura de pantalla**: elija **Bloquear** para impedir que se hagan capturas de pantalla en el dispositivo. **No configurado** permite que el usuario capture el contenido de la pantalla como imagen.
  - **Observación de pantalla remota desde la aplicación Aula (solo con supervisión)**: Elija **Bloquear** para evitar que la aplicación Classroom vea de forma remota la pantalla en el dispositivo. Para usar esta configuración, el dispositivo debe estar en modo de supervisión (iOS 9.3 y posteriores). **No configurado** permite que la aplicación Aula de Apple vea la pantalla.
  - **Observación de pantalla sin mensajes desde la aplicación Aula (solo con supervisión)**: Si está establecido en **Permitir**, los profesores pueden observar de manera silenciosa la pantalla de los dispositivos iOS de los estudiantes con la aplicación Aula sin que lo sepan los alumnos. Los dispositivos de alumnos inscritos en una clase con la aplicación Aula automáticamente dan permiso al profesor de ese curso. **No configurado** impide esta característica.
- **Certificados TLS que no son de confianza**: Elija **Bloquear** para evitar en el dispositivo los certificados de Seguridad de la capa de transporte (TLS) que no son de confianza. **No configurado** permite los certificados TLS.
- **Confianza de aplicaciones empresariales**: Elija **Bloquear** para quitar el botón **Trust Enterprise Developer** en Configuración > General > Administración de perfiles y dispositivos del dispositivo. **No configurado** permite que el usuario elija confiar en aplicaciones no descargadas de la tienda de aplicaciones.
- **Modificación de la cuenta (solo con supervisión)**: Cuando se establece en **Bloquear**, el usuario no puede actualizar la configuración específica del dispositivo en la aplicación de configuración de iOS. Por ejemplo, el usuario no puede crear nuevas cuentas de dispositivo ni modificar el nombre de usuario o la contraseña. **No configurado** permite que los usuarios cambien esta configuración.
  Esta característica también se aplica a la configuración accesible desde la aplicación de configuración de iOS, como Mail, Contacts, Calendar, Twitter, etc. Esta característica no se aplica a las aplicaciones con la configuración de la cuenta que no se pueden configurar desde la aplicación de configuración de iOS, como la aplicación Microsoft Outlook.
- **Habilitar restricciones en la configuración del dispositivo (solo con supervisión)**: Elija **Bloquear** para evitar que los usuarios habiliten restricciones en la configuración del dispositivo. **No configurado** permite que el usuario configure las restricciones (como los controles parentales) del dispositivo.
- **Usar la opción de borrar todo el contenido y la configuración del dispositivo (solo con supervisión)**: Elija **Bloquear** para que los usuarios no puedan usar la opción de borrar todo el contenido y la configuración del dispositivo (solo con supervisión). **No configurado** permite que los usuarios accedan a esta configuración.
- **Modificación del nombre del dispositivo (solo con supervisión)**: Elija **Bloquear** para que no se pueda cambiar el nombre del dispositivo. **No configurado** permite que el usuario cambie el nombre del dispositivo.
- **Modificación de la configuración de notificaciones (solo con supervisión)**: Elija **Bloquear** para que no se pueda cambiar la configuración de notificaciones. **No configurado** permite que el usuario cambie la configuración de las notificaciones del dispositivo.
- **Modificación del fondo de pantalla (solo con supervisión)**: **Bloquear** evita que se cambie el fondo de pantalla. **No configurado** permite que el usuario cambie el fondo de pantalla del dispositivo.
- **Modificación de la configuración de confianza de aplicaciones empresariales (solo con supervisión)**: **Bloquear** evita que el usuario cambie la configuración de confianza de aplicaciones empresariales en dispositivos supervisados. **No configurado** permite que el usuario confíe en aplicaciones no descargadas de la tienda de aplicaciones.
- **Cambios de perfil de configuración (solo con supervisión)**: **Bloquear** evita los cambios del perfil de configuración en el dispositivo. **No configurado** permite que el usuario instale perfiles de configuración.
- **Bloqueo de activación (solo con supervisión)**: Elija **Permitir** para habilitar Bloqueo de activación en dispositivos iOS supervisados. Bloqueo de activación dificulta que un dispositivo robado o perdido pueda reactivarse.
- **Bloquear la eliminación de aplicaciones (solo con supervisión)**: Elija **Bloquear** para evitar que los usuarios quiten aplicaciones. **No configurado** permite que los usuarios quiten aplicaciones del dispositivo.
- **Bloqueo del modo restringido de USB (solo con supervisión)**: Elija **Bloquear** para deshabilitar el modo restringido de USB en los dispositivos supervisados. El modo restringido de USB impide que los accesorios USB intercambien datos con un dispositivo bloqueado durante más de una hora. **No configurado** permite el modo restringido de USB.
- **Exigir fecha y hora automáticas (solo con supervisión)**: **Requerir** obliga a los dispositivos supervisados a establecer la fecha y la hora automáticamente. La zona horaria del dispositivo se actualiza cuando el dispositivo tiene conexiones móviles o tiene Wi-Fi con servicios de ubicación habilitados.
- **Requerir que los alumnos pidan permiso para dejar un curso de Aula (solo con supervisión)**: **Requerir** obliga a los alumnos inscritos en un curso no administrado con la aplicación Aula a pedir permiso al profesor para dejar el curso. Solo disponible en iOS 11.3 y posteriores. **No configurado** no obliga al alumno a pedir permiso.
- **Permitir actualizaciones de PKI de manera inalámbrica**: **Permitir** permite a los usuarios recibir actualizaciones de software sin tener que conectar los dispositivos a un equipo.
- **Limitar el seguimiento de publicidad**: Elija **Limitar** para deshabilitar el identificador de publicidad del dispositivo. **No configurado** lo mantiene habilitado.
- **Bloquear la creación de VPN (solo con supervisión)**: **Bloquear** evita que los usuarios creen una configuración de VPN. **No configurado** permite que los usuarios creen VPN en el dispositivo.

## <a name="configurations-requiring-supervision"></a>Configuraciones que requieren supervisión

El modo supervisado de iOS solo se puede habilitar durante la configuración inicial del dispositivo a través del Programa de inscripción de dispositivos de Apple o con Apple Configurator. Una vez activado el modo supervisado, Intune puede configurar un dispositivo con la funcionalidad siguiente:

- Bloqueo de aplicaciones (modo de aplicación única) 
- Proxy HTTP global 
- Bypass del bloqueo de activación 
- Modo de aplicación única autónoma 
- Filtro de contenido web 
- Establecer la pantalla de fondo y la pantalla de bloqueo 
- Inserción de aplicación silenciosa 
- VPN Always-On 
- Permitir la instalación de aplicaciones administradas de forma exclusiva 
- iBookstore 
- iMessages 
- Centro de juegos 
- AirDrop 
- AirPlay 
- Emparejamiento de host 
- Sincronización en la nube 
- Búsqueda en Spotlight 
- Handoff 
- Borrar dispositivo 
- Interfaz de usuario de restricciones 
- Instalación de perfiles de configuración por interfaz de usuario 
- Noticias 
- Accesos directos del teclado 
- Modificaciones de código de acceso 
- Cambios en los nombres de dispositivos 
- Descargas de aplicaciones automáticas 
- Cambios en la confianza de las aplicaciones empresariales 
- Apple Music 
- Mail Drop 
- Emparejamiento con Apple Watch 

> [!NOTE]
> Apple ha confirmado que ciertas opciones de configuración se trasladarán al modo de solo supervisión en 2019. Le recomendamos que lo tenga en cuenta a la hora de usar estas opciones, en lugar de esperar a que Apple las migre al modo de solo supervisión:
> - Instalación de la aplicación por los usuarios finales
> - Eliminación de aplicaciones
> - FaceTime
> - Safari
> - iTunes
> - Contenido explícito
> - Documentos y datos de iCloud
> - Juego multijugador
> - Agregar amigos del centro de juegos
> - Siri

## <a name="password"></a>Contraseña

- **Contraseña**: Exige que el usuario final escriba una contraseña para acceder al dispositivo. No configurado permite que los usuarios accedan al dispositivo sin tener que escribir una contraseña.
  - **Contraseñas sencillas**: Elija **Bloquear** para exigir contraseñas más complejas. **No configurado** permite contraseñas sencillas, como `0000` y `1234`.
  - **Tipo de contraseña requerida**: Elija el tipo de contraseña que requiere la organización. Las opciones son:
    - **Valor predeterminado de dispositivo**
    - **Numérico**
    - **Alfanumérico**
  - **Número de caracteres no alfanuméricos en la contraseña**: Especifique el número de caracteres de símbolo, como `#` o `@`, que deben incluirse en la contraseña.
  - **Longitud mínima de la contraseña**: Escriba la longitud mínima que un usuario debe escribir (entre 4 y 14 caracteres).
  - **Número de errores de inicio de sesión antes de borrar el dispositivo**: escriba el número de errores de inicio de sesión que se permiten antes de que se borre el dispositivo (entre 1 y 11).
  - **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**<sup>1</sup>: Especifique cuánto tiempo puede permanecer inactivo el dispositivo antes de que el usuario deba volver a escribir la contraseña. Si escribe un tiempo mayor al que está establecido actualmente en el dispositivo, este pasará por alto el tiempo que escribió. Compatible en dispositivos iOS 8.0 y más recientes.
  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**<sup>1</sup>: Escriba el número máximo de minutos de inactividad que se permiten en el dispositivo hasta que se bloquea la pantalla. Si escribe un tiempo mayor al que está establecido actualmente en el dispositivo, este pasará por alto el tiempo que escribió.
  - **Expiración de la contraseña (días)**: Especifique el número de días antes de que se deba cambiar la contraseña del dispositivo.
  - **Impedir la reutilización de contraseñas anteriores**: Escriba el número de contraseñas nuevas que se deben usar antes de poder reutilizar una antigua.
  - **Desbloqueo con huella digital**: Elija **Bloquear** para evitar el uso de la huella digital para desbloquear el dispositivo. **No configurado** permite que el usuario desbloquee el dispositivo con la huella digital.
- **Modificación del código de acceso (solo con supervisión)**: Elija **Bloquear** para evitar que se cambie, se agregue o se quite el código de acceso. En los dispositivos supervisados, los cambios en las restricciones del código de acceso se pasan por alto después de bloquear esta característica. **No configurado** permite agregar, cambiar o quitar códigos de acceso.
  - **Modificación de la huella digital (solo con supervisión)**: **Bloquear** evita que el usuario cambie, agregue o quite las huellas digitales de TouchID. **No configurado** permite que el usuario actualice las huellas digitales de TouchID del dispositivo.
- **Bloquear la característica Autorrellenar contraseñas (solo con supervisión)**: Elija **Bloquear** para evitar el uso de la característica Autorrellenar contraseñas en iOS. Al elegir **Bloquear**, también ocurre lo siguiente:
  - No se les pide a los usuarios que usen una contraseña guardada en Safari ni en ninguna aplicación.
  - Se deshabilitan las contraseñas seguras automáticas y no se sugieren contraseñas seguras a los usuarios.

  **No configurado** permite estas características.

- **Bloquear solicitudes de proximidad de contraseñas (solo con supervisión)**: Elija **Bloquear** para que el dispositivo de un usuario no solicite contraseñas de los dispositivos cercanos. **No configurado** permite estas solicitudes de contraseñas.
- **Bloquear el uso compartido de contraseñas (solo con supervisión)**: **Bloquear** evita el uso compartido de contraseñas entre dispositivos mediante AirDrop. **No configurado** permite compartir las contraseñas.

<sup>1</sup>Al configurar los valores **Máximo de minutos de inactividad hasta que se bloquea la pantalla** y **Máximo de minutos tras el bloqueo de la pantalla antes de solicitar la contraseña**, se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, a pantalla se apaga automáticamente transcurridos cinco minutos y el dispositivo se bloquea después de cinco minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apaga la pantalla, el dispositivo se bloquea cinco minutos más tarde.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

- **Acceso a Centro de control con dispositivo bloqueado**: Elija **Bloquear** para evitar el acceso a la aplicación Centro de control cuando el dispositivo está bloqueado. **No configurado** permite que los usuarios accedan a la aplicación Centro de control cuando el dispositivo está bloqueado.
- **Notificaciones con dispositivo bloqueado**: **Bloquear** evita el acceso a las notificaciones cuando el dispositivo está bloqueado. **No configurado** permite que el usuario acceda a las notificaciones sin que sea necesario desbloquear el dispositivo.
- **Notificaciones de Wallet con dispositivo bloqueado**: **Bloquear** evita el acceso a la aplicación Wallet cuando el dispositivo está bloqueado. **No configurado** permite que el usuario acceda a la aplicación Wallet mientras el dispositivo está bloqueado.
- **Vista Hoy con dispositivo bloqueado**: **Bloquear** evita el acceso a la vista Hoy cuando el dispositivo está bloqueado. **No configurado** permite que el usuario vea la vista Hoy cuando el dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>Tienda de aplicaciones, presentación de documentos, juegos

- **Tienda de aplicaciones**: **Bloquear** evita el acceso a la tienda de aplicaciones en dispositivos supervisados. **No configurado** permite el acceso.
  - **Instalación de aplicaciones de la Tienda de aplicaciones (solo con supervisión)**: Elija **Bloquear** para bloquear la Tienda de aplicaciones en la pantalla de inicio del dispositivo. Los usuarios finales pueden seguir usando iTunes o Apple Configurator para instalar aplicaciones. **No configurado** permite la tienda de aplicaciones en la pantalla principal.
  - **Descargas de aplicaciones automáticas (solo con supervisión)**: Elija **Bloquear** para evitar la descarga automática de las aplicaciones compradas en otros dispositivos. No afecta las actualizaciones de las aplicaciones existentes. **No configurado** permite descargar en el dispositivo las aplicaciones compradas en otros dispositivos iOS.
- **Contraseña para acceder a la tienda de aplicaciones**: **Requerir** exige al usuario que escriba una contraseña para poder visitar la Tienda de aplicaciones. **No configurado** permite el acceso a la tienda de aplicaciones sin que sea necesario escribir una contraseña.
- **Compras desde la aplicación**: Elija **Bloquear** para evitar las compras en la tienda desde la aplicación. **No configurado** permite las compras en la tienda dentro de una aplicación en ejecución.
- **Música, podcasts o contenido de noticias explícitos de iTunes (solo con supervisión)**: Elija **Bloquear** para evitar el contenido de música, podcasts o noticias explícito de iTunes. **No configurado** permite que el dispositivo acceda a contenido clasificado para adultos en la tienda.
- **Descargar contenido marcado como "Erótico" en iBooks Store**: Elija **Bloquear** para evitar que los usuarios descarguen archivos multimedia de iBooks Store marcados como eróticos. **No configurado** permite que el usuario descargue libros con la categoría "Erotismo".
- **Visualización de documentos corporativos en aplicaciones no administradas**: **Bloquear** evita la visualización de documentos no corporativos en aplicaciones no administradas. **No configurado** permite ver los documentos corporativos en cualquier aplicación. Por ejemplo, se quiere evitar que los usuarios guarden archivos de la aplicación OneDrive en Dropbox. Configure este valor como **Bloquear**. Después de que el dispositivo recibe la directiva (por ejemplo, después de un reinicio), ya no le permite guardar.
  - **Permitir que las aplicaciones administradas escriban contactos en cuentas de contactos no administradas**: Cuando se establece en **Permitir**, los usuarios pueden agregar o sincronizar la información de contacto de Outlook de cualquier persona, incluidos contactos empresariales y corporativos, en la aplicación de contactos integrada en el dispositivo. Cuando se establece en **Sin configurar**, los usuarios no pueden agregar contactos de Outlook a la aplicación de contactos integrada en el dispositivo.
  
    Para usar este valor, establezca la opción **Visualización de documentos corporativos en aplicaciones no administradas** en **Bloquear**.
  
- **Visualización de documentos no corporativos en aplicaciones corporativas**: **Bloquear** evita la visualización de documentos no corporativos en aplicaciones corporativas. **No configurado** permite ver cualquier documento en aplicaciones administradas corporativas.
  - **Permitir que las aplicaciones no administradas lean en cuentas de contactos administradas**: Cuando se establece en **Permitir**, los usuarios pueden agregar información de contacto de cualquier persona de la aplicación iContacts a Outlook. **Sin configurar** evita la lectura, incluso la eliminación de duplicados, en la aplicación de contactos integrada en el dispositivo.
  
    Para usar este valor, establezca la opción **Visualización de documentos no corporativos en aplicaciones corporativas** en **Bloquear**.
  
- **Tratar AirDrop como destino no administrado**: **Requerir** obliga a que se considere a Airdrop un destino para colocar no administrado. Impide que las aplicaciones administradas envíen datos mediante AirDrop. 
- **Agregando amigos de Game Center (solo con supervisión)**: **Bloquear** evita que los usuarios agreguen amigos de Game Center. **No configurado** permite que el usuario agregue amigos en Game Center.
- **Game Center (solo con supervisión)**: **Bloquear** evita el uso de la aplicación Game Center. **No configurado** permite usar la aplicación Game Center en el dispositivo.
- **Juegos multijugador (solo con supervisión)**: Elija **Bloquear** para evitar los juegos multijugador. **No configurado** permite que el usuario disfrute juegos multijugador en el dispositivo.
- **Región de clasificaciones**: Elija la región de clasificaciones que quiere usar para las descargas permitidas. y luego elija las clasificaciones permitidas para **Películas** y **Programas de TV**.
- **Aplicaciones**: Elija la clasificación por edades permitida de las aplicaciones que los usuarios pueden descargar. También puede elegir **Permitir todas las aplicaciones**.

## <a name="built-in-apps"></a>Aplicaciones integradas

- **Cámara**: elija **Bloquear** para impedir el acceso a la cámara del dispositivo. **No configurado** permite el acceso a la cámara del dispositivo.
  - **FaceTime**: **Bloquear** evita el acceso a la aplicación FaceTime. **No configurado** permite el acceso a la aplicación FaceTime en el dispositivo.
- **Siri**: **Bloquear** evita el acceso a Siri. **No configurado** permite usar el asistente de voz Siri en el dispositivo.
  - **Siri con dispositivo bloqueado**: Elija **Bloquear** para evitar el acceso a Siri cuando el dispositivo está bloqueado. **No configurado** permite usar el asistente de voz Siri en el dispositivo cuando está bloqueado.
  - **Filtro de obscenidad de Siri (solo con supervisión)**: **Requerir** evita que Siri dicte o hable con un lenguaje malsonante.
  - **Siri para consultar el contenido generado por el usuario de Internet (solo con supervisión)**: **Bloquear** evita que Siri acceda a sitios web para responder preguntas. **No configurado** permite que Siri acceda al contenido generado por usuarios de Internet.
- **Apple News (solo con supervisión)**: Elija **Bloquear** para evitar el acceso a la aplicación Apple News en el dispositivo. **No configurado** permite usar la aplicación Apple News.
- **Tienda de iBooks (solo con supervisión)**: **Bloquear** evita el acceso a la tienda de iBooks. **No configurado** permite que los usuarios examinen y compren libros en iBooks Store.
- **Aplicación Mensajes en el dispositivo (solo con supervisión)**: Elija **Bloquear** para que los usuarios no puedan usar la aplicación Mensajes en el dispositivo. **No configurado** permite usar la aplicación Mensajes para enviar y leer mensajes de texto.
- **Podcasts (solo con supervisión)**: **Bloquear** evita que los usuarios usen la aplicación Podcasts. **No configurado** permite usar la aplicación Podcasts.
- **Servicio Música (solo con supervisión)**: **Bloquear** revierte la aplicación Música al modo clásico y deshabilita el servicio Música. **No configurado** permite usar la aplicación Apple Music.
- **Servicio iTunes Radio (solo con supervisión)**: **Bloquear** evita que los usuarios usen la aplicación iTunes Radio. **No configurado** permite usar la aplicación iTunes Radio.
- **Hacer cambios en la configuración de la aplicación Buscar a mis amigos (solo con supervisión)**: **Bloquear** evita los cambios en la configuración de la aplicación Buscar a mis amigos. **No configurado** permite que el usuario cambie la configuración de la aplicación Buscar a mis amigos.
- **Búsqueda de Spotlight para devolver resultados de Internet (solo con supervisión)**: **Bloquear** evita que Spotlight devuelva resultados de una búsqueda en Internet. **No configurado** permite que la búsqueda de Spotlight se conecte a Internet para proporcionar resultados de la búsqueda.
- **Bloquear la eliminación de las aplicaciones del sistema del dispositivo (solo con supervisión)**: Elija **Bloquear** para deshabilitar la posibilidad de quitar aplicaciones del sistema del dispositivo. **No configurado** permite que los usuarios quiten aplicaciones de sistema.

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

- **Aplicaciones prohibidas**: Lista de aplicaciones no administradas por Intune que no quiere que se instalen en el dispositivo. Si un usuario instala una aplicación de esta lista, recibirá una notificación a través de Intune.
- **Aplicaciones aprobadas**: Lista de aplicaciones que los usuarios pueden instalar. Para mantener el cumplimiento, los usuarios no deben instalar otras aplicaciones. Las aplicaciones que se administran mediante Intune están permitidas automáticamente. Si un usuario instala una aplicación de esta lista, recibirá una notificación a través de Intune.

Para agregar aplicaciones a estas listas, puede:

- **Agregar** la dirección URL de la tienda de aplicaciones de iTunes de la aplicación que quiere instalar. Por ejemplo, para agregar la aplicación Carpetas de trabajo de Microsoft, escriba `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para buscar la dirección URL de una aplicación, abra la tienda de aplicaciones de iTunes y busque la aplicación. Por ejemplo, busque `Microsoft Remote Desktop` o `Microsoft Word`. Seleccione la aplicación y copie la dirección URL.

  También puede usar iTunes para buscar la aplicación y luego usar la tarea **Copiar vínculo** para obtener la dirección URL de la aplicación.

- Importe un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato `<app url>, <app name>, <app publisher>`. O bien exporte una lista existente que incluye la lista de aplicaciones restringidas en el mismo formato.

> [!IMPORTANT]
> Se deben asignar perfiles de dispositivo que usen configuración de aplicaciones restringidas para grupos de usuarios.

## <a name="show-or-hide-apps-supervised-only"></a>Mostrar u ocultar aplicaciones (solo con supervisión)

En la lista de aplicaciones visibles u ocultas, puede configurar una de las siguientes listas en dispositivos supervisados que ejecuten iOS 9.3 o posteriores.

- **Aplicaciones ocultas**: Escriba una lista de las aplicaciones ocultas a los usuarios. Los usuarios no pueden ver ni abrir estas aplicaciones.
- **Aplicaciones visibles**: Especifique una lista de las aplicaciones que los usuarios pueden ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.

Para agregar aplicaciones a estas listas, puede:

- **Agregar** la dirección URL de la tienda de aplicaciones de iTunes de la aplicación que quiere instalar. Por ejemplo, para agregar la aplicación Carpetas de trabajo de Microsoft, escriba `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para buscar la dirección URL de una aplicación, abra la tienda de aplicaciones de iTunes y busque la aplicación. Por ejemplo, busque `Microsoft Remote Desktop` o `Microsoft Word`. Seleccione la aplicación y copie la dirección URL.

  También puede usar iTunes para buscar la aplicación y luego usar la tarea **Copiar vínculo** para obtener la dirección URL de la aplicación.

- Importe un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato `<app url>, <app name>, <app publisher>`. O bien exporte una lista existente que incluye la lista de aplicaciones restringidas en el mismo formato.

## <a name="wireless"></a>Inalámbrico

- **Itinerancia de datos**: elija **Bloquear** para impedir la itinerancia de datos a través de la red de telefonía móvil. **No configurado** permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.
- **Captura de fondo global durante la itinerancia**: **Bloquear** evita el uso de la característica de captura de fondo global durante la itinerancia a través de la red de telefonía móvil. **No configurado** permite que el dispositivo capture datos, como el correo electrónico, durante la itinerancia en una red de telefonía celular.
- **Marcación por voz**: Elija **Bloquear** para evitar que los usuarios usen la característica de marcación por voz en el dispositivo. **No configurado** permite la marcación por voz en el dispositivo.
- **Itinerancia de voz**: Elija **Bloquear** para evitar la itinerancia de datos a través de la red de telefonía móvil. **No configurado** permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.
- **Cambios en la configuración de uso de datos móviles de la aplicación (solo con supervisión)**: Elija **Bloquear** para evitar los cambios en la configuración de uso de datos móviles de la aplicación. **No configurado** permite que el usuario controle qué aplicaciones pueden usar datos móviles.
- **Punto de acceso personal**: **Bloquear** evita que el dispositivo se use como punto de acceso personal. Esta opción puede que no sea compatible con algunos operadores. **No configurado** permite esta característica Administrador de contraseñas de Microsoft Edge.
- **Conexión a redes Wi-Fi solo con perfiles de configuración (solo con supervisión)**: **Requerir** fuerza al dispositivo a usar solo las redes Wi-Fi configuradas mediante perfiles de configuración de Intune. **No configurado** permite que el dispositivo use otras redes Wi-Fi.
- **Reglas de uso de datos móviles (solo aplicaciones administradas)**: Defina los tipos de datos que las aplicaciones administradas pueden usar cuando están en redes de telefonía móvil. Las opciones son:
  - **Bloquear el uso de datos móviles**: Bloquee el uso de los datos móviles en **Todas las aplicaciones administradas** o **Elegir aplicaciones específicas**.
  - **Bloquear uso de datos móviles en itinerancia**: Bloquee el uso de los datos móviles en itinerancia en **Todas las aplicaciones administradas** o **Elegir aplicaciones específicas**.

## <a name="connected-devices"></a>Dispositivos conectados

- **AirDrop (solo con supervisión)**: **Bloquear** evita el uso de AirDrop en el dispositivo. **No configurado** permite usar la característica AirDrop para intercambiar contenido con dispositivos cercanos.
- **Emparejamiento con Apple Watch (solo con supervisión)**: **Bloquear** evita el emparejamiento con Apple Watch. **No configurado** permite el emparejamiento del dispositivo con Apple Watch.
- **Detección de muñeca para Apple Watch enlazados**: **Requerir** fuerza a los dispositivos Apple Watch emparejados a usar la detección de muñeca. Cuando se requiere, el dispositivo Apple Watch no mostrará notificaciones si no se lleva puesto. 
- **Modificación de Bluetooth (solo con supervisión)**: **Bloquear** evita que el usuario final cambie la configuración de Bluetooth en el dispositivo. **No configurado** permite que el usuario cambie esta configuración.
- **Emparejamiento de host para controlar los dispositivos con los que se puede emparejar un dispositivo iOS (solo con supervisión)**: **Sin configurar** deja que el emparejamiento de host permita al administrador controlar con qué dispositivos se puede emparejar un dispositivo iOS. **Bloquear** impide el emparejamiento de host.
- **Requerir contraseña de emparejamiento para solicitudes salientes de AirPlay**: **Requerir** exige una contraseña de emparejamiento cuando el usuario usa AirPlay para transmitir contenido a otros dispositivos de Apple. **No configurado** permite que el usuario transmita contenido mediante AirPlay sin tener que escribir una contraseña.
- **Bloquear AirPrint (solo supervisado)**: Elija **Bloquear** para evitar el uso de la característica AirPrint en el dispositivo. **No configurado** permite que el usuario use AirPrint.
  - **Bloquear el almacenamiento de credenciales de AirPrint en Keychain (solo con supervisión)**: **Bloquear** evita el uso del almacenamiento de Keychain para nombres de usuario y contraseñas en el dispositivo. **No configurado** permite almacenar el nombre de usuario y la contraseña de AirPrint en la aplicación Keychain.
  - **Requerir un certificado TLS de confianza para AirPrint (solo con supervisión)**: **Requerir** fuerza al dispositivo a usar certificados de confianza para la comunicación de impresión de TLS.
  - **Bloquear la detección de iBeacon de impresoras AirPrint (solo supervisado)**: **Bloquear** evita que balizas Bluetooth de AirPrint malintencionadas suplanten la identidad en el tráfico de red. **No configurado** permite anunciar impresoras AirPrint en el dispositivo.

## <a name="keyboard-and-dictionary"></a>Teclado y diccionario

- **Búsqueda de definiciones de palabras (solo con supervisión)**: **Bloquear** evita que el usuario resalte una palabra y luego busque su definición en el dispositivo. **No configurado** permite el acceso a la característica de búsqueda de definiciones.
- **Teclados predictivos (solo supervisados)**: **No configurado** permite usar teclados predictivos para sugerir las palabras que pueda querer el usuario. **Bloquear** impide esta característica.
- **Autocorrección (solo supervisada)**: **No configurado** permite que el dispositivo corrija automáticamente las palabras mal escritas. **Bloquear** impide usar la autocorrección.
- **Revisión ortográfica de teclado (solo supervisada)**: **No configurado** permite usar el corrector ortográfico en el dispositivo. **Bloquear** permite el corrector ortográfico.
- **Métodos abreviados de teclado (solo con supervisión)**: **No configurado** permite usar métodos abreviados de teclado en el dispositivo. **Bloquear** impide que el usuario use los métodos abreviados de teclado.
- **Dictado (solo con supervisión)**: **Bloquear** evita que el usuario use la entrada de voz para escribir texto. **No configurado** permite que el usuario use la entrada de dictado.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

- **Copia de seguridad en iCloud**: **No configurado** permite que el usuario realice una copia de seguridad del dispositivo en iCloud. **Bloquear** impide que el usuario cree una copia de seguridad del dispositivo en iCloud.
- **Sincronización de documentos en iCloud (solo con supervisión)**: **Sin configurar** permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud. **Bloquear** impide que iCloud sincronice documentos y datos.
- **Sincronización de Photo Stream en iCloud**: **No configurado** permite que los usuarios habiliten **My Photo Stream** en su dispositivo para sincronizar en iCloud y que las fotos estén disponibles en todos los dispositivos del usuario. **Bloquear** impide la sincronización de Photo Stream en iCloud.
- **Copia de seguridad cifrada**: **Requerir** obliga a que las copias de seguridad del dispositivo se cifren.
- **Fototeca de iCloud**: Establezca en **Bloquear** para deshabilitar el uso de la Fototeca de iCloud para almacenar fotos y vídeos en la nube. Las fotos que no se hayan descargado de la Fototeca de iCloud en el dispositivo se quitarán del dispositivo. **No configurado** permite usar la Fototeca de iCloud.
- **Sincronización de aplicaciones administradas con la nube**: **No configurado** permite que Intune administre las aplicaciones para sincronizar los datos con la cuenta de iCloud del usuario. **Bloquear** impide que estos datos se sincronicen con iCloud.
- **Fotos en streaming compartidas**: Elija **Bloquear** para deshabilitar **Fotos compartidas en iCloud** en el dispositivo. **No configurado** permite las fotos compartidas.
- **Continuación de la actividad**: **No configurado** permite que los usuarios continúen el trabajo que iniciaron en un dispositivo iOS en otro dispositivo iOS o macOS (entrega). **Bloquear** impide esta entrega.
- **Bloquear la sincronización de Keychain en iCloud**: Elija **Bloquear** para deshabilitar la sincronización de las credenciales almacenadas en Keychain en iCloud. **No configurado** permite que los usuarios sincronicen estas credenciales.
- **Bloquear la copia de seguridad de libros empresariales**: Elija **Bloquear** para evitar que los usuarios hagan copias de seguridad de libros empresariales. **No configurado** permite que los usuarios hagan una copia de seguridad de estos libros.
- **Bloquear la sincronización de metadatos de libros empresariales (notas y eventos destacados)**: **Bloquear** evita la sincronización de notas y eventos destacados de libros empresariales. **No configurado** permite la sincronización.

## <a name="autonomous-single-app-mode-supervised-only"></a>Modo de aplicación única autónoma (solo supervisado)

Use estos valores para configurar los dispositivos iOS de modo que ejecuten aplicaciones específicas en modo de aplicación única autónoma. Cuando se configura este modo y se ejecuta la aplicación, el dispositivo se bloquea. Solo puede ejecutar esa aplicación. Por ejemplo, agregue una aplicación que permita que los usuarios hagan una prueba en el dispositivo. Cuando se completan las acciones de la aplicación o quita esta directiva, el dispositivo vuelve a su estado normal.

Para agregar aplicaciones, puede:

- Escribir el **nombre de la aplicación** y el **identificador del lote de aplicaciones** y seleccionar **Agregar**. La sección [Referencia de identificador de lote para aplicaciones iOS integradas](#bundle-id-reference-for-built-in-ios-apps) (en este artículo) incluye algunas aplicaciones con sus identificadores.
- **Importar** un archivo .csv con la lista de nombres de aplicaciones y sus identificadores de lote. O bien puede **Exportar** una lista existente que incluya las aplicaciones.

## <a name="kiosk-supervised-only"></a>Pantalla completa (solo supervisado)

- **Aplicación para ejecutar en modo de pantalla completa**: Elija el tipo de aplicaciones que quiere que se ejecuten en pantalla completa. Las opciones son: 
  - **Aplicación de la Tienda**: Escriba la dirección URL de una aplicación de la tienda de aplicaciones de iTunes.
  - **Aplicación administrada**: Elija una aplicación que haya agregado a Intune.
  - **Aplicación integrada**: Escriba el [identificador de lote](#bundle-id-reference-for-built-in-ios-apps) de la aplicación integrada.

- **AssistiveTouch**: **Requerir** que la configuración de accesibilidad AssistiveTouch se establezca en el dispositivo. Esta característica ayuda a los usuarios con gestos en pantalla que podrían ser difíciles para ellos. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Invertir colores**: **Requerir** la configuración de accesibilidad Invertir colores para que los usuarios con discapacidades visuales puedan cambiar la pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Audio mono**: **Requerir** que la configuración de accesibilidad Audio mono esté establecida en el dispositivo. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **VoiceOver**: **Requerir** que la configuración de accesibilidad VoiceOver esté establecida en el dispositivo para leer en voz alta el texto en pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Zoom**: **Requerir** que la configuración Zoom esté establecida en el dispositivo para que los usuarios usen un toque para acercar en la pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Bloqueo automático**: **Permitir** el bloqueo automático del dispositivo. **No configurado** deshabilita esta característica.
- **Cambio de timbre**: **Permitir** el cambio de timbre (silencio) en el dispositivo. **No configurado** deshabilita esta característica.
- **Rotación de pantalla**: **Permitir** el cambio de la orientación de la pantalla cuando el usuario gira el dispositivo. **No configurado** deshabilita esta característica.
- **Botón de suspensión de pantalla**: Elija **Permitir** para deshabilitar el botón de reactivación de suspensión de pantalla en el dispositivo. **No configurado** habilita esta característica.
- **Toque**: **Bloquear** deshabilita la pantalla táctil en el dispositivo. **No configurado** permite que el usuario use la pantalla táctil.
- **Botones de volumen**: **Permitir** el uso de los botones de volumen en el dispositivo. **No configurado** deshabilita los botones de volumen.
- **Control de AssistiveTouch**: **Permitir** permite que los usuarios usen la función AssistiveTouch. **No configurado** deshabilita esta característica.
- **Control Invertir colores**: **Permitir** invierte los cambios de color para que los usuarios puedan ajustar la función Invertir colores. **No configurado** deshabilita esta característica.
- **Leer el texto seleccionado**: **Permitir** que la configuración de accesibilidad Reproducir selección esté establecida en el dispositivo. Esta característica lee en voz alta el texto seleccionado por el usuario. **No configurado** deshabilita esta característica.
- **Control de VoiceOver**: **Permitir** cambios de VoiceOver para que los usuarios puedan actualizar la función VoiceOver, por ejemplo, la velocidad con que el texto en pantalla se lee en voz alta. **No configurado** impide los cambios en VoiceOver.
- **Control de zoom**: **Permitir** que el usuario haga cambios en el zoom. **No configurado** impide cambios en el zoom.

> [!NOTE]
> Antes de configurar un dispositivo iOS para pantalla completa, debe usar la herramienta Apple Configurator o el Programa de inscripción de dispositivos de Apple para pasar el dispositivo al modo supervisado. Consulte la guía de Apple sobre cómo usar la herramienta Apple Configurator.
> Si la aplicación iOS que escriba se instala después de asignar el perfil, el dispositivo no ingresará en el modo de pantalla completa hasta que se reinicie el dispositivo.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referencia de identificador de lote para aplicaciones iOS integradas

En esta lista se muestra el identificador de lote de algunas aplicaciones iOS comunes integradas. Póngase en contacto con el proveedor de software para encontrar el identificador de lote de otras aplicaciones.

| Identificador de lote                   | Nombre de la aplicación     | Publicador |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | Tienda de aplicaciones    | Apple     |
| com.apple.calculator        | Calculadora   | Apple     |
| com.apple.mobilecal         | Calendario     | Apple     |
| com.apple.camera            | Cámara       | Apple     |
| com.apple.mobiletimer       | Reloj        | Apple     |
| com.apple.compass           | Compass      | Apple     |
| com.apple.MobileAddressBook | Contactos     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Archivos        | Apple     |
| com.apple.mobileme.fmf1     | Buscar amigos | Apple     |
| com.apple.mobileme.fmip1    | Buscar mi iPhone  | Apple     |
| com.apple.gamecenter        | Centro de juegos  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Mantenimiento       | Apple     |
| com.apple.Home              | Inicio         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Asignaciones         | Apple     |
| com.apple.MobileSMS         | Mensajes     | Apple     |
| com.apple.Music             | Música        | Apple     |
| com.apple.news              | Noticias         | Apple     |
| com.apple.mobilenotes       | Notas        | Apple     |
| com.apple.Numbers           | Números      | Apple     |
| com.apple.Pages             | Páginas        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Fotos       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Recordatorios    | Apple     |
| com.apple.MobileSafari      | Safari       | Apple     |
| com.apple.Preferences       | Configuración     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Acciones       | Apple     |
| com.apple.tips              | Sugerencias         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Vídeos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Inspección        | Apple     |
| com.apple.weather           | Clima      | Apple     |

## <a name="safari"></a>Safari

- **Safari (solo con supervisión)**: **Bloquear** el uso del explorador Safari en el dispositivo. **No configurado** permite que los usuarios utilicen el explorador Safari.
- **Autorrellenar**: **Bloquear** deshabilita la característica Autorrellenar de Safari en el dispositivo. **No configurado** permite que los usuarios cambien la configuración de Autorrellenar del explorador web.
- **Cookies**: Elija cómo se administran las cookies en el dispositivo. Las opciones son:
  - Allow
  - Bloquear todas las cookies
  - Permitir cookies de sitios web visitados
  - Permitir cookies del sitio web actual
- **Javascript**: **Bloquear** evita que los scripts de Java del explorador se ejecuten en el dispositivo. **No configurado** permite los scripts de Java.
- **Advertencias de fraude**: **Requerir** que las advertencias de fraude se muestren en el explorador web en el dispositivo. **No configurado** deshabilita esta característica.
- **Elementos emergentes**: **Bloquear** para deshabilitar el bloqueador de elementos emergentes del explorador web. **No configurado** permite el bloqueador de elementos emergentes.

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Dominios de correo electrónico no marcados

En **Dirección URL de dominio de correo electrónico**, agregue una o varias direcciones URL a la lista. Cuando los usuarios finales reciben un correo electrónico de un dominio distinto de los dominios que especifica, el correo electrónico se marca como correo electrónico no de confianza en la aplicación Mail de iOS.

### <a name="managed-web-domains"></a>Dominios web administrados

En **Dirección URL de dominio web**, agregue una o varias direcciones URL a la lista. Los documentos que se descargan de los dominios que especifica se consideran administrados. Esta configuración solo se aplica a los documentos que se descargan con el explorador Safari.

### <a name="safari-password-autofill-domains"></a>Dominios de relleno automático de contraseña de Safari

En **Dirección URL de dominio**, agregue una o varias direcciones URL a la lista. Los usuarios solo pueden guardar contraseñas web de las direcciones URL que aparecen en esta lista. Esta configuración solo se aplica al explorador Safari y a dispositivos iOS 9.3 y versiones posteriores en modo supervisado. Si no especifica ninguna dirección URL, se podrán guardar contraseñas de todos los sitios web.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede establecer la configuración y las restricciones de dispositivo en dispositivos [macOS](device-restrictions-macos.md).
