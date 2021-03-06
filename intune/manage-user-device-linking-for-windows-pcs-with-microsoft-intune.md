---
title: Administrar la vinculación de dispositivos de usuario en PC de Windows
titlesuffix: Microsoft Intune
description: Cómo vincular un usuario a un PC de Windows administrado por Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e74183236063b1f77084a5ae9384f07a618e237
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842140"
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>Administrar la vinculación de dispositivos de usuario en PC de Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

La información de este tema se aplica solo a equipos de escritorio de Windows que está administrando como PC mediante el cliente de software de Intune. 

Antes de implementar software en un usuario, debe vincular el usuario a un PC. Puede vincular un usuario a varios PC, pero cada PC puede vincularse solo a un usuario. Los usuarios se vinculan automáticamente a los PC que tengan inscritos en Intune a través del portal de empresa.

Para vincular un usuario a un PC:

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** (u otro grupo que contenga el PC que quiera vincular a un usuario).

2. Seleccione el PC que quiera vincular a un usuario y, después, elija **Vincular usuario**.

   El cuadro de diálogo **Vincular usuario** muestra una lista de usuarios disponibles con su nombre para mostrar, id. de usuario, y el número de PC a los que cada usuario está vinculado. Si un usuario ya está vinculado al PC seleccionado, el nombre del usuario y su id. se muestran en **Usuario actual**. Si el PC no está vinculado a ningún usuario, aparece **Ningún usuario** bajo **Usuario actual**.

3. Realice una de las siguientes acciones:

   - Para dejar el PC vinculado a su usuario actual (si lo hay), seleccione **Cancelar**.

   - Para quitar el vínculo al usuario actual, en el caso de que lo hubiera, seleccione <strong>Quitar vínculo **&gt;** Aceptar</strong>.

   - Para vincular el PC a un usuario nuevo, en la lista **Todos los usuarios**, seleccione un usuario. Confirme que los datos de usuario son correctos y, luego, seleccione **Aceptar**.

> [!TIP]
> Si quiere restringir la capacidad de los usuarios finales para vincularse a PC, habilite la opción **Restringir la capacidad de los usuarios de vincularse a equipos PC** en la directiva de **Configuración de agente de Microsoft Intune**.

### <a name="see-also"></a>Consulte también

[Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
