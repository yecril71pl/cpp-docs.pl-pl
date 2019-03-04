---
title: Ustawianie trybu obiektu CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: a6d1a0edb356f9737aa287809dd8bca4146c1854
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287937"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Ustawianie trybu obiektu CStatusBarCtrl

Istnieją dwa tryby `CStatusBarCtrl` obiektu: proste i prostymi. W większości przypadków formant paska stanu ma jednej lub kilku części wraz z tekstu i prawdopodobnie ikony lub ikony. Jest to nazywane prostymi trybu. Aby uzyskać więcej informacji na ten tryb, zobacz [inicjowanie części obiektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Jednak istnieją przypadki, w którym wystarczy wyświetlić pojedynczy wiersz tekstu. W tym przypadku prosty tryb jest wystarczające dla Twoich potrzeb. Aby zmienić tryb `CStatusBarCtrl` do prostego obiektu, wywołanie [setsimple —](../mfc/reference/cstatusbarctrl-class.md#setsimple) funkcja elementu członkowskiego. Gdy formantu paska stanu jest w trybie uproszczonym, ustawić tekst, wywołując `SetText` funkcji członkowskiej, przekazując 255 jako wartość *nPane* parametru.

Możesz użyć [issimple —](../mfc/reference/cstatusbarctrl-class.md#issimple) funkcję, aby określić, jakie tryb `CStatusBarCtrl` obiekt jest w.

> [!NOTE]
>  Jeśli obiekt paska stanu został zmieniony z nonsimple na prostej lub na odwrót okna jest od razu ponownie rysowany i, jeśli ma to zastosowanie, wszelkie zdefiniowane elementy zostaną automatycznie przywrócone.

## <a name="see-also"></a>Zobacz także

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
