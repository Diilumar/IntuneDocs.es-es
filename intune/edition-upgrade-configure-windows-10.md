---
title: 'Actualización o uso del modo S en dispositivos Windows 10: Microsoft Intune (Azure) | Microsoft Docs'
description: Use Microsoft Intune para actualizar los dispositivos de Windows 10 a una edición diferente o habilite el modo S. Los administradores pueden usar un perfil de configuración de dispositivo para actualizar Windows 10 Professional a Windows 10 Enterprise y habilitar o desactivar el modo S. Consulte las rutas de actualización admitidas para Windows 10 Pro, N, Education, Cloud, Enterprise, Core, Holographic y Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1539a1c373126df13ed3e951bb0d4ecae728fd3
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851498"
---
# <a name="upgrade-windows-10-editions-or-enable-s-mode-on-devices-using-microsoft-intune"></a>Actualización de las ediciones de Windows 10 o habilitación del modo de S en dispositivos con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como parte de su solución de administración de dispositivos móviles (MDM), puede que le interese actualizar sus dispositivos Windows 10. Por ejemplo, puede actualizar los dispositivos Windows 10 Professional a Windows 10 Enterprise. O bien, puede habilitar el modo S para que los dispositivos solo ejecuten aplicaciones de Microsoft Store.

El [modo Windows 10 S](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) está diseñado por motivos de seguridad y rendimiento. Si los dispositivos solo ejecutan aplicaciones de Microsoft Store, puede usar el modo S para ayudar a proteger los dispositivos. Si los dispositivos usan aplicaciones que no están disponibles en Microsoft Store, salga del modo S. Solo se puede salir una vez del modo S. Una vez que salga de él, no podrá volver al modo Windows 10 S.

Esta característica se aplica a:

- Windows 10 y versiones posteriores
- Windows 10 1809 o posterior para el modo S
- Windows Holographic for Business

Estas características están disponibles en Intune y el administrador puede configurarlas. Intune usa "perfiles de configuración" para crear y personalizar estas configuraciones para las necesidades de su organización. Después de agregar estas características en un perfil, puede insertar o implementar el perfil en dispositivos Windows 10 de su organización. Al implementar el perfil, Intune habilita el modo S o actualiza los dispositivos automáticamente.

En este artículo se enumeran las rutas de actualización admitidas y se muestra cómo crear el perfil de configuración de dispositivo. También puede ver toda la actualización disponible y la configuración del modo S para [Windows 10](edition-upgrade-windows-settings.md).

> [!NOTE]
> Si después quita la asignación de directiva, la versión de Windows en el dispositivo no se revierte. El dispositivo sigue funcionando con normalidad.

## <a name="prerequisites"></a>Requisitos previos

Antes de actualizar los dispositivos, asegúrese de que se cumplen los siguientes requisitos previos:

- Tener una clave de producto válida para instalar la versión actualizada de Windows en todos los dispositivos de destino de la directiva (para ediciones de Windows 10 Desktop). Puede utilizar las claves de las claves de activación múltiple (MAK) o el servidor de administración de claves (KMS).
- Para las ediciones de Windows 10 Mobile y Windows 10 Holographic, puede usar un archivo de licencia de Microsoft. El archivo de licencia incluye la información de licencia para instalar la edición actualizada en todos los dispositivos de destino con la directiva.
- Los dispositivos Windows 10 a los que asigna la directiva están inscritos en Microsoft Intune. No puede usar la directiva de actualización de edición con equipos que ejecutan el software cliente de PC de Intune.

## <a name="supported-upgrade-paths"></a>Rutas de actualización compatibles

En la siguiente tabla, se muestran las rutas de actualización admitidas para el perfil de actualización de edición de Windows 10.

| Actualización de | Actualización a |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Edición Windows 10 Pro N | Edición Windows 10 Education N <br/>Edición Windows 10 Enterprise N <br/>Edición Windows 10 Pro Education N | 
| Windows 10 Pro Education | Windows 10 Education | 
| Edición Windows 10 Pro Education N | Edición Windows 10 Education N |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Edición Windows 10 Cloud N | Edición Windows 10 Education N <br/>Edición Windows 10 Enterprise N <br/>Edición Windows 10 Pro N <br/>Edición Windows 10 Pro Education N | 
| Windows 10 Enterprise | Windows 10 Education | 
| Edición Windows 10 Enterprise N | Edición Windows 10 Education N | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Edición Windows 10 Core N | Edición Windows 10 Education N <br/>Edición Windows 10 Enterprise N <br/>Edición Windows 10 Pro Education N | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Por ejemplo, escriba algo parecido a `Windows 10 edition upgrade profile` o `Windows 10 switch off S mode`.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione la plataforma:  

        - **Windows 10 y versiones posteriores**

    - **Tipo de perfil**: seleccione **Actualización de edición**.
    - **Configuración**: especifique la configuración que desee definir. Para una lista de todas las configuraciones, y lo que hacen, consulte:

        - [Actualización de Windows 10 y el modo S](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. Seleccione **Aceptar** > **Crear** para guardar los cambios. 

El perfil se crea y se muestra en la lista. Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

## <a name="next-steps"></a>Pasos siguientes

Una vez creado el perfil, está listo para asignarlo. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Vea la configuración de la actualización y del modo S para dispositivos [Windows 10](edition-upgrade-windows-settings.md) y [Windows Holographic for Business](holographic-upgrade.md).
