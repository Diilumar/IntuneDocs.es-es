---
# required metadata

title: Solucionar problemas de Endpoint Protection | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Troubleshoot Endpoint Protection in Microsoft Intune

Use la información de esta sección como ayuda para resolver los problemas que se producen al usar Microsoft Intune Endpoint Protection.

Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.


### Mensajes de error de Endpoint Protection
En esta sección se describen las posibles causas y soluciones de los siguientes errores y advertencias que aparecen en el panel **Estado de Endpoint Protection** de la [consola de administración de Intune](https://manage.microsoft.com)..

|Elemento de estado|Posibles causas|Posibles soluciones|
|---------------|--------------------|-----------------------|
|**Motor de Endpoint Protection no disponible**|El motor de Intune Endpoint Protection se ha dañado o eliminado.|Si el motor de Intune Endpoint Protection se ha dañado, puede intentar actualizar o reinstalar el software.<br /><br />Para forzar una actualización inmediata, haga clic en **Actualizar** en el software cliente de Endpoint Protection (se encuentra en la barra de tareas de los equipos administrados).<br /><br />Si no se puede actualizar, deberá reinstalar el motor de Endpoint Protection.<br /><br />En la lista de programas instalados, en el Panel de control del equipo administrado, localice **Agente de Microsoft Intune Endpoint Protection** y desinstale la aplicación.<br /><br />Durante la próxima sincronización de actualización, el Administrador de actualizaciones de Microsoft Online Management detectará el programa que falta y lo reinstalará a la hora de instalación programada.|
|**Endpoint Protection deshabilitado**|Intune Endpoint Protection deshabilitado por un administrador mediante una directiva o por el usuario en un equipo administrado.|Si Endpoint Protection está deshabilitado, puede habilitarlo desde la [consola de administración de Intune](https://manage.microsoft.com) o desde un equipo administrado. Realice una de las siguientes acciones:<br /><br />Para habilitar Endpoint Protection desde la [consola de administración de Intune](https://manage.microsoft.com), abra el área de trabajo **Directiva** y cambie la configuración de **Habilitar Endpoint Protection** en las directivas que se aplican a este equipo.<br /><br />O bien<br /><br />Para habilitar Endpoint Protection desde un equipo administrado, inicie el cliente de Intune Endpoint Protection en el área de notificación y se le pedirá que habilite Endpoint Protection.|
|**Protección en tiempo real deshabilitada**|Protección en tiempo real deshabilitada por un administrador (mediante una directiva) o por el usuario en un equipo administrado.|Si la protección en tiempo real está deshabilita, puede habilitarla desde la [consola de administración de Intune](https://manage.microsoft.com) o desde un equipo administrado. Realice una de las siguientes acciones:<br /><br />Para habilitar la protección en tiempo real desde la [consola de administración de Intune](https://manage.microsoft.com), abra el área de trabajo **Directiva** y cambie la configuración de **Habilitar protección en tiempo real** a **Sí** en las directivas que se aplican al equipo.<br /><br />O bien<br /><br />Para habilitar la protección en tiempo real desde un equipo administrado, inicie el software cliente de Endpoint Protection desde el área de notificación. En ese momento se le solicita que habilite la protección en tiempo real.|
|**Examen de descargas deshabilitado**|El examen de descargas ha sido deshabilitado por un administrador mediante el uso de una directiva o por un usuario en un equipo administrado.|Si el examen de descargas está deshabilitado, puede habilitarlo desde la [consola de administración de Intune](https://manage.microsoft.com) o desde un equipo administrado. Realice una de las siguientes acciones:<br /><br />Para habilitar el examen de descargas desde la [consola de administración de Intune](https://manage.microsoft.com), abra el área de trabajo **Directiva** y cambie la configuración de **Examinar todas las descargas** a **Sí** en las directivas que se aplican al equipo.<br /><br />O bien<br /><br />Para habilitar el examen de descargas desde un equipo administrado, inicie el software cliente de Endpoint Protection desde el área de notificación. Haga clic en la ficha **Configuración**, haga clic en **Protección en tiempo real**, active la casilla **Examinar todas las descargas** y haga clic en **Guardar cambios**..|
|**Supervisión de actividad de archivos y programas deshabilitada**|La supervisión de la actividad de archivos y programas fue deshabilitada por un administrador mediante el uso de una directiva o por un usuario en un equipo administrado.|Si la supervisión de la actividad de archivos y programas está deshabilitada, puede habilitarla desde la [consola de administración de Intune](https://manage.microsoft.com) o desde un equipo administrado. Realice una de las siguientes acciones:<br /><br />Para habilitar la supervisión de la actividad de archivos y programas desde la [consola de administración de Intune](https://manage.microsoft.com), abra el área de trabajo **Directiva** y cambie la configuración de **Supervisar la actividad de archivos y programas en los equipos** a **Sí** en las directivas aplicables al equipo.<br /><br />O bien<br /><br />Para habilitar la supervisión de la actividad de archivos y programas desde un equipo administrado, inicie el software cliente de Endpoint Protection desde el área de notificación. Haga clic en la ficha **Configuración**, haga clic en **Protección en tiempo real**, active la casilla **Supervisar la actividad de archivos y programas en el equipo** y haga clic en **Guardar cambios**..|
|**Supervisión de comportamiento deshabilitada**|Supervisión del comportamiento deshabilitada por un administrador (mediante una directiva) o por un usuario en un equipo administrado.|Si la supervisión del comportamiento está deshabilitada, puede habilitarla desde la [consola de administración de Intune](https://manage.microsoft.com) o desde un equipo administrado. Realice una de las siguientes acciones:<br /><br />Para habilitar la supervisión del comportamiento desde la [consola de administración de Intune](https://manage.microsoft.com), abra el área de trabajo **Directiva**, cambie la configuración de **Habilitar supervisión del comportamiento** a **Sí** en las directivas que se aplican a este equipo y reinicie el equipo administrado.<br /><br />O bien<br /><br />Para habilitar la supervisión del comportamiento desde un equipo administrado, inicie el software cliente de Endpoint Protection desde el área de notificación. Haga clic en la ficha **Configuración**, haga clic en **Protección en tiempo real**, active la casilla **Habilitar supervisión del comportamiento** y, a continuación, haga clic en **Guardar cambios**. A continuación, reinicie el equipo.|
|**Análisis de scripts deshabilitado**|Exploración de scripts deshabilitada por un administrador (mediante una directiva) o por un usuario en un equipo administrado.|Si la exploración de scripts está deshabilitada, puede habilitarla desde la [consola de administración de Intune](https://manage.microsoft.com) o desde un equipo administrado. Realice una de las siguientes acciones:<br /><br />Para habilitar la exploración de scripts desde la [consola de administración de Intune](https://manage.microsoft.com), abra el área de trabajo **Directiva** y cambie la configuración de **Habilitar exploración de scripts** a **Sí** en las directivas que se aplican a este equipo.<br /><br />O bien<br /><br />Para habilitar la exploración de scripts desde un equipo administrado, inicie el software cliente de Endpoint Protection desde el área de notificación. Haga clic en la pestaña **Configuración**, haga clic en **Protección en tiempo real**, active la casilla **Habilitar exploración de scripts** y haga clic en **Guardar cambios**..|
|**Sistema de inspección de red deshabilitado**|El sistema de inspección de red ha sido deshabilitado por un administrador mediante el uso de una directiva o por el usuario en un equipo administrado.|Si el Sistema de inspección de red está deshabilitado, puede habilitarlo desde la [consola de administración de Intune](https://manage.microsoft.com) o desde un equipo administrado. Realice una de las siguientes acciones:<br /><br />Para habilitar el Sistema de inspección de red desde la [consola de administración de Intune](https://manage.microsoft.com), abra el área de trabajo **Directiva**, cambie la configuración de **Habilitar Sistema de inspección de red** a **Sí** en las directivas que se aplican a este equipo y reinicie el equipo administrado.<br /><br />O bien<br /><br />Para habilitar el Sistema de inspección de red desde un equipo administrado, inicie el software cliente de Endpoint Protection desde el área de notificación. Haga clic en la ficha **Configuración**, haga clic en **Protección en tiempo real**, active la casilla **Habilitar Sistema de inspección de red** y, a continuación, haga clic en **Guardar cambios**. Reinicie el equipo.|
|**Definiciones de malware desactualizadas**|Puede que el equipo haya permanecido desconectado de Internet durante un período prolongado de tiempo y que sus definiciones de malware no hayan sido actualizadas aún. Este estado aparece cuando las definiciones de malware del equipo no se han actualizado como mínimo desde hace 14 días.|Si las definiciones de malware no están actualizadas, puede actualizarlas desde la [consola de administración de Intune](https://manage.microsoft.com) o desde el equipo administrado.<br /><br />Para más información, vea el tema [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune).|
|**Examen completo vencido**|No se ha completado un examen completo en los últimos 14 días. Esto puede deberse a un reinicio del equipo durante un examen completo.|Si una exploración completa vence, puede ejecutar una exploración completa única o programar exploraciones completas periódicas desde la [consola de administración de Intune](https://manage.microsoft.com) mediante la información del tema [Common Windows PC management tasks with the Microsoft Intune computer client](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client) (Tareas comunes de administración de equipos Windows con el cliente de equipo de Microsoft Intune)..|
|**Examen rápido vencido**|No se ha completado un examen rápido en los últimos 14 días. Esto puede deberse a un reinicio durante un examen rápido.|Si un examen rápido vence, puede ejecutar un examen rápido único o programar exámenes rápidos periódicos desde la [consola de administración de Intune](https://manage.microsoft.com) mediante la información del tema [Common Windows PC management tasks with the Microsoft Intune computer client](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client) (Tareas comunes de administración de equipos Windows con el cliente de equipo de Microsoft Intune)..|
|**Otra aplicación de protección de extremos en ejecución**|Se está ejecutando otra aplicación de protección de extremos y el equipo está en buenas condiciones.|De manera predeterminada, si hay otra aplicación de protección de extremos instalada e Intune detecta esa aplicación, Endpoint Protection se deshabilita a sí mismo automáticamente. Si Intune no detecta la otra aplicación de extremos, Endpoint Protection permanecerá habilitado. Para más información, vea [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune)..|

### Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune)..


<!--HONumber=May16_HO1-->

