---
title: Zmiana kodu rysującego (ALT — samouczek, część 4) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0da5f024e8dffd0115ba9bdbd6cf34f3f7c68a0e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065793"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Zmiana kodu rysującego (ATL — Samouczek, część 4)

Domyślnie wyświetla kod rysowania kontrolki kwadratu i tekst **PolyCtl**. W tym kroku zmienisz kod, aby wyświetlić ciekawsze. Obejmuje następujące zadania:

- Modyfikowanie pliku nagłówka

- Modyfikowanie `OnDraw` — funkcja

- Dodawanie metody do obliczania punktów wielokąta

- Inicjowanie kolor wypełnienia

## <a name="modifying-the-header-file"></a>Modyfikowanie pliku nagłówka

Rozpocznij, dodając obsługę funkcji matematycznych `sin` i `cos`, który będzie używany obliczania punktów wielokąta i tworząc tablicę do przechowywania umieszcza.

#### <a name="to-modify-the-header-file"></a>Aby zmodyfikować plik nagłówkowy

1. Dodaj wiersz `#include <math.h>` na początku PolyCtl.h. Na górze pliku powinien wyglądać następująco:

     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

2. Gdy punkty wielokąta są obliczane, będą przechowywane w tablicy typu `POINT`, dlatego Dodaj macierz po definicji `m_nSides` w PolyCtl.h:

     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Modyfikowanie OnDraw — metoda

Teraz należy zmodyfikować `OnDraw` metody w PolyCtl.h. Kod należy dodać tworzy nowy pióra i pędzla, za pomocą którego można narysować wielokąt usługi, a następnie wywołuje `Ellipse` i `Polygon` funkcji Win32 API do wykonania rzeczywistego rysowania.

#### <a name="to-modify-the-ondraw-function"></a>Aby zmodyfikować OnDraw — funkcja

1. Zastąp istniejące `OnDraw` metody w PolyCtl.h następującym kodem:

     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Dodawanie metody do obliczania punktów wielokąta

Dodaj metodę o nazwie `CalcPoints`, która obliczy współrzędne punktów, które tworzą obwód wielokąta. Te obliczenia będzie zależeć od zmiennej Prostokąt, który jest przekazywany do funkcji.

#### <a name="to-add-the-calcpoints-method"></a>Aby dodać metodę CalcPoints

1. Dodaj deklarację `CalcPoints` do `IPolyCtl` publicznej części `CPolyCtl` klasy w PolyCtl.h:

     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

     Ostatnia część sekcji publicznej `CPolyCtl` klasy będzie wyglądać następująco:

     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

2. Dodaj tej implementacji `CalcPoints` funkcji do końca PolyCtl.cpp:

     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>Inicjowanie kolor wypełnienia

Inicjowanie `m_clrFillColor` kolorem domyślne.

#### <a name="to-initialize-the-fill-color"></a>Aby zainicjować kolor wypełnienia

1. Pełnić domyślny kolor zielony, dodając ten wiersz, aby `CPolyCtl` konstruktora w PolyCtl.h:

     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Konstruktor wygląda teraz następująco:

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu

Ponownie skompiluj kontrolkę. Upewnij się, że plik PolyCtl.htm jest zamknięte, jeśli jest nadal otwarty, a następnie kliknij przycisk **Kompiluj Wielokąt** na **kompilacji** menu. Można wyświetlać kontroli ponownie na stronie PolyCtl.htm, ale tym razem użyj kontener testu kontrolki ActiveX.

#### <a name="to-use-the-activex-control-test-container"></a>Aby użyć kontener testu kontrolki ActiveX

1. Skompilować i uruchomić kontener testu kontrolki ActiveX. Aby uzyskać więcej informacji, zobacz [TSTCON próbki: Kontener testu kontrolki ActiveX](../visual-cpp-samples.md).

2. W kontenerze testów na **Edytuj** menu, kliknij przycisk **Wstaw nową kontrolkę**.

3. Znajdź kontrolki, która będzie wywoływana `PolyCtl Class`i kliknij przycisk **OK**. Zostanie wyświetlony zielony trójkąt w okręgu.

Spróbuj zmienić liczbę boków, wykonując następną procedurę. Aby zmodyfikować właściwości podwójnego interfejsu z kontenera testów, należy użyć **wywołania metody**.

#### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Aby zmodyfikować właściwości kontrolki z kontenera testu

1. Kontener testu kliknij **wywołania metody** na **kontroli** menu.

     **Wywołaj metodę** zostanie wyświetlone okno dialogowe.

2. Wybierz **PropPut** wersję **boki** właściwość **nazwę metody** pole listy rozwijanej.

3. Typ `5` w **wartość parametru** kliknij **ustaw wartość**i kliknij przycisk **Invoke**.

Należy pamiętać, że kontrolka nie zmienia się. Mimo że wewnętrznie zmienić liczbę boków, ustawiając `m_nSides` zmiennej, to nie spowodował, że formant do odświeżenia. Po przełączeniu do innej aplikacji i przejdź z powrotem do kontenera testu, znajdziesz, odświeżana ma i ma poprawną liczbę boków kontrolki.

Aby rozwiązać ten problem, dodaj wywołanie `FireViewChange` funkcję, zdefiniowaną w `IViewObjectExImpl`, po ustawieniu liczbę boków. Jeśli kontrolka jest uruchomiona w osobnym oknie `FireViewChange` wywoła `InvalidateRect` bezpośrednio metodę. Jeśli kontrolka działa bez okien, `InvalidateRect` metoda zostanie wywołana w interfejsie witryny kontenera. Zmusza to formant do odświeżenia sam.

#### <a name="to-add-a-call-to-fireviewchange"></a>Aby dodać wywołanie FireViewChange

1. Aktualizuj PolyCtl.cpp, dodając wywołania `FireViewChange` do `put_Sides` metody. Po zakończeniu, `put_Sides` metoda powinna wyglądać następująco:

     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Po dodaniu `FireViewChange`, skompiluj i spróbuj kontroli ponownie za kontener testu kontrolki ActiveX. Tym razem, gdy Zmień liczbę boków i kliknij `Invoke`, powinien zostać wyświetlony kontroli zmiany od razu.

W następnym kroku dodasz zdarzenie.

[Wróć do kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [do kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)<br/>
[Testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md)

