---
title: Dodawanie strony właściwości (ALT — Samouczek, część 6)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: 9287b7a15e3653212ed6a5428cdfe5a530ececc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198516"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Dodawanie strony właściwości (ALT — Samouczek, część 6)

Strony właściwości są implementowane jako oddzielne obiekty COM, które zezwolić im na udostępnionych, jeśli jest to wymagane. W tym kroku wykonasz następujące zadania, aby dodać stronę właściwości do kontrolki:

- Tworzenie zasobu strony właściwości

- Dodawanie kodu do tworzenia i zarządzania nimi na stronie właściwości

- Dodawanie strony właściwości do kontrolki

## <a name="creating-the-property-page-resource"></a>Tworzenie zasobu strony właściwości

Aby dodać stronę właściwości do kontrolki, należy użyć szablonu strony właściwości ATL.

### <a name="to-add-a-property-page"></a>Aby dodać stronę właściwości

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `Polygon`.

1. W menu skrótów kliknij **Dodaj** > **nowy element**.

1. Z listy szablonów wybierz **ATL** > **strony właściwości ATL** i kliknij przycisk **Dodaj**.

1. Gdy **Kreator strony właściwości ATL** pojawi się, wprowadź *PolyProp* jako **krótki** nazwy.

1. Kliknij przycisk **ciągi** otworzyć **ciągi** stronie, a następnie wprowadź **& wielokąta** jako **tytuł**.

   **Tytuł** właściwości strony jest ciąg, który pojawia się w karcie tej strony. **Ciąg dokumentu** znajduje się opis używającej ramka właściwości do umieszczenia w etykietce stan wiersza lub narzędzia. Pamiętaj, że ramka właściwości standardowych obecnie nie używać ten ciąg, dzięki czemu możesz pozostawić wartość domyślną. Nie wygeneruje **plik Pomocy** w chwili, więc Usuń wpis, w tym polu tekstowym.

1. Kliknij przycisk **Zakończ**, i zostanie utworzony obiekt strony właściwości.

Są tworzone trzy następujące pliki:

|Plik|Opis|
|----------|-----------------|
|PolyProp.h|Zawiera klasę C++ `CPolyProp`, który implementuje stronę właściwości.|
|PolyProp.cpp|Zawiera plik PolyProp.h.|
|PolyProp.rgs|Skrypt rejestru, który rejestruje obiekt strony właściwości.|

Również są wprowadzane następujące zmiany kodu:

- Nowa strona właściwości jest dodawana do mapy zapisu obiektu w Polygon.cpp.

- `PolyProp` Klasy są dodawane do pliku Polygon.idl.

- Nowy plik skryptu rejestru PolyProp.rgs zostanie dodany do zasobu projektu.

- Szablonu okna dialogowego zostanie dodany do zasobu projektu dla strony właściwości.

- Ciągi właściwości, które można określić są dodawane do tabeli ciągów zasobów.

Teraz Dodaj pola, które mają być wyświetlane na stronie właściwości.

### <a name="to-add-fields-to-the-property-page"></a>Aby dodać pola do strony właściwości

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik zasobu Polygon.rc. Spowoduje to otwarcie **widok zasobów**.

1. W **widok zasobów**, rozwiń węzeł `Dialog` węzła i kliknij dwukrotnie plik `IDD_POLYPROP`. Należy pamiętać, że zostanie wyświetlone okno dialogowe jest pusta, z wyjątkiem etykietę, która informuje Wprowadź tutaj swoje formanty.

1. Wybierz tej etykiety i zmień go ciągiem `Sides:` , zmieniając **podpis** tekstu w **właściwości** okna.

1. Zmienić rozmiar pola etykiety, tak aby mieścił się rozmiar tekstu.

1. Przeciągnij **Edytuj kontrolkę** z **przybornika** z prawej strony etykiety.

1. Na koniec zmień **identyfikator** kontrolki edycji `IDC_SIDES` przy użyciu **właściwości** okna.

Na tym kończy proces tworzenia zasobu strony właściwości.

## <a name="adding-code-to-create-and-manage-the-property-page"></a>Dodawanie kodu do tworzenia i zarządzania nimi na stronie właściwości

Teraz, po utworzeniu zasobu strony właściwości, należy napisać kod implementacji.

Najpierw należy włączyć `CPolyProp` klasy, aby ustawić liczbę boków obiektu podczas **Zastosuj** naciśnięciu przycisku.

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Aby zmodyfikować funkcję Zastosuj, aby ustawić liczbę boków

1. Zastąp `Apply` funkcji w PolyProp.h następującym kodem:

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

Strona właściwości może mieć więcej niż jeden klient dołączony w czasie, więc `Apply` funkcji w pętli wokół i wywołuje `put_Sides` na każdym komputerze klienckim z wartością pobierane pola edycji. Używasz [CComQIPtr](../atl/reference/ccomqiptr-class.md) klasy, która wykonuje `QueryInterface` dla każdego obiektu w celu uzyskania `IPolyCtl` interfejs z `IUnknown` interfejsu (przechowywane w `m_ppUnk` tablicy).

Kod sprawdza to ustawienie `Sides` właściwość tygodniowo. Jeśli nie powiedzie się, kod wyświetla okno komunikatu, wyświetlania szczegółów błędu z `IErrorInfo` interfejsu. Zazwyczaj kontener żąda obiektu dla `ISupportErrorInfo` interfejsu i wywołania `InterfaceSupportsErrorInfo` pierwszy, aby ustalić, czy obiekt obsługuje informacje o błędzie ustawienie. Można pominąć to zadanie.

[CComPtr](../atl/reference/ccomptr-class.md) pomoże Ci przy automatycznie zliczanie odwołań, więc nie trzeba wywoływać `Release` w interfejsie. `CComBSTR` pomoże Ci przy użyciu przetwarzania BSTR, dzięki czemu nie trzeba wykonać końcowe `SysFreeString` wywołania. Możesz także użyć jednej z różnych klas konwersji ciągów, dzięki czemu można przekonwertować BSTR, jeśli to konieczne, (jest to dlaczego makro USES_CONVERSION jest na początku funkcji).

Należy również ustawić flagę zanieczyszczone na stronie właściwości, aby wskazać, że **Zastosuj** przycisku powinno być włączone. Ten problem wystąpi, gdy użytkownik zmieni wartość w **boki** pole edycji.

### <a name="to-handle-the-apply-button"></a>Aby obsługa przycisku Zastosuj

1. W **Widok klas**, kliknij prawym przyciskiem myszy `CPolyProp` i kliknij przycisk **właściwości** w menu skrótów.

1. W **właściwości** okna, kliknij przycisk **zdarzenia** ikony.

1. Rozwiń `IDC_SIDES` węzła listy zdarzeń.

1. Wybierz `EN_CHANGE`, a z menu rozwijanego po prawej stronie kliknij pozycję  **\<Dodaj > OnEnChangeSides**. `OnEnChangeSides` Polyprop.h w celu wykonania procedury obsługi Polyprop.cpp zostanie dodana deklaracja procedury obsługi.

Następnie zmodyfikujesz program obsługi.

### <a name="to-modify-the-onenchangesides-method"></a>Aby zmodyfikować metodę OnEnChangeSides

1. Dodaj następujący kod w Polyprop.cpp do `OnEnChangeSides` — metoda (usuwanie wszelki kod, który Kreator ważną):

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

`OnEnChangeSides` zostanie wywołana kiedy `WM_COMMAND` wiadomość jest wysyłana za pomocą `EN_CHANGE` powiadomienie o `IDC_SIDES` kontroli. `OnEnChangeSides` następnie wywołuje `SetDirty` i przekazuje wartość TRUE, aby wskazać, na stronie właściwości teraz został zmieniony i **Zastosuj** przycisku powinno być włączone.

## <a name="adding-the-property-page-to-the-control"></a>Dodawanie strony właściwości do kontrolki

Szablon strony właściwości ATL i Kreator nie dodawaj strony właściwości do kontrolki dla Ciebie automatycznie, ponieważ może istnieć wiele formantów w projekcie. Należy dodać wpis do map właściwości formantu.

### <a name="to-add-the-property-page"></a>Aby dodać stronę właściwości

1. Otwórz PolyCtl.h i dodaj następujące wiersze do mapy właściwości:

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

Mapy właściwości formantów wygląda teraz następująco:

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

Można dodano `PROP_PAGE` makra o identyfikatorze CLSID strony właściwości, ale jeśli używasz `PROP_ENTRY` — makro, jak pokazano, `Sides` wartość właściwości jest również zapisywana, gdy kontrolka jest zapisywany.

Trzy parametry do makra są opisu właściwości, DISPID, właściwości i CLSID strony właściwości, która ma właściwość na nim. Jest to przydatne, jeśli na przykład załadować formantu w języku Visual Basic i ustaw liczbę stron w czasie projektowania. Ponieważ liczbę boków jest zapisywany, gdy użytkownik ponownie Załaduj projekt języka Visual Basic, zostanie przywrócony liczbę boków.

## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu

Teraz tworzenie tej kontrolki i wstawianie kontener testu kontrolki ActiveX. W **kontener testu**na **Edytuj** menu, kliknij przycisk **obiektu klasy PolyCtl**. Na stronie właściwości pojawia się z informacjami, którą dodałeś.

**Zastosuj** przycisk jest początkowo wyłączone. Zacznij wpisywać ciąg wartości w **boki** pole i **Zastosuj** uaktywni przycisku. Po wprowadzeniu wszystkich wartości, kliknij przycisk **Zastosuj** przycisku. Zmiany wyświetlania formantów i **Zastosuj** przycisk ponownie jest wyłączony. Spróbuj wprowadzić nieprawidłową wartość. Pojawi się okno komunikatu, zawierający opis błędu, który ustawiony z `put_Sides` funkcji.

Następnie należy umieścić swój formant na stronie sieci Web.

[Wróć do kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [do kroku 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>Zobacz także

[Samouczek](../atl/active-template-library-atl-tutorial.md)
