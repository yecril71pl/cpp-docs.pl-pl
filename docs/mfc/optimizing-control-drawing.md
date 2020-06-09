---
title: Optymalizacja rysowania formantów
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 17cb7318e667fe4e16416d51e7e7fba02553cfe6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621013"
---
# <a name="optimizing-control-drawing"></a>Optymalizacja rysowania formantów

Gdy kontrolka zostanie narysowana w kontekście urządzenia dostarczonego przez kontener, zwykle wybiera obiekty GDI (takie jak pióra, pędzle i czcionki) do kontekstu urządzenia, wykonuje operacje rysowania i przywraca poprzednie obiekty GDI. Jeśli kontener ma wiele kontrolek, które mają być narysowane w tym samym kontekście urządzenia, a każda kontrolka wybierze wymagane obiekty GDI, można zapisać czas, jeśli kontrolki nie odnoszą indywidualnie wszystkich wybranych obiektów. Po narysowaniu wszystkich kontrolek kontener może automatycznie przywrócić oryginalne obiekty.

Aby wykryć, czy kontener obsługuje tę technikę, formant może wywołać funkcję członkowską [COleControl:: IsOptimizedDraw](reference/colecontrol-class.md#isoptimizeddraw) . Jeśli ta funkcja zwraca **wartość true**, formant może pominąć normalny krok przywracania wcześniej wybranych obiektów.

Rozważmy kontrolkę, która ma następującą funkcję (niezoptymalizowaną) `OnDraw` :

[!code-cpp[NVC_MFC_AxOpt#15](codesnippet/cpp/optimizing-control-drawing_1.cpp)]

Pióro i pędzel w tym przykładzie są zmiennymi lokalnymi, co oznacza, że ich destruktory będą wywoływane, gdy wykraczają poza zakres (gdy `OnDraw` Funkcja zostanie zakończona). Destruktory spróbują usunąć odpowiednie obiekty GDI. Ale nie należy ich usuwać, jeśli planujesz pozostawić je wybrane do kontekstu urządzenia podczas powrotu z `OnDraw` .

Aby zapobiec zniszczeniu obiektów [CPen](reference/cpen-class.md) i [CBrush](reference/cbrush-class.md) po `OnDraw` zakończeniu, Zapisz je w zmiennych składowych zamiast zmiennych lokalnych. W deklaracji klasy kontrolki Dodaj deklaracje dla dwóch nowych zmiennych składowych:

[!code-cpp[NVC_MFC_AxOpt#16](codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](codesnippet/cpp/optimizing-control-drawing_3.h)]

Następnie `OnDraw` funkcję można napisać ponownie w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#18](codesnippet/cpp/optimizing-control-drawing_4.cpp)]

To podejście pozwala uniknąć tworzenia pióra i pędzla za każdym razem, gdy `OnDraw` jest wywoływana. Przyspieszenie zwiększa się w kosztach utrzymania dodatkowych danych wystąpienia.

Jeśli właściwość ForeColor lub BackColor zostanie zmieniona, należy ponownie utworzyć pióro lub pędzel. Aby to zrobić, Zastąp funkcje składowe [OnForeColorChanged](reference/colecontrol-class.md#onforecolorchanged) i [OnBackColorChanged](reference/colecontrol-class.md#onbackcolorchanged) :

[!code-cpp[NVC_MFC_AxOpt#19](codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Na koniec aby wyeliminować niepotrzebne `SelectObject` wywołania, należy zmodyfikować `OnDraw` w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#20](codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC: optymalizacja](mfc-activex-controls-optimization.md)<br/>
[Klasa COleControl](reference/colecontrol-class.md)<br/>
[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kreator kontrolek ActiveX MFC](reference/mfc-activex-control-wizard.md)<br/>
[Kontrolki ActiveX MFC: malowanie kontrolki ActiveX](mfc-activex-controls-painting-an-activex-control.md)
