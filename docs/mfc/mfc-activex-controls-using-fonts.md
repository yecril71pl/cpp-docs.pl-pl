---
title: 'Kontrolki ActiveX MFC: Używanie czcionek | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c34b4a842655ebce6fccaa89a1dfc6d4ef49add
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063487"
---
# <a name="mfc-activex-controls-using-fonts"></a>Kontrolki ActiveX MFC: używanie czcionek

Jeśli formant ActiveX jest wyświetlany tekst, możesz zezwolić użytkownikowi kontroli zmienić wygląd tekstu, zmieniając właściwość czcionki. Właściwości czcionki są implementowane jako obiekty czcionki i może być jednym z dwóch typów: podstawowy lub niestandardowy. Podstawowe właściwości czcionki są właściwości preimplemented czcionki, które można dodać za pomocą Kreatora dodawania właściwości. Właściwości czcionki niestandardowe nie są preimplemented i dewelopera kontrolek określa zachowanie i użycia właściwości.

W tym artykule omówiono następujące tematy:

- [Przy użyciu właściwości zapasów czcionki](#_core_using_the_stock_font_property)

- [Za pomocą właściwości niestandardowej czcionki w kontrolce](#_core_implementing_a_custom_font_property)

##  <a name="_core_using_the_stock_font_property"></a> Przy użyciu właściwości zapasów czcionki

Podstawowe właściwości czcionki są preimplemented przez klasę [COleControl](../mfc/reference/colecontrol-class.md). Oprócz standardowej strony właściwości czcionki jest również dostępny, umożliwiając użytkownikowi na zmianę różnych atrybutów obiektu czcionki, na przykład jej nazwę, rozmiar i stylu.

Dostęp do obiektu czcionki, za pośrednictwem [getfont —](../mfc/reference/colecontrol-class.md#getfont), [setfont —](../mfc/reference/colecontrol-class.md#setfont), i [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) funkcji `COleControl`. Kontrolka użytkownika będzie dostępu do obiektu czcionki, za pośrednictwem `GetFont` i `SetFont` funkcje w taki sam sposób jak inne właściwości Get/Set. Gdy dostęp do obiektu czcionki jest wymagana od znajdujących się pod kontrolą, przy użyciu `InternalGetFont` funkcji.

Zgodnie z opisem w [kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md), dodawanie właściwości standardowych jest bardzo proste dzięki [Kreator dodawania właściwości](../ide/names-add-property-wizard.md). Wybierz właściwość czcionki, a Kreator dodawania właściwości automatycznie wstawi zapasów czcionki wejścia Mapa wysyłania formantu.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Aby dodać właściwości czcionki zasobów za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W **nazwa właściwości** kliknij **czcionki**.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania formantu, znajduje się w pliku implementacji klasy:

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Ponadto Kreator dodawania właściwości dodaje następujący wiersz do kontrolki. Plik IDL:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Podstawowe właściwości podpisu jest przykładem właściwości tekstu, które mogą być wystawiane przy użyciu standardowych informacji o właściwości czcionki. Dodawanie zasobu właściwości podpisu do formantu używa kroki podobne do używanych dla zasobu właściwość czcionki.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Aby dodać podstawowe właściwości podpisu przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W **nazwa właściwości** kliknij **podpis**.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania formantu, znajduje się w pliku implementacji klasy:

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

##  <a name="_core_modifying_the_ondraw_function"></a> Modyfikowanie OnDraw — funkcja

Domyślna implementacja klasy `OnDraw` używa czcionki systemu Windows dla cały tekst wyświetlany w formancie. Oznacza to, że należy zmodyfikować `OnDraw` kodu, zaznaczając ten obiekt czcionki do kontekstu urządzenia. Aby to zrobić, należy wywołać [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) i Przekaż kontekst urządzenia dla formantu, jak pokazano w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Po `OnDraw` funkcja została zmodyfikowana, aby użyć obiektu czcionki, dowolny tekst w kontrolce jest wyświetlany za pomocą właściwości z właściwości czcionki zasobów formantu.

##  <a name="_core_using_custom_font_properties_in_your_control"></a> Za pomocą właściwości niestandardowej czcionki w kontrolce

Oprócz właściwości czcionki zasobów formant ActiveX może mieć właściwości czcionki niestandardowe. Aby dodać właściwość niestandardowej czcionki należy:

- Kreator dodawania właściwości do zaimplementowania właściwości niestandardowej czcionki.

- [Przetwarzanie powiadomień czcionki](#_core_processing_font_notifications).

- [Implementowanie nowy interfejs powiadomień czcionki](#_core_implementing_a_new_font_notification_interface).

###  <a name="_core_implementing_a_custom_font_property"></a> Implementowanie właściwości niestandardowej czcionki

Aby zaimplementować właściwości niestandardowej czcionki, należy użyć Kreatora dodawania właściwości Aby dodać właściwość, a następnie wprowadzenie pewnych zmian w kodzie. W poniższych sekcjach opisano sposób dodawania niestandardowej `HeadingFont` właściwości do kontrolki próbki.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Aby dodać niestandardowe właściwości czcionki przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie Kreatora dodawania właściwości.

1. W **nazwa właściwości** wpisz nazwę właściwości. W tym przykładzie użyj **HeadingFont**.

1. Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.

1. W **typ właściwości** wybierz opcję **IDispatch** <strong>\*</strong> dla typu właściwości.

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości tworzy kod, aby dodać `HeadingFont` niestandardowa właściwość `CSampleCtrl` klasy i próbki. Plik IDL. Ponieważ `HeadingFont` jest typem właściwości Get/Set modyfikuje Kreator dodawania właściwości `CSampleCtrl` Mapa wysyłania klasy, aby uwzględnić DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex) wpis makra:

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX — makro kojarzy `HeadingFont` nazwa właściwości z odpowiadającymi mu dostawcami `CSampleCtrl` klasy metody Get i Set, `GetHeadingFont` i `SetHeadingFont`. Typ wartości właściwości również jest określona; w tym przypadku VT_FONT.

Dodaj właściwość dodaje także deklaracji w pliku nagłówka (. H) dla `GetHeadingFont` i `SetHeadingFont` funkcje i dodaje szablony ich funkcji w pliku implementacji (. CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Ponadto Kreator dodawania właściwości modyfikuje formantu. Plik IDL, dodając wpis dla `HeadingFont` właściwości:

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Zmiany w kodzie sterującym

Teraz, po dodaniu `HeadingFont` właściwości do kontrolki, należy wprowadzić pewne zmiany na pliki nagłówkowy i implementacji kontroli do zapewnienia pełnej obsługi nowej właściwości.

W pliku nagłówka (. Godz.), dodaj następującą deklarację zmiennej elementu członkowskiego chronionego:

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

W pliku implementacji (. CPP), wykonaj następujące czynności:

- Inicjowanie *m_fontHeading* w Konstruktorze kontroli.

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Deklarowanie struktury statycznej FONTDESC zawierający domyślne atrybuty czcionki.

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- W kontrolce `DoPropExchange` element członkowski funkcji, dodaj wywołanie do `PX_Font` funkcji. Zapewnia to inicjowania i trwałości dla właściwości niestandardowej czcionki.

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Zakończenie wykonywania kontroli `GetHeadingFont` funkcja elementu członkowskiego.

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Zakończenie wykonywania kontroli `SetHeadingFont` funkcja elementu członkowskiego.

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Modyfikowanie kontrolki `OnDraw` funkcja elementu członkowskiego, aby zdefiniować zmienną do przechowywania wcześniej wybranej czcionki.

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Modyfikowanie kontrolki `OnDraw` funkcja elementu członkowskiego, aby wybrać niestandardowej czcionki do kontekstu urządzenia przez dodanie następujących wiersza wszędzie tam, gdzie ma być używana czcionka.

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Modyfikowanie kontrolki `OnDraw` funkcji elementu członkowskiego, aby wybrać poprzedniego czcionki do kontekstu urządzenia, dodając następujący wiersz, gdy została użyta czcionki.

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Po zaimplementowaniu właściwości niestandardowej czcionki standardowej strony właściwości czcionki powinny być zrealizowane, umożliwiając użytkownikom sterowania zmień bieżącą czcionkę formantu. Aby dodać identyfikator strony właściwości dla standardowej strony właściwości czcionki, Wstaw następujący wiersz po BEGIN_PROPPAGEIDS — makro:

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Za pomocą jednej, należy zwiększyć wartość parametru liczba BEGIN_PROPPAGEIDS — makro. Ilustruje poniższy wiersz, to:

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Po dokonaniu tych zmian, należy ponownie skompilować cały projekt, aby włączyć dodatkowe funkcje.

###  <a name="_core_processing_font_notifications"></a> Przetwarzanie powiadomień czcionki

W większości przypadków formant musi wiedzieć, kiedy zostały zmodyfikowane właściwości obiektu czcionki. Każdy obiekt czcionka jest w stanie związanych z udostępnianiem powiadomienia, gdy zmieni się przez wywołanie funkcji składowej typu `IFontNotification` interfejs implementowany przez `COleControl`.

Jeśli kontrolka używa właściwości czcionki zasobów, jego powiadomienia są obsługiwane przez `OnFontChanged` funkcji składowej typu `COleControl`. Po dodaniu właściwości niestandardowej czcionki, może mieć ich używać tego samego wdrożenia. W przykładzie w poprzedniej sekcji, to było wykonywane przez przekazanie &*m_xFontNotification* podczas inicjowania *m_fontHeading* zmiennej składowej.

![Implementowanie wielu interfejsów obiektów czcionek](../mfc/media/vc373q1.gif "vc373q1") Implementowanie wielu interfejsów obiektów czcionek

Linie ciągłe na powyższej ilustracji pokazano, że oba obiekty czcionki są przy użyciu tego samego wdrożenia `IFontNotification`. Może to powodować problemy, jeśli chce się rozróżnienia zmienione czcionki, która.

Jednym ze sposobów rozróżnienie między powiadomienia obiektu czcionki formantu jest utworzyć oddzielne implementacji `IFontNotification` interfejsu dla każdego obiektu czcionki w formancie. Ta technika pozwala zoptymalizować swój kod rysowania, aktualizując tylko ciąg znaków lub ciągów, które używają czcionki ostatnio zmodyfikowane. W poniższych sekcjach przedstawiono kroki niezbędne do zaimplementowania interfejsy oddzielne powiadomienie dla drugiego właściwość czcionki. Druga właściwość czcionki zakłada się, że `HeadingFont` właściwości, który został dodany w poprzedniej sekcji.

###  <a name="_core_implementing_a_new_font_notification_interface"></a> Implementowanie nowy interfejs powiadomień czcionki

Aby rozróżnić powiadomienia o co najmniej dwóch czcionek, nowy interfejs powiadomień musi być zaimplementowana dla każdej czcionki używany w kontrolce. Poniżej opisano sposób implementacji nowy interfejs powiadomień czcionki, modyfikując kontrolki pliki nagłówkowy i implementacji.

### <a name="additions-to-the-header-file"></a>Dodatki do pliku nagłówka

W pliku nagłówka (. Godz.), Dodaj następujące wiersze do deklaracji klasy:

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Spowoduje to utworzenie implementację `IPropertyNotifySink` interfejs o nazwie `HeadingFontNotify`. Ten interfejs zawiera metodę o nazwie `OnChanged`.

### <a name="additions-to-the-implementation-file"></a>Dodatki do pliku implementacji

W kodzie, który inicjuje Czcionka nagłówka (w Konstruktorze sterowania), należy zmienić &*m_xFontNotification* do &*m_xHeadingFontNotify*. Następnie dodaj następujący kod:

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef` i `Release` metody `IPropertyNotifySink` interfejsu zachować informacje o licznik odwołań dla obiektu formantu ActiveX. Gdy formant uzyskuje dostęp do wskaźnika interfejsu, kontrolka wywołuje `AddRef` się zwiększać liczbę odwołań. Po zakończeniu formant ze wskaźnikiem wywoływanych przez nią `Release`, w znacznym sposób `GlobalFree` może być wywołane w celu zwolnieniu bloku pamięci globalnej. Gdy licznik odwołań dla tego interfejsu zbliża się do zera, może być zwolniony implementacji interfejsu. W tym przykładzie `QueryInterface` funkcja zwraca wskaźnik do `IPropertyNotifySink` interfejsu dla określonego obiektu. Ta funkcja umożliwia zapytania to obiektowi ustalenie, jakie interfejsy obsługuje formant ActiveX.

Po wprowadzeniu tych zmian zostały wprowadzone do projektu, należy ponownie skompilować projekt i użyj kontener testu, aby przetestować interfejs. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat dostępu do kontenera testu.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: używanie obrazów w kontrolce ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)

