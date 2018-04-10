---
title: Dodawanie strony właściwości (ALT — samouczek, część 6) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: get-started-article
dev_langs:
- C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 067c5d662fee3838a33a3b53fd5dab2946ab50cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Dodawanie strony właściwości (ALT — Samouczek, część 6)
Strony właściwości są zaimplementowane jako osobne obiekty COM, które pozwalają na udostępnionym, jeśli jest to wymagane. W tym kroku spowoduje wykonanie następujących zadań, które można dodać strony właściwości do kontrolki:  
  
-   Tworzenie zasobu strony właściwości  
  
-   Dodawanie kodu do tworzenia i zarządzania strony właściwości  
  
-   Dodawanie strony właściwości do kontrolki  
  
## <a name="creating-the-property-page-resource"></a>Tworzenie zasobu strony właściwości  
 Aby dodać strony właściwości formantu, użyj Kreatora dodawania klasy ATL.  
  
#### <a name="to-add-a-property-page"></a>Aby dodać strony właściwości  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy wielokąta.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
3.  Wybierz z listy szablonów **stronę właściwości ATL** i kliknij przycisk **Dodaj**.  
  
4.  Gdy pojawi się Kreator strony właściwości ATL, wprowadź `PolyProp` jako **krótki** nazwy.  
  
5.  Kliknij przycisk **ciągów** otworzyć **ciągów** strony, a następnie wprowadź **& wielokąta** jako **tytuł**.  
  
     **Tytuł** właściwości strony jest ciągiem, który jest wyświetlany na karcie tej strony. **Doc string** jest opis, który używa ramka właściwości mają zostać umieszczone w etykietce wiersza lub narzędzia stanu. Należy pamiętać, że ramka standardowe właściwości obecnie nie korzysta z tych parametrów, dlatego pozostawić wartość domyślną. Nie będą generowane **plik Pomocy** w momencie, dlatego usunąć wpis w tym polu tekstowym.  
  
6.  Kliknij przycisk **Zakończ**, i zostanie utworzony obiekt strony właściwości.  
  
 Są tworzone trzy następujące pliki:  
  
|Plik|Opis|  
|----------|-----------------|  
|PolyProp.h|Zawiera klasę C++ `CPolyProp`, który implementuje stronę właściwości.|  
|PolyProp.cpp|Zawiera plik PolyProp.h.|  
|PolyProp.rgs|Skrypt rejestru, który rejestruje obiekt strony właściwości.|  
  
 Poniższy kod zmienia są również:  
  
-   Nowe strony właściwości jest dodawany do mapy wpis obiektu w Polygon.cpp.  
  
-   `PolyProp` Klas są dodawane do pliku Polygon.idl.  
  
-   Nowy plik skryptu rejestru PolyProp.rgs jest dodane do projektu zasobów.  
  
-   Szablon okno dialogowe zostanie dodany do zasobów projektu dla strony właściwości.  
  
-   Ciągi właściwości określone przez użytkownika są dodawane do tabeli ciągów zasobów.  
  
 Teraz Dodaj pola, które mają być wyświetlane na stronie właściwości.  
  
#### <a name="to-add-fields-to-the-property-page"></a>Aby dodać pola do strony właściwości  
  
1.  W Eksploratorze rozwiązań kliknij dwukrotnie plik zasobu Polygon.rc. Spowoduje to otwarcie widoku zasobów.  
  
2.  W widokach rozwiń węzeł okna dialogowego, a następnie kliknij dwukrotnie ikonę IDD_POLYPROP. Należy pamiętać, że okno dialogowe, która jest wyświetlana pusta z wyjątkiem etykietę, która informuje, aby wstawić formanty w tym miejscu.  
  
3.  Wybierz tej etykiety i zmień, aby odczytać `Sides:` , zmieniając **podpis** tekst w **właściwości** okna.  
  
4.  Tak, aby zmieścił się rozmiar tekstu, należy zmienić rozmiar pola etykiety.  
  
5.  Przeciągnij kontrolki edycji z przybornika z prawej strony etykiety.  
  
6.  Na koniec zmień **identyfikator** formantu edycji `IDC_SIDES` przy użyciu okna właściwości.  
  
 Na tym kończy proces tworzenia zasobu strony właściwości.  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>Dodawanie kodu do tworzenia i zarządzania strony właściwości  
 Teraz, po utworzeniu zasobu strony właściwości, należy napisać kod implementacji.  
  
 Najpierw włączyć `CPolyProp` klasy, aby ustawić liczbę stron w obiektu podczas **Zastosuj** przycisk jest naciśnięty.  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Aby zmodyfikować funkcja Zastosuj, aby ustawić liczbę stron  
  
1.  Zastąp `Apply` funkcji w PolyProp.h następującym kodem:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 Strony właściwości może mieć więcej niż jednego klienta, dołączony w czasie, więc `Apply` funkcji pętli wokół i wywołuje `put_Sides` na każdym komputerze klienckim z wartością pobierane z pola edycji. Używasz [CComQIPtr](../atl/reference/ccomqiptr-class.md) klasy, która wykonuje `QueryInterface` dla każdego obiektu w celu uzyskania `IPolyCtl` interfejsu z **IUnknown** interfejsu (przechowywane w `m_ppUnk` tablicy).  
  
 Kod sprawdza ustawienie `Sides` właściwości tygodniowo. Jeśli nie powiedzie się, kod wyświetla komunikat wyświetlanie szczegółów błędu z **IErrorInfo** interfejsu. Zazwyczaj kontener prosi obiekt **ISupportErrorInfo** interfejsu i wywołania `InterfaceSupportsErrorInfo` first, aby ustalić, czy obiekt obsługuje ustawienie informacje o błędzie. Można pominąć to zadanie.  
  
 [CComPtr](../atl/reference/ccomptr-class.md) pomaga przez automatycznie obsługi liczenie odwołań, dzięki czemu nie trzeba wywołać `Release` w interfejsie. `CComBSTR`pomaga przy `BSTR` przetwarzania, dzięki czemu nie trzeba wykonać ostatecznego `SysFreeString` wywołania. Możesz także użyć jednej z różnymi klasami Konwersja ciągu, można przekonwertować `BSTR` w razie potrzeby (jest to dlaczego `USES_CONVERSION` makro jest na początku funkcji).  
  
 Należy również ustawić stronę właściwości dirty flagi z informacją, że **Zastosuj** przycisku powinno być włączone. Dzieje się tak, gdy użytkownik zmieni wartość w **strony** polu edycji.  
  
#### <a name="to-handle-the-apply-button"></a>Aby obsługa przycisku Zastosuj  
  
1.  W widoku klas, kliknij prawym przyciskiem myszy CPolyProp, a następnie kliknij przycisk **właściwości** menu skrótów.  
  
2.  Kliknij w oknie właściwości **zdarzenia** ikony.  
  
3.  Rozwiń węzeł `IDC_SIDES` węzła listy zdarzeń.  
  
4.  Wybierz `EN_CHANGE`, a z menu rozwijanego po prawej stronie, kliknij przycisk  **\<Dodaj > OnEnChangeSides**. `OnEnChangeSides` Deklaracja obsługi zostaną dodane do Polyprop.h i implementację programu obsługi, aby Polyprop.cpp.  
  
 Następnie należy zmodyfikować program obsługi.  
  
#### <a name="to-modify-the-onenchangesides-method"></a>Aby zmodyfikować metodę OnEnChangeSides  
  
1.  Dodaj następujący kod w Polyprop.cpp do `OnEnChangeSides` — metoda (usuwanie kodu, który Kreator umieszczono):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides`będzie ona wywoływana podczas **WM_COMMAND** komunikat jest wysyłany z **EN_CHANGE** powiadomienia o `IDC_SIDES` formantu. `OnEnChangeSides`następnie wywołuje `SetDirty` i przekazuje `TRUE` można wskazać właściwości strony teraz jest zanieczyszczony i **Zastosuj** przycisku powinno być włączone.  
  
## <a name="adding-the-property-page-to-the-control"></a>Dodawanie strony właściwości do kontrolki  
 Kreator dodawania klasy ATL i Kreator strony właściwości ATL nie dodawaj stronę właściwości do formantu można automatycznie, ponieważ może istnieć wiele formantów w projekcie. Należy dodać wpis do mapy właściwości formantu.  
  
#### <a name="to-add-the-property-page"></a>Aby dodać strony właściwości  
  
1.  Otwórz PolyCtl.h i Dodaj następujący wiersz do mapy właściwości:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 Mapy właściwości formantu teraz wygląda następująco:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 Można dodano `PROP_PAGE` makro o identyfikatorze CLSID strony właściwości, ale jeśli używasz `PROP_ENTRY` makra, co zostało pokazane, `Sides` wartość właściwości jest także zapisane po zapisaniu formantu.  
  
 Trzy parametry do makra są opisu właściwości, identyfikator DISPID właściwości i identyfikatora CLSID strony właściwości, która ma właściwość z. Jest to przydatne, jeśli na przykład załadować formantu w języku Visual Basic i ustaw liczbę stron w czasie projektowania. Ponieważ jest zapisywany numer strony, gdy należy ponownie załadować projekt programu Visual Basic, liczba stron zostaną przywrócone.  
  
## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu  
 Teraz skompilować tego formantu i wstawić je do kontener testu formantu ActiveX. W kontenerze testowym na **Edytuj** menu, kliknij przycisk **obiektu klasy PolyCtl**. Zostanie wyświetlona strona właściwości; Kliknij przycisk **wielokąta** kartę.  
  
 **Zastosuj** przycisk początkowo jest wyłączony. Rozpocznij wprowadzanie wartości w **strony** pole i **Zastosuj** przycisk będzie stają się aktywny. Po wprowadzeniu wszystkich wartość, kliknij przycisk **Zastosuj** przycisku. Zmiany wyświetlania kontrolki i **Zastosuj** przycisk ponownie jest wyłączony. Spróbuj wprowadzić wartość jest nieprawidłowa. Zostanie wyświetlone pole komunikat zawierający opis błędu, który ustawiony z `put_Sides` funkcji.  
  
 Następnie należy umieścić formantu na stronie sieci Web.  
  
 [Wróć do kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [Do kroku 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)

