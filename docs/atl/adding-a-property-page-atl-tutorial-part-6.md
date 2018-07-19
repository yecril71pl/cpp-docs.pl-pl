---
title: Dodawanie strony właściwości (ALT — samouczek, część 6) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32b89b36318800ff35bc78fee35f094f75bdf36e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848694"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Dodawanie strony właściwości (ALT — Samouczek, część 6)
Strony właściwości są implementowane jako oddzielne obiekty COM, które zezwolić im na udostępnionych, jeśli jest to wymagane. W tym kroku wykonasz następujące zadania, aby dodać stronę właściwości do kontrolki:  
  
-   Tworzenie zasobu strony właściwości  
  
-   Dodawanie kodu do tworzenia i zarządzania nimi na stronie właściwości  
  
-   Dodawanie strony właściwości do kontrolki  
  
## <a name="creating-the-property-page-resource"></a>Tworzenie zasobu strony właściwości  
 Aby dodać stronę właściwości do kontrolki, należy użyć Kreatora dodawania klasy ATL.  
  
#### <a name="to-add-a-property-page"></a>Aby dodać stronę właściwości  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy wielokąta.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
3.  Z listy szablonów wybierz **strony właściwości ATL** i kliknij przycisk **Dodaj**.  
  
4.  Gdy pojawi się Kreator strony właściwości ATL, wprowadź *PolyProp* jako **krótki** nazwy.  
  
5.  Kliknij przycisk **ciągi** otworzyć **ciągi** stronie, a następnie wprowadź **& wielokąta** jako **tytuł**.  
  
     **Tytuł** właściwości strony jest ciąg, który pojawia się w karcie tej strony. **Ciąg dokumentu** znajduje się opis używającej ramka właściwości do umieszczenia w etykietce stan wiersza lub narzędzia. Pamiętaj, że ramka właściwości standardowych obecnie nie używać ten ciąg, dzięki czemu możesz pozostawić wartość domyślną. Nie wygeneruje **plik Pomocy** w chwili, więc Usuń wpis, w tym polu tekstowym.  
  
6.  Kliknij przycisk **Zakończ**, i zostanie utworzony obiekt strony właściwości.  
  
 Są tworzone trzy następujące pliki:  
  
|Plik|Opis|  
|----------|-----------------|  
|PolyProp.h|Zawiera klasę C++ `CPolyProp`, który implementuje stronę właściwości.|  
|PolyProp.cpp|Zawiera plik PolyProp.h.|  
|PolyProp.rgs|Skrypt rejestru, który rejestruje obiekt strony właściwości.|  
  
 Również są wprowadzane następujące zmiany kodu:  
  
-   Nowa strona właściwości jest dodawana do mapy zapisu obiektu w Polygon.cpp.  
  
-   `PolyProp` Klasy są dodawane do pliku Polygon.idl.  
  
-   Nowy plik skryptu rejestru PolyProp.rgs zostanie dodany do zasobu projektu.  
  
-   Szablonu okna dialogowego zostanie dodany do zasobu projektu dla strony właściwości.  
  
-   Ciągi właściwości, które można określić są dodawane do tabeli ciągów zasobów.  
  
 Teraz Dodaj pola, które mają być wyświetlane na stronie właściwości.  
  
#### <a name="to-add-fields-to-the-property-page"></a>Aby dodać pola do strony właściwości  
  
1.  W Eksploratorze rozwiązań kliknij dwukrotnie plik zasobu Polygon.rc. Spowoduje to otwarcie widoku zasobów.  
  
2.  W widoku zasobu rozwiń węzeł okna dialogowego, a następnie kliknij dwukrotnie IDD_POLYPROP. Należy pamiętać, że zostanie wyświetlone okno dialogowe jest pusta, z wyjątkiem etykietę, która informuje Wprowadź tutaj swoje formanty.  
  
3.  Wybierz tej etykiety i zmień go ciągiem `Sides:` , zmieniając **podpis** tekstu w **właściwości** okna.  
  
4.  Zmienić rozmiar pola etykiety, tak aby mieścił się rozmiar tekstu.  
  
5.  Przeciągnij formant edycji z przybornika z prawej strony etykiety.  
  
6.  Na koniec zmień **identyfikator** kontrolki edycji `IDC_SIDES` w oknie właściwości.  
  
 Na tym kończy proces tworzenia zasobu strony właściwości.  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>Dodawanie kodu do tworzenia i zarządzania nimi na stronie właściwości  
 Teraz, po utworzeniu zasobu strony właściwości, należy napisać kod implementacji.  
  
 Najpierw należy włączyć `CPolyProp` klasy, aby ustawić liczbę boków obiektu podczas **Zastosuj** naciśnięciu przycisku.  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Aby zmodyfikować funkcję Zastosuj, aby ustawić liczbę boków  
  
1.  Zastąp `Apply` funkcji w PolyProp.h następującym kodem:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 Strona właściwości może mieć więcej niż jeden klient dołączony w czasie, więc `Apply` funkcji w pętli wokół i wywołuje `put_Sides` na każdym komputerze klienckim z wartością pobierane pola edycji. Używasz [CComQIPtr](../atl/reference/ccomqiptr-class.md) klasy, która wykonuje `QueryInterface` dla każdego obiektu w celu uzyskania `IPolyCtl` interfejs z `IUnknown` interfejsu (przechowywane w `m_ppUnk` tablicy).  
  
 Kod sprawdza to ustawienie `Sides` właściwość tygodniowo. Jeśli nie powiedzie się, kod wyświetla okno komunikatu, wyświetlania szczegółów błędu z `IErrorInfo` interfejsu. Zazwyczaj kontener żąda obiektu dla `ISupportErrorInfo` interfejsu i wywołania `InterfaceSupportsErrorInfo` pierwszy, aby ustalić, czy obiekt obsługuje informacje o błędzie ustawienie. Można pominąć to zadanie.  
  
 [CComPtr](../atl/reference/ccomptr-class.md) pomoże Ci przy automatycznie zliczanie odwołań, więc nie trzeba wywoływać `Release` w interfejsie. `CComBSTR` pomoże Ci przy użyciu przetwarzania BSTR, dzięki czemu nie trzeba wykonać końcowe `SysFreeString` wywołania. Możesz także użyć jednej z różnych klas konwersji ciągów, dzięki czemu można przekonwertować BSTR, jeśli to konieczne, (jest to dlaczego makro USES_CONVERSION jest na początku funkcji).  
  
 Należy również ustawić flagę zanieczyszczone na stronie właściwości, aby wskazać, że **Zastosuj** przycisku powinno być włączone. Ten problem wystąpi, gdy użytkownik zmieni wartość w **boki** pole edycji.  
  
#### <a name="to-handle-the-apply-button"></a>Aby obsługa przycisku Zastosuj  
  
1.  W widoku klas kliknij prawym przyciskiem myszy CPolyProp, a następnie kliknij przycisk **właściwości** w menu skrótów.  
  
2.  W oknie dialogowym właściwości kliknij **zdarzenia** ikony.  
  
3.  Rozwiń `IDC_SIDES` węzła listy zdarzeń.  
  
4.  Wybierz `EN_CHANGE`, a z menu rozwijanego po prawej stronie kliknij pozycję  **\<Dodaj > OnEnChangeSides**. `OnEnChangeSides` Polyprop.h w celu wykonania procedury obsługi Polyprop.cpp zostanie dodana deklaracja procedury obsługi.  
  
 Następnie zmodyfikujesz program obsługi.  
  
#### <a name="to-modify-the-onenchangesides-method"></a>Aby zmodyfikować metodę OnEnChangeSides  
  
1.  Dodaj następujący kod w Polyprop.cpp do `OnEnChangeSides` — metoda (usuwanie wszelki kod, który Kreator ważną):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides` wywoływane w sytuacji, gdy zostanie wysłana wiadomość WM_COMMAND z powiadomieniem EN_CHANGE dla `IDC_SIDES` kontroli. `OnEnChangeSides` następnie wywołuje `SetDirty` i przekazuje wartość TRUE, aby wskazać, na stronie właściwości teraz został zmieniony i **Zastosuj** przycisku powinno być włączone.  
  
## <a name="adding-the-property-page-to-the-control"></a>Dodawanie strony właściwości do kontrolki  
 Kreator dodawania klasy ATL i Kreator strony właściwości ATL nie dodawaj strony właściwości do kontrolki dla Ciebie automatycznie, ponieważ może istnieć wiele formantów w projekcie. Należy dodać wpis do map właściwości formantu.  
  
#### <a name="to-add-the-property-page"></a>Aby dodać stronę właściwości  
  
1.  Otwórz PolyCtl.h i Dodaj następujący wiersz do mapy właściwości:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 Mapy właściwości formantów wygląda teraz następująco:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 Można dodać makra PROP_PAGE o identyfikatorze CLSID strony właściwości, ale jeśli używasz makro PROP_ENTRY, jak pokazano, `Sides` wartość właściwości jest również zapisywana, gdy kontrolka jest zapisywany.  
  
 Trzy parametry do makra są opisu właściwości, DISPID, właściwości i CLSID strony właściwości, która ma właściwość na nim. Jest to przydatne, jeśli na przykład załadować formantu w języku Visual Basic i ustaw liczbę stron w czasie projektowania. Ponieważ liczbę boków jest zapisywany, gdy użytkownik ponownie Załaduj projekt języka Visual Basic, zostanie przywrócony liczbę boków.  
  
## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu  
 Teraz tworzenie tej kontrolki i wstawianie kontener testu kontrolki ActiveX. W kontenerze testów na **Edytuj** menu, kliknij przycisk **obiektu klasy PolyCtl**. Zostanie wyświetlona strona właściwości; Kliknij przycisk **wielokąta** kartę.  
  
 **Zastosuj** przycisk jest początkowo wyłączone. Zacznij wpisywać ciąg wartości w **boki** pole i **Zastosuj** uaktywni przycisku. Po wprowadzeniu wszystkich wartości, kliknij przycisk **Zastosuj** przycisku. Zmiany wyświetlania formantów i **Zastosuj** przycisk ponownie jest wyłączony. Spróbuj wprowadzić nieprawidłową wartość. Pojawi się okno komunikatu, zawierający opis błędu, który ustawiony z `put_Sides` funkcji.  
  
 Następnie należy umieścić swój formant na stronie sieci Web.  
  
 [Wróć do kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [do kroku 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)

