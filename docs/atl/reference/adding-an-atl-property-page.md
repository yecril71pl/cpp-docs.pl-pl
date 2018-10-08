---
title: Dodawanie strony właściwości ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c46adc199a5d6b0bc814cc203b94ac3d268a560d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860631"
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

## <a name="see-also"></a>Zobacz też

[Strony właściwości](../../atl/atl-com-property-pages.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Przykład: Implementowanie strony właściwości](../../atl/example-implementing-a-property-page.md)
