---
title: "Przewijanie i skalowanie widoków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8bd42a7da91f984c4cedc4deafc0ab9f4417495
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="scrolling-and-scaling-views"></a>Przewijanie i skalowanie widoków
MFC obsługuje widoki, które przewiń i widoki, które są automatycznie przeskalowany do rozmiaru okna ramki, która wyświetla je. Klasa `CScrollView` obsługuje oba rodzaje widoków.  
  
 Aby uzyskać więcej informacji na temat przewijanie i skalowanie, zobacz klasy [CScrollView](../mfc/reference/cscrollview-class.md) w *odwołania MFC*. Na przykład przewijania, zobacz [próbki bazgrołów](../visual-cpp-samples.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   Przewijanie widoku  
  
-   Skalowanie widoku  
  
-   [Wyświetlanie współrzędnych](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a>Przewijanie widoku  
 Często rozmiar pliku jest większy niż rozmiar widoku jego mogą być wyświetlane. Może to nastąpić, ponieważ dane dokumentu zwiększa lub użytkownik zmniejsza okno widoku ramki. W takich przypadkach widok musi obsługiwać przewijania.  
  
 Dowolny widok może obsłużyć komunikaty paska przewijania w jego `OnHScroll` i `OnVScroll` funkcji elementów członkowskich. Można albo zaimplementuj paska przewijania komunikat — Obsługa w tych funkcji, wykonanie całej pracy samodzielnie, lub można użyć `CScrollView` klasy do obsługi przewijanie dla Ciebie.  
  
 `CScrollView`wykonuje następujące czynności:  
  
-   Zarządza rozmiarów okna i okienka ekranu i tryby mapowania  
  
-   Przewija automatycznie w odpowiedzi na komunikaty paska przewijania  
  
 Można określić, ile przewiń "page", (po kliknięciu przez użytkownika w wale paska przewijania) i "wiersz" (gdy użytkownik kliknie strzałkę przewijania). Te wartości do własnych rodzaj widoku planu. Można na przykład przewiń 1 piksel w widoku grafiki, ale w przyrostach oparte na wysokość wiersza w dokumentach tekstu.  
  
##  <a name="_core_scaling_a_view"></a>Skalowanie widoku  
 Widok, aby automatycznie Dopasuj rozmiar okna ramki, należy służy `CScrollView` skalowania zamiast przewijania. Widok logiczny jest rozciągany tak, lub zmniejszyć, aby dokładnie dopasować obszaru klienckiego okna. Skalowanie widoku nie ma pasków przewijania.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoków](../mfc/using-views.md)

