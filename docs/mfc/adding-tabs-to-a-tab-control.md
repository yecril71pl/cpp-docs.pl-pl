---
title: Dodawanie kart do formantu karty
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 89132e94396b51bee4a111b963c67d029f3dd9df
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616530"
---
# <a name="adding-tabs-to-a-tab-control"></a>Dodawanie kart do formantu karty

Po utworzeniu kontrolki karta ([CTabCtrl](reference/ctabctrl-class.md)) Dodaj dowolną liczbę kart w miarę potrzeb.

### <a name="to-add-a-tab-item"></a>Aby dodać element karty

1. Przygotuj strukturę [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) .

1. Wywołaj metodę [CTabCtrl:: InsertItem](reference/ctabctrl-class.md#insertitem), przekazując strukturę.

1. Powtórz kroki 1 i 2 w przypadku dodatkowych elementów tabulacji.

Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki karta](/windows/win32/Controls/tab-controls) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTabCtrl](using-ctabctrl.md)<br/>
[Formanty](controls-mfc.md)
