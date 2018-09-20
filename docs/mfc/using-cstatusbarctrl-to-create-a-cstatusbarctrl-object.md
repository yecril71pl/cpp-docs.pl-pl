---
title: Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c68603eff0393d76af4e0617548e5bf1dd4aa63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413695"
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

