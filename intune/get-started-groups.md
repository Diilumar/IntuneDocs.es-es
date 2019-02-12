---
title: Crear un grupo en Microsoft Intune
titleSuffix: ''
description: Organice a los usuarios en grupos para administrar las directivas y las aplicaciones a las que pueden acceder con más facilidad.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b7e187bb182db0491e055ce3af3833d82e578de
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842412"
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>Crear un grupo para administrar los usuarios y el acceso a datos

Los grupos se usan para administrar los usuarios y controlar el acceso de los empleados a los recursos de la empresa. Estos recursos pueden formar parte de su directorio. También pueden ser recursos externos, como las aplicaciones de SaaS o los sitios de SharePoint.

Microsoft Intune usa Azure Active Directory (Azure AD) para administrar el acceso a los recursos de la empresa. Este acceso está controlado mediante roles en el directorio. Entonces Intune administra este acceso para los dispositivos móviles, que permite a los miembros de ese grupo tener acceso a los recursos.

## <a name="how-do-i-create-a-group"></a>¿Cómo se crea un grupo?

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Después de abrir el panel **Microsoft Intune**, seleccione **Grupos**.
4. En el panel **Usuarios y grupos: todos los grupos**, seleccione el comando **Nuevo grupo**.
5. En el panel **Grupo**, elija un **Tipo de grupo**.
5. Agregue un **Nombre** y una **Descripción** para el grupo.
6. Establezca el **Tipo de pertenencia** como **Asignado**. No **habilite las características de Office** para el grupo de prueba.
7. Seleccione **Miembros** para el grupo.
7. Haga clic en **Crear**.

Si ha creado correctamente un grupo, debe aparecer en la lista de **Todos los grupos**. Si no aparece ahí, pruebe a crear otro grupo.

## <a name="next-steps"></a>Pasos siguientes

[Introducción a las directivas](get-started-policies.md): cree directivas para evitar que los usuarios usen sus dispositivos de forma no autorizada.

## <a name="learn-more"></a>Obtener más información

* [Establecer restricciones de inscripción mediante grupos en Intune](groups-add.md)
* [Administrar el acceso a los recursos de la empresa mediante grupos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
