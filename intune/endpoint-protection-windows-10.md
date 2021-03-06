---
title: 'Configuración de la protección para dispositivos Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: En los dispositivos Windows 10 puede usar o configurar opciones de protección de punto de conexión para habilitar características de Windows Defender, como Protección de aplicaciones, firewall, SmartScreen, cifrado y BitLocker, Protección contra vulnerabilidades, Control de aplicaciones, Centro de seguridad y seguridad de dispositivos locales en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/23/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f87c2fa5fcb7e76fa8d398018e87ec0b15c05e9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843398"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Configuración de Windows 10 (y versiones posteriores) para proteger dispositivos mediante Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En Microsoft Intune se incluyen varias opciones de configuración para ayudarle a proteger sus dispositivos. En este artículo se describen todas las opciones que puede habilitar y configurar en Windows 10 y dispositivos más recientes. Estas opciones se crean en un perfil de configuración de Endpoint Protection, en Intune, para controlar la seguridad, incluidos BitLocker y Windows Defender.

Para configurar el Antivirus de Windows Defender, vea [Restricciones de dispositivos con Windows 10](device-restrictions-windows-10.md#windows-defender-antivirus).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivos de Endpoint Protection](endpoint-protection-configure.md).

## <a name="windows-defender-application-guard"></a>Protección de aplicaciones de Windows Defender

Compatible con las siguientes ediciones de Windows 10:

- Enterprise
- Professional

Al utilizar Microsoft Edge, Protección de aplicaciones de Windows Defender protege su entorno de sitios que no son de confianza para su organización. Cuando los usuarios visitan sitios que no aparecen en el límite de red aislada, estos se abren en una sesión de exploración virtual de Hyper-V. Los sitios de confianza se definen mediante un límite de red, que puede configurarse en Configuración de dispositivos.

Protección de aplicaciones solo está disponible para dispositivos de Windows 10 (de 64 bits). Con este perfil se instala un componente de Win32 para activar Protección de aplicaciones.

- **Protección de aplicaciones**: **habilite** esta característica para abrir los sitios no aprobados en un contenedor de exploración virtualizado de Hyper-V. **No configurado** (valor predeterminado) significa que cualquier sitio (aprobado o no) se abre en el dispositivo.
- **Comportamiento del Portapapeles**: seleccione qué acciones de copiar y pegar se permiten entre el equipo local y el explorador virtual de la Protección de aplicaciones.
- **Contenido externo en sitios de empresa**: establezca esta opción en **Bloquear** para impedir que se cargue contenido de sitios web no aprobados. **No configurado** (valor predeterminado) significa que los sitios que no sean de empresa se pueden abrir en el dispositivo.
- **Imprimir desde el explorador virtual** : si establece esta opción en **Permitir**, las impresoras locales, de red, PDF y XPS podrán imprimir contenido desde el explorador virtual. **No configurado** (valor predeterminado) deshabilita todas las funciones de impresión.
- **Recopilar registros**: si establece esta opción en **Permitir**, se recopilarán registros de eventos que se producen dentro de una sesión de exploración de Protección de aplicaciones. **No configurado** (valor predeterminado) no recopila ningún registro dentro de la sesión de exploración.
- **Conservar los datos del explorador generados por el usuario**: si establece esta opción en **Permitir**, se guardarán los datos de usuario (como las contraseñas, los favoritos y las cookies) creados durante la sesión de exploración virtual de la Protección de aplicaciones. **No configurado** (valor predeterminado) descarta los datos y los archivos descargados por el usuario cuando se reinicia el dispositivo, o cuando un usuario cierra sesión.
- **Aceleración gráfica**: **habilite** esta opción para cargar vídeos y sitios web con un uso intensivo de gráficos de forma más rápida mediante el acceso a una unidad de procesamiento de gráficos virtuales. **No configurado** (valor predeterminado) usa la CPU del dispositivo para los gráficos; no usa la unidad de procesamiento de gráficos virtual.
- **Descargar archivos al sistema de archivos host**: **habilite** esta opción para que los usuarios puedan descargar archivos desde el explorador virtualizado al sistema operativo host. **No configurado** mantiene los archivos locales en el dispositivo (valor predeterminado) y no descarga archivos en el sistema de archivos host.

## <a name="windows-defender-firewall"></a>Firewall de Windows Defender

Compatible con las siguientes ediciones de Windows 10:
- Inicio
- Professional
- Empresa
- Enterprise
- Education
- Móvil
- Mobile Enterprise

### <a name="global-settings"></a>Configuración global

Esta configuración se aplica a todos los tipos de redes.

- **Protocolo de transferencia de archivos**: establezca esta opción en **Bloquear** para deshabilitar FTP con estado. Cuando se establece en **No configurado** (valor predeterminado), el firewall no realiza el filtrado de FTP con estado para permitir las conexiones secundarias.
- **Tiempo de inactividad de asociación de seguridad antes de la eliminación**: las asociaciones de seguridad se eliminan si no se detecta tráfico de red durante *n* segundos. Especifique un tiempo de inactividad en segundos.
- **Codificación de clave previamente compartida**: **habilite** esta opción para usar una codificación de clave previamente compartida con UTF-8. **No configurado** (valor predeterminado) usa el valor del almacén local.
- **Exenciones de IPsec**: configure el tráfico específico que tenga que estar exento de IPsec, como:
  - **Códigos de tipo ICMP de IPv6 de descubrimiento de vecinos**
  - **ICMP**
  - **Códigos de tipo ICMP de IPv6 de descubrimiento de enrutadores**
  - **Tráfico de red DHCP de IPv4 e IPv6** 
- **Comprobación de la lista de revocación de certificados**: seleccione la forma en la que el dispositivo debe comprobar la lista de revocación de certificados. Algunas de las opciones son **Deshabilitar comprobación CRL**, **Error de comprobación de CRL solo al encontrar un certificado revocado** y **Error de comprobación de CRL al encontrar cualquier error**.
- **Coincidencia pertinente del conjunto de autenticación por módulo de generación de claves**: **habilite** esta opción para que los módulos de generación de claves TENGAN que omitir solo los conjuntos de aplicaciones de autenticación que no admitan. Cuando se establece en **No configurado**, los módulos de generación de claves MUST ignoran el conjunto de autenticación en su totalidad si no admiten todos los conjuntos de autenticación especificados.
- **Puesta de paquetes en cola**: especifique cómo se habilita el escalado de software en el lado de recepción para la recepción cifrada y el reenvío de texto no cifrado para un escenario de puerta de enlace de túnel IPsec. Esta opción garantiza que se conserve el orden de los paquetes.

### <a name="network-settings"></a>Configuración de red

Estas opciones son aplicables a tipos de red específicos, incluidas la **red del dominio (área de trabajo)**, la **red privada (reconocible)** y la **red pública (no reconocible)**.

#### <a name="general-settings"></a>Configuración general

- **Firewall de Windows Defender**: **habilite** esta opción para activar el firewall y la seguridad avanzada. **No configurado** (valor predeterminado) permite todo el tráfico de red, independientemente de las demás configuraciones de directiva.
- **Modo sigiloso**: establezca esta opción en **Bloquear** para impedir que el firewall funcione en el modo sigiloso. Bloquear el modo sigiloso también le permite bloquear la **exención de paquete protegido por IPsec**. **No configurado** (valor predeterminado) funciona el firewall en modo sigiloso, lo que ayuda a evitar respuestas a solicitudes de sondeo.
- **Blindada**: establezca esta opción en **Bloquear** para desactivar esta característica. **No configurado** (valor predeterminado) habilita esta configuración. Cuando esta configuración y el firewall de Windows Defender están activados, entonces se bloquea todo el tráfico entrante, con independencia de otras configuraciones de directiva.
- **Permitir respuestas de unidifusión a tráfico de difusión o multidifusión**: establezca esta opción en **Bloquear** para deshabilitar las respuestas de unidifusión a las difusiones multidifusión. Normalmente, no desea recibir respuestas de unidifusión a mensajes de difusión o multidifusión. Estas respuestas pueden indicar un ataque por denegación de servicio (DDoS) o un atacante que intenta buscar un equipo activo conocido. **No configurado** (valor predeterminado) habilita esta configuración.
- **Notificaciones entrantes**: establezca esta opción en **Bloquear** para ocultar las notificaciones a los usuarios cuando se impide que una aplicación escuche en un puerto. **No configurado** (valor predeterminado) habilita esta configuración y puede mostrar una notificación a los usuarios cuando se impide que una aplicación escuche en un puerto.
- **Acción predeterminada para conexiones entrantes**: establezca esta opción en **Bloquear** para que no se ejecute la acción predeterminada del firewall en las conexiones entrantes. Cuando se establece en **No configurado** (valor predeterminado), la acción predeterminada del firewall es actuar sobre las conexiones entrantes.

#### <a name="rule-merging"></a>Combinación de reglas

- **Reglas de Firewall de Windows Defender de aplicación autorizada del almacén local**: **habilite** esta opción para aplicar las reglas del firewall en el almacén local de forma que se reconozcan y se exija su cumplimiento. Cuando se establece en **No configurado** (valor predeterminado), las reglas de firewall de aplicación autorizada en el almacén loca se omiten y no se aplican.
- **Reglas de Firewall de Windows Defender de puerto globales del almacén local**: **habilite** esta opción para aplicar las reglas de puertos globales del firewall en el almacén local de forma que se reconozcan y se exija su cumplimiento. Cuando se establece en **No configurado** (valor predeterminado), las reglas firewall de puerto globales en el almacén local se omiten y no se aplican.
- **Reglas de Firewall de Windows Defender del almacén local**: **habilite** esta opción para aplicar las reglas del firewall en el almacén local de forma que se reconozcan y se exija su cumplimiento. Cuando se establece en **No configurado** (valor predeterminado), las reglas de firewall de puerto globales del almacén local se omiten y no se aplican.
- **Reglas IPsec del almacén local**: **habilite** esta opción para aplicar las reglas de seguridad de conexión del almacén local, independientemente del esquema o de las versiones de dichas reglas. Cuando se establece en **No configurado** (valor predeterminado), las reglas de seguridad de conexión del almacén local se omiten y no se aplican, independientemente de la versión de esquema y la versión de regla de seguridad de conexión.

## <a name="windows-defender-smartscreen-settings"></a>Configuración de SmartScreen de Windows Defender

Compatible con las siguientes ediciones de Windows 10 que tengan Microsoft Edge instalado:
- Inicio
- Professional
- Empresa
- Enterprise
- Education
- Móvil
- Mobile Enterprise

**Configuración**:

- **SmartScreen para aplicaciones y archivos**: **habilite** Windows SmartScreen para permitir la ejecución de archivos y de aplicaciones. SmartScreen es un componente de antimalware y contra la suplantación de identidad basado en la nube. **No configurado** (valor predeterminado) deshabilita SmartScreen.
- **Ejecución de archivos no comprobados**: establezca esta opción en **Bloquear** para impedir que los usuarios finales ejecuten archivos que no se hayan comprobado mediante Windows SmartScreen. **No configurado** (valor predeterminado) deshabilita esta característica y permite que los usuarios finales ejecuten archivos que no se han comprobado.

## <a name="windows-encryption"></a>Cifrado de Windows

### <a name="windows-settings"></a>Configuración de Windows

Compatible con las siguientes ediciones de Windows 10:

- Professional
- Empresa
- Enterprise
- Education
- Móvil
- Mobile Enterprise

**Configuración**:

- **Cifrar los dispositivos**: establezca esta opción en **Requerir** para pedir a los usuarios que habiliten el cifrado de dispositivo. En función de la edición de Windows y la configuración del sistema, se podría pedir a los usuarios lo siguiente:  
  - Confirmar que no está habilitado el cifrado de otro proveedor
  - Obligación de desactivar el cifrado de unidad Bitlocker y, después, volver a activar Bitlocker
    
    Si el cifrado de Windows se habilita mientras otro método de cifrado está activo, el dispositivo puede volverse inestable. 
- **Cifrar la tarjeta de almacenamiento (solo móvil)**: use la opción **Requerir** para cifrar todas las tarjetas de almacenamiento extraíbles su usadas por el dispositivo. **No configurado** (valor predeterminado) no requiere el cifrado de tarjetas de almacenamiento y no solicita al usuario que lo active. Esta configuración solo se aplica a dispositivos móviles Windows 10.

### <a name="bitlocker-base-settings"></a>Configuración base de BitLocker

Compatible con las siguientes ediciones de Windows 10:

- Enterprise
- Education
- Móvil
- Mobile Enterprise
- Professional

La configuración base es la configuración de BitLocker universal para todos los tipos de unidades de datos. Esta configuración administra las tareas de cifrado o las opciones de configuración de unidades que el usuario final puede modificar en todos los tipos de unidades de datos.

- **Advertencia para otro cifrado de disco**: establezca esta opción en **Bloquear** para deshabilitar el mensaje de advertencia si hay otro servicio de cifrado de disco activado en el dispositivo. **No configurado**: (valor predeterminado) permite que se muestren estos mensajes de advertencia.
    - **Permitir a los usuarios estándar habilitar el cifrado durante la unión a Azure AD**: cuando se elige **Permitir**, los usuarios convencionales y lo que no son administradores puede habilitar el cifrado de BitLocker cuando el usuario ha iniciado sesión. Esta configuración solo se aplica a dispositivos unidos a Azure Active Directory (Azure ADJ). **No configurada** solo permite a los administradores habilitar el cifrado de BitLocker en el dispositivo.
      
      Esta configuración solo se aplica a dispositivos unidos a Azure Active Directory (Azure ADJ). También requiere que la opción **Advertencia para otro cifrado de disco** esté establecida en **Bloqueo**.
- **Configurar métodos de cifrado**: **habilite** esta opción para configurar algoritmos de cifrado para el sistema operativo, los datos y las unidades extraíbles. Cuando está establecido en **No configurado** (valor predeterminado), BitLocker usa XTS-AES de 128 bits como método de cifrado predeterminado o el método de cifrado especificado por cualquier script de instalación.
  - **Cifrado para unidades de sistema operativo**: seleccione el método de cifrado para las unidades del sistema operativo. Se recomienda que use el algoritmo XTS-AES.
  - **Cifrado para unidades de datos fijas**: seleccione el método de cifrado para las unidades de datos fijas (integradas). Se recomienda que use el algoritmo XTS-AES.
  - **Cifrado para unidades de datos extraíbles**: seleccione el método de cifrado para unidades de datos extraíbles. Si la unidad extraíble se usa con dispositivos que no ejecutan Windows 10, entonces se recomienda que use el algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Configuración de BitLocker para unidades de sistema operativo
Compatible con las siguientes ediciones de Windows 10:

- Enterprise
- Education
- Móvil
- Mobile Enterprise
- Professional

Esta configuración se aplica específicamente a las unidades de datos de sistema operativo.

- **Autenticación adicional al inicio**: seleccione **Requerir** para configurar los requisitos de autenticación para el inicio de equipos, incluido el uso del Módulo de plataforma segura (TPM). Seleccione **No configurado** (valor predeterminado) para configurar solo las opciones básicas en dispositivos con un TPM.
  - **BitLocker con un chip TPM no compatible**: establezca esta opción en **Bloquear** (deshabilitar) con BitLocker cuando un dispositivo no tenga un chip TPM compatible. Cuando se establece en **No configurado**, los usuarios pueden usar BitLocker sin un chip de TPM compatible. BitLocker puede requerir una contraseña o una clave de inicio.
  - **Inicio de TPM compatible**: seleccione una opción para permitir, no permitir o exigir el uso de chip TPM.
  - **PIN de inicio de TPM compatible**: seleccione una opción para permitir, no permitir o exigir el uso de un PIN de inicio con el chip TPM. Habilitar un PIN de inicio requiere la interacción del usuario final. 
  - **Clave de inicio de TPM compatible**: seleccione una opción para permitir, no permitir o exigir el uso de una clave de inicio con el chip TPM. Habilitar una clave de inicio requiere la interacción del usuario final. 
  - **PIN y clave de inicio de TPM compatible**: seleccione una opción para permitir, no permitir o exigir el uso de una clave de inicio y un PIN con el chip TPM. Habilitar una clave y un PIN de inicio requiere la interacción del usuario final.
- **Longitud de PIN mínima**: **habilite** esta opción para configurar una longitud mínima del PIN de inicio de TPM. Cuando se establece en **No configurado** (valor predeterminado), los usuarios pueden configurar un PIN de inicio de cualquier longitud entre 6 y 20 dígitos.
  - **Mínimo de caracteres**: escriba el número de caracteres necesarios para el PIN de inicio entre **4**- y **20**.
- **Recuperación de unidades de sistema operativo**: **habilite** esta opción para controlar cómo se recuperan las unidades del sistema operativo protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible. Cuando se establece en **No configurado** (valor predeterminado), se admiten las opciones de recuperación predeterminadas para la recuperación de BitLocker. De forma predeterminada, se permite un DRA, las opciones de recuperación las especifica el usuario, incluida la contraseña de recuperación y la clave de recuperación, y no se guarda una copia de seguridad de la información de recuperación en AD DS.
  - **Agente de recuperación de datos basada en certificados**: establezca esta opción en **Bloquear** para impedir que se use el agente de recuperación de datos con unidades del SO protegidas mediante BitLocker. Establézcalo en **No configurado** (valor predeterminado) para habilitar esta opción, que permite que los agentes de recuperación de datos se usen con las unidades de sistema operativo protegidas mediante BitLocker.
  - **Creación de contraseña de recuperación por el usuario**: seleccione las opciones de los usuarios para generar una contraseña de recuperación de 48 dígitos (permitido, exigido o no permitido).
  - **Creación de clave de recuperación por el usuario**: seleccione las opciones de los usuarios para generar una clave de recuperación de 256 bits (permitido, exigido o no permitido).
  - **Opciones de recuperación en el asistente para configuración de BitLocker**: establezca esta opción en **Bloquear** para que los usuarios no puedan ver ni cambiar las opciones de recuperación. Si se establece en **No configurado** (valor predeterminado), los usuarios podrán ver y modificar las opciones de recuperación cuando activen BitLocker.
  - **Guardar información de recuperación de BitLocker en AD DS**: **habilite** esta opción para almacenar la información de recuperación de BitLocker en Azure Active Directory (AAD). Si se establece en **No configurado** (valor predeterminado), la información de recuperación no se guardará en AAD.
  - **Información de recuperación de BitLocker almacenada en AD DS**: configure qué partes de la información de recuperación de BitLocker se almacenan en Azure AD. Elija de entre las siguientes opciones:
    - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**
    - **Realizar copia de seguridad solo de contraseñas de recuperación**
  - **Almacenar la información de recuperación en AD DS antes de habilitar BitLocker**: establezca esta opción en **Requerir** para impedir que los usuarios activen BitLocker hasta que la información de recuperación de BitLocker se almacene correctamente en Azure Active Directory (AD). Si se establece en **No configurado** (valor predeterminado), se permite que los usuarios activen BitLocker, incluso aunque la información de recuperación no esté almacenada correctamente en Azure AD.
- **URL y mensaje de recuperación previos al arranque**: **habilite** esta opción para configurar el mensaje y la dirección URL que se muestra en la pantalla de recuperación de clave antes del arranque. **No configurado** (valor predeterminado) deshabilita esta característica.
  - **Mensaje de recuperación previo al arranque**: configure la forma en la que se muestra a los usuarios el mensaje de recuperación previo al arranque. Elija de entre las siguientes opciones:
    - **Usar la dirección URL y el mensaje de recuperación predeterminados**
    - **Usar URL y mensaje de recuperación vacíos**
    - **Usar un mensaje de recuperación personalizado**
    - **Usar una dirección URL de recuperación personalizada**

### <a name="bitlocker-fixed-data-drive-settings"></a>Configuración de BitLocker para unidades de datos fijas

Compatible con las siguientes ediciones de Windows 10:

- Enterprise
- Education
- Móvil
- Mobile Enterprise
- Professional

**Configuración**:

- **Acceso de escritura a unidad de datos fija no protegida con BitLocker**: establezca esta opción en **Bloquear** para conceder acceso de solo lectura a las unidades de datos que no estén protegidas mediante BitLocker. Si se establece en **No configurado** (valor predeterminado), se concederá acceso de lectura y escritura a unidades de datos que no estén protegidas con BitLocker.
- **Recuperación de unidad fija**: **habilite** esta opción para controlar cómo se recuperan las unidades fijas protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible. **No configurado** (valor predeterminado) deshabilita esta característica.
  - **Agente de recuperación de datos**: establezca esta opción en **Bloquear** para impedir el uso del agente de recuperación de datos con el editor de directivas de unidades fijas protegidas mediante BitLocker. **No configurado** (valor predeterminado) habilita el uso de agentes de recuperación de datos con las unidades fijas protegidas por BitLocker.
  - **Creación de contraseña de recuperación por el usuario**: configure si los usuarios pueden generar una contraseña de recuperación de 48 dígitos (permitido, exigido o no permitido).  
  - **Creación de clave de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una clave de recuperación de 256 bits.
  - **Opciones de recuperación en el asistente para configuración de BitLocker**: establezca esta opción en **Bloquear** para que los usuarios no puedan ver ni cambiar las opciones de recuperación. Si se establece en **No configurado** (valor predeterminado), los usuarios podrán ver y modificar las opciones de recuperación cuando activen BitLocker.
  - **Guardar información de recuperación de BitLocker en AD DS**: **habilite** esta opción para almacenar la información de recuperación de BitLocker en Azure Active Directory (Azure AD). Si se establece en **No configurado** (valor predeterminado), la información de recuperación no se guardará en Azure AD.
  - **Información de recuperación de BitLocker en AD DS**: configure qué partes de la información de recuperación de BitLocker se almacenan en Azure AD. Las opciones son:
    - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**
    - **Realizar copia de seguridad solo de contraseñas de recuperación**
  - **Almacenar la información de recuperación en AD DS antes de habilitar BitLocker**: establezca esta opción en **Requerir** para impedir que los usuarios activen BitLocker hasta que la información de recuperación de BitLocker se almacene correctamente en Azure AD. Si se establece en **No configurado** (valor predeterminado), se permitirá que los usuarios activen BitLocker, incluso aunque la información de recuperación no esté almacenada correctamente en Azure AD.

### <a name="bitlocker-removable-data-drive-settings"></a>Configuración de BitLocker para unidades de datos extraíbles

Compatible con las siguientes ediciones de Windows 10:

- Enterprise
- Education
- Móvil
- Mobile Enterprise
- Professional

**Configuración**:

- **Acceso de escritura a discos de datos extraíbles no protegidos con BitLocker**: establezca esta opción en **Bloquear** para conceder acceso de solo lectura a las unidades de datos que no estén protegidas mediante BitLocker. Si se establece en **No configurado** (valor predeterminado), se concederá acceso de lectura y escritura a unidades de datos que no estén protegidas con BitLocker.
  - **Acceso de escritura a dispositivos configurados en otra organización**: establezca esta opción en **Bloquear** para impedir el acceso de escritura a los dispositivos configurados en otra organización. **No configurado** (valor predeterminado) deniega el acceso de escritura.

## <a name="windows-defender-exploit-guard"></a>Protección contra vulnerabilidades de seguridad de Windows Defender

Compatible con las siguientes ediciones de Windows 10:

- Inicio
- Professional
- Empresa
- Enterprise
- Education
- Móvil
- Mobile Enterprise

Use la [Protección contra vulnerabilidades de seguridad de Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) para administrar y reducir la superficie expuesta a ataques de las aplicaciones que usan sus empleados.

### <a name="attack-surface-reduction"></a>Reducción de la superficie expuesta a ataques

- **Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows**

  Ayudar a [evitar las acciones y aplicaciones](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) usadas normalmente por malware que busca vulnerabilidades de seguridad para infectar equipos.

#### <a name="rules-to-prevent-office-macro-threats"></a>Reglas para evitar amenazas de macros de Office

Impedir que las aplicaciones de Office realicen las siguientes acciones:

- **Inserción de aplicaciones de Office en otros procesos (sin excepciones)**
- **Macros o aplicaciones de Office que crean contenido ejecutable**
- **Aplicaciones de Office que inician procesos secundarios**
- **Importación de Win32 desde código de macros de Office**

#### <a name="rules-to-prevent-script-threats"></a>Reglas para evitar amenazas de scripts

Bloquee los siguientes elementos para evitar las amenazas de script:

- **Código de js/vbs/ps/macro ofuscado**
- **js/vbs que ejecuta carga útil descargada de Internet (sin excepciones)**
- **Creación del proceso desde comandos PSExec y WMI**
- **Procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB**
- **Archivos ejecutables que no cumplen unos criterios de uso habitual, edad o lista de confianza**

#### <a name="rules-to-prevent-email-threats"></a>Reglas para evitar amenazas de correo electrónico

Bloquee los siguientes elementos para evitar las amenazas de correo electrónico:

- **Activación de contenido ejecutable (exe, dll, ps, js, vbs, etc.) eliminada del correo electrónico (correo electrónico web/cliente de correo electrónico) (sin excepciones)**

#### <a name="rules-to-protect-against-ransomware"></a>Reglas para protegerse del ransomware
- **Protección de ransomware avanzada**

> [!TIP]
> En [Reducir las superficies de ataque con Protección contra vulnerabilidades de seguridad de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) se proporciona más información detallada sobre estas reglas.

#### <a name="attack-surface-reduction-exceptions"></a>Excepciones de reducción de la superficie expuesta a ataques

- **Archivos y carpetas que se excluirán de las reglas de reducción de la superficie expuesta a ataques**: importe o agregue una lista de ubicaciones que se excluirán de las reglas configuradas.

### <a name="controlled-folder-access"></a>Acceso controlado a carpetas

Ayude a proteger los datos importantes de las amenazas y las aplicaciones malintencionadas, como ransomware.

- **Protección de carpetas**: proteja archivos y carpetas de cambios no deseados por aplicaciones malintencionadas. Puede importar una **lista de aplicaciones que tienen acceso a carpetas protegidas** o agregarlas manualmente. También puede agregar una **lista de carpetas adicionales que necesita proteger** mediante una carga o agregarlas manualmente.

### <a name="network-filtering"></a>Filtrado de red

Bloquear las conexiones salientes desde cualquier aplicación a IP y dominios de mala reputación.

### <a name="exploit-protection"></a>Protección contra vulnerabilidades

Para usar la protección contra vulnerabilidades, cree un archivo XML que incluya la configuración que prefiera para la mitigación de las aplicaciones y del sistema. Hay dos métodos:

 1. PowerShell: use uno o varios de los cmdlets de PowerShell Get-ProcessMitigation, Set-ProcessMitigation y ConvertTo-ProcessMitigationPolicy. Los cmdlets configuran los valores de mitigación y exportan una representación XML de ellos.

 2. Interfaz de usuario de Seguridad de Windows: en Seguridad de Windows, haga clic en Control de aplicaciones y explorador y, después, vaya a la parte inferior de la pantalla y busque Protección contra vulnerabilidades. Primero, use las pestañas Configuración del sistema y Configuración del programa para establecer la configuración de mitigación. Después, busque el vínculo Exportar configuración en la parte inferior de la pantalla para exportar una representación XML de esta.

Impida la **edición por el usuario de la interfaz de Protección contra vulnerabilidades** mediante la carga de un archivo XML que le permite configurar la memoria, el flujo de control y las restricciones de directiva. La configuración del archivo XML puede usarse para proteger una aplicación frente a las vulnerabilidades. **No configurado** (valor predeterminado) no envía una configuración personalizada. 

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Compatible con las siguientes ediciones de Windows 10:

**Administración de dispositivos móviles (MDM)**: 
- Professional
- Empresa
- Enterprise
- Education
- Móvil
- Mobile Enterprise

**Administración de directivas de grupo**: 
- Enterprise

Use **directivas de integridad del código de control de aplicaciones** para elegir aplicaciones adicionales que están auditadas o son de confianza para ejecutarse mediante Windows Defender Application Control. Se confía automáticamente en la ejecución de los componentes de Windows y de todas las aplicaciones de la Tienda Windows.

Las aplicaciones no se bloquearán al ejecutarse en modo **solo auditoría**. El modo **Solo auditoría** registra todos los eventos en registros locales del cliente.

Una vez habilitado, el control de aplicaciones solo puede deshabilitarse si se cambia el modo de **Aplicar** a **Solo auditoría**. El cambio de modo de **Aplicar** a **No configurado** da lugar a que el control de aplicaciones siga aplicándose en los dispositivos asignados.

## <a name="windows-defender-credential-guard"></a>Credential Guard de Windows Defender

Compatible con las siguientes ediciones de Windows 10:

- Enterprise

Credential Guard de Windows Defender protege frente a los ataques de robo de credenciales. Aísla secretos para que solo el software del sistema con privilegios pueda acceder a ellos.

La configuración de **Credential Guard** incluye:

- **Deshabilitar**: desactiva Credential Guard de forma remota si se ha activado anteriormente con la opción **Habilitar sin bloqueo UEFI**.

- **Habilitar con bloqueo UEFI**: Credential Guard no puede deshabilitarse de forma remota mediante una clave del Registro o una directiva de grupo.

    > [!NOTE]
    > Si usa esta configuración y, posteriormente, quiere deshabilitar Credential Guard, debe establecer la directiva de grupo en **Deshabilitado**. Además, borre físicamente la información de configuración de UEFI de cada equipo. Mientras se conserve la configuración de UEFI, Credential Guard estará habilitado.

- **Habilitar sin bloqueo UEFI**: permite deshabilitar Credential Guard de forma remota mediante una directiva de grupo. Los dispositivos que usan esta opción deben ejecutar Windows 10 versión 1511 o posterior.

Al habilitar Credential Guard, también se habilitan las siguientes características necesarias:

- **Seguridad basada en virtualización** (VBS): se activa en el próximo reinicio. La seguridad basada en la virtualización usa el hipervisor de Windows para proporcionar compatibilidad con los servicios de seguridad.
- **Arranque seguro con acceso directo a memoria**: activa las protecciones de VBS con arranque seguro y acceso directo a memoria (DMA). Las protecciones de DMA requieren compatibilidad con el hardware y solo se habilitan en dispositivos configurados correctamente.

## <a name="windows-defender-security-center"></a>Centro de seguridad de Windows Defender

Compatible con las siguientes ediciones de Windows 10:

- Inicio
- Professional
- Empresa
- Enterprise
- Education
- Móvil
- Mobile Enterprise

El Centro de seguridad de Windows Defender funciona como una aplicación o proceso independiente de cada una de las características individuales. Las notificaciones se muestran a través del Centro de actividades. Actúa como recopilador o lugar único para ver el estado y configurar algunas opciones para cada una de las características. Obtenga más información en los documentos de [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Aplicación y notificaciones del Centro de seguridad de Windows Defender

Bloquear el acceso del usuario final a las diversas áreas de la aplicación Centro de seguridad de Windows Defender. Si se oculta una sección, también se bloquean las notificaciones relacionadas.

- **Protección contra amenazas y virus**
- **Mantenimiento y estado del dispositivo**
- **Firewall y protección de red**
- **Control de aplicaciones y explorador**
- **Opciones de familia**
- **Notificaciones de las áreas que se muestran de la aplicación**: seleccione las notificaciones que se mostrarán a los usuarios finales. Las notificaciones que no son críticas incluyen resúmenes de la actividad del Antivirus de Windows Defender, así como notificaciones cuando se completan los exámenes. Todas las otras notificaciones se consideran críticas.

#### <a name="it-contact-information"></a>Información de contacto de TI

Proporcione la información de contacto de TI que aparecerá en la aplicación Centro de seguridad de Windows Defender y en las notificaciones de la aplicación. Puede elegir **Mostrar en la aplicación y en las notificaciones**, **Mostrar solo en la aplicación**, **Mostrar solo en las notificaciones** o **No mostrar**. Escriba el **nombre de la organización de TI** y al menos una de las siguientes opciones de contacto:

- **Número de teléfono o usuario de Skype del departamento de TI**
- **Dirección de correo electrónico del departamento de TI**
- **Dirección URL del sitio web de soporte técnico del departamento de TI**

## <a name="local-device-security-options"></a>Opciones de seguridad de dispositivos locales

Compatible con las siguientes ediciones de Windows 10:
 
- Inicio
- Professional
- Empresa
- Enterprise
- Education

Use estas opciones para configurar la seguridad local en dispositivos Windows 10.

### <a name="accounts"></a>Cuentas

- **Agregar nuevas cuentas de Microsoft**: establezca esta opción en **Bloquear** para impedir que los usuarios puedan agregar nuevas cuentas de Microsoft al dispositivo. Cuando se establece en **No configurado** (valor predeterminado), los usuarios pueden usar cuentas de Microsoft en el dispositivo.
- **Inicio de sesión remoto sin contraseña**: **habilite** esta opción para permitir que las cuentas locales con contraseñas en blanco puedan iniciar sesión con el teclado del dispositivo. **No configurado** (valor predeterminado) permite que las cuentas locales con contraseñas en blanco inicien sesión desde ubicaciones distintas al dispositivo físico.

#### <a name="admin"></a>Administración

- **Cuenta de administrador local**: **habilite** esta opción para permitir la cuenta de administrador local. Establézcalo en **No configurado** (valor predeterminado) para deshabilitar la cuenta de administrador local.
- **Cambiar nombre de la cuenta de administrador**: defina otro nombre de cuenta para asociarlo al identificador de seguridad (SID) de la cuenta de administrador.

#### <a name="guest"></a>Invitado

- **Cuenta de invitado**: **habilite** esta opción para permitir la cuenta de invitado local. Establézcalo en **No configurado** (valor predeterminado) para deshabilitar la cuenta de invitado local.
- **Cambiar nombre de cuenta de invitado**: defina un nombre de cuenta distinto para asociarlo al identificador de seguridad (SID) de la cuenta de invitado.

### <a name="devices"></a>Dispositivos

- **Desacoplar dispositivo sin iniciar sesión**: establezca esta opción en **Bloquear** para que los usuarios puedan presionar el botón de expulsión física de un dispositivo portátil acoplado para desacoplar el dispositivo de forma segura. **No configurado** (valor predeterminado) requiere que el usuario inicie sesión en el dispositivo y reciba permiso para desacoplar el dispositivo.
- **Instalar controladores de impresora para impresoras compartidas**: **habilite** esta opción para permitir que cualquier usuario pueda instalar un controlador de impresora como parte de la conexión a una impresora compartida. Cuando se establece en **No configurado** (valor predeterminado), solo los administradores pueden instalar un controlador de impresora como parte de la conexión a una impresora compartida.
- **Restringir el acceso al CD-ROM a un usuario activo local**: **habilite** esta opción para que solo el usuario que haya iniciado la sesión de forma interactiva puede usar los medios de CD-ROM. Si esta directiva está habilitada y nadie ha iniciado sesión, entonces se accede al CD-ROM a través de la red. Cuando se establece en **No configurado** (valor predeterminado), cualquier usuario tiene acceso al CD-ROM.
- **Formatear y expulsar medios extraíbles**: defina quién tiene permiso para formatear y expulsar medios extraíbles NTFS:
  - **No configurado**.
  - **Administradores**
  - **Administrators and Power Users** (Administradores y usuarios avanzados)
  - **Administrators and Interactive Users** (Administradores y usuarios interactivos)

### <a name="interactive-logon"></a>Inicio de sesión interactivo

- **Minutos de inactividad de la pantalla de bloqueo hasta que se activa el protector de pantalla**: escriba el número máximo de minutos de inactividad en la pantalla de inicio de sesión interactiva del escritorio hasta que se active el protector de pantalla.
- **Requerir CTRL+ALT+SUPR para iniciar sesión**: **habilite** esta opción para que los usuarios no tengan que presionar CTRL+ALT+SUPR para iniciar la sesión. Establézcalo en **No configurado** (valor predeterminado) para exigir que los usuarios presionen CTRL + ALT + SUPR antes de iniciar sesión en Windows.
- **Comportamiento de extracción de tarjeta inteligente**: determina lo que sucede cuando la tarjeta inteligente de un usuario que haya iniciado sesión se extrae del lector de tarjetas inteligentes. Las opciones son:

  - **Bloquear la estación de trabajo**: la estación de trabajo se bloquea cuando se quita la tarjeta inteligente. Esta opción permite a los usuarios abandonar el área, llevarse consigo su tarjeta inteligente y seguir manteniendo una sesión protegida.
  - **Forzar cierre de sesión**: se cierra automáticamente la sesión del usuario cuando se quita la tarjeta inteligente.
  - **Desconectar si es una sesión de Servicios de Escritorio remoto**: al extraer una tarjeta inteligente, se desconecta la sesión sin cerrar la del usuario. Esta opción permite al usuario insertar la tarjeta inteligente y reanudar la sesión más tarde o en otro equipo equipado con lector de tarjeta inteligente, sin necesidad de volver a iniciar la sesión. Si la sesión es local, esta directiva funciona de forma idéntica a Bloquear estación de trabajo.

    En [LocalPoliciesSecurity options](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) (Opciones de LocalPoliciesSecurity) se proporciona más información.

#### <a name="display"></a>Pantalla

- **Información del usuario al bloquearse la pantalla**: configure la información del usuario que se muestra cuando se bloquea la sesión. Si no se configura, se muestran el nombre de usuario, el dominio y el nombre para mostrar del usuario.
  - **No configurado**.
  - **Nombre para mostrar de usuario, dominio y nombre de usuario**
  - **User display name only** (Solo nombre para mostrar del usuario)
  - **Do not display user information** (No mostrar información del usuario)
- **Ocultar el último usuario que inició sesión**: **habilite** esta opción para ocultar el nombre de usuario. **No configurado** (valor predeterminado) muestra el nombre de usuario.
- **Ocultar el nombre de usuario al iniciar sesión**: **habilite** esta opción para ocultar el nombre de usuario. **No configurado** (valor predeterminado) muestra el nombre de usuario.
- **Título del mensaje de inicio de sesión**: establece el título del mensaje para los usuarios que inicien sesión.
- **Texto del mensaje de inicio de sesión**: establece el texto del mensaje para los usuarios que inicien sesión.

### <a name="network-access-and-security"></a>Seguridad y acceso a la red

- **Acceso anónimo a los recursos compartidos y las canalizaciones con nombre**: si se establece en **No configurado** (valor predeterminado), se restringe el acceso anónimo a la configuración de recursos compartidos y canalizaciones con nombre. Se aplica a la configuración a la que se puede acceder de forma anónima.
- **Enumeración anónima de cuentas SAM**: si se establece en **Permitir**, los usuarios anónimos podrán enumerar las cuentas SAM. Windows permite a los usuarios anónimos enumerar los nombres de las cuentas de dominio y de los recursos compartidos de red.
- **Enumeración anónima de recursos compartidos y cuentas SAM**: si se establece en **No configurado** (valor predeterminado), los usuarios anónimos pueden enumerar los nombres de los recursos compartidos de red y las cuentas de dominio. Para impedir la enumeración anónima de cuentas y recursos compartidos de SAM, ajuste esta opción en **Bloquear**.
- **Valor hash de LAN Manager almacenado al cambiar la contraseña**: en el próximo cambio de contraseña, seleccione la opción **Permitir** para que LAN Manager (LM) almacene el valor hash de la nueva contraseña. Cuando se establece en **No configurado** (valor predeterminado), no se almacena el valor hash.
- **Solicitudes de autenticación PKU2U**: establezca esta opción en **Bloquear** para impedir que las solicitudes de autenticación de PKU2U enviadas al dispositivo usen identidades en Internet. **No configurado**: esta opción predeterminada permite estas solicitudes.
- **Restringir las conexiones RPC remotas a SAM**: si establece esta opción en **Permitir**, la cadena predeterminada de lenguaje de definición de descriptores de seguridad impedirá que los usuarios y grupos realicen llamadas remotas a SAM. **No configurado**: esta opción predeterminada permite que la cadena predeterminada de lenguaje de definición de descriptor de seguridad permita a los usuarios y grupos realizar llamadas remotas a SAM.
  - **Descriptor de seguridad**

### <a name="recovery-console-and-shutdown"></a>Cierre y consola de recuperación

- **Borrar archivo de paginación de la memoria virtual al apagar**: **habilite** esta opción para borrar el archivo de paginación de la memoria virtual cuando se apague el dispositivo. **No configurado** no borra la memoria virtual.
- **Apagar sin inicio de sesión**: establezca esta opción en **Bloquear** para ocultar la opción de apagado en la pantalla de inicio de sesión de Windows. Los usuarios deben iniciar sesión en el dispositivo y, después, apagarlo. si se establece en **No configurado** (valor predeterminado), se permite que los usuarios apaguen el dispositivo desde la pantalla de inicio de sesión de Windows.

### <a name="user-account-control"></a>Control de cuentas de usuario

- **Integridad UIA sin ubicación segura**: **habilite** esta opción para que las aplicaciones en una ubicación segura del sistema de archivos solo se ejecuten con la integridad de UIAccess. **No configurado** (valor predeterminado) permite que las aplicaciones se ejecuten con integridad UIAccess, incluso si las aplicaciones no están en una ubicación segura del sistema de archivos.
- **Virtualizar errores de escritura para archivos y Registro de ubicaciones definidas por usuario**: establezca esta opción en **Bloquear** para que los errores de escritura de aplicaciones redirijan en tiempo de ejecución a ubicaciones definidas por el usuario en el sistema de archivos y el Registro. Cuando se establece en **No configurado** (valor predeterminado), las aplicaciones que escriben datos en ubicaciones protegidas devuelven un error.
- **Elevar solo los archivos ejecutables firmados y validados**: **habilite** esta opción para exigir la validación de la ruta de certificación de PKI de un archivo ejecutable antes de ejecutarlo. Establézcalo en **No configurado** (valor predeterminado) para no aplicar la validación de la ruta de certificación de PKI antes de que se pueda ejecutar un archivo ejecutable.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Configuración del comportamiento de petición de elevación de UIA

- **Petición de elevación para los administradores**: define el comportamiento de la petición de elevación para los administradores en Modo de aprobación de administrador:
  - **Elevar sin preguntar**
  - **Prompt for credentials on the secure desktop** (Pedir credenciales en el escritorio seguro)
  - **Prompt for consent on the secure desktop** (Pedir consentimiento en el escritorio seguro)
  - **Prompt for credentials** (Pedir credenciales)
  - **Prompt for consent** (Pedir consentimiento)
  - **No configurado**: Pedir consentimiento para binarios que no son de Windows
- **Petición de elevación para usuarios estándar**: permite definir el comportamiento de la petición de elevación para los usuarios estándar:
  - **Denegar solicitudes de elevación automáticamente**
  - **Prompt for credentials on the secure desktop** (Pedir credenciales en el escritorio seguro)
  - **No configurado**: Pedir credenciales
- **Enrutar peticiones de elevación al escritorio interactivo del usuario**: **habilite** esta opción para que todas las solicitudes de elevación de privilegios vayan al escritorio del usuario interactivo, no al escritorio seguro. Se usa cualquier configuración de directiva de comportamiento de petición para administradores y usuarios estándar. **No configurado**(valor predeterminado) obliga a que todas las solicitudes de elevación vayan al escritorio seguro independientemente de la configuración de la directiva de comportamiento de petición para administradores y usuarios estándar.
- **Petición con privilegios elevados para instalaciones de aplicaciones**: establezca esta opción en **Bloquear** para que los paquetes de instalación de aplicaciones no se detecten ni se solicite la confirmación de privilegios elevados. Si se establece en **No configurado** (valor predeterminado) y un paquete de instalación de aplicación necesita privilegios elevados, se pide al usuario el nombre de usuario y la contraseña del usuario administrativo.
- **Petición de elevación UIA sin escritorio seguro**: **habilite** esta opción para permitir que las aplicaciones de UIAccess pidan confirmación de elevación de permisos sin usar el escritorio seguro. Cuando se establece en **No configurado** (valor predeterminado), las peticiones de elevación usan un escritorio seguro.

#### <a name="admin-approval-mode-settings"></a>Configuración del Modo de aprobación de administrador

- **Modo de aprobación de administrador para la cuenta predefinida de administrador**: **habilite** esta opción para permitir que la cuenta predefinida de administrador use el modo de aprobación de administrador. Cualquier operación que requiera la elevación de privilegios solicita al usuario que apruebe la operación. **No configurado** (valor predeterminado) ejecuta todas las aplicaciones con privilegios completos de administrador.
- **Ejecutar todos los administradores en Modo de aprobación de administrador**: establezca esta opción en **Bloquear** para deshabilitar el modo de aprobación de administrador y todas las opciones de configuración de directiva de UAC relacionadas. **No configurado** (valor predeterminado) habilita el Modo de aprobación de administrador.

### <a name="microsoft-network-client"></a>Cliente de redes de Microsoft

- **Firmar digitalmente las comunicaciones (si el servidor lo permite)**: determina si el cliente de SMB negocia la firma de paquetes SMB. Cuando se establece en **No configurado** (valor predeterminado), el cliente de redes de Microsoft solicita al servidor que lleve a cabo la firma de paquetes SMB tras la configuración de la sesión. Si la firma de paquetes está habilitada en el servidor, esta se negocia. Si se establece en **Deshabilitar** (valor predeterminado), el cliente SMB nunca negocia la firma de paquetes SMB.
- **Enviar contraseña sin cifrar a servidores SMB de terceros**: **habilite** esta opción para que el redirector de Bloque de mensajes del servidor (SMB) pueda enviar contraseñas sin cifrar a servidores SMB que no sean de Microsoft no compatibles con el cifrado de contraseñas durante la autenticación. Cuando se establece en **No configurado** (valor predeterminado), las contraseñas están cifradas.

### <a name="microsoft-network-server"></a>Servidor de red de Microsoft

- **Firmar digitalmente las comunicaciones (si el cliente lo permite)**: determina si el servidor SMB negocia la firma de paquetes de SMB con los clientes que la solicitan. Cuando se establece en **Habilitar**, el servidor de red de Microsoft negocia la firma de paquetes SMB a petición del cliente. Es decir, si está habilitada la firma de paquetes en el cliente, esta se negocia. Cuando la opción es **No configurado** o está deshabilitada (valor predeterminado), el cliente SMB nunca negocia la firma de paquetes SMB.
- **Firmar digitalmente las comunicaciones (siempre)**: determina si el componente de servidor SMB exige la firma de paquetes. Cuando se establece en **Habilitar**, el servidor de red de Microsoft no se comunicará con un cliente de red de Microsoft a menos que este acepte la firma de paquetes SMB. Cuando se establece en **No configurado** o deshabilitado (valor predeterminado), la firma de paquetes SMB se negocia entre el cliente y el servidor.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

Configure las opciones de protección de los puntos de conexión en los dispositivos [macOS](endpoint-protection-macos.md).
