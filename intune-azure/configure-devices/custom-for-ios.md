---
title: "Configuración personalizada de Intune para dispositivos iOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca la configuración que puede usar en un perfil personalizado de iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6da8caa8-65c2-4f47-842f-9570dcb1ac22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: d8e6d0d641dd55c79442f68e7e97d21efcdad7fa
ms.lasthandoff: 02/16/2017


---

# <a name="microsoft-intune-custom-settings-for-ios-devices"></a>Configuración personalizada de Microsoft Intune para dispositivos iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use el perfil personalizado de iOS de Microsoft Intune para implementar la configuración que ha creado mediante la [herramienta Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) en dispositivos iOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en un perfil personalizado de iOS de Intune y asignar la configuración a usuarios y dispositivos de su organización.

Esta funcionalidad permite implementar la configuración de iOS que no se puede configurar con otros tipos de perfiles de Intune.


1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](how-to-configure-custom-settings.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), especifique lo siguiente:

- **Nombre del perfil de configuración personalizado**: proporcione un nombre para la directiva que se mostrará en el dispositivo y en los informes de estado de Intune.
- **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator.
Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de iOS en los dispositivos en los que implementa la directiva personalizada de iOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **Referencia de perfiles de configuración** y la **Referencia del protocolo de administración de dispositivos móviles** en el sitio web de [Apple Developer](https://developer.apple.com/).

El archivo importado se mostrará en el área de **contenido del archivo** de la hoja.
