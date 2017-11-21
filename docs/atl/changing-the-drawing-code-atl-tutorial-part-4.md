---
title: "Zmiana kodu rysującego (ATL — samouczek, część 4) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords: _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bc0c5ab0a76d77898b2249f63c699f76b10a628b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Zmiana kodu rysującego (ATL — Samouczek, część 4)
Domyślnie kod rysowania formantu Wyświetla kwadrat i tekst **PolyCtl**. W tym kroku zostanie zmieniony kod, aby wyświetlić ciekawsze. Obejmuje następujące zadania:  
  
-   Modyfikowanie pliku nagłówka  
  
-   Modyfikowanie `OnDraw` — funkcja  
  
-   Dodawanie metody do obliczania punktów wielokąta  
  
-   Inicjowanie kolor wypełnienia  
  
## <a name="modifying-the-header-file"></a>Modyfikowanie pliku nagłówka  
 Rozpocznij od dodania obsługę funkcje matematyczne `sin` i `cos`, należy obliczyć punktów wielokąta i tworząc tablicę do przechowywania pozycji.  
  
#### <a name="to-modify-the-header-file"></a>Aby zmodyfikować plik nagłówka  
  
1.  Dodaj wiersz `#include <math.h>` PolyCtl.h na początku. Na początku pliku powinna wyglądać następująco:  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  Po punktów wielokąta mają być obliczane, będą przechowywane w tablicy typu `POINT`, a więc Dodaj tablicy po definicji `m_nSides` w PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## <a name="modifying-the-ondraw-method"></a>Modyfikowanie OnDraw — metoda  
 Teraz należy zmodyfikować `OnDraw` w PolyCtl.h metody. Należy dodać kodu tworzy nowy pióra i pędzla z do rysowania programu wielokąta, a następnie wywołuje `Ellipse` i `Polygon` funkcji Win32 API do rysowania rzeczywistego wykonania.  
  
#### <a name="to-modify-the-ondraw-function"></a>Aby zmodyfikować funkcja OnDraw  
  
1.  Zastąp istniejące `OnDraw` metody w PolyCtl.h następującym kodem:  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Dodawanie metody do obliczania punktów wielokąta  
 Dodaj metodę o nazwie `CalcPoints`, który będzie obliczać współrzędne punktów tworzących wielokąt obwodu. Te obliczenia w oparciu zmiennej RECT, która została przekazana do funkcji.  
  
#### <a name="to-add-the-calcpoints-method"></a>Aby dodać metodę CalcPoints  
  
1.  Dodawanie deklaracji `CalcPoints` do `IPolyCtl` publicznej części `CPolyCtl` klasy w PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     Ostatnia część sekcji publicznego `CPolyCtl` klasy będzie wyglądać następująco:  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  Dodaj ta implementacja `CalcPoints` funkcja na końcu PolyCtl.cpp:  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## <a name="initializing-the-fill-color"></a>Inicjowanie kolor wypełnienia  
 Inicjowanie `m_clrFillColor` kolorem domyślne.  
  
#### <a name="to-initialize-the-fill-color"></a>Aby zainicjować kolor wypełnienia  
  
1.  Użyj jako domyślny kolor zielony, przez dodanie tego wiersza, aby `CPolyCtl` konstruktora w PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 Konstruktor teraz wygląda następująco:  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu  
 Odbuduj formantu. Upewnij się, że plik PolyCtl.htm jest zamknięty, jeśli jest nadal otwarty, a następnie kliknij przycisk **kompilacji wielokąta** na **kompilacji** menu. Można wyświetlić kontroli ponownie ze strony PolyCtl.htm, ale teraz używać kontener testu formantu ActiveX.  
  
#### <a name="to-use-the-activex-control-test-container"></a>Aby użyć kontener testu formantu ActiveX  
  
1.  Skompilować i uruchomić kontener testu formantu ActiveX. Aby uzyskać więcej informacji, zobacz [TSTCON próbki: Kontener testu formantu ActiveX](../visual-cpp-samples.md).  
  
2.  W kontenerze testowym na **Edytuj** menu, kliknij przycisk **Wstaw nowy formant**.  
  
3.  Zlokalizuj formant, która będzie wywoływana `PolyCtl Class`i kliknij przycisk **OK**. Zostanie wyświetlony zielony trójkąt w okręgu.  
  
 Spróbuj zmienić liczbę stron, wykonując następną procedurę. Aby zmodyfikować właściwości podwójną interfejsu z kontenera testu, należy użyć **wywołania metody**.  
  
#### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Aby zmodyfikować właściwości formantu z kontenera testu  
  
1.  W kontenerze testowym kliknij **wywołania metody** na **kontroli** menu.  
  
     **Wywołania metody** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz **PropPut** wersji **strony** właściwość z **nazwę metody** pole listy rozwijanej.  
  
3.  Typ `5` w **wartość parametru** kliknij **ustaw wartość**i kliknij przycisk **Invoke**.  
  
 Należy pamiętać, że kontrolka nie ulega zmianie. Mimo że wewnętrznie zmianie liczby stron przez ustawienie `m_nSides` zmiennej, to nie spowodowało formantu do odświeżenia. Jeśli Przełącz do innej aplikacji, a następnie przełączać się do kontenera testu, będą dostępne, czy formant ma odowieżany i ma prawidłowy numer strony.  
  
 Aby rozwiązać ten problem, dodaj wywołanie do `FireViewChange` funkcji zdefiniowanej w `IViewObjectExImpl`po Ustaw liczbę stron. Jeśli formant jest uruchomiony w osobnym oknie `FireViewChange` wywoła `InvalidateRect` metody bezpośrednio. Jeśli formant jest uruchomiony bez okien, `InvalidateRect` metoda zostanie wywołana w interfejsie lokacji kontenera. Dzięki temu formantu do samej siebie odświeżenia.  
  
#### <a name="to-add-a-call-to-fireviewchange"></a>Aby dodać wywołanie FireViewChange  
  
1.  Zaktualizuj PolyCtl.cpp przez dodanie wywołanie `FireViewChange` do `put_Sides` metody. Po zakończeniu, `put_Sides` metoda powinna wyglądać następująco:  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 Po dodaniu `FireViewChange`, skompiluj ponownie i spróbuj ponownie kontener testu formantu ActiveX kontrolki. Teraz po zmiany liczby stron i kliknięciu przycisku `Invoke`, powinny pojawić się kontrolka zmienić natychmiast.  
  
 W następnym kroku należy dodać zdarzenie.  
  
 [Wróć do kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [Do kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)   
 [Testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md)

