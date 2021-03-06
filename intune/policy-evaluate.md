---
title: Determinación de cuántos usuarios se rigen por una directiva
titlesuffix: Microsoft Intune
description: Determinación de cuántos usuarios se rigen por una directiva
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38e8a2e2-2329-11e8-b467-0ed5f89f718b
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b059d3512576faaa6049bd2c91be9e94ff919058
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55844316"
---
# <a name="evaluate-how-many-users-are-targeted-by-a-policy"></a>Evaluación de cuántos usuarios se rigen por una directiva
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Puede usar el botón **Evaluar** para averiguar cuántos usuarios se rigen por una directiva de cumplimiento de dispositivos o de configuración del dispositivo. Esta característica solamente calcula los usuarios, no los dispositivos.

1.  En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Cumplimiento del dispositivo** o **Configuración del dispositivo** y, después, seleccione **Directivas**.
2.  Elija una de las directivas, o bien cree una y después elija **Asignaciones**.
3.  Haga clic en **Evaluar**. Aparece un mensaje en el que se muestra el número de usuarios a los que se aplica esta directiva.

Si el botón **Evaluar** está atenuado, asegúrese de que la directiva se ha asignado a uno o más grupos.

