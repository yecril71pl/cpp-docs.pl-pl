---
title: Ustawianie trybu obiektu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: 79b499533196447898ce62ea9dc86c1674fc0302
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446427"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Ustawianie trybu obiektu CStatusBarCtrl

Istnieją dwa tryby dla `CStatusBarCtrl` obiektu: proste i nieproste. W większości przypadków kontrolka pasek stanu będzie zawierać co najmniej jedną część, wraz z tekstem i prawdopodobnie ikoną lub ikonami. Jest to nazywane trybem nieprostym. Aby uzyskać więcej informacji na temat tego trybu, zobacz [Inicjowanie części obiektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Istnieją jednak przypadki, w których wystarczy tylko wyświetlić pojedynczy wiersz tekstu. W takim przypadku tryb prosty jest wystarczający dla Twoich potrzeb. Aby zmienić tryb obiektu `CStatusBarCtrl` na prosty, należy wywołać funkcję [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) składowej. Gdy kontrolka pasek stanu jest w trybie prostym, Ustaw tekst, wywołując funkcję elementu członkowskiego `SetText`, przekazując 255 jako wartość parametru *nPane* .

Można użyć funkcji [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) do określenia trybu, w którym znajduje się `CStatusBarCtrl` obiektu.

> [!NOTE]
>  Jeśli obiekt paska stanu jest zmieniany z nieproste na prosta lub na odwrót, okno zostanie natychmiast ponownie narysowane i, w razie potrzeby, wszystkie zdefiniowane części zostaną automatycznie przywrócone.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
