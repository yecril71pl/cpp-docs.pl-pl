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
ms.openlocfilehash: 8103e1e342756f9b715c1a0959ed256403e130bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-control-drawing"></a>Optymalizacja rysowania formantów
Gdy formant jest instrukcją do rysowania się do kontekstu urządzenia dostarczonych przez kontener, zazwyczaj wybiera obiekty GDI (na przykład pióra, pędzle i czcionki) do kontekstu urządzenia, wykonuje jego operacje rysowania i przywraca poprzednie obiekty GDI. Jeśli kontener ma wiele formantów, które mają być tworzone w tym samym kontekście urządzenia i każdej kontrolki wybiera obiekty GDI, które wymaga, czas może zostać zapisany, jeśli formanty nie przywracaj indywidualnie wcześniej wybrane obiekty. Po zostały wystawione wszystkie formanty, kontener może automatycznie Przywracanie oryginalnych obiektów.  
  
 Aby wykryć, czy kontener obsługuje ta technika, można wywołać formantu [COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) funkcję elementu członkowskiego. Jeśli ta funkcja zwraca **TRUE**, formantu można pominąć krok normalne przywracania wcześniej wybranych obiektów.  
  
 Należy wziąć pod uwagę formantu, który ma następujące (niezoptymalizowane) `OnDraw` funkcji:  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]  
  
 Pióro i pędzla w tym przykładzie są zmiennych lokalnych, co oznacza ich destruktory zostanie wywołany, gdy przejdą poza zakresem (gdy `OnDraw` funkcji kończy się). Destruktory podejmie próbę usunięcia odpowiednich obiektów GDI. Ale ich nie powinny być usuwane Planując pozostaw je wybrane do kontekstu urządzenia na zwracanie z `OnDraw`.  
  
 Aby zapobiec [cpen —](../mfc/reference/cpen-class.md) i [cbrush —](../mfc/reference/cbrush-class.md) obiektów z niszczony po `OnDraw` zakończeniu przechowywać je w zmiennych Członkowskich zamiast zmiennych lokalnych. W deklaracji klasy formantu Dodaj deklaracje dla dwa nowe zmienne Członkowskie:  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]  
  
 Następnie `OnDraw` funkcji można ponownie zapisać w następujący sposób:  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]  
  
 Takie podejście pozwala uniknąć tworzenie pióra i pędzla zawsze `OnDraw` jest wywoływana. Poprawa prędkości odbywa się kosztem zachowanie danych dodatkowego wystąpienia.  
  
 Zmiana właściwości ForeColor lub BackColor pióro lub pędzla musi zostać utworzona ponownie. Aby to zrobić, należy zastąpić [OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) i [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) funkcji elementów członkowskich:  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]  
  
 Na koniec aby wyeliminować niepotrzebne `SelectObject` wywołań, zmodyfikuj `OnDraw` w następujący sposób:  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty MFC ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md)   
 [Colecontrol — klasa](../mfc/reference/colecontrol-class.md)   
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)   
 [Kontrolki ActiveX MFC: malowanie kontrolki ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)

