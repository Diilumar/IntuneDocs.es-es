---
title: "Definir los términos y condiciones en Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Establezca los términos y condiciones que los usuarios ven en el Portal de empresa de Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d53e91e24988d1bc71ff8df425f0d82e0fc43b58
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017

---

# <a name="ensure-users-accept-company-terms-for-access"></a>Garantía de que los usuarios acepten los términos de acceso de la empresa

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Como administrador de Intune, puede elegir requerir que los usuarios acepten los términos y condiciones de la empresa antes de que puedan usar el Portal de empresa para inscribir sus dispositivos y tener acceso a recursos de la empresa, como aplicaciones y correo electrónico. La configuración de términos y condiciones es opcional.

Puede crear varios conjuntos de términos y asignarlos a grupos distintos, como para admitir distintos lenguajes.

## <a name="create-terms-and-conditions"></a>Creación de términos y condiciones
Complete estos pasos para crear los términos y condiciones. El nombre para mostrar y la descripción son para uso administrativo mientras las propiedades de términos se muestran a los usuarios en el Portal de empresa.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja Intune, elija **Inscripción de dispositivos** y, luego, elija **Términos y condiciones**.

3. Seleccione **Crear**.
![Captura de pantalla del portal Intune que muestra el botón Crear para los términos y condiciones](media/terms-create-terms.png)

4. Especifique la información siguiente en la hoja de expansión:

   - **Nombre para mostrar**: nombre de los términos en el portal de Intune. Los usuarios no ven este nombre.

   - **Descripción**: detalles opcionales que le ayudan a identificar este conjunto de términos en el portal Intune.

5. Seleccione la flecha situada junto a Define terms of use (Definir términos de uso) para abrir la hoja Términos y condiciones y, luego, escriba la siguiente información:

   ![Captura de pantalla de la pantalla de aceptación de los Términos y condiciones por parte del usuario final, con un resumen de los términos](./media/terms-summary-create.png)

   - **Título**: título que ven los usuarios en el Portal de empresa.

   - **Resumen de los términos**: texto que explica lo que significa que los usuarios acepten los términos. Por ejemplo, "Al inscribir el dispositivo, acepta los términos de uso establecidos por Contoso. Lea los términos detenidamente antes de continuar".

   - **Términos y condiciones**: los términos y condiciones que los usuarios ven y deben aceptar o rechazar.

6. Seleccione **Aceptar** y, luego, **Crear**.

## <a name="assign-terms-and-conditions"></a>Asignación de los términos y condiciones

Puede asignar términos y condiciones a grupos de usuarios que deben aceptarlos antes de usar el Portal de empresa.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja Intune, elija **Inscripción de dispositivos** y, luego, elija **Términos y condiciones**.

3. En la lista de términos y condiciones, seleccione los términos que desea asignar y, luego, seleccione **Grupos asignados**.
![Captura de pantalla de la hoja Asignar grupo del portal Intune que muestra los botones Seleccionar grupo y Seleccionar para la asignación de términos y condiciones](media/terms-assign-groups.png)

4. Haga clic en el botón **Seleccionar grupo** y, en la hoja **Seleccionar grupos**, seleccione los grupos a los que desea asignar los términos y, luego, haga clic en **Seleccionar**.

5. En la hoja **Grupos asignados**, haga clic en **Guardar**.  Los términos y condiciones ahora están asociados a usuarios en los grupos seleccionados. La próxima vez que los usuarios accedan al portal de la empresa deberán aceptar los términos.

   ![Captura de pantalla de la pantalla de aceptación de los Términos y condiciones por parte del usuario final, con un resumen de los términos](./media/terms-summary-accept.png)

## <a name="monitor-a-terms-and-conditions"></a>Supervisión de términos y condiciones

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**. En la hoja Intune, elija **Inscripción de dispositivos** y, luego, elija **Términos y condiciones**.
2. En la lista de términos y condiciones, seleccione los términos para los que desea ver aceptación y, luego, seleccione **Estados de aceptación**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Trabajar con varias versiones de los términos y las condiciones
Puede editar los términos y condiciones y administrar sus versiones. Se recomienda aumentar el número de versión y exigir aceptación cada vez que realice cambios importantes en los términos y condiciones. Si va a corregir errores tipográficos o cambiar el formato, por ejemplo, mantenga el número de versión actual.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja Intune, elija **Inscripción de dispositivos**, elija **Términos y condiciones**, seleccione los términos y condiciones que desea modificar y, luego, seleccione **Propiedades**.

4. En la hoja **Propiedades**, seleccione **Términos y condiciones** y, luego, modifique el **título**, el **resumen de los términos** y los **términos y condiciones**, según corresponda. Si los cambios hechos hacen que los usuarios tengan que volver a aceptar los términos nuevos, haga clic en **Solicite a los usuarios que acepten de nuevo los términos e incremente el número de versión a** 

4.  Seleccione **Aceptar** y, luego, **Guardar**.
