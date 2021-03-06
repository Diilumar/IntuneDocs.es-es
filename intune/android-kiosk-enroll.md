---
title: Configuración de la inscripción en Intune de dispositivos dedicados de Android Enterprise
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos dedicados de Android Enterprise en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e71ae4add82482bf0bfbde25adac69c51570966
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834048"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Configuración de la inscripción en Intune de dispositivos dedicados de Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android admite dispositivos de propiedad corporativa y uso único en modo de quiosco multimedia con su conjunto de soluciones para dispositivos dedicados. Estos dispositivos tienen un solo fin, que puede ser la señalización digital, la impresión de vales o la administración de inventario, por nombrar solo algunos. Los administradores bloquean el uso de un dispositivo para un conjunto limitado de aplicaciones y vínculos web. También impide que los usuarios agreguen otras aplicaciones o lleven a cabo otras acciones en el dispositivo.

Con Intune es más fácil implementar aplicaciones y configuraciones en dispositivos Android dedicados. Para obtener detalles específicos sobre Android Enterprise, consulte [Requisitos para usar dispositivos Android en una empresa](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Los dispositivos que administre de esta forma se inscriben en Intune sin una cuenta de usuario y no están asociados a ningún usuario final. No están pensadas para aplicaciones de uso personal o aplicaciones que tengan un requisito importante de datos concretos de la cuenta del usuario, como Outlook o Gmail.

## <a name="device-requirements"></a>Requisitos de los dispositivos

Para poder administrarlos como dispositivos dedicados de Android Enterprise, los dispositivos deben cumplir estos requisitos:

- Android OS versión 5.1 y versiones posteriores.
- Los dispositivos deben ejecutar una versión de Android que tenga conectividad con Servicios de Google para móviles (GMS). Los dispositivos deben tener GMS disponible y deben ser capaces de conectarse a GMS.

## <a name="set-up-android-dedicated-device-management"></a>Configurar la administración de dispositivos dedicados de Android

Para configurar la administración de dispositivos dedicados de Android, siga estos pasos:

1. Para prepararse para administrar dispositivos móviles, debe [establecer la entidad de administración de dispositivos móviles (MDM) en **Microsoft Intune**](mdm-authority-set.md) para obtener instrucciones. Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles.
2. [Conecte su cuenta de inquilino de Intune a su cuenta de Android Enterprise](connect-intune-android-enterprise.md).
3. [Cree un perfil de inscripción](#create-an-enrollment-profile).
4. [Cree un grupo de dispositivos](#create-a-device-group).
5. [Inscribir los dispositivos dedicados](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Crear un perfil de inscripción

Debe crear un perfil de inscripción para poder inscribir los dispositivos dedicados. Al crear el perfil, obtiene un token de inscripción (cadena aleatoria) y un código QR. Según el sistema operativo Android y la versión del dispositivo, puede usar el token o un código QR para [inscribir el dispositivo dedicado](#enroll-the-dedicated-devices).

1. Vaya al [portal de Intune](https://portal.azure.com) y elija **Inscripción de dispositivos** > **Inscripción de Android** > **Inscripciones de dispositivos de tareas y quiosco multimedia**.
2. Elija **Crear** y rellene los campos obligatorios.
    - **Nombre**: escriba el nombre que va a usar al asignar el perfil al grupo de dispositivos dinámicos.
    - **Fecha de expiración del token**: la fecha en que caduca el token. Google exige un máximo de 90 días.
3. Elija **Crear** para guardar el perfil.

### <a name="create-a-device-group"></a>Creación de un grupo de dispositivos

Puede dirigir las aplicaciones y directivas a grupos de dispositivos dinámicos o asignados. Puede configurar grupos de dispositivos de AAD dinámicos para que los dispositivos que están inscritos con un perfil de inscripción determinada se rellenen automáticamente. Para ello, siga estos pasos:

1. Vaya al [portal de Intune](https://portal.azure.com) y elija **Grupos** > **Todos los grupos** > **Grupo nuevo**.
2. En la hoja **Grupo**, rellene los campos obligatorios, como se indica a continuación:
    - **Tipo de grupo**: Seguridad
    - **Nombre de grupo**: escriba un nombre intuitivo (como Dispositivos de fábrica 1)
    - **Tipo de pertenencia**: dispositivo dinámico
3. Elija **Agregar una consulta dinámica**.
4. En la hoja **Reglas de pertenencia dinámica**, rellene los campos del modo siguiente:
    - **Agregar regla de pertenencia dinámica**: regla simple
    - **Add devices where** (Agregar dispositivos aquí): enrollmentProfileName
    - En el cuadro central, elija **Coincidencia**.
    - En el último campo, escriba el nombre del perfil de inscripción que creó anteriormente.
    Para más información sobre las reglas de pertenencia dinámica, vea [Reglas de pertenencia dinámica a grupos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Elija **Agregar consulta** > **Crear**.

### <a name="replace-or-remove-tokens"></a>Reemplazar o quitar tokens

Puede reemplazar o quitar los tokens y los códigos QR.

- **Reemplazar el token**: al acercarse el momento de expiración de un token, puede generar uno nuevo o un código QR usando Reemplazar el token.
- **Revocar token**: puede hacer que el token o el código QR expire inmediatamente. A partir de este momento, el código QR o token ya no se puede usar. Puede usar esta opción si:
    - comparte accidentalmente el código QR o token con un tercero no autorizado,
    - finaliza todas las inscripciones y ya no necesita el token o código QR.

El reemplazo o la revocación de un código QR o token no tendrán ningún efecto en los dispositivos que ya estén inscritos.

1. Vaya al [portal de Intune](https://portal.azure.com) y elija **Inscripción de dispositivos** > **Inscripción de Android** > **Inscripciones de dispositivos de tareas y quiosco multimedia**.
2. Elija el perfil con el que quiera trabajar.
3. Elija **Token**.
4. Para reemplazar el token, elija **Reemplazar el token**.
5. Para revocar el token, elija **Revocar el token**.

## <a name="enroll-the-dedicated-devices"></a>Inscribir los dispositivos dedicados

Ya puede [inscribir los dispositivos dedicados](android-dedicated-devices-fully-managed-enroll.md).

## <a name="managing-apps-on-android-dedicated-devices"></a>Administración de aplicaciones en dispositivos dedicados de Android

Solo las aplicaciones que tienen como tipo de asignación [Establecer en obligatorio](apps-deploy.md#assign-an-app) se pueden instalar en dispositivos dedicados de Android. Las aplicaciones se instalan desde Google Play Store administrado del mismo modo que en los dispositivos de perfil de trabajo Android.

Cuando el desarrollador de aplicaciones publica una actualización en Google Play, las aplicaciones se actualizan automáticamente en los dispositivos administrados.

Para quitar una aplicación de dispositivos dedicados de Android, puede realizar una de las siguientes acciones:
-   Eliminar la implementación obligatoria de la aplicación.
-   Crear una implementación de desinstalación de la aplicación.

## <a name="next-steps"></a>Pasos siguientes
- [Implementar aplicaciones Android](apps-deploy.md)
- [Agregar directivas de configuración de Android](device-profiles.md)
