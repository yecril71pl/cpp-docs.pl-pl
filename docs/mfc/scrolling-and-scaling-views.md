---
title: Przewijanie i skalowanie widoków
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: 7d26bc656dec3fdcbb8fc5ea4918ec7d59bc5afc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777585"
---
# <a name="scrolling-and-scaling-views"></a>Przewijanie i skalowanie widoków

Biblioteka MFC obsługuje widoki, które przewiń i widoki, które są automatycznie skalowane do rozmiaru okna ramki, które wyświetla je. Klasa `CScrollView` obsługuje oba rodzaje widoków.

Aby uzyskać więcej informacji na temat przewijanie i skalowanie Zobacz klasy [CScrollView](../mfc/reference/cscrollview-class.md) w *odwołanie MFC*. Na przykład przewijania, zobaczyć [próbki Bazgroły](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- Przewijanie widoku

- Skalowanie w widoku

- [Wyświetlanie współrzędnych](/windows/desktop/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a> Przewijanie widoku

Często rozmiaru dokumentu jest większy niż rozmiar, który można wyświetlić jej widok. Może to nastąpić, ponieważ dane dokumentu zwiększa się lub użytkownik zmniejsza okno, który określa widoku. W takich przypadkach widok musi obsługiwać przewijania.

Dowolny widok może obsługiwać komunikaty paska przewijania w jego `OnHScroll` i `OnVScroll` funkcji elementów członkowskich. Można albo obsługa komunikatów paska przewijania implementacji tych funkcji samodzielnie wykonać całą pracę, lub możesz użyć `CScrollView` klasy do obsługi przewijanie za Ciebie.

`CScrollView` wykonuje następujące czynności:

- Zarządza tryby mapowania i rozmiary okna i okienka ekranu

- Przewija automatycznie w odpowiedzi na komunikaty paska przewijania

Można określić, ile przewiń "page", (gdy użytkownik kliknie wałka pasek przewijania) i "wiersz" (po kliknięciu przez użytkownika w strzałki przewijania). Należy zaplanować te wartości w zależności od charakteru widoku. Na przykład można przewijać w 1 piksel w celu wyświetlenia grafiki, ale w przyrostach oparte na wysokość wiersza tekstu, dokumentów.

##  <a name="_core_scaling_a_view"></a> Skalowanie w widoku

Jeśli chcesz, aby widok, aby automatycznie Dopasuj rozmiar okna ramki, można użyć `CScrollView` skalowania zamiast przewijania. Widok logiczny jest rozciągana lub zmniejszyć, aby dokładnie dopasować obszaru klienckiego okna. Przeskalowano widoku nie ma pasków przewijania.

## <a name="see-also"></a>Zobacz także

[Używanie widoków](../mfc/using-views.md)
