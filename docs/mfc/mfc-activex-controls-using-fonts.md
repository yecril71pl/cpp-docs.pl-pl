---
title: 'Formanty MFC ActiveX: używanie czcionek'
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
ms.openlocfilehash: c336ec6c29b5478655ca8f19f71378a2b446ac64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358269"
---
# <a name="mfc-activex-controls-using-fonts"></a>Formanty MFC ActiveX: używanie czcionek

Jeśli formant ActiveX wyświetla tekst, można zezwolić użytkownikowi sterującemu na zmianę wyglądu tekstu przez zmianę właściwości czcionki. Właściwości czcionki są implementowane jako obiekty czcionek i mogą być jednym z dwóch typów: stock lub custom. Właściwości czcionki magazynowej są wstępnie uzupełnione właściwości czcionki, które można dodać za pomocą Kreatora dodawania właściwości. Właściwości czcionki niestandardowej nie są wstępnieimplementowane, a deweloper formantu określa zachowanie i użycie właściwości.

W tym artykule omówiono następujące tematy:

- [Korzystanie z właściwości Czcionka zapasowa](#_core_using_the_stock_font_property)

- [Korzystanie z niestandardowych właściwości czcionek w formancie](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>Korzystanie z właściwości Czcionka giełdowa

Właściwości czcionki magazynowej są wstępnie preimplementowane przez klasę [COleControl](../mfc/reference/colecontrol-class.md). Ponadto dostępna jest również standardowa strona właściwości Font, umożliwiająca użytkownikowi zmianę różnych atrybutów obiektu czcionki, takich jak jego nazwa, rozmiar i styl.

Dostęp do obiektu czcionki za pośrednictwem funkcji [GetFont](../mfc/reference/colecontrol-class.md#getfont), `COleControl` [SetFont](../mfc/reference/colecontrol-class.md#setfont)i [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) . Użytkownik formantu będzie uzyskiwać dostęp do obiektu czcionki za pośrednictwem `GetFont` i `SetFont` funkcji w taki sam sposób, jak każdy inny Get/Set właściwości. Gdy dostęp do obiektu czcionki jest wymagany z `InternalGetFont` poziomu formantu, należy użyć funkcji.

Jak wspomniano w [MFC ActiveX Controls: Właściwości](../mfc/mfc-activex-controls-properties.md), dodawanie właściwości zapasów jest łatwe dzięki [Kreatorowi dodawania właściwości](../ide/names-add-property-wizard.md). Wybierz Font właściwości i Dodaj Kreator właściwości automatycznie wstawia wpis czcionki czas do mapy wysyłki formantu.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Aby dodać właściwość czcionka giełdowa za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W polu **Nazwa właściwości** kliknij pozycję **Czcionka**.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłki formantu, znajdującej się w pliku implementacji klasy kontrolnej:

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Ponadto Kreator dodawania właściwości dodaje następujący wiersz do formantu . Plik IDL:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Właściwość stock Caption jest przykładem właściwości tekstowej, którą można narysować przy użyciu informacji o właściwości font. Dodawanie akcji Caption właściwość do formantu używa kroków podobnych do tych używanych dla magazynu Font właściwości.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Aby dodać właściwość Podpis zapasów za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W polu **Nazwa właściwości** kliknij pozycję **Podpis**.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłki formantu, znajdującej się w pliku implementacji klasy kontrolnej:

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>Modyfikowanie funkcji OnDraw

Domyślna implementacja `OnDraw` używa czcionki systemu Windows dla całego tekstu wyświetlanego w formancie. Oznacza to, że `OnDraw` należy zmodyfikować kod, wybierając obiekt czcionki w kontekście urządzenia. Aby to zrobić, należy wywołać [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) i przekazać kontekst urządzenia formantu, jak pokazano w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Po `OnDraw` zmodyfikowaniu funkcji w celu użycia obiektu czcionki, każdy tekst w formancie jest wyświetlany z cechami z właściwości Font magazynu formantu.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>Korzystanie z niestandardowych właściwości czcionek w formancie

Oprócz właściwości Font stock formant ActiveX może mieć niestandardowe właściwości czcionki. Aby dodać właściwość czcionki niestandardowej, należy:

- Użyj Kreatora dodawania właściwości, aby zaimplementować niestandardową właściwość Font.

- [Przetwarzanie powiadomień o czcionkach](#_core_processing_font_notifications).

- [Implementowanie nowego interfejsu powiadomień o czcionkach](#_core_implementing_a_new_font_notification_interface).

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>Implementowanie właściwości czcionki niestandardowej

Aby zaimplementować niestandardową właściwość Font, należy użyć Kreatora dodawania właściwości, aby dodać właściwość, a następnie wprowadzić pewne modyfikacje do kodu. W poniższych sekcjach opisano `HeadingFont` sposób dodawania właściwości niestandardowej do przykładowego formantu.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Aby dodać niestandardową właściwość Font za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W polu **Nazwa właściwości** wpisz nazwę właściwości. W tym przykładzie użyj **headingfont**.

1. W przypadku **typu implementacji**kliknij pozycję **Pobierz/Ustaw metody**.

1. W polu **Typ właściwości** wybierz **pozycję IDispatch** <strong>\*</strong> dla typu właściwości.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości tworzy kod, aby `CSampleCtrl` dodać właściwość niestandardową `HeadingFont` do klasy i SAMPLE. IDL. Ponieważ `HeadingFont` jest typem właściwości Pobierz/Ustaw, Kreator `CSampleCtrl` dodawania właściwości modyfikuje mapę wysyłki klasy w celu uwzględnienia DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex) wpisu makra:

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

Makro DISP_PROPERTY_EX kojarzy nazwę `HeadingFont` właściwości z `CSampleCtrl` odpowiadającą mu klasą Get and Set metody `GetHeadingFont` oraz `SetHeadingFont`. Określa się również typ wartości właściwości; w tym przypadku VT_FONT.

Kreator dodawania właściwości dodaje również deklarację w pliku nagłówka formantu (. H) dla `GetHeadingFont` `SetHeadingFont` funkcji i i dodaje ich szablony funkcji w pliku implementacji formantu (. CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Na koniec Kreator dodawania właściwości modyfikuje formant . IDL przez dodanie wpisu `HeadingFont` dla właściwości:

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Modyfikacje kodeksu kontroli

Teraz, gdy dodano `HeadingFont` właściwość do formantu, należy wprowadzić pewne zmiany w nagłówku formantu i pliki implementacji, aby w pełni obsługiwać nową właściwość.

W pliku nagłówka formantu (. H), dodaj następującą deklarację chronionej zmiennej członkowskiej:

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

W pliku implementacji formantu (. CPP), wykonaj następujące czynności:

- Zainicjować *m_fontHeading* w konstruktorze sterowania.

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Zadeklaruj statyczną strukturę FONTDESC zawierającą domyślne atrybuty czcionki.

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- W funkcji `DoPropExchange` elementu członkowskiego formantu `PX_Font` dodaj wywołanie do funkcji. Zapewnia inicjowanie i trwałość dla niestandardowej font właściwości.

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Zakończ implementowanie `GetHeadingFont` funkcji elementu członkowskiego formantu.

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Zakończ implementowanie `SetHeadingFont` funkcji elementu członkowskiego formantu.

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Zmodyfikuj funkcję elementu członkowskiego formantu, `OnDraw` aby zdefiniować zmienną do przechowywania wcześniej wybranej czcionki.

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Zmodyfikuj funkcję elementu członkowskiego formantu, `OnDraw` aby wybrać czcionkę niestandardową w kontekście urządzenia, dodając następujący wiersz wszędzie tam, gdzie ma być używana czcionka.

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Zmodyfikuj funkcję elementu członkowskiego formantu, `OnDraw` aby wybrać poprzednią czcionkę z powrotem w kontekście urządzenia, dodając następujący wiersz po użyciu czcionki.

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Po zaimplementowano niestandardową właściwość Font, należy zaimplementować standardową stronę właściwości Font, umożliwiając użytkownikom kontroli zmianę bieżącej czcionki formantu. Aby dodać identyfikator strony właściwości dla standardowej strony właściwości Czcionka, wstaw następujący wiersz po BEGIN_PROPPAGEIDS makra:

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Należy również zwiększać parametr liczby BEGIN_PROPPAGEIDS makra o jeden. Poniższy wiersz ilustruje to:

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Po włączeniu tych zmian odbuduj cały projekt, aby uwzględnić dodatkowe funkcje.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>Przetwarzanie powiadomień o czcionkach

W większości przypadków formant musi wiedzieć, kiedy właściwości obiektu czcionki zostały zmodyfikowane. Każdy obiekt czcionki jest w stanie dostarczać powiadomienia, `IFontNotification` gdy się zmienia, wywołując funkcję elementu członkowskiego interfejsu, zaimplementowana przez `COleControl`program .

Jeśli formant używa właściwości Font, jej powiadomienia są `OnFontChanged` obsługiwane przez `COleControl`funkcję elementu członkowskiego . Po dodaniu właściwości czcionki niestandardowej, można je użyć tej samej implementacji. W przykładzie w poprzedniej sekcji zostało to osiągnięte przez przekazanie &*m_xFontNotification* podczas inicjowania zmiennej *m_fontHeading* elementu członkowskiego.

![Implementowanie wielu interfejsów obiektów czcionek](../mfc/media/vc373q1.gif "Implementowanie wielu interfejsów obiektów czcionek") <br/>
Implementowanie wielu interfejsów obiektów czcionek

Linie ciągłe na powyższym rysunku pokazują, że oba `IFontNotification`obiekty czcionek używają tej samej implementacji programu . Może to spowodować problemy, jeśli chcesz odróżnić, która czcionka została zmieniona.

Jednym ze sposobów rozróżnienia między powiadomieniami obiektu czcionki formantu jest utworzenie oddzielnej implementacji `IFontNotification` interfejsu dla każdego obiektu czcionki w formancie. Ta technika umożliwia optymalizację kodu rysunku przez aktualizację tylko ciągu lub ciągów znaków, które używają ostatnio zmodyfikowanej czcionki. W poniższych sekcjach przedstawiono kroki niezbędne do zaimplementowania oddzielnych interfejsów powiadomień dla drugiej Font właściwości. Przyjmuje się, że właściwość `HeadingFont` drugiej czcionki jest właściwością dodaną w poprzedniej sekcji.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>Implementowanie nowego interfejsu powiadomień o czcionkach

Aby odróżnić powiadomienia dwóch lub więcej czcionek, dla każdej czcionki używanej w formancie należy zaimplementować nowy interfejs powiadomień. W poniższych sekcjach opisano sposób implementacji nowego interfejsu powiadomień czcionki, modyfikując nagłówek formantu i pliki implementacji.

### <a name="additions-to-the-header-file"></a>Dodatki do pliku nagłówka

W pliku nagłówka formantu (. H), dodaj następujące wiersze do deklaracji klasy:

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Spowoduje to utworzenie `IPropertyNotifySink` implementacji `HeadingFontNotify`interfejsu o nazwie . Ten nowy interfejs zawiera `OnChanged`metodę o nazwie .

### <a name="additions-to-the-implementation-file"></a>Dodatki do pliku implementacji

W kodzie, który inicjuje czcionkę nagłówka (w konstruktorze formantu) zmień &*m_xFontNotification* na &*m_xHeadingFontNotify*. Następnie dodaj następujący kod:

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

I `AddRef` `Release` metody w `IPropertyNotifySink` interfejsie śledzić liczbę odwołań dla obiektu kontrolnego ActiveX. Gdy formant uzyskuje dostęp do wskaźnika `AddRef` interfejsu, formant wywołuje przyrost liczby odwołań. Po zakończeniu kontroli ze wskaźnikiem, `Release`wywołuje , w `GlobalFree` taki sam sposób, który może być wywoływany, aby zwolnić blok pamięci globalnej. Gdy liczba odwołań dla tego interfejsu idzie do zera, implementacji interfejsu można zwolniono. W tym przykładzie `QueryInterface` funkcja zwraca `IPropertyNotifySink` wskaźnik do interfejsu na określonym obiekcie. Ta funkcja umożliwia formantowi ActiveX wykonywanie zapytań do obiektu w celu określenia, jakie interfejsy obsługuje.

Po wniesieniu tych zmian do projektu, odbuduj projekt i użyj kontenera testowego, aby przetestować interfejs. Zobacz [testowanie właściwości i zdarzenia z kontenerem testowym,](../mfc/testing-properties-and-events-with-test-container.md) aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: używanie obrazów w kontrolce ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)
