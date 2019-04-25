---
title: Umieszczanie kontrolki na stronie sieci Web (ALT — Samouczek, część 7)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
ms.openlocfilehash: baf0ca56ae7512ac76f64b29e3060e0749c083c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261543"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Umieszczanie kontrolki na stronie sieci Web (ALT — Samouczek, część 7)

Formant jest już ukończona. Aby zobaczyć swój formant działający w sytuacji rzeczywistej, umieścić go na stronie sieci Web. Plik HTML, który zawiera formant został utworzony po zdefiniowaniu formantu. Otwórz plik PolyCtl.htm z **Eksploratora rozwiązań**, i zobaczysz swój formant na stronie sieci Web.

W tym kroku możesz dodawać funkcje do formantu i skrypt strony sieci Web w celu reagowania na zdarzenia. Zmodyfikujesz również formant aby pozwolić programowi Internet Explorer wiedzieć, że formant jest bezpieczny dla skryptów.

## <a name="adding-new-functionality"></a>Dodawanie nowej funkcji

### <a name="to-add-control-features"></a>Aby dodać funkcje kontroli

1. Otwórz PolyCtl.cpp, a następnie zastąp następujący kod:

    ```cpp
    if (PtInRegion(hRgn, xPos, yPos))
        Fire_ClickIn(xPos, yPos);
    else
        Fire_ClickOut(xPos, yPos);
    ```

    with

    ```cpp
    short temp = m_nSides;
    if (PtInRegion(hRgn, xPos, yPos))
    {
        Fire_ClickIn(xPos, yPos);
        put_Sides(++temp);
    }
    else
    {
        Fire_ClickOut(xPos, yPos);
        put_Sides(--temp);
    }
    ```

Kształt będzie teraz dodawać i usuwać stronach w zależności od tego, gdzie należy kliknąć.

## <a name="scripting-the-web-page"></a>Skrypty strony sieci Web

Formant jeszcze nic nie, więc zmieniasz strony sieci Web w celu reagowania na zdarzenia, które wysyłasz.

### <a name="to-script-the-web-page"></a>Aby utworzyć skrypt strony sieci Web

1. Otwórz plik PolyCtl.htm i wybierz widok HTML. Dodaj następujące wiersze kodu HTML. Powinny one zostać dodane po `</OBJECT>` lecz przed `</BODY>`.

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - adding side")
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - removing side")
        End Sub
    -->
    </SCRIPT>
    ```

1. Zapisz plik HTM.

Dodano kilka kod w języku VBScript, który pobiera właściwość boki z formantu i zwiększa o jeden liczbę boków, po kliknięciu wewnątrz formantu. Jeśli klikniesz poza kontrolą, zmniejszasz liczbę boków o jeden.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Wskazującą, czy formant jest bezpieczny dla skryptów

Można wyświetlić strony sieci Web za pomocą kontrolki w programie Internet Explorer lub wygodniej, używając widoku przeglądarki sieci Web, które są wbudowane w Visual C++. Aby wyświetlić formant w widoku przeglądarki sieci Web, kliknij prawym przyciskiem myszy plik PolyCtl.htm, a następnie kliknij przycisk **Pokaż w przeglądarce**.

> [!NOTE]
> Jeśli formant nie jest widoczne, wiadomo, że niektóre przeglądarki wymagać dostosowania ustawień, aby uruchomić formanty ActiveX. Zapoznaj się dokumentacją przeglądarki dotyczące włączania kontrolek ActiveX.

Oparte na bieżące ustawienia zabezpieczeń programu Internet Explorer, może pojawić się okno dialogowe pola stwierdzający, że formant może nie być bezpieczny dla skryptu i może potencjalnie uszkodzić Alert zabezpieczeń. Na przykład gdyby istniał formant, który jest wyświetlany plik, ale również istniała `Delete` metody, która usuwa plik, będzie bezpiecznie tylko wyświetlić na stronie. Byłby bezpiecznie skryptu, ponieważ ktoś mógłby wywołać `Delete` metody.

> [!IMPORTANT]
> Na potrzeby tego samouczka możesz zmienić ustawienia zabezpieczeń w programie Internet Explorer, aby uruchomić formanty ActiveX, które nie zostały oznaczone jako bezpieczne. W Panelu sterowania kliknij **właściwości internetowe** i kliknij przycisk **zabezpieczeń** zmienić odpowiednie ustawienia. Po ukończeniu tego samouczka, należy zmienić ustawienia zabezpieczeń do ich stanu oryginalnego.

Możesz programowo powiadomić Internet Explorer, nie trzeba wyświetlenia okna dialogowego Alert zabezpieczeń dla tego określonego formantu. Można to zrobić za pomocą `IObjectSafety` interfejsu, ATL dostarcza implementację tego interfejsu w klasie [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Aby dodać interfejs do formantu, Dodaj `IObjectSafetyImpl` do listy dziedziczonych klas i Dodaj wpis dla niego na mapie com.

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Aby dodać IObjectSafetyImpl do formantu

1. Dodaj następujący wiersz na końcu listy klasy dziedziczone w PolyCtl.h i Dodaj przecinek do poprzedniego wiersza:

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. Dodaj następujący wiersz do mapy COM w PolyCtl.h:

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu

Kompiluj wersję. Po zakończeniu kompilacji, otwórz plik PolyCtl.htm w przeglądarce ponownie. Tym razem strona sieci Web powinien być wyświetlany bezpośrednio bez **Alert bezpieczeństwa** okno dialogowe. Kliknij wewnątrz wielokąta; Liczba boków zwiększa się o jeden. Kliknij poza wielokątem, aby zmniejszyć liczbę boków.

[Wróć do kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>Następne kroki

To jest koniec samouczka ATL. Aby uzyskać łącza do informacji na temat biblioteki ATL, zobacz [ATL strony początkowej](../atl/active-template-library-atl-concepts.md).

## <a name="see-also"></a>Zobacz także

[Samouczek](../atl/active-template-library-atl-tutorial.md)
