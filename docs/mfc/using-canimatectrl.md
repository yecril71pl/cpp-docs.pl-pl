---
title: Korzystanie z CAnimateCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5685d6aed00cd57f4329b3865f96fa75226d7cf6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-canimatectrl"></a>Korzystanie z CAnimateCtrl
Formantu animacji reprezentowany przez klasę [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), jest oknem, które wyświetla klip wideo z przeplotem AVI (Audio) format — standardowy format audio/wideo systemu Windows. Klip AVI jest szereg ramki mapy bitowej, takich jak filmu.  
  
 Ponieważ wykonywania podczas klip AVI zostanie wyświetlony w wątku sieci będzie nadal występował, jednym z typowych zastosowań formantu animacji jest wskazująca działania systemu podczas długotrwałej operacji. Na przykład okno dialogowe Znajdź Windows wyświetla przenoszenie Lupa jako system wyszukuje plik.  
  
 Formanty animacji można odtwarzać tylko proste klipy AVI, a nie obsługują dźwięku. (Aby uzyskać pełną listę ograniczenia, zobacz [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Ponieważ możliwości formantu animacji są znacznie ograniczone i mogą ulec zmianie, należy użyć zamiast takich jak kontrola MCIWnd Jeśli potrzebujesz formantu zapewnienie odtwarzania multimediów i/lub funkcje rejestrowania. Aby uzyskać więcej informacji na temat kontroli MCIWnd zobacz dokumentację multimediów.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Używanie kontrolki animacji](../mfc/using-an-animation-control.md)  
  
-   [Powiadomienia wysyłane przez kontrolki animacji](../mfc/notifications-sent-by-animation-controls.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki](../mfc/controls-mfc.md)

