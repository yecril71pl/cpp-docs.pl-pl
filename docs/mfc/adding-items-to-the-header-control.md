---
title: Dodawanie elementów do formantu nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 5749a0cae2dfe7e6c9f4c166eca487e36c2d21d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616469"
---
# <a name="adding-items-to-the-header-control"></a>Dodawanie elementów do formantu nagłówka

Po utworzeniu kontrolki nagłówka ([CHeaderCtrl](reference/cheaderctrl-class.md)) w oknie nadrzędnym Dodaj dowolną liczbę "elementów nagłówka", ile potrzebujesz: zwykle jednej na kolumnę.

### <a name="to-add-a-header-item"></a>Aby dodać element nagłówka

1. Przygotuj strukturę [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) .

1. Wywołaj metodę [CHeaderCtrl:: InsertItem](reference/cheaderctrl-class.md#insertitem), przekazując strukturę.

1. Powtórz kroki 1 i 2 w przypadku dodatkowych elementów.

Aby uzyskać więcej informacji, zobacz [Dodawanie elementu do kontrolki nagłówka](/windows/win32/Controls/header-controls) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](using-cheaderctrl.md)<br/>
[Formanty](controls-mfc.md)
