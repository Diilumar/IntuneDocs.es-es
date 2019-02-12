---
title: 'Configuración de directivas de actualización de software de iOS en Microsoft Intune: Azure | Microsoft Docs'
description: En Microsoft Intune, cree o agregue una directiva de configuración para restringir cuándo se instalan automáticamente las actualizaciones de software en los dispositivos iOS administrados o supervisados por Intune. Puede elegir la fecha y hora en la que no se instalarán las actualizaciones. También puede asignar esta directiva a grupos, usuarios o dispositivos y comprobar si hay errores de instalación.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
search.appverid: MET150
ms.openlocfilehash: d73dc96c966b93f26269cc53527a787824c94d3b
ms.sourcegitcommit: 00fe2b601e3becbe5d644fcbd35a706da3b43af2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652636"
---
# <a name="configure-ios-update-policies-in-intune"></a>Configuración de directivas de actualización de iOS en Intune

Las directivas de actualización de software permiten forzar a los dispositivos iOS supervisados a instalar automáticamente la actualización de sistema operativo más reciente disponible. Esta característica solo está disponible en los dispositivos supervisados. Al configurar una directiva, puede agregar las horas y los días en los que no quiere que los dispositivos instalen una actualización. 

El dispositivo se registra con Intune aproximadamente cada ocho horas. Si hay una actualización disponible, fuera de un período restringido, el dispositivo descarga e instala la actualización de sistema operativo más reciente. No se necesita ninguna interacción del usuario para actualizar el dispositivo. La directiva no impide que un usuario actualice el sistema operativo de forma manual.

Esta característica es compatible con dispositivos que ejecutan iOS 10.3 y versiones posteriores. La configuración del retardo está disponible en iOS 11.3 y versiones posteriores.

## <a name="configure-the-policy"></a>Configurar la directiva
1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Actualizaciones de software** > **Directivas de actualización para iOS** > **Crear**.
4. Escriba un nombre y una descripción para la directiva.
5. Haga clic en **Configuración**. 

    Escriba los detalles para cuándo los dispositivos iOS no están obligados a instalar las actualizaciones más recientes. Esta configuración crea un período de tiempo restringido. Puede configurar los **días** de la semana, la **zona horaria**, la **hora de inicio**, la **hora de finalización**  y si se **retrasa la visibilidad de actualizaciones de software (días)** para escribir usuarios. Puede seleccionar un intervalo de retraso de actualizaciones de software de 1 a 90 días. Cuando el retraso expire, los usuarios recibirán una notificación para actualizar a la versión más antigua del sistema operativo que estaba disponible cuando se desencadenó el retraso. Para no participar en la configuración de un retraso de la actualización de software, escriba 0. Estas actualizaciones de configuración solo se aplicarán a los dispositivos iOS supervisados.
  
    Por ejemplo, si iOS 12.a está disponible el **1 de enero** y tiene **Delay OS Updates** (Retrasar actualizaciones del SO) establecido en **5 días**, esa versión no aparecerá como una actualización disponible en el dispositivo de ningún usuario final asignado a ese perfil. El **sexto día** después de la publicación, esa actualización aparecerá como disponible y todos los usuarios finales podrán iniciarla.


6. Haga clic en **Aceptar** para guardar los cambios. Haga clic en **Crear** para crear la directiva.

El perfil se crea y se muestra en la lista de directivas. MDM de Apple no permite forzar a un dispositivo a instalar las actualizaciones en una hora o fecha determinada. 

## <a name="change-the-restricted-times-for-the-policy"></a>Cambio de los períodos restringidos de la directiva

1. En **Actualizaciones de Software**, seleccione **Directivas de actualización para iOS**.
2. Elija una directiva existente > **Propiedades**.
3. Actualice la hora restringida:
    
    1. Seleccione los días de la semana.
    2. Elija la zona horaria en la que se aplica esta directiva.
    3. Escriba la hora de inicio y de finalización de las horas incluidas en la lista de bloqueados.

    > [!NOTE]
    > Si **Hora de inicio** y **Hora de finalización** están establecidas en las 12 a.m., se desactiva la comprobación de la hora de mantenimiento.

## <a name="assign-the-policy-to-users"></a>Asignar la directiva a los usuarios

Las directivas existentes se asignan a grupos, usuarios o dispositivos. Cuando se asigna, la directiva se aplica.

1. En **Actualizaciones de Software**, seleccione **Directivas de actualización para iOS**.
2. Elija una directiva existente > **Asignaciones**. 
3. Seleccione los grupos, usuarios o dispositivos de Azure Active Directory que se van a incluir o excluir de la directiva.
4. Haga clic en **Guardar** para implementar la directiva en los usuarios.

Se evalúa la comprobación de actualizaciones por parte de los dispositivos usados por los usuarios a los que se destina la directiva. Esta directiva también es compatible con los dispositivos sin usuario.

## <a name="monitor-device-installation-failures"></a>Supervisión de errores de instalación de dispositivos
En <!-- 1352223 -->
**Actualizaciones de software** > **Errores de instalación para dispositivos iOS** se muestra una lista de los dispositivos iOS supervisados a los que se destina una directiva de actualización, que han intentado una actualización y que no se pudieron actualizar. Para cada dispositivo, puede ver el estado por el que el dispositivo no se ha actualizado automáticamente. Los dispositivos actualizados y que estén en buen estado no se muestran en la lista. Los dispositivos "actualizados" incluyen la actualización más reciente que el propio dispositivo puede admitir.

