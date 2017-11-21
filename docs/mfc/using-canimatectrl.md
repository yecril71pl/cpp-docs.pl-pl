---
title: Korzystanie z CAnimateCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CAnimateCtrl
dev_langs: C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2054fcd5ca73263f8d26713c4e6c1e9a59323659
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-canimatectrl"></a>Korzystanie z CAnimateCtrl
Formantu animacji reprezentowany przez klasę [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), jest oknem, które wyświetla klip wideo z przeplotem AVI (Audio) format — standardowy format audio/wideo systemu Windows. Klip AVI jest szereg ramki mapy bitowej, takich jak filmu.  
  
 Ponieważ wykonywania podczas klip AVI zostanie wyświetlony w wątku sieci będzie nadal występował, jednym z typowych zastosowań formantu animacji jest wskazująca działania systemu podczas długotrwałej operacji. Na przykład okno dialogowe Znajdź Windows wyświetla przenoszenie Lupa jako system wyszukuje plik.  
  
 Formanty animacji można odtwarzać tylko proste klipy AVI, a nie obsługują dźwięku. (Aby uzyskać pełną listę ograniczenia, zobacz [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Ponieważ możliwości formantu animacji są znacznie ograniczone i mogą ulec zmianie, należy użyć zamiast takich jak kontrola MCIWnd Jeśli potrzebujesz formantu zapewnienie odtwarzania multimediów i/lub funkcje rejestrowania. Aby uzyskać więcej informacji na temat kontroli MCIWnd zobacz dokumentację multimediów.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Używanie formantu animacji](../mfc/using-an-animation-control.md)  
  
-   [Powiadomienia wysyłane przez formanty animacji](../mfc/notifications-sent-by-animation-controls.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty](../mfc/controls-mfc.md)

