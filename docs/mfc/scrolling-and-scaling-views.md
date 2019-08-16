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
ms.openlocfilehash: 7064880c5ceef8e7dc3e35bb7ef5bc700b0842d2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511233"
---
# <a name="scrolling-and-scaling-views"></a>Przewijanie i skalowanie widoków

MFC obsługuje widoki, które przewijają i przeglądają automatycznie do rozmiaru okna ramki, które wyświetla. Klasa `CScrollView` obsługuje oba rodzaje widoków.

Aby uzyskać więcej informacji na temat przewijania i skalowania, zobacz Class [CScrollView](../mfc/reference/cscrollview-class.md) in the *MFC Reference*. Aby zapoznać się z przykładem przewijania, zobacz [przykład bazgrołów](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- Przewijanie widoku

- Skalowanie widoku

- [Wyświetl współrzędne](/windows/win32/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a>Przewijanie widoku

Często rozmiar dokumentu jest większy niż rozmiar, który może być wyświetlany w widoku. Może się tak zdarzyć, ponieważ dane dokumentu rosną lub użytkownik zmniejsza okno, które przechodzą w widok. W takich przypadkach widok musi obsługiwać przewijanie.

Dowolny widok może obsługiwać komunikaty paska przewijania w jego `OnHScroll` `OnVScroll` funkcjach składowych. Można zaimplementować obsługę komunikatów paska przewijania w tych funkcjach, wykonując wszystkie czynności samodzielnie lub korzystając z `CScrollView` klasy, aby obsłużyć przewijanie.

`CScrollView`wykonuje następujące czynności:

- Zarządza rozmiaru okna i okienka ekranu oraz trybów mapowania

- Przewija automatycznie w odpowiedzi na komunikaty paska przewijania

Możesz określić, jak dużo ma być przewijana dla "strony" (gdy użytkownik kliknie ikonę paska przewijania) i "linia" (gdy użytkownik kliknie strzałkę przewijania). Zaplanuj te wartości, aby odpowiadały charakterowi widoku. Na przykład możesz chcieć przewinąć o 1-pikselowe przyrosty dla widoku grafiki, ale w przyrostach na podstawie wysokości linii w dokumentach tekstowych.

##  <a name="_core_scaling_a_view"></a>Skalowanie widoku

Gdy widok ma automatycznie pasować do rozmiaru okna ramki, można użyć `CScrollView` do skalowania zamiast przewijania. Widok logiczny jest rozciągany lub zmniejszany w celu dopasowania go do obszaru klienta okna. Widok skalowany nie ma pasków przewijania.

## <a name="see-also"></a>Zobacz także

[Używanie widoków](../mfc/using-views.md)
