---
title: Vea el inventario de software y hardware para equipos Windows
titlesuffix: Microsoft Intune
description: Cómo ver información de hardware y software sobre escritorios de Windows que administra como PC con el cliente de software de Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: f2bdb86913610f1d1317269a7778afc796db4fe8
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835527"
---
# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Visualización del inventario de software y hardware para equipos Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Intune recopila información detallada sobre el hardware y software de los escritorios que administra como PC con el cliente de software de Intune. Use la información de los siguientes procedimientos para aprender a crear:

-   Un informe que muestra información sobre las características de hardware de los PC que administra.

-   Un informe que muestra el software instalado en cada PC.

-   Cómo actualizar un inventario de PC para asegurarse de que los datos del informe están actualizados.

## <a name="to-display-information-about-pcs-you-manage"></a>Para mostrar información sobre los PC que administra

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Informes** &gt; **Informes de inventario de equipos**.

2.  En la página **Crear nuevo informe** , acepte los valores predeterminados o personalícelos para filtrar los resultados devueltos por el informe. Por ejemplo, puede seleccionar que en el informe solo se muestren los PC que ejecutan Windows 8.1.

3.  Elija **Ver informe** para abrir el **Informe de inventario de equipos** en otra ventana.

    Para ordenar el informe por cualquiera de las columnas, seleccione el encabezado de columna correspondiente, como **Nombre**, **Tipo de chasis** o **Fabricante**.

## <a name="to-display-software-installed-on-pcs-you-manage"></a>Para mostrar el software instalado en los PC que administra

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Informes** &gt; **Informes de software detectado**.

2.  En la página **Crear nuevo informe** , acepte los valores predeterminados o personalícelos para filtrar los resultados devueltos por el informe. Por ejemplo, puede seleccionar que en el informe sólo se muestre el software publicado por Microsoft.

3.  Elija **Ver informe** para abrir el **Informe de software detectado** en otra ventana.

    Para ordenar el informe por cualquiera de las columnas, seleccione el encabezado de columna correspondiente, como **Nombre**, **Editor** o **Categoría**. Puede seleccionar la flecha de dirección situada junto al elemento de lista para expandir las actualizaciones de la lista para mostrar más detalles (como los PC en los que están instaladas).

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Para actualizar el inventario de equipos a fin de asegurarse de que está al día

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos**  (u otro grupo que contenga el PC para el que quiera actualizar el inventario).

2.  Seleccione un PC o mantenga presionada la tecla **Ctrl** para seleccionar varios PC.

3.  En la barra de tareas, seleccione **Tareas remotas** &gt; **Actualizar inventario**.

4.  Para ver el estado de la tarea, seleccione **Tareas remotas** en la esquina inferior derecha de la página.

    Se abre el cuadro de diálogo **Estado de la tarea** , que muestra las tareas remotas actuales, el estado de la tarea, el nombre del dispositivo y los errores notificados, y proporciona un vínculo a información de solución de problemas, si es necesario.

### <a name="see-also"></a>Consulte también

[Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
