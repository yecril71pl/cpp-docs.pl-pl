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
ms.openlocfilehash: 366f0e2953e5190f80a2877804bff2fc7dbbd520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372788"
---
# <a name="scrolling-and-scaling-views"></a>Przewijanie i skalowanie widoków

MFC obsługuje widoki, które przewijają i widoki, które są automatycznie skalowane do rozmiaru okna ramki, które je wyświetla. Klasa `CScrollView` obsługuje oba rodzaje widoków.

Aby uzyskać więcej informacji na temat przewijania i skalowania, zobacz klasy [CScrollView](../mfc/reference/cscrollview-class.md) w *odwołaniu MFC*. Przykład przewijania można znaleźć w [przykładzie Bazgrołów](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- Przewijanie widoku

- Skalowanie widoku

- [Wyświetlanie współrzędnych](/windows/win32/gdi/window-coordinate-system)

## <a name="scrolling-a-view"></a><a name="_core_scrolling_a_view"></a>Przewijanie widoku

Często rozmiar dokumentu jest większy niż rozmiar, który może być wyświetlany w jego widoku. Może to nastąpić, ponieważ dane dokumentu zwiększa lub użytkownik zmniejsza okno, które ramki widoku. W takich przypadkach widok musi obsługiwać przewijanie.

Każdy widok może obsługiwać komunikaty paska przewijania w jego `OnHScroll` i `OnVScroll` funkcji członkowskich. Można zaimplementować obsługę komunikatów na pasku przewijania w tych `CScrollView` funkcjach, wykonując całą pracę samodzielnie lub można użyć klasy do obsługi przewijania dla Ciebie.

`CScrollView`wykonuje następujące czynności:

- Zarządza rozmiarami okien i rzutni oraz trybami mapowania

- Przewija się automatycznie w odpowiedzi na komunikaty paska przewijania

Można określić, ile przewinąć dla "strony" (gdy użytkownik kliknie w wału paska przewijania) i "linii" (gdy użytkownik kliknie strzałkę przewijania). Zaplanuj te wartości tak, aby odpowiadał charakterowi widoku. Na przykład można przewijać przyrosty o 1 piksel dla widoku grafiki, ale w przyrostach opartych na wysokości linii w dokumentach tekstowych.

## <a name="scaling-a-view"></a><a name="_core_scaling_a_view"></a>Skalowanie widoku

Jeśli chcesz, aby widok automatycznie pasował do rozmiaru okna `CScrollView` ramki, można użyć do skalowania zamiast przewijania. Widok logiczny jest rozciągnięty lub skurczony, aby dokładnie dopasować obszar klienta okna. Widok skalowany nie ma pasków przewijania.

## <a name="see-also"></a>Zobacz też

[Używanie widoków](../mfc/using-views.md)
