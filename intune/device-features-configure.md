---
title: Creación de perfiles de dispositivos iOS o Mac OS con Microsoft Intune - Azure |Microsoft Docs
description: Agregue o cree un perfil de dispositivo para iOS o macOS y después configure los valores de AirPrint, AirPlay, diseño de la pantalla principal, notificaciones de aplicaciones, dispositivo compartido, inicio de sesión único y configuración de filtro de contenido web en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2282ba4dd3caf8c71c8624884bc124393ea52d2f
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203100"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Agregar la configuración de características de dispositivos iOS o Mac OS en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Las características del dispositivo le permiten controlar una serie de opciones y características en los dispositivos iOS y Mac OS, como:

- Configuración de AirPrint y AirPlay
- Diseño de la pantalla principal
- Notificaciones de aplicaciones
- Mensaje de la pantalla de bloqueo
- Configuración del inicio de sesión único
- Filtrar el contenido web

En este artículo se muestran los conceptos básicos para configurar perfiles de características de dispositivos iOS. A continuación, puede consultar otros artículos para configurar valores específicos de la plataforma para los dispositivos.

## <a name="create-a-device-profile"></a>Creación del perfil de un dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
4. Escriba las propiedades siguientes:

   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
   - **Descripción**: escriba una descripción para el perfil. (Esta configuración es opcional, pero se recomienda aplicarla).
   - **Plataforma**: seleccione su tipo de plataforma:
     - **iOS**
     - **macOS**
   - **Tipo de perfil**: seleccione **Características del dispositivo**.
   - **Configuración**: los valores de configuración dependerán de la plataforma que seleccione. En los siguientes temas se describen los valores de cada tipo de perfil:

     - [Configuración de AirPrint para iOS y MacOS](air-print-settings-ios-macos.md)
     - [Configuración de AirPlay para iOS](airplay-settings-ios.md)
     - [Configuración de diseño de pantalla principal para iOS](home-screen-settings-ios.md)
     - [Configuración de notificaciones de aplicación para iOS](app-notification-settings-ios.md)
     - [Configuración del mensaje de la pantalla de bloqueo para iOS](shared-device-settings-ios.md)
     - [Configuración del inicio de sesión único de Intune para dispositivos iOS](sso-ios.md)
     - [Configuración de filtro de contenido web para iOS](web-content-filter-settings-ios.md)

5. Cuando haya terminado, seleccione **Aceptar**y elija **Crear** para guardar los cambios.

Se creará el perfil y aparecerá en la lista.

## <a name="next-step"></a>Paso siguiente

Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).