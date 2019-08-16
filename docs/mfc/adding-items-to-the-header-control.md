---
title: Dodawanie elementów do formantu nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: d9a35123ddbe77b8e5e1779651fc4cde233863ae
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509320"
---
# <a name="adding-items-to-the-header-control"></a>Dodawanie elementów do formantu nagłówka

Po utworzeniu kontrolki nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) w oknie nadrzędnym Dodaj dowolną liczbę "elementów nagłówka", ile potrzebujesz: zwykle jednej na kolumnę.

### <a name="to-add-a-header-item"></a>Aby dodać element nagłówka

1. Przygotuj strukturę [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-_hd_itemw) .

1. Wywołaj metodę [CHeaderCtrl:: InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), przekazując strukturę.

1. Powtórz kroki 1 i 2 w przypadku dodatkowych elementów.

Aby uzyskać więcej informacji, zobacz [Dodawanie elementu do kontrolki nagłówka](/windows/win32/Controls/header-controls) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
