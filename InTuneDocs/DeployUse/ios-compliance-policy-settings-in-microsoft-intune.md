---
# required metadata

title: Configuración de directivas de cumplimiento para dispositivos iOS | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Configuración de directivas de cumplimiento para dispositivos iOS en Microsoft Intune

La configuración de directiva que se describe en este tema se aplica a los dispositivos que ejecuten iOS 6 y versiones posteriores.

Si desea obtener información sobre otras plataformas, seleccione uno de los siguientes temas:
> [!div class="op_single_selector"]
- [Configuración de directivas de cumplimiento para dispositivos Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Configuración de directivas de cumplimiento para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Configuración de seguridad del sistema
### Contraseña
- **Requerir una contraseña para desbloquear dispositivos móviles:** establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña antes de
  tener acceso a sus dispositivos. Los dispositivos iOS que usan contraseñas están cifrados.

- **Permitir contraseñas sencillas:**    establezca esta opción
   en **Sí** para permitir a los usuarios crear contraseñas sencillas
   como "**1234**" o "**1111**".

-  **Longitud mínima de la contraseña:**
  especifique el número mínimo de dígitos o caracteres que
  debe contener la contraseña del usuario.
- **Tipo de contraseña requerida:** especifique si los usuarios deben crear
una contraseña **Alfanumérica** o **Numérica**.

- **Número mínimo de conjuntos de caracteres:** si establece **Tipo de contraseña obligatoria** en
**Alfanumérica**, use esta opción para especificar el número mínimo de
conjuntos de caracteres que debe contener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
  -   Letras minúsculas
  -   Letras mayúsculas
  -   Símbolos
  -   Números

  Si se establece un número superior para este valor de configuración, los usuarios deberán crear contraseñas más complejas.

  En el caso de dispositivos iOS, este valor de configuración se refiere al número de caracteres especiales (por ejemplo, **!**,**#**,**&amp;**) que deben incluirse en la contraseña.
- **Minutos de inactividad antes de que sea necesaria la contraseña:** especifique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.

- **Caducidad de contraseña (días):** seleccione el número de días que faltan para que la contraseña caduque
y se deba crear otra.

- **Recordar historial de contraseñas:** use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para evitar que el usuario
cree contraseñas usadas anteriormente.

- **Impedir la reutilización de contraseñas anteriores:** si se ha seleccionado **Recordar historial de contraseñas**, especifique el
número de contraseñas usadas previamente que no se pueden volver a usar.

- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad:**
Esta valor debe usarse junto con el de la opción **Minutos de inactividad antes de que se requiera la contraseña**. Se pedirá a los usuarios que escriban una contraseña para obtener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción
**Minutos de inactividad antes de que se pida la contraseña**.

### Perfil de correo electrónico
- **Intune debe administrar la cuenta de correo electrónico:** cuando esta opción se establece en **Sí**, el dispositivo debe utilizar el correo electrónico no conforme implementado en el dispositivo. El dispositivo se considera no conforme en las situaciones siguientes:
  - El perfil de correo electrónico también debe implementarse en el mismo grupo de usuarios que el grupo de usuarios de destino de la directiva de cumplimiento. De lo contrario, los dispositivos de los usuarios se considerarán no conformes.
  - El dispositivo no será conforme si el usuario ya ha configurado una cuenta de correo electrónico en el dispositivo que coincida con el perfil de correo electrónico de Intune implementando en el dispositivo. Intune no puede sobrescribir el perfil aprovisionado por el usuario y, por tanto,
  no puede administrarlo. Para garantizar el cumplimiento, el usuario debe quitar la
  configuración de correo electrónico existente y, después, Intune podrá instalar el perfil
  de correo electrónico administrado.


- **Seleccione el perfil de correo electrónico que Intune debe administrar:**
     si la opción **Intune debe administrar la cuenta de correo electrónico** está seleccionada,
     elija **Seleccionar** para especificar el perfil de correo electrónico de Intune. El perfil de correo electrónico debe estar presente en el dispositivo.

     Para obtener información detallada sobre los perfiles de correo electrónico, consulte [Configurar el acceso al
     correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## Configuración de estado del dispositivo

- **El dispositivo no debe estar descodificado o descifrado:** si habilita esta opción,
los dispositivos descodificados no serán compatibles.

##  Propiedades del dispositivo
- **Versión mínima del sistema operativo:** cuando un dispositivo no cumple el requisito de versión mínima
del sistema operativo, se notifica como no conforme.
Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.

- **Maximum OS version allowed:** (Versión de SO máxima permitida) cuando un dispositivo usa una
versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.


<!--HONumber=May16_HO1-->

