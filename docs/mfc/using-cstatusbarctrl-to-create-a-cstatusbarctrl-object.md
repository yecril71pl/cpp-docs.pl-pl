---
title: Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 05baf212f53956095af89377c0877db79b6e25ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552766"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl

Oto przykład typowym zastosowaniem [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>Aby użyć formantu paska stanu z częściami

1. Konstruowania `CStatusBarCtrl` obiektu.

1. Wywołaj [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) obszar na rysunku, jeśli chcesz ustawić minimalną wysokość formantu paska stanu.

1. Wywołaj [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) Aby ustawić kolor tła formantu paska stanu.

1. Wywołaj [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) ustawiania części w stan formantu i współrzędne prawą krawędzią każdej części paska.

1. Wywołaj [SetText —](../mfc/reference/cstatusbarctrl-class.md#settext) można ustawić tekst w danej części formantu paska stanu. Komunikat unieważnia części kontrolki, które uległy zmianie, powodując go, aby wyświetlić nowy tekst w przypadku, gdy formant uzyskuje następny komunikat WM_PAINT.

W niektórych przypadkach na pasku stanu musi tylko wyświetla wiersz tekstu. W takim przypadku wywołania [setsimple —](../mfc/reference/cstatusbarctrl-class.md#setsimple). To umieszcza formantu paska stanu w tryb "prosta", który wyświetla pojedynczy wiersz tekstu.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

