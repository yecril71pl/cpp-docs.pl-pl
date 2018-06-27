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
ms.openlocfilehash: fa2628df5f446105e6b7881709a0c72c19fe230e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950493"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Używanie paska dialogowego z formantem paska pomocniczego
Jak wspomniano w [formanty paska pomocniczego i paski](../mfc/rebar-controls-and-bands.md), każdej grupy może zawierać tylko jeden podrzędny okna (lub sterowania). Może to być to ograniczenie, jeśli chcesz mieć więcej niż jedno okno podrzędne na poza pasmem. Obejście wygodny jest tworzenie zasobu paska dialogowego z wielu formantów, a następnie dodaj obiekt band paska pomocniczego (paska dialogowego zawierający) z formantem paska pomocniczego.  
  
 Zwykle Jeśli potrzebujesz pasmem pasek okna dialogowego do przezroczysty ustawić ws_ex_transparent — rozszerzone style dla obiektu paska dialogowego. Jednak ponieważ ws_ex_transparent — ma problemy z prawidłowo malowanie tła paska dialogowego, należy wykonać nieco dodatkowej pracy w celu osiągnięcia pożądanych efektów.  
  
 Poniższe szczegóły procedury kroki niezbędne do uzyskania przejrzystości bez użycia ws_ex_transparent — rozszerzone style.  
  
### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Aby zaimplementować paska dialogowego przezroczyste w paśmie paska pomocniczego  
  
1.  Przy użyciu [okno dialogowe Dodaj klasę](../mfc/reference/adding-an-mfc-class.md), Dodaj nową klasę (na przykład `CMyDlgBar`), który zawiera obiekt pasek okna dialogowego.  
  
2.  Dodaj obsługę wiadomości WM_ERASEBKGND.  
  
3.  W nowy program obsługi Zmień istniejący kod w celu dopasowania w poniższym przykładzie:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  Dodaj obsługę wiadomości WM_MOVE.  
  
5.  W nowy program obsługi Zmień istniejący kod w celu dopasowania w poniższym przykładzie:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 Nowe obsługi symulować przezroczystość paska dialogowego przekazywania wiadomości WM_ERASEBKGND do nadrzędnego okna i wymuszanie odświeżenia za każdym razem, gdy obiektu paska dialogowego zostanie przeniesiony.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

