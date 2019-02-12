---
title: Asignación de aplicaciones a grupos en Microsoft Intune
titlesuffix: ''
description: Aprenda a asignar una aplicación de Intune a grupos de usuarios o dispositivos mediante Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ff89d1776d71dc24ea675de167f3fd22d6bdf04
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838774"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Asignación de aplicaciones a grupos con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Después de [agregar una aplicación](apps-add.md) a Microsoft Intune, puede asignarla a los usuarios y los dispositivos. Es importante que sepa que puede asignar una aplicación a un dispositivo tanto si el dispositivo está administrado por Intune como si no. 

> [!NOTE]
> No se admite el intento de implementación disponible para grupos de dispositivos; solo se admiten grupos de usuarios.

En esta tabla se muestran las diversas opciones para asignar aplicaciones a usuarios y dispositivos:

|   | Dispositivos inscritos en Intune | Dispositivos no inscritos en Intune |
|-------------------------------------------------------------------------------------------|------------------------------|----------------------------------|
| Asignar a usuarios | Sí | Sí |
| Asignar a dispositivos | Sí | No |
| Asignar aplicaciones encapsuladas o aplicaciones que incorporan el SDK de Intune (para directivas de protección de aplicaciones) | Sí | Sí |
| Asignar aplicaciones como disponibles | Sí | Sí |
| Asignar aplicaciones como obligatorias | Sí | No |
| Desinstalar aplicaciones | Sí | No |
| Recibir actualizaciones de aplicaciones de Intune | Sí | No |
| Los usuarios finales instalan las aplicaciones disponibles desde la aplicación Portal de empresa | Sí | No |
| Los usuarios finales instalan las aplicaciones disponibles desde el Portal de empresa basado en web | Sí | Sí |

> [!NOTE]
> Actualmente, puede asignar aplicaciones iOS y Android (tanto de línea de negocio como compradas en la tienda) a dispositivos que no estén inscritos en Intune.
>
> Para recibir actualizaciones de aplicaciones en dispositivos que no están inscritos en Intune, los usuarios de los dispositivos deben dirigirse al Portal de empresa de su organización e instalar manualmente las actualizaciones de aplicaciones.

## <a name="assign-an-app"></a>Asignación de una aplicación

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el menú **Intune**, seleccione **Aplicaciones cliente**.
4. En la sección **Administrar** del menú, seleccione **Aplicaciones**.
5. En el panel **Aplicaciones**, seleccione la aplicación que quiere asignar.
6. En la sección **Administrar** del menú, seleccione **Asignaciones**.
7. Seleccione **Agregar grupo** para abrir el panel **Agregar grupo** que está relacionado con la aplicación.
8. Para la aplicación específica, seleccione un **tipo de asignación**:
   - **Disponible para dispositivos inscritos**: se asigna la aplicación a grupos de usuarios que pueden instalar la aplicación desde la aplicación o el sitio web Portal de empresa.
   - **Disponible con o sin inscripción**: se asigna esta aplicación a grupos de usuarios cuyos dispositivos no se han inscrito en Intune. Se debe asignar a los usuarios una licencia de Intune; consulte [Licencias que incluyen Intune](licenses.md).
   - **Requerido**: la aplicación se instala en los dispositivos de los grupos seleccionados. Algunas plataformas pueden tener mensajes adicionales para el usuario final para confirmar antes de que comience la instalación de la aplicación.
   - **Desinstalar**: La aplicación se desinstala de los dispositivos de los grupos seleccionados si Intune ha instalado la aplicación anteriormente en el dispositivo a través de una asignación "Disponible para dispositivos inscritos" o "Requerido" utilizando la misma implementación. Los vínculos web no se puede quitar después de la implementación.

     > [!NOTE]
     > **Solo para aplicaciones iOS**: si ha creado un perfil de VPN para iOS que contiene la configuración de VPN por aplicación, puede seleccionarlo en **VPN**. Cuando se ejecuta la aplicación, se abre la conexión VPN. Para obtener más información, vea [Configuración de VPN para dispositivos iOS](vpn-settings-ios.md).
     >
     > **Solo para aplicaciones Android**: si implementa una aplicación Android como **Disponible con o sin inscripción**, el estado de notificación solo estará disponible en los dispositivos inscritos.

9. Para seleccionar los grupos de usuarios que resultan afectados por esta asignación de aplicaciones, seleccione **Grupos incluidos**.
10. Después de haber seleccionado uno o varios grupos para incluir, seleccione **Seleccionar**.
11. En el panel **Asignar**, seleccione **Aceptar** para completar la selección de grupos incluidos.
12. Si quiere excluir algún grupo de usuarios para que no se vea afectado por esta asignación de aplicaciones, seleccione **Excluir grupos**.
13. Si ha elegido excluir algún grupo, en **Seleccionar grupos**, seleccione **Seleccionar**.
14. En el panel **Agregar grupo**, seleccione **Aceptar**.
15. En el panel **Asignaciones** de la aplicación, seleccione **Guardar**.

La aplicación ahora se asigna a los grupos que ha seleccionado. Para obtener más información sobre cómo incluir y excluir asignaciones de aplicaciones, vea [Inclusión y exclusión de asignaciones de aplicaciones](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Cómo se resuelven los conflictos entre las intenciones de aplicación

A veces, la misma aplicación se asigna a varios grupos, pero con diferentes intenciones. La información de la tabla siguiente puede ayudarle a comprender la intención resultante cuando esto sucede:

| Intención del grupo 1 | Intención del grupo 2 | Intención resultante |
|-----------------------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Usuario Requerido|Usuario disponible|Requerido y Disponible|
|Usuario Requerido|Usuario no disponible|Requerido|
|Usuario Requerido|Desinstalar usuario|Requerido|
|Usuario disponible|Usuario no disponible|No disponible|
|Usuario disponible|Desinstalar usuario|Desinstalar|
|Usuario no disponible|Desinstalar usuario|Desinstalar
|Usuario Requerido|Dispositivo Requerido|Ambos existen, Intune trata los Requeridos
|Usuario Requerido|Desinstalar dispositivo|Ambos existen, Intune resuelve los Requeridos
|Usuario disponible|Dispositivo Requerido|Ambos existen, Intune resuelve los Requeridos (Requeridos y Disponibles)
|Usuario disponible|Desinstalar dispositivo|Ambos existen, Intune resuelve los Disponibles.<br><br>La aplicación se muestra en el Portal de empresa.<br><br>Si la aplicación ya está instalada (como una aplicación requerida con la intención anterior), entonces la aplicación se desinstala.<br><br>Si el usuario selecciona **Install from the Company Portal** (Instalar desde el Portal de empresa), la aplicación se instala y la intención de desinstalación no se respeta.|
|Usuario no disponible|Dispositivo Requerido|Requerido|
|Usuario no disponible|Desinstalar dispositivo|Desinstalar|
|Desinstalar usuario|Dispositivo Requerido|Ambos existen, Intune resuelve los Requeridos|
|Desinstalar usuario|Desinstalar dispositivo|Ambos existen, se necesita resolver Intune como Desinstalar|
|Dispositivo Requerido|Desinstalar dispositivo|Requerido|
|Usuario Requerido y Disponible|Usuario disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Desinstalar usuario|Requerido y Disponible|
|Usuario Requerido y Disponible|Usuario no disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Dispositivo Requerido|Ambas existen, Requeridas y Disponibles
|Usuario Requerido y Disponible|Dispositivo no disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Desinstalar dispositivo|Ambos existen, Intune resuelve los Requeridos (Requeridos y Disponibles)
|Usuario no disponible|Dispositivo no disponible|No disponible|
|Usuario disponible|Dispositivo no disponible|Available|
|Usuario Requerido|Dispositivo no disponible|Requerido|
|Usuario disponible sin inscripción|Usuario Requerido y Disponible|Requerido y Disponible
|Usuario disponible sin inscripción|Usuario Requerido|Requerido
|Usuario disponible sin inscripción|Usuario no disponible|No disponible
|Usuario disponible sin inscripción|Usuario disponible|Available|
|Usuario disponible sin inscripción|Dispositivo Requerido|Requerido y Disponible sin inscripción|
|Usuario disponible sin inscripción|Dispositivo no disponible|Disponible sin inscripción|
|Usuario disponible sin inscripción|Desinstalar dispositivo|Desinstalar y Disponible sin inscripción.<br><br>Si el usuario no ha instalado la aplicación desde el Portal de empresa, entonces se respeta la desinstalación.<br><br>Si el usuario instala la aplicación desde el Portal de empresa, entonces la instalación tiene prioridad sobre la desinstalación.|

> [!NOTE]
> Solo en el caso de aplicaciones administradas de la tienda de iOS, cuando agrega estas aplicaciones a Microsoft Intune y las asigna como **Requeridas**, se crean automáticamente con las intenciones **Requerida** y **Disponible**.<br><br>
> Las aplicaciones de la tienda de iOS (distintas de las aplicaciones VPP de iOS) que se asignan como destino con intención necesaria se aplicarán en el dispositivo en el momento del registro del dispositivo en el repositorio y también se mostrarán en la aplicación Portal de empresa.

## <a name="android-enterprise-app-we-app-deployment"></a>Implementación de aplicaciones APP-WE de Android Enterprise
En el caso de los dispositivos Android en un escenario de implementación de directiva de protección de aplicaciones sin inscripción (APP-WE) no inscrito, ahora puede usar Google Play administrado para implementar aplicaciones de la tienda y aplicaciones de LOB en los usuarios. En concreto, puede brindar a los usuarios finales un catálogo de aplicaciones y experiencia de instalación que ya no requiere que los usuarios finales flexibilicen la posición de seguridad de sus dispositivos al permitir instalaciones de orígenes desconocidos. Además, este escenario de implementación proporcionará una mejor experiencia del usuario final. Para consultar los pasos que debe seguir para asignar una aplicación, vea [Asignación de una aplicación](apps-deploy.md#assign-an-app).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la supervisión de las asignaciones de aplicaciones, consulte [Supervisión de las aplicaciones](apps-monitor.md).
