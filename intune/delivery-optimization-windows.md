---
title: 'Configuración de Optimización de distribución para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Configure cómo las actualizaciones de software se distribuyen a sus dispositivos mediante los servicios en la nube de Optimización de distribución disponibles con dispositivos Windows 10 y versiones posteriores. En Intune, cree un perfil de configuración de dispositivos para instalar actualizaciones desde Internet. Consulte también cómo reemplazar los círculos de actualizaciones existentes con un perfil de Optimización de distribución.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a59cab5f709897e064b315193b292cb46dc2f2e
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831554"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Configuración de Optimización de distribución de Windows 10 (y versiones posteriores) en Microsoft Intune

> [!NOTE]
> **Actualizaciones de software: los círculos de actualizaciones de Windows 10** los reemplaza la configuración **Optimización de distribución**. Los círculos de actualizaciones existentes se pueden cambiar para usar la configuración **Optimización de distribución**. La sección [Traslado de los anillos de actualizaciones existentes a la optimización de distribución](#move-existing-update-rings-to-delivery-optimization) (en este artículo) enumera los pasos. 


Esta característica se aplica a la siguiente plataforma:

- Windows 10 y versiones posteriores

En este artículo se muestran y describen todas las opciones de Optimización de distribución que puede configurar para dispositivos Windows 10. Estos valores se agregan a un perfil de configuración de dispositivo y luego se asignan o implementan en los dispositivos mediante Microsoft Intune.

[Optimización de distribución de actualizaciones](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) es un gran recurso para aprender más sobre la optimización de distribución en Windows 10.

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Intune**.

2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.

3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione la plataforma:  

        - **Windows 10 y versiones posteriores**

    - **Tipo de perfil**: seleccione **Optimización de distribución**.
    - **Configuración**: elija cómo desea que las actualizaciones descargadas. Las opciones son: 

        - **No configurado**: los usuarios finales actualizan sus dispositivos con sus propios métodos, que pueden ser usar los valores de configuración **Actualizaciones de Windows** o **Optimización de distribución** disponibles con el sistema operativo.
        - **HTTP solo, sin emparejamiento**: obtenga actualizaciones solo de internet. No obtenga actualizaciones de otros equipos de la red (lo que se denomina emparejamiento o de punto a punto).
        - **HTTP combinado con el emparejamiento que se encuentra en la misma NAT**: obtenga actualizaciones de Internet y de otros equipos de la red. 
        - **HTTP combinado con el emparejamiento de un grupo privado**: El emparejamiento se produce en dispositivos del mismo sitio de Active Directory (si existe) o en el mismo dominio. Cuando se selecciona esta opción, el emparejamiento cruza sus direcciones IP de Traducción de direcciones de red (NAT).
        - **HTTP combinado con emparejamiento de Internet**: obtenga actualizaciones de Internet y de otros equipos de la red.
        - **Modo de descarga sencillo sin emparejamiento**: obtenga actualizaciones de Internet, directamente del propietario de la actualización, como Microsoft. No se pone en contacto con los servicios en la nube de Optimización de distribución.
        - **Modo de omisión**: use el Servicio de transferencia inteligente en segundo plano (BITS) para obtener actualizaciones. No use la optimización de distribución.

4. Cuando termine, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Traslado de los anillos de actualizaciones existentes a la optimización de distribución

**Actualizaciones de software: los círculos de actualizaciones de Windows 10** los reemplaza la configuración **Optimización de distribución**. Los círculos de actualizaciones existentes se pueden cambiar fácilmente para usar la configuración **Optimización de distribución**. Pasos:

1. Cree un perfil de configuración de optimización de distribución:

    1. En Intune, seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
    2. Escriba las propiedades siguientes:

        - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
        - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
        - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
        - **Tipo de perfil**: seleccione **Optimización de distribución**.
        - **Configuración**: En **Modo de descarga de Optimización de distribución**, elija el mismo modo usado por el círculo de actualizaciones de software existente. Las opciones son:
            - **No configurado**.
            - **HTTP solo, sin emparejamiento**
            - **HTTP combinado con el emparejamiento que se encuentra en la misma NAT** 
            - **HTTP combinado con el emparejamiento de un grupo privado**
            - **HTTP combinado con emparejamiento de Internet**
            - **Modo de descarga sencillo sin emparejamiento**
            - **Modo de omisión**

2. Asigne este perfil nuevo a los mismos dispositivos y usuarios que el círculo de actualizaciones de software existente. [Asignar el perfil](device-profile-assign.md) muestra los pasos.

3. Quite la configuración del círculo de actualizaciones de software existente:
    1. En Intune, vaya a **Actualizaciones de software** > Círculos de actualizaciones de Windows 10.
    2. En la lista, seleccione el círculo de actualizaciones.
    3. En la configuración, establezca **Modo de descarga de optimización de distribución** en **No configurado**.
    4. **Aceptar** > **Guardar** los cambios.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md) el estado.
