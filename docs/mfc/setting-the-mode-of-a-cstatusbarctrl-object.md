---
title: Ustawianie trybu obiektu CStatusBarCtrl | Dokumentacja firmy Microsoft
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
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b398fedb8637ae6ce539a876410222485054919b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409548"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Ustawianie trybu obiektu CStatusBarCtrl

Istnieją dwa tryby `CStatusBarCtrl` obiektu: proste i prostymi. W większości przypadków formant paska stanu ma jednej lub kilku części wraz z tekstu i prawdopodobnie ikony lub ikony. Jest to nazywane prostymi trybu. Aby uzyskać więcej informacji na ten tryb, zobacz [inicjowanie części obiektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Jednak istnieją przypadki, w którym wystarczy wyświetlić pojedynczy wiersz tekstu. W tym przypadku prosty tryb jest wystarczające dla Twoich potrzeb. Aby zmienić tryb `CStatusBarCtrl` do prostego obiektu, wywołanie [setsimple —](../mfc/reference/cstatusbarctrl-class.md#setsimple) funkcja elementu członkowskiego. Gdy formantu paska stanu jest w trybie uproszczonym, ustawić tekst, wywołując `SetText` funkcji członkowskiej, przekazując 255 jako wartość *nPane* parametru.

Możesz użyć [issimple —](../mfc/reference/cstatusbarctrl-class.md#issimple) funkcję, aby określić, jakie tryb `CStatusBarCtrl` obiekt jest w.

> [!NOTE]
>  Jeśli obiekt paska stanu został zmieniony z nonsimple na prostej lub na odwrót okna jest od razu ponownie rysowany i, jeśli ma to zastosowanie, wszelkie zdefiniowane elementy zostaną automatycznie przywrócone.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

