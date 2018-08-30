---
title: Przewijanie i skalowanie widoków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89a899c7604f3342564a315ba704fc2fcd31ec36
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206941"
---
# <a name="scrolling-and-scaling-views"></a>Przewijanie i skalowanie widoków
Biblioteka MFC obsługuje widoki, które przewiń i widoki, które są automatycznie skalowane do rozmiaru okna ramki, które wyświetla je. Klasa `CScrollView` obsługuje oba rodzaje widoków.  
  
 Aby uzyskać więcej informacji na temat przewijanie i skalowanie Zobacz klasy [CScrollView](../mfc/reference/cscrollview-class.md) w *odwołanie MFC*. Na przykład przewijania, zobaczyć [próbki Bazgroły](../visual-cpp-samples.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat  
  
-   Przewijanie widoku  
  
-   Skalowanie w widoku  
  
-   [Wyświetlanie współrzędnych](/windows/desktop/gdi/window-coordinate-system)  
  
##  <a name="_core_scrolling_a_view"></a> Przewijanie widoku  
 Często rozmiaru dokumentu jest większy niż rozmiar, który można wyświetlić jej widok. Może to nastąpić, ponieważ dane dokumentu zwiększa się lub użytkownik zmniejsza okno, który określa widoku. W takich przypadkach widok musi obsługiwać przewijania.  
  
 Dowolny widok może obsługiwać komunikaty paska przewijania w jego `OnHScroll` i `OnVScroll` funkcji elementów członkowskich. Można albo obsługa komunikatów paska przewijania implementacji tych funkcji samodzielnie wykonać całą pracę, lub możesz użyć `CScrollView` klasy do obsługi przewijanie za Ciebie.  
  
 `CScrollView` wykonuje następujące czynności:  
  
-   Zarządza tryby mapowania i rozmiary okna i okienka ekranu  
  
-   Przewija automatycznie w odpowiedzi na komunikaty paska przewijania  
  
 Można określić, ile przewiń "page", (gdy użytkownik kliknie wałka pasek przewijania) i "wiersz" (po kliknięciu przez użytkownika w strzałki przewijania). Należy zaplanować te wartości w zależności od charakteru widoku. Na przykład można przewijać w 1 piksel w celu wyświetlenia grafiki, ale w przyrostach oparte na wysokość wiersza tekstu, dokumentów.  
  
##  <a name="_core_scaling_a_view"></a> Skalowanie w widoku  
 Jeśli chcesz, aby widok, aby automatycznie Dopasuj rozmiar okna ramki, można użyć `CScrollView` skalowania zamiast przewijania. Widok logiczny jest rozciągana lub zmniejszyć, aby dokładnie dopasować obszaru klienckiego okna. Przeskalowano widoku nie ma pasków przewijania.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoków](../mfc/using-views.md)

