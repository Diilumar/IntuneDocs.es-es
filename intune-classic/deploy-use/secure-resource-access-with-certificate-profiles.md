---
title: Perfiles de certificado para el acceso a los recursos | Microsoft Docs
description: "Proteja VPN, Wi-Fi y el acceso al correo electrónico con un certificado instalado en cada dispositivo de usuario."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3dd6e5971d084773640c577cace43c2f011dbb69
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="secure-resource-access-with-certificate-profiles-in-microsoft-intune"></a>Secure resource access with certificate profiles in Microsoft Intune (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Si proporciona a los usuarios acceso a los recursos corporativos a través de VPN, Wi-Fi o perfiles de correo electrónico, tiene la opción de protegerlo con un certificado instalado en el dispositivo de cada usuario. Funciona de la siguiente manera:

1. Asegúrese de disponer de la infraestructura de certificados correcta, como se explica en [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) y en [Configurar la infraestructura de certificados](configure-certificate-infrastructure-for-pfx.md).

2. Instale un certificado raíz o certificado de entidad de certificación (CA) intermedia en cada dispositivo para que el dispositivo reconozca la legitimidad de la entidad de certificación. Para ello, cree e implemente un **perfil de certificado de confianza**. Al implementar este perfil, los dispositivos que se administran con Intune solicitarán y recibirán el certificado raíz. Debe crear un perfil independiente para cada plataforma. El **perfil de certificado de confianza** está disponible para estas plataformas:
 -  iOS 8.0 y versiones posteriores
 -  Mac OS X 10.9 y versiones posteriores
 -  Android 4.0 y versiones posteriores
 -  Android for Work
 -  Windows 8.1 y posterior
 -  Windows Phone 8.1 y versiones posteriores

3. Cree perfiles de certificados de manera que los dispositivos soliciten un certificado que se use para la autenticación del acceso al correo electrónico, Wi-Fi y VPN, tal como se describe en [Configure Intune certificate profiles](configure-intune-certificate-profiles.md) (Configurar perfiles de certificado de Intune). Puede crear e implementar un **perfil de certificado PKCS #12 (.PFX)** *o* un **perfil de certificado SCEP** para dispositivos en estas plataformas:

  -  iOS 8.0 y versiones posteriores
  -  Android 4.0 y versiones posteriores
  -  Android for Work
  -  Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores

  Use un **perfil de certificado SCEP** para dispositivos en estas plataformas:
    -   Mac OS X 10.9 y versiones posteriores
    -   Windows Phone 8.1

Debe crear un perfil independiente para cada plataforma. Al crear el perfil, debe asociarlo al **perfil de certificado raíz de confianza** que creó previamente.

> [!NOTE]           
> - Si no dispone de una entidad de certificación empresarial, debe crear una.
>- Si decide, en función de sus plataformas de dispositivo, usar el Protocolo de inscripción de certificados simple (SCEP), también tendrá que configurar un servidor del Servicio de inscripción de dispositivos de red (NDES).
>-  Si planea usar SCEP o perfiles PFX, debe descargar y configurar el conector de certificado de Microsoft Intune.
>-  Conozca cómo configurar todos los servicios obligatorios en [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) y [Configurar la infraestructura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md).

### <a name="next-steps"></a>Pasos siguientes
- [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md)
- [Configurar la infraestructura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md)
- [Configurar perfiles de certificado de Intune](configure-intune-certificate-profiles.md)
