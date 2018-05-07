---
title: Uso de ATP de Windows Defender en Microsoft Intune - Azure | Microsoft Docs
description: Consulte cómo habilitar la Protección contra amenazas avanzada (ATP) de Windows Defender en un escenario de un extremo a otro, incluida la activación de ATP en Intune y el Centro de seguridad de Windows Defender (portal de ATP), incorporar dispositivos con un perfil de configuración de protección ATP, crear una directiva de configuración de cumplimiento de dispositivo de Intune, crear una directiva de acceso condicional de Azure AD y supervisar el cumplimiento de dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e99ed0bd1eb5bae90913aedba5973e5e1282f70
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2018
---
# <a name="enable-windows-defender-atp-with-conditional-access-in-intune"></a>Habilitación de ATP de Windows Defender con acceso condicional en Intune

La Protección contra amenazas avanzada (ATP) de Windows Defender y Microsoft Intune funcionan conjuntamente para ayudar a evitar infracciones de seguridad y limitar el impacto de dichas infracciones dentro de una organización.

Esta característica se aplica a los dispositivos Windows 10.

Por ejemplo, alguien envía datos adjuntos de Word con código malintencionado insertado a un usuario dentro de su organización. El usuario abre los datos adjuntos y habilita el contenido. Se inicia un ataque con privilegios elevados y un atacante desde una máquina remota tiene derechos de administrador al dispositivo de la víctima. Después, el atacante, accede remotamente a otros dispositivos del usuario.

Esta infracción de seguridad puede afectar a toda la organización.

ATP de Windows Defender puede resolver eventos de seguridad como el de este escenario. El Centro de seguridad de Windows Defender (consola ATP) informa que los dispositivos son de “alto riesgo” e incluye un informe detallado de una actividad sospechosa. En nuestro ejemplo, ATP de Windows Defender detecta que el dispositivo ejecutó código anómalo, experimentó un aumento de privilegios de proceso, inyectó código malintencionado y emitió un shell remoto sospechoso. Después, ATP de Windows Defender le ofrece opciones para mitigar la amenaza.

Mediante Intune, puede crear una directiva de cumplimiento que determine un nivel de riesgo aceptable. Si un dispositivo supera este riesgo, el dispositivo pasa a ser no compatible. Cuando se combina con el Acceso condicional de Azure Active Directory (AD), el usuario tiene el acceso bloqueado desde los recursos corporativos.

En este artículo se muestra cómo:

- Habilitar Intune en ATP y viceversa. Estas tareas crean una conexión de servicio a servicio entre Intune y ATP de Windows Defender. Esta conexión permite que ATP de Windows Defender escriba el riesgo de máquina para los dispositivos de Intune.
- Crear la directiva de cumplimiento en Intune.
- Habilitar el acceso condicional en Azure Active Directory (AD) en los dispositivos según su nivel de amenaza.

## <a name="prerequisites"></a>Requisitos previos

Para usar ATP con Intune, asegúrese de que tiene lo siguientes configurado y listo para usar:

- Inquilino con licencia para Enterprise Mobility + Security E5 y Windows E5 (o Microsoft 365 Enterprise E5)
- Entorno de Microsoft Intune, con dispositivos Windows 10 [administrados por Intune](windows-enroll.md) que también están unidos a Azure AD
- [ATP de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) y acceso al Centro de seguridad de Windows Defender (portal de ATP)

## <a name="enable-windows-defender-atp-in-intune"></a>Habilitación de ATP de Windows Defender en Intune

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Cumplimiento del dispositivo** > **ATP de Windows Defender** > **Open the Windows Defender Advanced Threat Protection admin console** (Abrir la consola de administración de Protección contra amenazas avanzada de Windows Defender).

    ![Texto alternativo](./media/atp-device-compliance-open-windows-defender.png)

4. En el **Centro de seguridad de Windows Defender**:
    1. Seleccione **Configuración** > **Características avanzadas**.
    2. Para **Microsoft Intune connection** (Conexión con Intune), elija **Activado**:

        ![Texto alternativo](./media/atp-security-center-intune-toggle.png)

    3. Seleccione **Guardar preferencias**.

5. Vuelva a Intune, **Cumplimiento del dispositivo** > **ATP de Windows Defender**. Establezca **Connect Windows 10.0.15063+ devices to Windows Defender Advanced Threat Protection** (Conectar dispositivos Windows 10.0.15063+ a Protección contra amenazas avanzada de Windows Defender) en **Activado**.
6. Seleccione **Guardar**.

Por lo general, esta tarea se realiza una vez. Por tanto, si ATP ya se ha habilitado en el recurso de Intune, no necesita hacerlo de nuevo.

## <a name="onboard-devices-using-a-configuration-profile"></a>Incorporación de dispositivos mediante un perfil de configuración

Windows Defender incluye un paquete de configuración incorporado que se instala en los dispositivos. Cuando se instala, el paquete se comunica con los [servicios de ATP de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) para examinar los archivos, detectar las amenazas e informar del riesgo a ATP de Windows Defender. Mediante Intune, puede crear un perfil de configuración que utilice este paquete de configuración. Después, asigne este perfil a los dispositivos que incorpora por primera vez.

Una vez incorporado un dispositivo mediante el paquete de configuración, no es necesario que vuelva a hacerlo. Suele ser una tarea que se hace una sola vez.

También puede incorporar dispositivos mediante una [directiva de grupo o System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection).

En los pasos siguientes se muestra cómo realizar las incorporaciones mediante Intune.

#### <a name="download-configuration-package"></a>Descarga de un paquete de configuración

1. En el [Centro de seguridad de Windows Defender](https://securitycenter.windows.com), seleccione **Configuración** > **Incorporación**.
2. Escriba los valores siguientes:
  - **Sistema operativo**: Windows 10
  - **Onboard a machine**(Incorporar una máquina) > **Método de implementación**: Administración de dispositivos móviles o Microsoft Intune
3. Seleccione **Descargar paquete** y guarde el archivo **WindowsDefenderATPOnboardingPackage.zip**. Extraiga el archivo.

Este archivo zip incluye **WindowsDefenderATP.onboarding**, que lo necesita en los pasos siguientes.

#### <a name="create-the-atp-configuration-profile"></a>Creación de un perfil de configuración de ATP

Este perfil usa el paquete de incorporación que descargó en el paso anterior.

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba la información que desee en **Nombre** y **Descripción**.
4. En **Plataforma**, seleccione **Windows 10 y versiones posteriores**.
5. En **Tipo de perfil**, seleccione **ATP de Windows Defender (Windows 10 Desktop)**.
6. Defina la configuración:

  - **Cargar paquete de configuración**: busque y seleccione el archivo **WindowsDefenderATP.onboarding** que ha descargado. Este archivo habilita una configuración de forma que los dispositivos pueden informar al servicio de ATP de Windows Defender.
  - **Uso compartido de muestras para todos los archivos**: permite recopilar muestras y compartirlas con ATP de Windows Defender. Por ejemplo, si ve un archivo sospechoso, puede enviarlo a ATP de Windows Defender para un análisis profundo.
  - **Frecuencia de informes de telemetría urgentes**: para los dispositivos que presentan un riesgo alto, habilite esta opción para informar de la telemetría al servicio de ATP de Windows Defender con más frecuencia.
  - **Descargar paquete de configuración**: si desea quitar, o "descargar" la supervisión de ATP de Windows Defender, puede descargar un paquete de descarga en el [Centro de seguridad de Windows Defender](https://securitycenter.windows.com) y agregarlo. De lo contrario, pase por alto esta propiedad.

    [Incorporar máquinas Windows 10 con System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) tiene más detalles sobre estas configuraciones de ATP de Windows Defender.

7. Seleccione **Aceptar** y **Crear** para guardar los cambios, lo que crea el perfil.

## <a name="create-the-compliance-policy"></a>Creación de la directiva de cumplimiento
La directiva de cumplimiento determina un nivel de riesgo aceptable en un dispositivo.

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Cumplimiento del dispositivo** > **Directivas** > **Crear directiva**.
3. Escriba la información que desee en **Nombre** y **Descripción**.
4. En **Plataforma**, seleccione **Windows 10 y versiones posteriores**.
5. En **Estado de dispositivos**, establezca **Requerir que el dispositivo tenga el nivel de amenaza del dispositivo** en el nivel que prefiera:

  - **Protegido**: este nivel es el más seguro. El dispositivo no puede tener ninguna amenaza existente y aún puede acceder a los recursos de la empresa. Si se encuentra alguna amenaza, el dispositivo se clasificará como no conforme.
  - **Bajo**: el dispositivo se evalúa como compatible si solo hay amenazas de nivel bajo. Los dispositivos con niveles de amenaza medio o alto no son compatibles.
  - **Medio**: el dispositivo se evalúa como compatible si las amenazas que se encuentran en él son de nivel bajo o medio. Si se detectan amenazas de nivel alto, se determinará que el dispositivo no es compatible.
  - **Alto**: este nivel es el menos seguro, ya que permite que todos los niveles de amenaza. Por tanto, los dispositivos con niveles de amenaza alto, medio o bajo se consideran compatibles.

6. Seleccione **Aceptar** y **Crear** para guardar los cambios (y crear la directiva).

## <a name="assign-the-policy"></a>Asignación de la directiva

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Cumplimiento del dispositivo** > **Directivas**> Seleccione la directiva de cumplimiento de ATP de Windows Defender.
3. Seleccione **Asignaciones**.
4. Incluya o excluya los grupos de Azure AD para asignarlos a la directiva.
5. Para implementar la directiva a los grupos, seleccione **Guardar**. Se evalúa el cumplimiento por parte de los dispositivos de usuario a los que se aplique la directiva.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Crear una directiva de acceso condicional de Azure AD
La directiva de acceso condicional bloquea el acceso a los recursos *s i* el dispositivo no es compatible. Por tanto, si un dispositivo supera el nivel de amenaza, puede bloquear el acceso a recursos corporativos, como SharePoint o Exchange Online.

1. En [Azure Portal](https://portal.azure.com), abra **Azure Active Directory** > **Acceso condicional** > **Nueva directiva**.
2. En **Nombre**, escriba un nombre de directiva y seleccione **Usuarios y grupos**. Utilice las opciones Incluir o Excluir para agregar los grupos para la directiva y seleccione **Listo**.
3. Seleccione **Aplicaciones en la nube** y elija las aplicaciones que desea proteger. Por ejemplo, elija **Seleccionar aplicaciones** y seleccione **Office 365 SharePoint Online** y **Office 365 Exchange Online**.

    Haga clic en **Listo** para guardar los cambios.

4. Seleccione **Condiciones** > **Aplicaciones cliente** para aplicar la directiva a las aplicaciones y los exploradores. Por ejemplo, seleccione **Sí** y habilite **Explorador** y **Aplicaciones móviles y aplicaciones de escritorio**.

    Haga clic en **Listo** para guardar los cambios.

5. Seleccione **Conceder** para aplicar el acceso condicional basado en el cumplimiento del dispositivo. Por ejemplo, seleccione **Conceder acceso** > **requieren que el dispositivo se marquen como compatibles**.

    Elija **Seleccionar** para guardar los cambios.

6. Seleccione **Habilitar directiva** y luego **crear** para guardar los cambios.

[¿Qué es el acceso condicional?](conditional-access.md) es un buen recurso.

## <a name="monitor-device-compliance"></a>Supervisión del cumplimiento del dispositivo
A continuación, supervise el estado de los dispositivos que tienen la directiva de cumplimiento de ATP de Windows Defender.

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Cumplimiento del dispositivo** > **Directiva y cumplimiento**.
3. Busque la directiva de ATP de Windows Defender en la lista y vea qué dispositivos son compatibles o no compatibles.

## <a name="more-good-stuff"></a>Más cosas interesantes
[Acceso condicional de ATP de Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Panel de riesgo de ATP de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md)  
[Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)