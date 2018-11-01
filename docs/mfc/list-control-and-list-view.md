---
title: Kontrolka listy i widok listy
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: 9d57e1a3370b1b868178ac9e7e40ea97bce6e3c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440459"
---
# <a name="list-control-and-list-view"></a>Kontrolka listy i widok listy

Dla wygody MFC hermetyzuje kontrolki listy na dwa sposoby. Możesz użyć kontrolki listy:

- Bezpośrednio, osadzając [CListCtrl](../mfc/reference/clistctrl-class.md) obiekt klasy okien dialogowych.

- Pośrednio, za pomocą klasy [CListView](../mfc/reference/clistview-class.md).

`CListView` można łatwo zintegrować formantu listy z architektury dokument/widok MFC, zawieranie kontrolki znacznie jako [CEditView](../mfc/reference/ceditview-class.md) hermetyzuje formant edycji: formant wypełnia cały obszar powierzchni widoku MFC. (Widok *jest* kontrolki rzutować `CListView`.)

A `CListView` dziedziczy obiektu [CCtrlView](../mfc/reference/cctrlview-class.md) i klasy bazowej i dodaje funkcję członkowską do pobrania podstawowego kontrolki listy. Wyświetl członków należy używać do pracy z widok jako widok. Użyj [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl) funkcja elementu członkowskiego w celu uzyskania dostępu do kontrolki listy elementów członkowskich. Użyj tych członków, aby:

- Dodawanie, usuwanie lub manipulowania "elementy" na liście.

- Set lub get atrybuty formantu listy.

Aby uzyskać odwołanie do `CListCtrl` bazowego `CListView`, wywołania `GetListCtrl` od Twojej klasy widoku listy:

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

W tym temacie opisano obie sposoby korzystania z formantu listy.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

