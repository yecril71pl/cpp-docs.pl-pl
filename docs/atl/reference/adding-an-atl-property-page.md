---
title: Dodawanie strony właściwości ATL
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: 4cd7444d18d26124f8c3c642bba55fb7592f5c8b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499320"
---
# <a name="adding-an-atl-property-page"></a>Dodawanie strony właściwości ATL

> [!NOTE]
> Kreator strony właściwości ATL nie jest dostępny w programie Visual Studio 2019 i nowszych.

Aby dodać stronę właściwości Active Template Library (ATL) do projektu, projekt musi zostać utworzony jako aplikacja ATL lub aplikacja MFC, która zawiera obsługę ATL. Za pomocą [Kreatora projektu ATL](../../atl/reference/atl-project-wizard.md) można utworzyć aplikację ATL lub [dodać obiekt ATL do aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) w celu zaimplementowania obsługi ATL dla aplikacji MFC.

Jeśli dodajesz stronę właściwości kontrolki, formant musi obsługiwać interfejs [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) . Domyślnie ten interfejs znajduje się na liście rodzajów pochodnych klasy kontrolki podczas [tworzenia kontrolki ATL](../../atl/reference/adding-an-atl-control.md) przy użyciu [Kreatora kontrolki ATL](../../atl/reference/atl-control-wizard.md).

> [!NOTE]
> Jeśli Klasa kontrolki nie ma [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) na liście pochodnych, należy ją dodać ręcznie.

## <a name="to-add-an-atl-property-page-to-your-project"></a>Aby dodać stronę właściwości ATL do projektu

1. W **Eksplorator rozwiązań** lub [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać stronę właściwości ATL.

1. W menu skrótów kliknij pozycję **Dodaj** , a następnie kliknij pozycję **Dodaj klasę**.

1. W oknie dialogowym [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) w okienku **Szablony** kliknij pozycję **Strona właściwości ATL** , a następnie kliknij przycisk **Otwórz** , aby wyświetlić [Kreatora strony właściwości ATL](../../atl/reference/atl-property-page-wizard.md).

Po utworzeniu strony właściwości dla kontrolki musisz podać wpis [PROP_PAGE](property-map-macros.md#prop_page) w mapie właściwości dla kontrolki.

## <a name="see-also"></a>Zobacz też

[Strony właściwości](../../atl/atl-com-property-pages.md)<br/>
[Podstawowe informacje o obiektach COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Przykład: implementowanie strony właściwości](../../atl/example-implementing-a-property-page.md)
