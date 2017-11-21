---
title: Tworzenie formantu paska pomocniczego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d0f1cc709bf09d03f211f3123bd47c82bb590348
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-rebar-control"></a>Tworzenie formantu paska pomocniczego
[Crebarctrl —](../mfc/reference/crebarctrl-class.md) obiektów należy utworzyć przed obiektem nadrzędnym jest widoczny. Pozwala to zmniejszyć możliwości malowania problemów.  
  
 Na przykład formanty paska pomocniczego (używane w obiektach okno ramowe) są często używane jako nadrzędny systemu windows dla formanty paska narzędzi. W związku z tym nadrzędnego formantu paska pomocniczego jest obiektem ramki okna. Ponieważ obiekt window ramki jest elementem nadrzędnym `OnCreate` umieścić Tworzenie formantu paska pomocniczego jest funkcja członkowska (nadrzędnego).  
  
 Aby użyć `CReBarCtrl` obiektu, zazwyczaj będzie wykonaj następujące kroki:  
  
### <a name="to-use-a-crebarctrl-object"></a>Aby użyć obiektu crebarctrl —  
  
1.  Utworzyć [crebarctrl —](../mfc/reference/crebarctrl-class.md) obiektu.  
  
2.  Wywołanie [Utwórz](../mfc/reference/crebarctrl-class.md#create) utworzyć typowe kontrolki paska pomocniczego systemu Windows i dołączenie go do `CReBarCtrl` obiektu, określając wszelkie potrzebne style.  
  
3.  Załadować mapy bitowej, w wyniku wywołania [CBitmap::LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap), ma być używany jako tło obiekt formantu paska pomocniczego.  
  
4.  Utwórz i zainicjuj wszystkie okna obiektów podrzędnych (paski narzędzi, formantów okna dialogowego itd.) znajdujące przez obiekt formantu paska pomocniczego.  
  
5.  Inicjowanie **REBARBANDINFO** struktury niezbędne informacje dla grupy o do wstawienia.  
  
6.  Wywołanie [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) do wstawienia istniejących okien podrzędnych (takich jak `m_wndReToolBar`) do nowego formantu paska pomocniczego. Aby uzyskać więcej informacji na wstawianie pasm do istniejącego formantu paska pomocniczego, zobacz [formanty paska pomocniczego i paski](../mfc/rebar-controls-and-bands.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

