---
title: Zmiana kodu rysującego (ATL — Samouczek, część 4)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: df89837e8f453443dc092a1b96e9c3f395fa2353
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127383"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Zmiana kodu rysującego (ATL — Samouczek, część 4)

Domyślnie kod rysowania kontrolki Wyświetla kwadrat i tekst **PolyCtl**. W tym kroku zmienisz kod w taki sposób, aby wyświetlał coś bardziej interesujący. Uwzględnione są następujące zadania:

- Modyfikowanie pliku nagłówkowego

- Modyfikowanie funkcji `OnDraw`

- Dodawanie metody w celu obliczenia punktów wielokąta

- Inicjowanie koloru wypełnienia

## <a name="modifying-the-header-file"></a>Modyfikowanie pliku nagłówkowego

Zacznij od dodania obsługi funkcji matematycznych `sin` i `cos`, które będą używane do obliczania punktów wielokątów, a następnie tworząc tablicę do przechowywania pozycji.

### <a name="to-modify-the-header-file"></a>Aby zmodyfikować plik nagłówka

1. Dodaj wiersz `#include <math.h>` na górze PolyCtl. h. Góra pliku powinna wyglądać następująco:

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Zaimplementuj interfejs `IProvideClassInfo`, aby dostarczyć informacje o metodzie dla kontrolki, dodając następujący kod do PolyCtl. h. W klasie `CPolyCtl` Zastąp wiersz:

    ```cpp
    public CComControl<CPolyCtl>
    ```

    elementem

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    i w `BEGIN_COM_MAP(CPolyCtl)`Dodaj wiersze:

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. Po obliczeniu punktów wielokąta zostaną one zapisane w tablicy typu `POINT`, więc Dodaj tablicę po instrukcji definicji `short m_nSides;` w PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Modyfikowanie metody OnDraw

Teraz należy zmodyfikować metodę `OnDraw` w PolyCtl. h. Kod, który dodasz, tworzy nowe pióro i Pędzel, za pomocą których można narysować Wielokąt, a następnie wywołuje `Ellipse` i `Polygon` Win32 API funkcje, aby wykonać rzeczywiste Rysowanie.

### <a name="to-modify-the-ondraw-function"></a>Aby zmodyfikować funkcję OnDraw

1. Zastąp istniejącą metodę `OnDraw` w PolyCtl. h następującym kodem:

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Dodawanie metody w celu obliczenia punktów wielokąta

Dodaj metodę o nazwie `CalcPoints`, która będzie obliczać współrzędne punktów, które tworzą obwód wielokąta. Te obliczenia będą oparte na zmiennej RECT, która jest przenoszona do funkcji.

### <a name="to-add-the-calcpoints-method"></a>Aby dodać metodę CalcPoints

1. Dodaj deklarację `CalcPoints` do sekcji publicznej `IPolyCtl` klasy `CPolyCtl` w PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    Ostatnia część publicznej sekcji klasy `CPolyCtl` będzie wyglądać następująco:

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. Dodaj tę implementację funkcji `CalcPoints` na końcu PolyCtl. cpp:

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>Inicjowanie koloru wypełnienia

Zainicjuj `m_clrFillColor` z domyślnym kolorem.

### <a name="to-initialize-the-fill-color"></a>Aby zainicjować kolor wypełnienia

1. Użyj zielonej jako koloru domyślnego poprzez dodanie tego wiersza do konstruktora `CPolyCtl` w PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Konstruktor wygląda teraz następująco:

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Kompilowanie i testowanie kontrolki

Ponownie skompiluj formant. Upewnij się, że plik PolyCtl. htm jest zamknięty, jeśli jest nadal otwarty, a następnie kliknij pozycję **Kompiluj Wielokąt** w menu **kompilacja** . Możesz ponownie wyświetlić formant na stronie PolyCtl. htm, ale ten czas użyje kontenera testów kontrolki ActiveX.

### <a name="to-use-the-activex-control-test-container"></a>Aby użyć kontenera testów kontrolki ActiveX

1. Kompiluj i uruchamiaj kontener testów kontrolki ActiveX. [Przykład TSTCON: kontener testowy kontrolki ActiveX](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) można znaleźć w witrynie GitHub.

    > [!NOTE]
    > W przypadku błędów dotyczących `ATL::CW2AEX`w programie Script. cpp należy zamienić wiersz `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` z `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`i wiersz `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` z `TRACE( "Source Text: %s\n", bstrSourceLineText );`.<br/>
    > W przypadku błędów dotyczących `HMONITOR`Otwórz StdAfx. h w projekcie `TCProps` i Zastąp:
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    > elementem
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. W **kontenerze Test**w menu **Edycja** kliknij polecenie **Wstaw nową kontrolkę**.

1. Znajdź swój formant, który zostanie wywołany `PolyCtl class`i kliknij przycisk **OK**. Zobaczysz zielony trójkąt w okręgu.

Spróbuj zmienić liczbę stron, wykonując następną procedurę. Aby zmodyfikować właściwości na podwójnym interfejsie z poziomu **kontenera testowego**, użyj **metody Invoke**.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Aby zmodyfikować właściwość kontrolki z kontenera testów

1. W **kontenerze Test**kliknij polecenie **wywołaj metody** w menu **sterowania** .

    Zostanie wyświetlone okno dialogowe **wywoływanie metody** .

1. W polu listy rozwijanej **Nazwa metody** wybierz **propput** wersję właściwości **boki** .

1. W polu **wartość parametru** wpisz `5` kliknij pozycję **Ustaw wartość**, a następnie kliknij pozycję **Wywołaj**.

Należy zauważyć, że formant nie zmienia się. Mimo że liczba stron wewnętrznie została zmieniona przez ustawienie zmiennej `m_nSides`, to nie powodowało odświeżenia formantu. Jeśli przełączysz się do innej aplikacji, a następnie wrócisz do **kontenera testowego**, zobaczysz, że formant został odmalowany i ma poprawną liczbę boków.

Aby rozwiązać ten problem, należy dodać wywołanie funkcji `FireViewChange` zdefiniowanej w `IViewObjectExImpl`, po ustawieniu liczby boków. Jeśli kontrolka działa w osobnym oknie, `FireViewChange` wywoła metodę `InvalidateRect` bezpośrednio. Jeśli kontrolka działa bez okna, Metoda `InvalidateRect` zostanie wywołana w interfejsie lokacji kontenera. Powoduje to wymuszenie odświeżenia formantu.

### <a name="to-add-a-call-to-fireviewchange"></a>Aby dodać wywołanie do FireViewChange

1. Zaktualizuj PolyCtl. cpp przez dodanie wywołania do `FireViewChange` do metody `put_Sides`. Po zakończeniu metoda `put_Sides` powinna wyglądać następująco:

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Po dodaniu `FireViewChange`Odbuduj i spróbuj ponownie wykonać kontrolę w kontenerze testów kontrolki ActiveX. Tym razem, gdy zmienisz liczbę boków i klikniesz przycisk `Invoke`, kontrolka powinna być natychmiast widoczna.

W następnym kroku dodasz zdarzenie.

[Powrót do kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [w kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)<br/>
[Testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md)
