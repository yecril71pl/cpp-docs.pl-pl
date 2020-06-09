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
ms.openlocfilehash: d308cfe83f02dcfe3687790c6638d268cc69fc24
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621429"
---
# <a name="list-control-and-list-view"></a>Kontrolka listy i widok listy

Dla wygody MFC hermetyzuje formant listy na dwa sposoby. Można użyć kontrolek list:

- Bezpośrednio poprzez osadzenie obiektu [CListCtrl](reference/clistctrl-class.md) w klasie okna dialogowego.

- Pośrednio, za pomocą klasy [CListView](reference/clistview-class.md).

`CListView`ułatwia integrację kontrolki listy z architekturą dokumentu MFC/widoku, hermetyzując kontrolkę tak, jakby [elementu CEditView](reference/ceditview-class.md) hermetyzuje kontrolkę edycji: formant wypełnia cały obszar powierzchni widoku MFC. (Widok *to* formant, Rzutowanie na `CListView` ).

`CListView`Obiekt dziedziczy z [CCtrlView](reference/cctrlview-class.md) i jego klas podstawowych i dodaje funkcję członkowską do pobrania podstawowej kontrolki listy. Użyj widoku elementów członkowskich do pracy z widokiem jako widoku. Użyj funkcji składowej [funkcji GetListCtrl](reference/clistview-class.md#getlistctrl) , aby uzyskać dostęp do funkcji składowych kontrolki listy. Użyj tych elementów członkowskich, aby:

- Dodawanie, usuwanie i manipulowanie elementami na liście.

- Ustaw lub Pobierz atrybuty kontrolki listy.

Aby uzyskać odwołanie do `CListCtrl` bazowego a `CListView` , wywołaj `GetListCtrl` z klasy widoku listy:

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

W tym temacie opisano obie metody korzystania z formantu listy.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](using-clistctrl.md)<br/>
[Formanty](controls-mfc.md)
