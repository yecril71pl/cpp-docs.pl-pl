---
title: Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 12d5664b9fc59c4569ec2ee7db4ae883911f7bcd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442383"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl

Oto przykład typowego użycia [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>Aby użyć kontrolki paska stanu z częściami

1. Konstruowanie obiektu `CStatusBarCtrl`.

1. Wywołaj [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) , jeśli chcesz ustawić minimalną wysokość obszaru rysowania kontrolki pasek stanu.

1. Wywołaj [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) , aby ustawić kolor tła kontrolki paska stanu.

1. Wywołaj metodę [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) , aby ustawić liczbę części w kontrolce pasek stanu i współrzędną prawej krawędzi każdej części.

1. Wywołaj [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) , aby ustawić tekst w danej części kontrolki pasek stanu. Komunikat unieważnia część kontrolki, która zmieniła się, powodując wyświetlenie nowego tekstu, gdy kontrolka odbierze komunikat WM_PAINT.

W niektórych przypadkach pasek stanu musi wyświetlać tylko wiersz tekstu. W takim przypadku należy wywołać metodę [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). Spowoduje to umieszczenie kontrolki pasek stanu w trybie prostym, który wyświetla pojedynczy wiersz tekstu.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
