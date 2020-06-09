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
ms.openlocfilehash: 58f387ba6f4d7cdffb3ffc1f7be6f9acde8314f4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618166"
---
# <a name="mfc-activex-controls-using-fonts"></a>Formanty MFC ActiveX: używanie czcionek

Jeśli kontrolka ActiveX wyświetla tekst, można zezwolić użytkownikowi kontrolnym na zmianę wyglądu tekstu, zmieniając właściwość Font. Właściwości czcionki są implementowane jako obiekty czcionek i mogą być jednym z dwóch typów: giełdowo lub niestandardowych. Właściwości czcionki giełdowej są preimplementowanymi właściwościami czcionek, które można dodać za pomocą Kreatora dodawania właściwości. Niestandardowe właściwości czcionki nie są wdrażane, a deweloper kontrolki określa zachowanie i użycie właściwości.

W tym artykule omówiono następujące tematy:

- [Korzystanie z właściwości font giełdowy](#_core_using_the_stock_font_property)

- [Używanie niestandardowych właściwości czcionki w kontrolce](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>Korzystanie z właściwości font giełdowy

Właściwości czcionki giełdowej są implementowane przez klasę [COleControl](reference/colecontrol-class.md). Ponadto dostępna jest również standardowa Strona właściwości czcionki, umożliwiając użytkownikowi zmianę różnych atrybutów obiektu czcionki, takich jak nazwa, rozmiar i styl.

Uzyskaj dostęp do obiektu Font za pomocą funkcji [GetFont](reference/colecontrol-class.md#getfont), [SetFont](reference/colecontrol-class.md#setfont)i [InternalGetFont](reference/colecontrol-class.md#internalgetfont) `COleControl` . Użytkownik kontrolny uzyskuje dostęp do obiektu czcionki za pośrednictwem `GetFont` `SetFont` funkcji i w taki sam sposób jak jakakolwiek inna Właściwość get/set. Gdy dostęp do obiektu Font jest wymagany z wewnątrz kontrolki, użyj `InternalGetFont` funkcji.

Zgodnie z opisem w [kontrolce ActiveX MFC: właściwości](mfc-activex-controls-properties.md), dodawanie właściwości do zasobów jest łatwe w [Kreatorze dodawania właściwości](../ide/names-add-property-wizard.md). Wybierz właściwość Font, a Kreator dodawania właściwości automatycznie wstawi wpis czcionki giełdowej do mapy wysyłania kontrolki.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Aby dodać właściwość "podstawowe czcionki" przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W polu **Nazwa właściwości** kliknij pozycję **czcionka**.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania kontrolki znajdującej się w pliku implementacji klasy kontroli:

[!code-cpp[NVC_MFC_AxFont#1](codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Ponadto Kreator dodawania właściwości dodaje do kontrolki Poniższy wiersz. Plik IDL:

[!code-cpp[NVC_MFC_AxFont#2](codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Właściwość Caption giełdowy jest przykładem właściwości text, którą można narysować przy użyciu informacji o właściwościach podstawowych czcionki. Dodanie właściwości Caption do kontrolki powoduje użycie czynności podobnych do tych, które są używane dla właściwości "podstawowe czcionki".

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Aby dodać właściwość Caption giełdowy przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W polu **Nazwa właściwości** kliknij pozycję **podpis**.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania kontrolki znajdującej się w pliku implementacji klasy kontroli:

[!code-cpp[NVC_MFC_AxFont#3](codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>Modyfikowanie funkcji OnDraw

Domyślna implementacja programu `OnDraw` używa czcionki systemu Windows dla całego tekstu wyświetlanego w kontrolce. Oznacza to, że należy zmodyfikować `OnDraw` kod, wybierając obiekt Font w kontekście urządzenia. W tym celu należy wywołać [COleControl:: SelectStockFont](reference/colecontrol-class.md#selectstockfont) i przekazać kontekst urządzenia kontrolki, jak pokazano w następującym przykładzie:

[!code-cpp[NVC_MFC_AxFont#4](codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Po `OnDraw` zmodyfikowaniu funkcji tak, aby korzystała z obiektu Font, dowolny tekst w kontrolce jest wyświetlany z charakterystyką z właściwości font giełdowy formantu.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>Używanie niestandardowych właściwości czcionki w kontrolce

Oprócz właściwości fontal, formant ActiveX może mieć niestandardowe właściwości czcionki. Aby dodać niestandardową Właściwość czcionki, należy:

- Użyj Kreatora dodawania właściwości, aby zaimplementować Właściwość czcionki niestandardowej.

- [Przetwarzanie powiadomień czcionki](#_core_processing_font_notifications).

- [Implementowanie nowego interfejsu powiadomień czcionki](#_core_implementing_a_new_font_notification_interface).

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>Implementowanie niestandardowej właściwości czcionki

Aby zaimplementować niestandardową Właściwość czcionki, należy użyć Kreatora dodawania właściwości, aby dodać właściwość, a następnie wprowadzić pewne modyfikacje kodu. W poniższych sekcjach opisano, jak dodać właściwość niestandardową `HeadingFont` do kontrolki przykładowej.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Aby dodać niestandardową Właściwość Font przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W polu **Nazwa właściwości** wpisz nazwę właściwości. Na potrzeby tego przykładu Użyj **HeadingFont**.

1. W obszarze **Typ implementacji**kliknij pozycję **Pobierz/ustaw metody**.

1. W polu **Typ właściwości** wybierz opcję **IDispatch** <strong>\*</strong> dla typu właściwości.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości tworzy kod, aby dodać `HeadingFont` właściwość niestandardową do `CSampleCtrl` klasy i przykładu. Plik IDL. Ponieważ `HeadingFont` jest typem właściwości get/set, Kreator dodawania właściwości modyfikuje `CSampleCtrl` mapę wysyłania klasy w celu uwzględnienia DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex) wpis makra:

[!code-cpp[NVC_MFC_AxFont#5](codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

Makro DISP_PROPERTY_EX kojarzy `HeadingFont` nazwę właściwości z odpowiadającą jej `CSampleCtrl` klasą metody get i Set `GetHeadingFont` oraz `SetHeadingFont` . Typ wartości właściwości jest również określony; w tym przypadku VT_FONT.

Kreator dodawania właściwości dodaje również deklarację w pliku nagłówka kontrolki (. H) dla `GetHeadingFont` funkcji i `SetHeadingFont` dodaje ich szablony funkcji w pliku implementacji kontroli (. CPP):

[!code-cpp[NVC_MFC_AxFont#6](codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Na koniec Kreator dodawania właściwości modyfikuje formant. Plik IDL przez dodanie wpisu dla `HeadingFont` Właściwości:

[!code-cpp[NVC_MFC_AxFont#7](codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Modyfikacje kodu sterującego

Po dodaniu `HeadingFont` właściwości do kontrolki musisz wprowadzić pewne zmiany w nagłówku kontrolki i plikach implementacji, aby w pełni obsługiwać nową właściwość.

W pliku nagłówkowym formantu (. H) Dodaj następującą deklarację chronionej zmiennej składowej:

[!code-cpp[NVC_MFC_AxFont#8](codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

W pliku implementacji formantu (. CPP), wykonaj następujące czynności:

- Zainicjuj *m_fontHeading* w konstruktorze formantów.

   [!code-cpp[NVC_MFC_AxFont#9](codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Zadeklaruj statyczną strukturę FONTDESC zawierającą atrybuty domyślne czcionki.

   [!code-cpp[NVC_MFC_AxFont#10](codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- W `DoPropExchange` funkcji członkowskiej kontroli Dodaj wywołanie do `PX_Font` funkcji. Zapewnia to inicjalizację i trwałość dla niestandardowej właściwości czcionki.

   [!code-cpp[NVC_MFC_AxFont#11](codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Zakończ implementowanie `GetHeadingFont` funkcji członkowskiej kontroli.

   [!code-cpp[NVC_MFC_AxFont#12](codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Zakończ implementowanie `SetHeadingFont` funkcji członkowskiej kontroli.

   [!code-cpp[NVC_MFC_AxFont#13](codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Zmodyfikuj `OnDraw` funkcję elementu członkowskiego kontroli, aby zdefiniować zmienną do przechowywania wcześniej wybranej czcionki.

   [!code-cpp[NVC_MFC_AxFont#14](codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Zmodyfikuj `OnDraw` funkcję elementu członkowskiego kontrolki, aby wybrać czcionkę niestandardową w kontekście urządzenia, dodając następujący wiersz, wszędzie tam, gdzie ma być używana czcionka.

   [!code-cpp[NVC_MFC_AxFont#15](codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Zmodyfikuj `OnDraw` funkcję elementu członkowskiego kontroli, aby wybrać poprzednią czcionkę z powrotem do kontekstu urządzenia, dodając następujący wiersz po użyciu czcionki.

   [!code-cpp[NVC_MFC_AxFont#16](codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Po zaimplementowaniu niestandardowej właściwości czcionki powinna zostać zaimplementowana Strona właściwości czcionki standardowej, która pozwala formantom zmieniać bieżącą czcionkę kontrolki. Aby dodać identyfikator strony właściwości dla standardowej strony właściwości czcionki, Wstaw następujący wiersz po makro BEGIN_PROPPAGEIDS:

[!code-cpp[NVC_MFC_AxFont#17](codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Należy również zwiększyć liczbę parametrów BEGIN_PROPPAGEIDS makra. Poniższy wiersz ilustruje:

[!code-cpp[NVC_MFC_AxFont#18](codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Po wprowadzeniu tych zmian Odbuduj cały projekt, aby uwzględnić dodatkowe funkcje.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>Przetwarzanie powiadomień o czcionkach

W większości przypadków formant musi wiedzieć, kiedy charakterystyki obiektu czcionki zostały zmodyfikowane. Każdy obiekt czcionki jest w stanie dostarczać powiadomienia, gdy zmienia się, wywołując funkcję członkowską `IFontNotification` interfejsu, implementowaną przez `COleControl` .

Jeśli kontrolka używa właściwości fontal, jej powiadomienia są obsługiwane przez `OnFontChanged` funkcję elementu członkowskiego `COleControl` . Po dodaniu niestandardowych właściwości czcionki mogą one używać tej samej implementacji. W przykładzie w poprzedniej sekcji zostało to osiągnięte przez przekazanie &*m_xFontNotification* podczas inicjowania zmiennej członkowskiej *m_fontHeading* .

![Implementowanie wielu interfejsów obiektów czcionek](../mfc/media/vc373q1.gif "Implementowanie wielu interfejsów obiektów czcionek") <br/>
Implementowanie wielu interfejsów obiektów czcionek

Linie kryjące na powyższej ilustracji pokazują, że oba obiekty czcionki używają tej samej implementacji `IFontNotification` . Może to spowodować problemy, jeśli chcesz rozróżnić czcionkę, którą zmieniono.

Jednym ze sposobów rozróżniania powiadomień obiektu czcionki kontrolki jest utworzenie oddzielnej implementacji `IFontNotification` interfejsu dla każdego obiektu czcionki w formancie. Ta technika pozwala zoptymalizować kod rysowania przez zaktualizowanie tylko ciągu lub ciągów, które używają niedawno modyfikowanej czcionki. W poniższych sekcjach przedstawiono kroki niezbędne do zaimplementowania oddzielnych interfejsów powiadomień dla drugiej właściwości czcionki. Właściwość drugiej czcionki przyjmuje wartość `HeadingFont` właściwości, która została dodana w poprzedniej sekcji.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>Implementowanie nowego interfejsu powiadomień czcionek

Aby rozróżnić powiadomienia o dwóch lub większej liczbie czcionek, należy zaimplementować nowy interfejs powiadomienia dla każdej czcionki używanej w formancie. W poniższych sekcjach opisano sposób implementacji nowego interfejsu powiadomień czcionek poprzez modyfikację nagłówka i plików implementacji formantu.

### <a name="additions-to-the-header-file"></a>Dodatki do pliku nagłówkowego

W pliku nagłówkowym formantu (. H) Dodaj następujące wiersze do deklaracji klasy:

[!code-cpp[NVC_MFC_AxFont#19](codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Spowoduje to utworzenie implementacji `IPropertyNotifySink` interfejsu o nazwie `HeadingFontNotify` . Ten nowy interfejs zawiera metodę o nazwie `OnChanged` .

### <a name="additions-to-the-implementation-file"></a>Dodatki do pliku implementacji

W kodzie, który inicjuje czcionkę nagłówka (w konstruktorze formantów), Zmień *m_xFontNotification* &na &*m_xHeadingFontNotify*. Następnie Dodaj następujący kod:

[!code-cpp[NVC_MFC_AxFont#20](codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef`Metody i `Release` w `IPropertyNotifySink` interfejsie śledzą liczbę odwołań dla obiektu kontrolki ActiveX. Gdy formant uzyskuje dostęp do wskaźnika interfejsu, kontrolka wywołuje, `AddRef` Aby zwiększyć liczbę odwołań. Gdy kontrolka zostanie zakończona wskaźnikiem, wywołuje `Release` , w podobny sposób, który `GlobalFree` może zostać wywołany w celu zwolnienia globalnego bloku pamięci. Gdy liczba odwołań dla tego interfejsu jest równa zero, implementacja interfejsu można zwolnić. W tym przykładzie `QueryInterface` Funkcja zwraca wskaźnik do `IPropertyNotifySink` interfejsu dla określonego obiektu. Ta funkcja umożliwia kontrolce ActiveX wykonywanie zapytań względem obiektu w celu określenia interfejsów, które obsługuje.

Po dokonaniu tych zmian w projekcie ponownie skompiluj projekt i Użyj kontenera testów do przetestowania interfejsu. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testów,](testing-properties-and-events-with-test-container.md) Aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: używanie obrazów w kontrolce ActiveX](mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[Kontrolki ActiveX MFC: używanie stron właściwości standardowych](mfc-activex-controls-using-stock-property-pages.md)
