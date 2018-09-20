---
title: Optymalizacja rysowania formantów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cf929f55b2333bf40cf6fd4ac2588ce17842312
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377789"
---
# <a name="optimizing-control-drawing"></a>Optymalizacja rysowania formantów

Gdy formant jest zobowiązany do rysowania się do kontekstu urządzenia dostarczonych kontenerów, zwykle wybiera obiekty GDI (na przykład pióra, pędzli i czcionki) do kontekstu urządzenia, przeprowadza jego operacji rysowania i przywraca poprzednie obiekty GDI. Jeśli kontener ma wiele formantów, które mają być tworzone w tym samym kontekście urządzenia i każdej kontrolki wybiera obiekty GDI, który wymaga, można zapisać czasu, jeśli kontrolki nie należy przywracać indywidualnie wcześniej wybrane obiekty. Po rysowania wszystkie kontrolki kontenera automatycznie można przywrócić oryginalnych obiektów.

Aby wykryć, czy kontener obsługuje tej techniki, można wywołać kontrolki [COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) funkcja elementu członkowskiego. Jeśli ta funkcja zwróci **TRUE**, formant pominąć krok normalne przywracania wcześniej wybrane obiekty.

Należy wziąć pod uwagę formant, który ma (niezoptymalizowane) `OnDraw` funkcji:

[!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]

Pióro i pędzla, w tym przykładzie są zmiennych lokalnych, co oznacza, destruktory zostanie wywołana, gdy wykraczają poza zakres (gdy `OnDraw` funkcja kończy się). Destruktory podejmie próbę usunięcia odpowiednie obiekty GDI. Ale one nie powinny być usuwane Jeśli planujesz opuścić je zaznaczone w kontekście urządzenia po powrocie z `OnDraw`.

Aby zapobiec [CPen](../mfc/reference/cpen-class.md) i [CBrush](../mfc/reference/cbrush-class.md) obiekty są niszczone, gdy `OnDraw` zostanie zakończone, przechowywać je w zmiennych elementu członkowskiego zamiast zmiennych lokalnych. W deklaracji klasy formantu Dodaj deklaracje dwóch nowych zmiennych elementu członkowskiego:

[!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]

Następnie `OnDraw` funkcja może zostać przepisane, w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]

W tym podejściu unika pióra i pędzla co godzina utworzenia `OnDraw` jest wywoływana. Poprawa prędkości pochodzi kosztem obsługi danych dodatkowego wystąpienia.

Zmiana właściwości ForeColor lub BackColor pióra lub pędzla należy utworzyć ponownie. Aby to zrobić, należy zastąpić [OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) i [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) elementów członkowskich:

[!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Na koniec wyeliminowanie niepotrzebnych `SelectObject` wywołań, zmodyfikuj `OnDraw` w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)<br/>
[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Kontrolki ActiveX MFC: malowanie kontrolki ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)

