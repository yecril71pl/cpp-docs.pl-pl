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
ms.openlocfilehash: c881e31d178d6303939c94d68e2824fb11ec2cbd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425407"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Używanie paska dialogowego z formantem paska pomocniczego

Jak wspomniano w [formanty paska pomocniczego i paski](../mfc/rebar-controls-and-bands.md), każdego pasma może zawierać tylko jeden podrzędny okna (lub sterowania). Może to być to ograniczenie, jeśli chcesz mieć więcej niż jedno okno podrzędne na poza pasmem. Wygodne obejście polega na tworzenie zasobu paska dialogowego z wieloma formantami, a następnie dodaj obiekt band paska pomocniczego (zawierające Pasek dialogowy) do formantu paska pomocniczego.

Normalnie jeśli chce się poza pasmem paska dialogowego były przezroczyste, należy ustawić ws_ex_transparent — rozszerzone style dla obiektu paska dialogowego. Jednak ponieważ WS_EX_TRANSPARENT ma problemy z prawidłowo malowanie tła paska dialogowego, należy wykonać wykonaniu dodatkowych czynności w celu osiągnięcia pożądanych efektów.

Poniższe szczegóły procedury kroki niezbędne do osiągnięcia przejrzystości bez użycia ws_ex_transparent — rozszerzone style.

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Aby zaimplementować paska dialogowego przezroczyste pasma paska pomocniczego

1. Za pomocą [okno dialogowe Dodaj klasę](../mfc/reference/adding-an-mfc-class.md), Dodaj nową klasę (na przykład `CMyDlgBar`), który zawiera obiekt paska dialogowego.

1. Dodaj program obsługi komunikatów WM_ERASEBKGND.

1. W nowy program obsługi Zmień istniejący kod do zgodnie z poniższym przykładem:

     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. Dodaj program obsługi komunikatów WM_MOVE.

1. W nowy program obsługi Zmień istniejący kod do zgodnie z poniższym przykładem:

     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

Nowe procedury obsługi symulować przezroczystość paska dialogowego przekazywania wiadomości WM_ERASEBKGND do nadrzędnego okna i wymuszanie repaint za każdym razem, gdy obiekt paska dialogowego jest przenoszony.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

