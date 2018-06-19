---
title: Używanie paska dialogowego z formantem paska pomocniczego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WM_EX_TRANSPARENT
dev_langs:
- C++
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47894c14e3b3d694847f94e7f981c9397383e598
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382909"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Używanie paska dialogowego z formantem paska pomocniczego
Jak wspomniano w [formanty paska pomocniczego i paski](../mfc/rebar-controls-and-bands.md), każdej grupy może zawierać tylko jeden podrzędny okna (lub sterowania). Może to być to ograniczenie, jeśli chcesz mieć więcej niż jedno okno podrzędne na poza pasmem. Obejście wygodny jest tworzenie zasobu paska dialogowego z wielu formantów, a następnie dodaj obiekt band paska pomocniczego (paska dialogowego zawierający) z formantem paska pomocniczego.  
  
 Zwykle, jeśli chce pasmem pasek okna dialogowego do przezroczysty, należy ustawić **ws_ex_transparent —** rozszerzone style dla obiektu pasek okna dialogowego. Jednak ponieważ **ws_ex_transparent —** ma problemy z prawidłowo malowanie tła paska dialogowego, trzeba będzie wykonać nieco dodatkowej pracy w celu osiągnięcia pożądanych efektów.  
  
 Poniższej procedurze szczegółowo omówiono kroki niezbędne do uzyskania przejrzystości bez użycia **ws_ex_transparent —** rozszerzone style.  
  
### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Aby zaimplementować paska dialogowego przezroczyste w paśmie paska pomocniczego  
  
1.  Przy użyciu [okno dialogowe Dodaj klasę](../mfc/reference/adding-an-mfc-class.md), Dodaj nową klasę (na przykład `CMyDlgBar`), który zawiera obiekt pasek okna dialogowego.  
  
2.  Dodaj obsługę `WM_ERASEBKGND` wiadomości.  
  
3.  W nowy program obsługi Zmień istniejący kod w celu dopasowania w poniższym przykładzie:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  Dodaj obsługę `WM_MOVE` wiadomości.  
  
5.  W nowy program obsługi Zmień istniejący kod w celu dopasowania w poniższym przykładzie:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 Nowe obsługi symulować przezroczystość paska dialogowego przekazywania `WM_ERASEBKGND` wiadomości do okna nadrzędnego i wymuszanie odświeżenia za każdym razem, gdy obiektu paska dialogowego zostanie przeniesiony.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

