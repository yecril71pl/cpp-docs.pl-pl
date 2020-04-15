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
ms.openlocfilehash: e09a7bd274c44df2da48bbc007a95802fadd8cf0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365417"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Ustawianie trybu obiektu CStatusBarCtrl

Istnieją dwa tryby `CStatusBarCtrl` dla obiektu: proste i nieproste. W większości przypadków kontrolka paska stanu będzie miała jedną lub więcej części wraz z tekstem i być może ikoną lub ikonami. Jest to tak zwany tryb nonsimple. Aby uzyskać więcej informacji na temat tego trybu, zobacz [Inicjowanie części obiektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Istnieją jednak przypadki, w których wystarczy wyświetlić tylko jeden wiersz tekstu. W takim przypadku prosty tryb jest wystarczający do Twoich potrzeb. Aby zmienić tryb `CStatusBarCtrl` obiektu na prosty, należy wywołać [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) funkcji elementu członkowskiego. Gdy formant paska stanu jest w trybie `SetText` prostym, ustaw tekst, wywołując funkcję elementu członkowskiego, przekazując 255 jako wartość parametru *nPane.*

Za pomocą funkcji [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) można określić, w jakim trybie znajduje się `CStatusBarCtrl` obiekt.

> [!NOTE]
> Jeśli obiekt paska stanu jest zmieniany z nieproszkanego na prosty lub odwrotnie, okno jest natychmiast ponownie rysowane i, w stosownych przypadkach, wszystkie zdefiniowane części są automatycznie przywracane.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
