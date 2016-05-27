---
# required metadata

title: Configurar la administración de Windows 10 Mobile y Windows Phone con Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Configurar la administración de Windows Phone y Windows 10 Mobile con Microsoft Intune
Para poder administrar dispositivos Windows 10 Mobile o Windows Phone con Microsoft Intune, los dispositivos deben poder comunicarse con Intune. Para simplificar este proceso, puede crear un registro DNS para que los usuarios no tengan que escribir la dirección del servidor. Los pasos siguientes describen cómo simplificar la inscripción de los usuarios.  

En la mayoría de los escenarios, los usuarios pueden instalar la aplicación de portal de empresa desde la Tienda Windows. Si administra dispositivos Windows Phone 8.0 o necesita implementar el portal de empresa en dispositivos Windows Phone, también debe descargar y firmar la aplicación de portal de empresa. Vea [Set up Windows Phone 8.0 management](set-up-windows-phone-8.0-management-with-microsoft-intune.md) (Configurar la administración de Windows Phone 8.0)..

1.  **Configurar Intune**
    Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) como **Microsoft Intune** y configure MDM.

2.  **Establecer un alias DNS para la dirección del servidor de inscripción** (opcional)

    La creación de un alias DNS (tipo de registro CNAME) facilita a los usuarios la inscripción de sus dispositivos. Si no crea un alias DNS, el usuario tendrá que hacer lo siguiente:

  1.  Debe crear registros de recursos DNS **CNAME** para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a manage.microsoft.com. Si hay más de un dominio comprobado, debe crear un registro CNAME para cada dominio. Los registros de recursos CNAME deben contener la siguiente información:

      |TYPE|Nombre de host|Apunta a|TTL|
      |--------|-------------|-------------|-------|
      |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
      |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

      Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

      **EnterpriseEnrollment-s.manage.microsoft.com**: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

      **EnterpriseRegistration.windows.net**: admite dispositivos Windows 8.1 y Windows 10 Mobile que se registrarán con Azure Active Directory con su cuenta profesional o educativa.

    2.  En la [consola de administración de Intune](http://manage.microsoft.com), haga clic en **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows Phone**..

      ![Configurar la administración de dispositivos móviles para el cuadro de diálogo de Windows](../media/windows-device-enrollment.png)

    3.  Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y, después, haga clic en **Probar detección automática**..



No es necesario ningún trabajo adicional a menos que vaya a implementar el portal de empresa en dispositivos.  Puede omitir sin ningún problema los pasos 2, 3 y 4 de la consola de administración.


<!--HONumber=May16_HO1-->

