---
title: Agregar y asignar aplicaciones de MTD en Intune
titleSuffix: Intune on Azure
description: "Agregar aplicaciones de MTD, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS en Intune en Azure"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7edd80c7bae429c1f4032cf59aaaf8d91786f92c
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2017
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Agregar y asignar aplicaciones de Mobile Threat Defense (MTD) con Intune

> [!NOTE] 
> La información de este tema se aplica a todos los asociados de Mobile Threat Defense.

Puede usar Intune para agregar e implementar las aplicaciones de MTD para que los usuarios finales puedan recibir notificaciones cuando se identifique una amenaza en sus dispositivos móviles y para recibir orientación para solucionar tales amenazas.

Para los dispositivos iOS, necesita [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) de manera que los usuarios puedan comprobar sus identidades con Azure AD. Además, necesita la directiva de configuración de aplicaciones para iOS que indica la aplicación iOS de MTD para usarla con Intune.

> [!TIP]
> El portal de empresa de Intune funciona como el agente de los dispositivos Android, de manera que los usuarios puedan comprobar sus identidades con Azure AD.

## <a name="before-you-begin"></a>Antes de comenzar

-   Los pasos que se indican a continuación deben completarse en [Azure Portal](https://portal.azure.com/).

-   Asegúrese de estar familiarizado con los siguientes procesos:

    -   [Agregar una aplicación en Intune](apps-add.md)

    -   [Descargar una directiva de configuración de aplicación de iOS en Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)

    -   [Asignar una aplicación con Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

    -   [Agregar una directiva de configuración de aplicaciones iOS](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-add-apps"></a>Para agregar aplicaciones

### <a name="all-mtd-partners"></a>Todos los asociados de MTD

#### <a name="microsoft-authenticator-app-for-ios"></a>Aplicación de Microsoft Authenticator para iOS

- Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones de Microsoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) en el **paso 5** en la sección **Configurar la información de la aplicación**.

### <a name="skycure"></a>Skycure

#### <a name="android"></a>Android

- Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Skycure](https://play.google.com/store/apps/details?id=com.skycure.skycure) en el **paso 7**.

#### <a name="ios"></a>iOS

- Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones de Skycure](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) en el **paso 5** en la sección **Configurar la información de la aplicación**.

### <a name="lookout"></a>Lookout

#### <a name="android"></a>Android
- Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Lookout for Work para Google](https://play.google.com/store/apps/details?id=com.lookout.enterprise) en el **paso 7**.

#### <a name="ios"></a>iOS

- Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones de Lookout for Work para iOS](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) en el **paso 5** en la sección **Configurar la información de la aplicación**.

#### <a name="lookout-for-work-app-outside-the-apple-store"></a>Aplicación Lookout for Work fuera de la tienda de Apple

Necesita volver a firmar la aplicación Lookout for Work para iOS. Lookout distribuye su aplicación Lookout for Work de iOS fuera de la tienda App Store de iOS. Antes de distribuir la aplicación, deberá volver a firmar la aplicación con su certificado de desarrollador empresarial de iOS.

Para obtener información sobre cómo volver a firmar las aplicaciones Lookout for Work de iOS, vea [el proceso de volver a firmar la aplicación Lookout for Work de iOS](https://personal.support.lookout.com/hc/articles/114094038714) en el sitio web de Lookout.

##### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Habilitar la autenticación de Azure AD para la aplicación Lookout for Work para iOS

Habilite la autenticación de Azure Active Directory para los usuarios de iOS haciendo lo siguiente:

1. Vaya a [Azure Portal](https://portal.sazure.com), inicie sesión con sus credenciales y, después, vaya a la página de la aplicación.
  
2. Agregue la **aplicación Lookout for Work de iOS** como una **aplicación de cliente nativ**.

3. Reemplace **com.lookout.enterprise.yourcompanyname** por el ID de agrupación del cliente que ha seleccionado cuando se registró el IPA.

4.  Agregue un URI de redireccionamiento adicional: **&lt;companyportal://code/>** seguido de una versión codificada por URL del URI de redireccionamiento original.

5.  Agregue los **permisos delegados** a la aplicación.

    > [!NOTE] 
    > Para obtener más información, vea [Configurar una aplicación de cliente nativo con Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

##### <a name="add-the-lookout-for-work-ipa-file"></a>Agregar el archivo IPA de Lookout for Work

- Cargue el archivo .ipa que se ha vuelto a firmar como se describe en el tema [Agregar aplicaciones LOB para iOS con Intune](lob-apps-ios.md). También necesita establecer la versión mínima del sistema operativo en iOS 8.0 o posterior.

### <a name="check-point-sandblast-mobile"></a>SandBlast Mobile de Check Point

#### <a name="android"></a>Android

- Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](store-apps-android.md). Utilice esta [URL de la tienda de aplicaciones móviles de SandBlast Mobile de Check Point](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) en el **paso 7**.

#### <a name="ios"></a>iOS

- Póngase en contacto con el equipo de [SandBlast Mobile de Check Point](https://www.checkpoint.com/products/sandblast-mobile/) para obtener la aplicación para iOS. Consulte las instrucciones para [agregar aplicaciones del App Store a Microsoft Intune](store-apps-ios.md); después, utilice la URL de la tienda de Apple en el **paso 5** de la sección **Configuración de la información de la aplicación**.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>Para asociar la aplicación de MTD con una directiva de configuración de aplicaciones iOS

### <a name="for-skycure"></a>Para Skycure

-   Utilice la misma cuenta de Azure AD configurada previamente en la [consola de administración de Skycure](https://aad.skycure.com), que debe ser la misma que se usó para iniciar sesión en la consola clásica de Intune.

-   Debe **descargar** el archivo de directiva de configuración de aplicaciones para iOS: 
    -   Vaya a la [consola de administración de Skycure](https://aad.skycure.com) e inicie sesión con sus credenciales de administrador.
    
    -   Vaya a **Configuración** &gt; **Device Management Integrations** (Integraciones de administración de dispositivos)&gt; **EMM Integration Selection** (Selección de integración de EMM), elija **Microsoft Intune** y, a continuación, guarde la selección.
    
    -   Haga clic en el vínculo **Archivos de configuración de integración** y guarde el archivo \*.zip generado. El archivo .zip contiene el archivo **skycure\_configuration.plist**, que se utilizará para crear la directiva de configuración de aplicaciones para iOS en Intune.
    
    -   Vea las instrucciones para [usar las directivas de configuración de aplicaciones de Microsoft Intune para iOS](app-configuration-policies-use-ios.md) para agregar la directiva de configuración de aplicaciones de Skycure para iOS.
    
    - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido del archivo **skycure_configuration.plist** y péguelo en el cuerpo de la directiva de configuración.

También puede copiar el contenido de **skycure_configuration.plist** desde aquí:

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-lookout"></a>Para Lookout

- Cree la directiva de configuración de aplicaciones para iOS como se describe en el tema [Usar la directiva de configuración de aplicaciones para iOS](app-configuration-policies-use-ios.md).

### <a name="for-check-point-sandblast-mobile"></a>Para SandBlast Mobile de Check Point

- Consulte las instrucciones para [usar las directivas de configuración de aplicaciones de Microsoft Intune para iOS](app-configuration-policies-use-ios.md) con el fin de agregar la directiva de configuración de aplicaciones de SandBlast Mobile de Check Point para iOS.
    - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido siguiente y péguelo en el cuerpo de la directiva de configuración.

```
<dict><key>MDM</key><string>INTUNE</string></dict>

```
## <a name="to-assign-apps-all-mtd-partners"></a>Para asignar aplicaciones (todos los asociados de MTD)

- Consulte las instrucciones para [asignar aplicaciones a grupos con Intune](apps-deploy.md).

## <a name="next-steps"></a>Pasos siguientes

- [Configuración de la integración de Lookout con Intune](lookout-mtd-connector-integration.md)
- [Configuración de la integración de Skycure con Intune](skycure-mtd-connector-integration.md)
- [Configurar la integración de SandBlast de Check Point con Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)