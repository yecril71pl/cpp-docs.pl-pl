---
title: Dodawanie kart do formantu karty
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 8915b3af083ebe318e8527b2f83099bf61e7e3ce
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509300"
---
# <a name="adding-tabs-to-a-tab-control"></a>Dodawanie kart do formantu karty

Po utworzeniu kontrolki karta ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) Dodaj dowolną liczbę kart w miarę potrzeb.

### <a name="to-add-a-tab-item"></a>Aby dodać element karty

1. Przygotuj strukturę [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) .

1. Wywołaj metodę [CTabCtrl:: InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), przekazując strukturę.

1. Powtórz kroki 1 i 2 w przypadku dodatkowych elementów tabulacji.

Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki karta](/windows/win32/Controls/tab-controls) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
