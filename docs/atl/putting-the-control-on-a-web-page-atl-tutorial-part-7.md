---
title: Umieszczanie kontrolki na stronie sieci Web (ALT — samouczek, część 7) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edc45522aaff12077de6115105b344ecf41e187e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762827"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Umieszczanie kontrolki na stronie sieci Web (ALT — Samouczek, część 7)

Formant jest już ukończona. Aby zobaczyć swój formant działający w sytuacji rzeczywistej, umieścić go na stronie sieci Web. Plik HTML, który zawiera formant został utworzony po zdefiniowaniu formantu. Otwórz plik PolyCtl.htm z **Eksploratora rozwiązań**, i zobaczysz swój formant na stronie sieci Web.

W tym kroku zostanie skrypt strony sieci Web w celu reagowania na zdarzenia. Zmodyfikujesz również formant aby pozwolić programowi Internet Explorer wiedzieć, że formant jest bezpieczny dla skryptów.

## <a name="scripting-the-web-page"></a>Skrypty strony sieci Web

Formant jeszcze nic nie, więc zmieniasz strony sieci Web w celu reagowania na zdarzenia, które wysyłasz.

#### <a name="to-script-the-web-page"></a>Aby utworzyć skrypt strony sieci Web

1. Otwórz plik PolyCtl.htm i wybierz widok HTML. Dodaj następujące wiersze kodu HTML. Powinny one zostać dodane po `</OBJECT>` lecz przed `</BODY>`.

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            PolyCtl.Sides = PolyCtl.Sides + 1
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            PolyCtl.Sides = PolyCtl.Sides - 1
        End Sub
    -->
    </SCRIPT>
    ```

2. Zapisz plik HTM.

Dodano kilka kod w języku VBScript, który pobiera właściwość boki z formantu i zwiększa o jeden liczbę boków, po kliknięciu wewnątrz formantu. Jeśli klikniesz poza kontrolą, zmniejszasz liczbę boków o jeden.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Wskazującą, czy formant jest bezpieczny dla skryptów

Można wyświetlić strony sieci Web za pomocą kontrolki w programie Internet Explorer lub wygodniej, używając widoku przeglądarki sieci Web, które są wbudowane w Visual C++. Aby wyświetlić formant w widoku przeglądarki sieci Web, kliknij prawym przyciskiem myszy plik PolyCtl.htm, a następnie kliknij przycisk **Pokaż w przeglądarce**.

Oparte na bieżące ustawienia zabezpieczeń programu Internet Explorer, może pojawić się okno dialogowe pola stwierdzający, że formant może nie być bezpieczny dla skryptu i może potencjalnie uszkodzić Alert zabezpieczeń. Na przykład gdyby istniał formant, który jest wyświetlany plik, ale również istniała `Delete` metody, która usuwa plik, będzie bezpiecznie tylko wyświetlić na stronie. Byłby bezpiecznie skryptu, ponieważ ktoś mógłby wywołać `Delete` metody.

> [!IMPORTANT]
> Na potrzeby tego samouczka możesz zmienić ustawienia zabezpieczeń w programie Internet Explorer, aby uruchomić formanty ActiveX, które nie zostały oznaczone jako bezpieczne. W Panelu sterowania kliknij **właściwości internetowe** i kliknij przycisk **zabezpieczeń** zmienić odpowiednie ustawienia. Po ukończeniu tego samouczka, należy zmienić ustawienia zabezpieczeń do ich stanu oryginalnego.

Możesz programowo powiadomić Internet Explorer, nie trzeba wyświetlenia okna dialogowego Alert zabezpieczeń dla tego określonego formantu. Można to zrobić za pomocą `IObjectSafety` interfejsu, ATL dostarcza implementację tego interfejsu w klasie [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Aby dodać interfejs do formantu, Dodaj `IObjectSafetyImpl` do listy dziedziczonych klas i Dodaj wpis dla niego na mapie com.

#### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Aby dodać IObjectSafetyImpl do formantu

1. Dodaj następujący wiersz na końcu listy klasy dziedziczone w PolyCtl.h i Dodaj przecinek do poprzedniego wiersza:

[!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

2. Dodaj następujący wiersz do mapy COM w PolyCtl.h:

[!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu

Kompiluj wersję. Po zakończeniu kompilacji, otwórz plik PolyCtl.htm w przeglądarce ponownie. Tym razem strona sieci Web powinna być wyświetlana bezpośrednio, bez okna dialogowego Alert bezpieczeństwa. Kliknij wewnątrz wielokąta; Liczba boków zwiększa się o jeden. Kliknij poza wielokątem, aby zmniejszyć liczbę boków. Jeśli użytkownik próbuje zmniejszyć liczbę boków do poniżej trzech, pojawi się komunikat o błędzie, który został ustawiony.

[Wróć do kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>Następne kroki

To jest koniec samouczka ATL. Aby uzyskać łącza do informacji na temat biblioteki ATL, zobacz [ATL strony początkowej](../atl/active-template-library-atl-concepts.md).

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)
