---
# required metadata

title: VPN por aplicación para Android mediante Pulse Secure | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 05/08/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: chrisbal
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Usar una directiva personalizada para crear un perfil de VPN por aplicación para dispositivos Android

Puede crear un perfil de VPN por aplicación para dispositivos Android administrados por Intune. Primero creará un perfil de VPN que use el tipo de conexión Pulse Secure y, después, una directiva de configuración personalizada que asocie dicho perfil a aplicaciones específicas. Después de implementar las directivas en los grupos de dispositivos o usuarios de Android, cuando abra una de las aplicaciones especificadas en dichos dispositivos, abrirá una conexión VPN para esa aplicación. 

### Paso 1: crear un perfil de VPN

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** > **Agregar directiva**.
2. Seleccione una plantilla para la nueva directiva. Para ello, expanda **Android** y elija **Perfil de VPN (Android 4 y versiones posteriores)**.

3. En la plantilla, para **Tipo de conexión**, elija **Pulse Secure**.
4. Complete y guarde el perfil de VPN. Para obtener más información sobre los perfiles de VPN, consulte [VPN profiles](Help%20users%20connect%20to%20their%20work%20using%20VPN%20profiles%20with%20Microsoft%20Intune.md) (Perfiles de VPN).

> [!NOTE]
Tome nota del nombre del perfil de VPN para usarlo en el paso siguiente. Por ejemplo, **MyAppVpnProfile**.
   
### Paso 2: crear una directiva de configuración personalizada
    
   1. En la consola de administración de Intune, seleccione **Directiva** -> **Agregar directiva** -> **Android** -> **Configuración personalizada** -> **Crear directiva**.
   2. Indique un nombre para la directiva.
   3. En **Configuración de OMA-URI**, haga clic en **Agregar**.
   4. Proporcione un nombre de configuración.
   5. Para **Tipo de datos**, especifique **Cadena**.
   6. Para **OMA-URI**, especifique esta cadena: **./Vendor/MSFT/VPN/Profile/*Nombre*/PackageList**, donde *Nombre* es el nombre del perfil de VPN que anotó en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   En **Valor**, proporcione una lista de los paquetes que se deben asociar con el perfil separados por punto y coma.  Por ejemplo, si quiere que Excel y el explorador Google Chrome usen la conexión VPN, escriba: **com.microsoft.office.excel;com.android.chrome**.
  

   ![Directiva personalizada de ejemplo de VPN por aplicación de Android](..\media\android_per_app_vpn_oma_uri.png) 
#### Establecer la lista de aplicaciones como lista negra o lista blanca (opcional)
Puede especificar que la lista de aplicaciones *no* tiene permiso para usar la conexión VPN mediante el valor **BLACKLIST**.  Todas las demás aplicaciones se conectarán a través de VPN.

También puede especificar que *solo* las aplicaciones especificadas pueden usar la conexión VPN mediante el valor **WHITELIST**.
 

1.  En Configuración de OMA-URI, haga clic en **Agregar**.
2.  Proporcione un nombre de configuración.
3.  Para **Tipo de datos**, especifique **Cadena**.
4.  Para **OMA-URI**, especifique esta cadena: **./Vendor/MSFT/VPN/Profile/*Nombre*/Mode**, donde *Nombre* es el nombre del perfil de VPN que anotó en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
5.  En **Valor**, escriba **BLACKLIST** o **WHITELIST**. 


   
### Paso 3: Implementar ambas directivas

Debe implementar *ambas* directivas en los *mismos* grupos de Intune.

   1.  En el área de trabajo **Directiva** , seleccione la directiva que quiera implementar y, a continuación, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   **Para implementar la directiva**: seleccione uno o más grupos en los que quiera implementar la directiva y haga clic en **Agregar** &gt; **Aceptar**.

    -   **Para cerrar el cuadro de diálogo sin implementarla**: haga clic en **Cancelar**.

En el área de trabajo **Directiva** de la página **General** , un resumen de estado y las alertas identifican los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo Panel.



<!--HONumber=Jun16_HO1-->

