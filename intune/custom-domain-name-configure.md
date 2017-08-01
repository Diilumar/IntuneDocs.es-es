---
title: "Configuración de un nombre de dominio personalizado"
description: "Agregue un nombre de dominio personalizado para su suscripción de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1223d215058509a6a672c7a34bb22eee893b1350
ms.sourcegitcommit: b287025b1a0d09d41faf51cf98c34b676fa1d98e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2017
---
# <a name="configure-a-custom-domain-name"></a>Configuración de un nombre de dominio personalizado

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

En este tema se explica a los administradores cómo pueden crear un CNAME de DNS para simplificar y personalizar su experiencia de inicio de sesión.

Cuando su organización se registra en un servicio en la nube de Microsoft como es Intune, se le asigna un nombre de dominio inicial hospedado en Azure Active Directory (AD) similar a **su-dominio.onmicrosoft.com**. En este ejemplo, **su-dominio** es el nombre del dominio que eligió al suscribirse. **onmicrosoft.com** es el sufijo asignado a las cuentas que agregue a su suscripción. Puede configurar el dominio personalizado de su organización para obtener acceso a Intune en lugar del nombre de dominio proporcionado con la suscripción.

Le recomendamos encarecidamente que, antes de crear nuevas cuentas de usuario o de sincronizar su instancia de Active Directory local, decida si va a usar únicamente el dominio .onmicrosoft.com o si va a agregar uno o más nombres de dominio personalizados. Configure un dominio personalizado antes de agregar usuarios para simplificar la administración de usuarios. Gracias a esto, los usuarios podrán iniciar sesión con las credenciales que usan para obtener acceso a otros recursos del dominio.

Al suscribirse a un servicio basado en la nube de Microsoft, la instancia de ese servicio se convierte en un [inquilino de Microsoft Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), que proporciona servicios de identidad y directorio al servicio basado en la nube. Además, como las tareas de configuración de Intune para que use el nombre de dominio personalizado de las organizaciones son las mismas que para otros inquilinos de Azure AD, puede usar la información y los procedimientos que se describen en [Agregar el dominio](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Para obtener más información sobre los dominios personalizados, consulte [Información general conceptual de nombres de dominio personalizado en Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

No puede cambiar el nombre del dominio inicial onmicrosoft.com ni quitarlo. Puede agregar, comprobar o quitar los nombres de dominio personalizado usados en Intune para identificar claramente su negocio.

## <a name="to-add-and-verify-your-custom-domain"></a>Para agregar y comprobar el dominio personalizado

1. Vaya al [Portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx) e inicie sesión en la cuenta del administrador.

2. En el panel de navegación, elija **Configuración** &gt; **Dominios**.

3. Elija **Agregar dominio** y escriba el nombre de su dominio personalizado.
   ![Captura de pantalla del Centro de administración de Office 365 con la opción Configuración > Dominios seleccionada y un nombre de dominio nuevo agregado](./media/domain-custom-add.png)
4. El cuadro de diálogo **Comprobar dominio** se abre proporcionándole los valores para crear el registro TXT en su proveedor de host DNS.
    - **Usuarios de GoDaddy**: el Portal de administración de Office 365 le redirige a la página de inicio de sesión de GoDaddy. El registro TXT se crea automáticamente después de escribir sus credenciales y de aceptar el acuerdo del permiso de cambio de dominio. También puede [crear el registro TXT](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Usuarios de Register.com**: siga las [instrucciones paso a paso](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) para crear el registro TXT.

Los pasos para agregar y comprobar un dominio personalizado también se pueden [realizar en Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Puede obtener más información [sobre su dominio inicial onmicrosoft.com en Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)