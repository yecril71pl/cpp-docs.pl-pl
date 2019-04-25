---
title: Dodawanie strony właściwości ATL
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: c61f666865d3e1db4cdcf2dc6d3e07c2113a79c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249102"
---
# <a name="adding-an-atl-property-page"></a>Dodawanie strony właściwości ATL

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
[Przykład: Implementowanie strony właściwości](../../atl/example-implementing-a-property-page.md)
