---
title: Datos que JAMF Pro envía a Intune | Microsoft Intune
description: Lista de datos que Jamf Pro envía a Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 114a5c09ed99b5debe9a13692b8a5400c04382df
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833725"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Datos que Jamf Pro envía a Intune

Cuando se usa [Jamf Pro](https://www.jamf.com) para administrar los equipos Mac de los usuarios finales con Intune, Jamf Pro captura información de inventario sobre los dispositivos macOS administrados. Jamf Pro informa lo siguiente a Intune:

* Id. de Azure AD del dispositivo
* Estado del inventario JAMF (el estado de inventario de un equipo registrado con Jamf Pro en las últimas 24 horas)
* Versión del SO
* Id. de Azure AD del usuario
* Cifrado (FileVault 2)
* Estado del equipo selector
* Contraseña: número mínimo de conjuntos de caracteres
* Expiración de contraseña (días)
* Tipo de contraseña: simple, alfanumérico o desconocido
* Evitar inicio de sesión automático
* Longitud necesaria del código de acceso
* Contraseña: número de contraseñas anteriores para impedir su reutilización
* Protección de la integridad del sistema
* Hora de última comprobación
* Tipo de arquitectura
* Ranuras de RAM disponibles
* Capacidad de la batería
* ROM de arranque
* Velocidad de bus
* Tamaño de caché
* Nombre del dispositivo
* Unión al dominio
* Id. de Jamf
* Dirección MAC
* Marca
* Modelo
* Identificador de modelo
* Velocidad de NIC
* Número de núcleos
* Número de procesadores
* Sistema operativo
* Plataforma
* Velocidad del procesador
* Tipo de procesador
* Dirección MAC secundaria
* Número de serie
* Versión de SMC
* RAM total
* UDID
* Correo electrónico del usuario


Puede quitar un dispositivo administrado por Jamf de la consola de Intune si selecciona **Eliminar** en la vista **Todos los dispositivos**. La eliminación de dispositivos de forma masiva puede habilitarse si se seleccionan varios dispositivos y se hace clic en **Eliminar**.

Obtenga información sobre cómo [quitar un dispositivo administrado por Jamf en los documentos de Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). También puede presentar una incidencia de soporte técnico al [soporte técnico de Jamf](https://www.jamf.com/support/) para obtener más ayuda. 

