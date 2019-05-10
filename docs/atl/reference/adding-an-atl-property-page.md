---
title: Dodawanie strony właściwości ATL
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: 81f793fbdc6d9dda567051b8c35a96f3d3f2f470
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524628"
---
# <a name="adding-an-atl-property-page"></a>Dodawanie strony właściwości ATL

> [!NOTE] 
> Kreator strony właściwości ATL nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

Aby dodać stronę właściwości Active Template Library (ATL) do projektu, projekt musi być utworzony jako aplikacji ATL lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md) do tworzenia aplikacji ATL lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

W przypadku dodawania strony właściwości dla formantu, formant musi obsługiwać [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) interfejsu. Domyślnie ten interfejs jest na liście pochodnym kontroli nad klasy, gdy użytkownik [tworzenia kontrolki ATL](../../atl/reference/adding-an-atl-control.md) przy użyciu [Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md).

> [!NOTE]
> Jeśli nie ma klasy kontrolki [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) liście pochodnym, należy dodać ją ręcznie.

## <a name="to-add-an-atl-property-page-to-your-project"></a>Aby dodać strony właściwości ATL do projektu

1. W obu **Eksploratora rozwiązań** lub [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać stronę właściwości ATL.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj klasę**.

1. W [Dodaj klasę](../../ide/add-class-dialog-box.md) dialogowym **szablony** okienku kliknij **strony właściwości ATL** a następnie kliknij przycisk **Otwórz** do wyświetlenia [Kreator strony właściwości ATL](../../atl/reference/atl-property-page-wizard.md).

Po utworzeniu strony właściwości kontrolki, należy podać [PROP_PAGE](property-map-macros.md#prop_page) wpis map właściwości dla formantu.

## <a name="see-also"></a>Zobacz także

[Strony właściwości](../../atl/atl-com-property-pages.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Przykład: implementowanie strony właściwości](../../atl/example-implementing-a-property-page.md)
