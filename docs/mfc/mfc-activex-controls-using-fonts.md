---
title: "Formanty MFC ActiveX: Używanie czcionek | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
dev_langs: C++
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
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a788285aed8e8b7483e13c954ee193aca69d1100
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-using-fonts"></a>Kontrolki ActiveX MFC: używanie czcionek
Jeśli formant ActiveX jest wyświetlany tekst, można zezwolić użytkownikowi kontroli Zmienianie wyglądu tekstu, zmieniając właściwość czcionki. Właściwości czcionki są zaimplementowane jako obiekty czcionki i może być jedna z dwóch typów: standardowych lub niestandardowych. Właściwości podstawowe czcionki są właściwości preimplemented czcionki, które można dodać za pomocą Kreatora dodawania właściwości. Właściwości niestandardowe czcionki nie są preimplemented i dewelopera kontrolek określa zachowanie i użycia właściwości.  
  
 W tym artykule omówiono następujące tematy:  
  
-   [Za pomocą właściwości zasobów czcionki](#_core_using_the_stock_font_property)  
  
-   [Za pomocą właściwości niestandardowe czcionki formantu](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a>Za pomocą właściwości standardowych czcionki  
 Właściwości podstawowe czcionki są preimplemented przez klasę [colecontrol —](../mfc/reference/colecontrol-class.md). Ponadto standardowe strony właściwości czcionki jest również dostępny, umożliwiając użytkownikom na zmianę różnych atrybutów obiektu czcionki, takie jak jej nazwę, rozmiar i styl.  
  
 Dostęp do obiektu czcionki za pośrednictwem [GetFont](../mfc/reference/colecontrol-class.md#getfont), [SetFont](../mfc/reference/colecontrol-class.md#setfont), i [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) funkcji `COleControl`. Formant użytkownika będą uzyskiwać dostęp do obiektu czcionki za pośrednictwem `GetFont` i `SetFont` funkcje w taki sam sposób jak inne właściwości Get i Set. Podczas dostępu do obiektu czcionki jest wymagana od w formancie, użyj `InternalGetFont` funkcji.  
  
 Zgodnie z opisem w [kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md), dodawanie właściwości standardowych jest bardzo proste dzięki [Dodaj Kreatora właściwości](../ide/names-add-property-wizard.md). Wybierz właściwość czcionki, a Kreator dodawania właściwości automatycznie wstawia standardowych wejścia czcionki formantu mapy wysyłania.  
  
#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Aby dodać za pomocą Kreatora dodawania właściwości standardowych właściwość czcionki  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
     Spowoduje to otwarcie Kreatora dodawania właściwości.  
  
5.  W **nazwa właściwości** kliknij **czcionki**.  
  
6.  Kliknij przycisk **Zakończ**.  
  
 Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania formantu, znajduje się w pliku implementacji klasy:  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]  
  
 Ponadto Kreator dodawania właściwości dodaje następujący wiersz do formantu. Plik IDL:  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]  
  
 Podstawowe właściwości podpisu jest przykładem właściwości tekstu, które mogą być wystawiane przy użyciu standardowych informacji o właściwościach czcionki. Dodawanie właściwości podpisu podstawowego do formantu używa kroki podobne do akcji właściwość czcionki.  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Aby dodać podstawowe właściwości podpisu za pomocą Kreatora dodawania właściwości  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
     Spowoduje to otwarcie Kreatora dodawania właściwości.  
  
5.  W **nazwa właściwości** kliknij **podpis**.  
  
6.  Kliknij przycisk **Zakończ**.  
  
 Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania formantu, znajduje się w pliku implementacji klasy:  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a>Modyfikowanie funkcji OnDraw  
 Domyślna implementacja `OnDraw` używa czcionki systemu Windows dla cały tekst wyświetlany w formancie. Oznacza to, że należy zmodyfikować `OnDraw` kodu, wybierając obiekt czcionki do kontekstu urządzenia. Aby to zrobić, należy wywołać [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) i Przekaż kontekst urządzenia formantu, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]  
  
 Po `OnDraw` funkcja została zmodyfikowana, aby używać obiektu czcionki, dowolny tekst w formancie zostanie wyświetlony z właściwości ze standardowych właściwość czcionki formantu.  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a>Za pomocą właściwości niestandardowe czcionki formantu  
 Oprócz standardowych właściwość czcionki formantu ActiveX może mieć właściwości niestandardowe czcionki. Aby dodać właściwości niestandardowe czcionki należy:  
  
-   Kreator dodawania właściwości do zaimplementowania niestandardowego właściwość czcionki.  
  
-   [Przetwarzanie powiadomień czcionki](#_core_processing_font_notifications).  
  
-   [Implementowanie nowy interfejs powiadomień czcionki](#_core_implementing_a_new_font_notification_interface).  
  
###  <a name="_core_implementing_a_custom_font_property"></a>Implementowanie właściwości niestandardowe czcionki  
 Aby wdrożyć niestandardowy właściwość czcionki, umożliwia Kreatora dodawania właściwości Dodaj właściwości, a następnie wprowadź niektóre zmiany w kodzie. W poniższych sekcjach opisano sposób dodawania niestandardowego `HeadingFont` właściwości do kontrolki próbki.  
  
##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Aby dodać niestandardowe właściwości Font za pomocą Kreatora dodawania właściwości  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
     Spowoduje to otwarcie Kreatora dodawania właściwości.  
  
5.  W **nazwa właściwości** wpisz nazwę właściwości. Na przykład użyć **HeadingFont**.  
  
6.  Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.  
  
7.  W **typ właściwości** wybierz opcję **IDispatch\***  dla typu właściwości.  
  
8.  Kliknij przycisk **Zakończ**.  
  
 Kreator dodawania właściwości tworzy kod, aby dodać `HeadingFont` niestandardowa właściwość `CSampleCtrl` klasy i próbka. Plik IDL. Ponieważ `HeadingFont` jest typu Get/Set właściwości modyfikuje Kreatora dodawania właściwości `CSampleCtrl` klasy mapy wysyłania do uwzględnienia `DISP_PROPERTY_EX_ID` [disp_property_ex —](../mfc/reference/dispatch-maps.md#disp_property_ex) wpis makra:  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]  
  
 `DISP_PROPERTY_EX` Kojarzy makro `HeadingFont` nazwa właściwości z odpowiadającymi mu dostawcami `CSampleCtrl` klasy metody Get i Set, `GetHeadingFont` i `SetHeadingFont`. Typ wartości właściwości jest też określona; w takim przypadku **VT_FONT**.  
  
 Dodaj właściwość dodaje także deklaracji w pliku nagłówka (. H) dla `GetHeadingFont` i `SetHeadingFont` funkcje i dodaje szablony ich funkcji w pliku implementacji (. CPP):  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]  
  
 Ponadto Kreator dodawania właściwości modyfikuje formantu. Plik IDL, dodając wpis dotyczący `HeadingFont` właściwości:  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]  
  
### <a name="modifications-to-the-control-code"></a>Zmiany w kodzie formantu  
 Teraz, dodano `HeadingFont` właściwości do kontrolki, musi wprowadzić pewne zmiany do formantu nagłówka i implementacji plików do zapewnienia pełnej obsługi nowej właściwości.  
  
 W pliku nagłówka (. H) dodaj następujące deklaracji zmiennej członka chronionego:  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]  
  
 W pliku implementacji (. CPP), wykonaj następujące czynności:  
  
-   Inicjowanie `m_fontHeading` w Konstruktorze formantu.  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   Deklarowanie statycznego **FONTDESC** struktury zawierającej domyślne atrybuty czcionki.  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   W formancie `DoPropExchange` elementu członkowskiego działać, dodaj wywołanie do `PX_Font` funkcji. Zapewnia to inicjowania i trwałości dla właściwości niestandardowej czcionki.  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   Zakończ wdrożenie formantu `GetHeadingFont` funkcję elementu członkowskiego.  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   Zakończ wdrożenie formantu `SetHeadingFont` funkcję elementu członkowskiego.  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   Modyfikowanie formantu `OnDraw` funkcji członkowskiej, aby zdefiniować zmienną do przechowywania wcześniej wybranej czcionki.  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   Modyfikowanie formantu `OnDraw` funkcji członkowskiej, aby wybrać niestandardowy czcionki do kontekstu urządzenia przez dodanie następująca linia wszędzie tam, gdzie czcionki ma być używany.  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   Modyfikowanie formantu `OnDraw` funkcji członkowskiej wybierz poprzedniej czcionki do kontekstu urządzenia, dodając następujący wiersz po czcionki.  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]  
  
 Po zaimplementowaniu niestandardowe właściwości Font standardowe strony właściwości czcionki powinny zostać wdrożone, umożliwiając użytkownikom kontroli zmiany bieżącej czcionki formantu. Aby dodać identyfikator strony właściwości dla standardowej strony właściwości czcionki, Wstaw następujący wiersz po `BEGIN_PROPPAGEIDS` makra:  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]  
  
 Należy również zwiększyć parametr liczba Twojej `BEGIN_PROPPAGEIDS` makro o jeden. Następujący wiersz przedstawiono to:  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]  
  
 Po dokonaniu zmian, skompiluj ponownie cały projekt, aby włączyć dodatkowe funkcje.  
  
###  <a name="_core_processing_font_notifications"></a>Przetwarzanie powiadomień czcionki  
 W większości przypadków kontrolki musi znać modyfikacji właściwości obiektu czcionki. Każdy obiekt czcionki jest w stanie dostarczać powiadomienia o zmianie przez wywołanie funkcji członkowskiej klasy **IFontNotification** interfejsu implementowanego przez `COleControl`.  
  
 Jeśli formant używa standardowych właściwość czcionki, jego powiadomienia są obsługiwane przez `OnFontChanged` funkcji członkowskiej klasy `COleControl`. Podczas dodawania właściwości niestandardowe czcionki, może mieć za pomocą tego samego wykonania. W przykładzie w poprzedniej sekcji, to osiągnąć, przekazywanie &**m_xFontNotification** podczas inicjowania **m_fontHeading** zmiennej członkowskiej.  
  
 ![Wdrażanie wielu interfejsów obiektów czcionek](../mfc/media/vc373q1.gif "vc373q1")  
Wdrażanie wielu interfejsów obiektów czcionek  
  
 Pokaż linie ciągłe na powyższej ilustracji czy oba obiekty czcionki korzystają z tego samego wykonania **IFontNotification**. Może to powodować problemy, aby odróżnić zmianie czcionki, która.  
  
 Jednym ze sposobów rozróżnienia powiadomienia obiektu czcionki formantu jest utworzenie oddzielnych implementacja **IFontNotification** interfejsu dla każdego obiektu font w formancie. Ta technika pozwala optymalizacji kodu rysunku, aktualizując tylko ciąg lub ciągi, korzystających z ostatnio zmodyfikowane czcionki. Poniższe sekcje przedstawiają kroki niezbędne do zaimplementowania interfejsów osobne powiadomienie dla drugiego właściwość czcionki. Druga właściwość czcionki zakłada się, że `HeadingFont` właściwość, która została dodana w poprzedniej sekcji.  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a>Implementowanie nowy interfejs powiadomień czcionki  
 Aby odróżnić powiadomienia o dwóch lub więcej czcionek, nowy interfejs powiadomień musi być implementowana dla każdej czcionki używany w formancie. W poniższych sekcjach opisano sposobu wdrażania nowy interfejs powiadomienie czcionki przez zmodyfikowanie pliki formant nagłówka i implementacji.  
  
### <a name="additions-to-the-header-file"></a>Dodatki do pliku nagłówka  
 W pliku nagłówka (. H) dodaj następujące wiersze do deklaracji klasy:  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]  
  
 Spowoduje to utworzenie implementacja `IPropertyNotifySink` interfejs o nazwie `HeadingFontNotify`. Ten interfejs zawiera metodę o nazwie `OnChanged`.  
  
### <a name="additions-to-the-implementation-file"></a>Dodatki do pliku implementacji  
 W kodzie, który inicjuje Czcionka nagłówka (w Konstruktorze sterowania), należy zmienić `&m_xFontNotification` do `&m_xHeadingFontNotify`. Następnie dodaj następujący kod:  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]  
  
 `AddRef` i `Release` metod w `IPropertyNotifySink` interfejsu zachować informacje o liczebności referencyjnej dla obiekt formantu ActiveX. Gdy formant uzyska dostęp do wskaźnika interfejsu, kontrolka wywołuje `AddRef` Aby zwiększyć liczbę odwołań. Po zakończeniu formantu ze wskaźnikiem wywołuje `Release`, znacznie tak samo jak robi **GlobalFree** może być wywołane w celu zwolnienia blok pamięci globalnej. Gdy liczba odwołań dla tego interfejsu przechodzi do zera, może zostać zwolnione implementacji interfejsu. W tym przykładzie `QueryInterface` funkcja zwraca wskaźnik do `IPropertyNotifySink` interfejsu dla określonego obiektu. Ta funkcja umożliwia formantu ActiveX do obiektu w celu określenia, jakie interfejsy obsługuje zapytania.  
  
 Po wprowadzeniu tych zmian zostały wprowadzone do projektu, należy ponownie skompilować projekt i przetestować interfejs przy użyciu kontenera testu. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat sposobu dostępu kontener testu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: Używanie obrazów w formancie ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)

