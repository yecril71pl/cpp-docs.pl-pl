---
title: Umieszczanie kontrolki na stronie sieci Web (ALT — Samouczek, część 7)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
ms.openlocfilehash: db6dcc57ff9f3748d802e76617ef18dea8f9506c
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344356"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Umieszczanie kontrolki na stronie sieci Web (ALT — Samouczek, część 7)

Formant jest już ukończona. Aby zobaczyć swój formant działający w sytuacji rzeczywistej, umieścić go na stronie sieci Web. Plik HTML, który zawiera formant został utworzony po zdefiniowaniu formantu. Otwórz plik PolyCtl.htm z **Eksploratora rozwiązań**, i zobaczysz swój formant na stronie sieci Web.

W tym kroku należy dodać funkcje do formantu i skrypt strony sieci Web w celu reagowania na zdarzenia. Zmodyfikujesz również formant aby pozwolić programowi Internet Explorer wiedzieć, że formant jest bezpieczny dla skryptów.

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

Kontrolka nie jeszcze nic, więc zmieniasz strony sieci Web w celu reagowania na zdarzenia, które wysyłasz.

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

Dodano kilka kod VBScript, który pobiera właściwość boki z formantu. Zwiększa liczbę boków o jeden, po kliknięciu wewnątrz formantu. Jeśli klikniesz poza kontrolą, zmniejszasz liczbę boków o jeden.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Wskazującą, czy formant jest bezpieczny dla skryptów

Można wyświetlić strony sieci Web za pomocą kontrolki tylko w programie Internet Explorer. Inne przeglądarki nie obsługują już kontrolki ActiveX ze względu na słabe strony zabezpieczeń.

> [!NOTE]
> Jeśli formant nie jest widoczne, wiadomo, że niektóre przeglądarki wymagać dostosowania ustawień, aby uruchomić formanty ActiveX. Zajrzyj do dokumentacji w przeglądarce na temat włączania formantów ActiveX.

Oparte na bieżące ustawienia zabezpieczeń programu Internet Explorer, może pojawić się okno dialogowe Alert zabezpieczeń. Stwierdza, że formant może nie być bezpieczny dla skryptu i może potencjalnie uszkodzić. Na przykład gdyby istniał formant, który jest wyświetlany plik, ale również istniała `Delete` metody, która usuwa plik, będzie bezpiecznie tylko wyświetlić na stronie. Byłby bezpiecznie skryptu, ponieważ ktoś mógłby wywołać `Delete` metody.

> [!IMPORTANT]
> Na potrzeby tego samouczka możesz zmienić ustawienia zabezpieczeń w programie Internet Explorer, aby uruchomić formanty ActiveX, które nie zostały oznaczone jako bezpieczne. W Panelu sterowania kliknij **właściwości internetowe** i kliknij przycisk **zabezpieczeń** zmienić odpowiednie ustawienia. Po ukończeniu tego samouczka, należy zmienić ustawienia zabezpieczeń do ich stanu oryginalnego.

Możesz programowo powiadomić Internet Explorer, nie należy do wyświetlenia okna dialogowego Alert zabezpieczeń dla tego określonego formantu. Możesz zrobić to za pomocą `IObjectSafety` interfejsu. ATL dostarcza implementację tego interfejsu w klasie [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Aby dodać interfejs do formantu, Dodaj `IObjectSafetyImpl` do listy dziedziczonych klas i Dodaj wpis dla niego na mapie com.

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Aby dodać IObjectSafetyImpl do formantu

1. Dodaj następujący wiersz na końcu listy klasy dziedziczone w PolyCtl.h i Dodaj przecinek do poprzedniego wiersza:

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. Dodaj następujący wiersz do mapy COM w PolyCtl.h:

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu

Kompiluj wersję. Po zakończeniu kompilacji, otwórz plik PolyCtl.htm w przeglądarce ponownie. Tym razem strona sieci Web powinien być wyświetlany bezpośrednio bez **Alert bezpieczeństwa** okno dialogowe. Po kliknięciu wewnątrz wielokąta liczbę boków zwiększa się o jeden. Kliknij poza wielokątem, aby zmniejszyć liczbę boków.

[Wróć do kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>Następne kroki

Ten krok jest koniec samouczka ATL. Aby uzyskać łącza do informacji na temat biblioteki ATL, zobacz [ATL strony początkowej](../atl/active-template-library-atl-concepts.md).

## <a name="see-also"></a>Zobacz także

[Samouczek](../atl/active-template-library-atl-tutorial.md)
