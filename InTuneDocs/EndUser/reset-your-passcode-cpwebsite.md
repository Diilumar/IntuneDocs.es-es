---
# required metadata

title: Restablecer el código de acceso de un dispositivo desde el sitio web del portal de empresa | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Restablecer el código de acceso de un dispositivo desde el sitio web del portal de empresa

Si pierde el PIN o la contraseña de un dispositivo inscrito en Intune, puede usar el [sitio web del portal de empresa](http://portal.manage.microsoft.com) para restablecerlos. El sitio web del portal de empresa es una página web que puede usar para administrar equipos y dispositivos que haya inscrito en Intune y para realizar la mayoría de las mismas tareas que se pueden realizar con la aplicación de portal de empresa.

> [!NOTE] 
> Es posible que no vea el botón de restablecimiento de contraseña en el sitio web del portal de empresa, según cómo haya configurado Intune el administrador de TI. El restablecimiento del código de acceso no se admite en dispositivos Windows 8.1 y Windows RT.

Para restablecer el código de acceso:

1.  Abra el [sitio web del portal de empresa](http://portal.manage.microsoft.com) y pulse el dispositivo cuyo código de acceso quiere restablecer.

2.  Pulse **Restablecer el código de acceso**..

    ![tap-passcode-to-reset](./media/iwp-1-tap-reset-passcode.png)

3.  Pulse **cerrar sesión** y vuelva a iniciar sesión con las credenciales de su cuenta profesional o educativa. Tendrá que volver a iniciar sesión en un plazo de cinco minutos.

    ![sign-out-sign-back-in](./media/iwp-2-sign-out.png)

4.  Pulse **Restablecer el código de acceso**..

    ![tap-reset-passcode](./media/iwp-3-tap-reset-passcode-after-signin.png)

    Compruebe la tabla para ver cómo funciona en su dispositivo el restablecimiento del código de acceso.

    |Plataforma|Support|
    |------------|-----------|
    |Android|Crea un código de acceso nuevo, temporal y alfanumérico.|
    |iOS|Quita el código de acceso del dispositivo y no crea un nuevo código de acceso temporal. Si usa Touch ID deberá volver a configurarlo en el dispositivo, ya que se eliminará al restablecer el código de acceso.|
    |Windows 10 (solo para dispositivos móviles)|Crea un código de acceso nuevo, temporal y alfanumérico. Windows Hello es compatible.|
    |Windows Phone 8,1|Crea un código de acceso nuevo, temporal y numérico.|
    Después de desbloquear el dispositivo, puede establecer un código de acceso nuevo, Para ello, vaya a **Configuración** en el dispositivo.

5.  Desbloquee el dispositivo y establezca un código de acceso nuevo, o bien cambie el código de acceso temporal en **Configuración** en el dispositivo.

    Para ver una notificación que confirme que la contraseña se restableció correctamente, haga clic en la marca de notificación en la parte superior derecha del sitio del portal de empresa.

### Consulte también
[Usar el sitio web del Portal de empresa de Intune](using-the-intune-company-portal-website.md)

<!--HONumber=May16_HO1-->

