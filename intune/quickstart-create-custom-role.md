---
title: 'Inicio rápido: Crear y asignar un rol personalizado en Intune'
description: 'Inicio rápido: Crear y asignar un rol personalizado para un administrador de dispositivos remoto.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: 5de108835254d6a65546b8f1c9e8d0e9c32dbd26
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189935"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>Inicio rápido: Crear y asignar un rol personalizado

En este inicio rápido de Intune, creará un rol personalizado con permisos específicos para un departamento de operaciones de seguridad. Después, asignará el rol a un grupo de operadores de este tipo. Hay varios roles predeterminados que puede usar de inmediato. Pero al crear roles personalizados como este, tendrá control de acceso preciso a todas las partes del sistema de administración de dispositivos móviles.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos

- Para completar este inicio rápido, debe [crear un grupo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune.

## <a name="create-a-custom-role"></a>Crear un rol personalizado

Cuando se crea un rol personalizado, se pueden establecer permisos para una amplia gama de acciones. Para el rol de operaciones de seguridad, estableceremos algunos permisos de lectura para que el operador pueda revisar las configuraciones y las directivas de un dispositivo.

1. En Intune, elija **Roles** > **Todos los roles** > **Agregar**.
![Explorador](media/quickstart-create-custom-role/add-custom-role.png)
2. En **Agregar rol personalizado**, en el cuadro **Nombre**, escriba *Operaciones de seguridad*.
3. En el cuadro **Descripción**, escriba *Este rol permite a un operador de seguridad supervisar la configuración del dispositivo y la información de cumplimiento.*
4. Elija **Configurar** > **Identificadores de dispositivo corporativos** > **Sí** junto a **Lectura** > **Aceptar**.
![Explorador](media/quickstart-create-custom-role/corp-device-id-read.png)
5. Elija **Todas las directivas de cumplimiento de los dispositivos** > **Sí** junto a **Lectura** > **Aceptar**.
6. Elija **Configuraciones de dispositivos** > **Sí** junto a **Lectura** > **Aceptar**.
7. Elija **Organización** > **Sí** junto a **Lectura** > **Aceptar**.
8. Elija **Aceptar** > **Crear**.

## <a name="assign-the-role-to-a-group"></a>Asignar el rol a un grupo

Para que el operador de seguridad pueda usar los nuevos permisos, debe asignar el rol a un grupo que contenga el usuario de seguridad.

1. En Intune, elija **Roles** > **Todos los roles** > **Security operations** (Operaciones de seguridad).
2. En **Roles de Intune**, elija **Asignaciones** > **Asignar**.
3. En el cuadro **Nombre de asignación**, escriba *Oper. seg.*
4. Elija **Miembros (grupos)** > **Agregar**.
5. Elija el grupo **Contoso Testers** (Evaluadores de Contoso).
6. Elija **Seleccionar** > **Aceptar**.
7. Elija **Ámbito (grupos)** > **Seleccionar grupos para incluir** > **Contoso Testers** (Evaluadores de Contoso).
8. Elija **Seleccionar** > **Aceptar** > **Aceptar**.

Ahora, todos los miembros del grupo pertenecen al rol *Operaciones de seguridad* y pueden revisar esta información sobre un dispositivo: identificadores de dispositivos corporativos, directivas de cumplimiento de dispositivos, configuraciones de dispositivo e información de organización.

## <a name="clean-up-resources"></a>Limpieza de recursos

Si ya no quiere usar más el nuevo rol personalizado, puede eliminarlo. Elija **Roles** > **Todos los roles** > elija el botón de puntos suspensivos junto al rol > **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial ha creado un rol de operaciones de seguridad personalizado y lo ha asignado a un grupo. Para obtener más información sobre los roles de Intune, consulte [Control de administración basada en roles (RBAC) con Microsoft Intune](role-based-access-control.md)

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Crear un perfil de dispositivo de correo para iOS](quickstart-email-profile.md)
