---
title: Dodawanie kart do formantu karty
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: f769de7bcf3e410cca717c17237d1e49ef8562c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394770"
---
# <a name="adding-tabs-to-a-tab-control"></a>Dodawanie kart do formantu karty

Po utworzeniu formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), Dodaj dowolną liczbę kart.

### <a name="to-add-a-tab-item"></a>Aby dodać element karty

1. Przygotowanie [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktury.

1. Wywołaj [CTabCtrl::InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), przekazywanie struktury.

1. Powtórz kroki 1 i 2 dla elementów dodatkową kartę.

Aby uzyskać więcej informacji, zobacz [Tworzenie formantu karty](/windows/desktop/Controls/tab-controls) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
