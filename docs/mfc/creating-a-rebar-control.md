---
title: Tworzenie formantu paska pomocniczego
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 0fb651aef599b64b787d96a668e2e1496c1dff8e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274465"
---
# <a name="creating-a-rebar-control"></a>Tworzenie formantu paska pomocniczego

[Z CReBarCtrl](../mfc/reference/crebarctrl-class.md) obiektów należy utworzyć przed obiektem nadrzędnym jest widoczna. W ten sposób możliwości problemów malowania.

Na przykład formanty paska pomocniczego (używane w obiektach okna ramki) są powszechnie używane jako nadrzędny systemu windows dla formantów paska narzędzi. Dlatego nadrzędnego formantu paska pomocniczego jest obiekt okna w ramce. Ponieważ obiekt okna ramki jest elementem nadrzędnym `OnCreate` funkcji elementu członkowskiego (nadrzędnego) to doskonałe miejsce, aby utworzyć formant paska pomocniczego.

Aby użyć `CReBarCtrl` obiektu będzie najczęściej wykonaj następujące kroki:

### <a name="to-use-a-crebarctrl-object"></a>Aby użyć obiektu z CReBarCtrl

1. Konstruowania [z CReBarCtrl](../mfc/reference/crebarctrl-class.md) obiektu.

1. Wywołaj [Utwórz](../mfc/reference/crebarctrl-class.md#create) do tworzenia formantu typowego paska pomocniczego Windows i dołącz je do `CReBarCtrl` obiektu, określając dowolne żądane style.

1. Ładowanie mapy bitowej przy użyciu wywołania do [CBitmap::LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap), który zostanie użyty jako tło obiekt formantu paska pomocniczego.

1. Utwórz i zainicjuj wszystkie okna obiektów podrzędnych (paski narzędzi, formantów okna dialogowego i tak dalej), które będzie zawierać obiekt formantu paska pomocniczego.

1. Inicjowanie **REBARBANDINFO** struktury wymaganych informacji dla urządzenia band o do wstawienia.

1. Wywołaj [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) do wstawienia istniejących okien podrzędnych (takich jak `m_wndReToolBar`) do nowej kontrolki paska pomocniczego. Aby uzyskać więcej informacji na temat Wstawianie pasma do istniejącej kontrolki paska pomocniczego, zobacz [formanty paska pomocniczego i paski](../mfc/rebar-controls-and-bands.md).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
