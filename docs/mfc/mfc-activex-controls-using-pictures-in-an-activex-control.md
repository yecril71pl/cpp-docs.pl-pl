---
title: 'Kontrolki ActiveX MFC: Używanie obrazów w kontrolce ActiveX'
ms.date: 11/04/2016
f1_keywords:
- LPPICTUREDISP
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
ms.openlocfilehash: 86e9bd220d06e714030f7d44888b210ba35fd345
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264563"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>Kontrolki ActiveX MFC: Używanie obrazów w kontrolce ActiveX

W tym artykule opisano typowe typu obrazu i sposobie jego implementowania w kontrolce ActiveX. Tematy obejmują:

- [Przegląd właściwości obrazu niestandardowego](#_core_overview_of_custom_picture_properties)

- [Implementowanie właściwości obrazu niestandardowego w kontrolce ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [Dodatki do projektu kontroli](#_core_additions_to_your_control_project)

##  <a name="_core_overview_of_custom_picture_properties"></a> Przegląd właściwości obrazu niestandardowego

Typ obrazu jest jednym z grupą typów wspólnych dla niektórych formantów ActiveX. Typ obrazu obsługuje metapliki, mapy bitowe lub ikony i pozwala użytkownikowi na określenie obraz do wyświetlenia w kontrolce ActiveX. Niestandardowe właściwości obrazu są implementowane za pomocą obiektu obrazu i funkcje Get/Set, które umożliwiają sterowanie dostępem użytkowników do właściwości obrazu. Użytkownicy kontroli dostępu do właściwości niestandardowych obrazów przy użyciu akcji strona właściwości obrazu.

Oprócz standardowych typ obrazu czcionek i kolorów są również dostępne typy. Aby uzyskać więcej informacji na temat używania standardowych typ czcionki w kontrolce ActiveX, zobacz artykuł [kontrolki ActiveX MFC: Używanie czcionek](../mfc/mfc-activex-controls-using-fonts.md).

Klasy kontrolek ActiveX zapewniają kilka składników służących do zaimplementowania właściwość obraz w kontrolce. Te składniki obejmują:

- [CPictureHolder](../mfc/reference/cpictureholder-class.md) klasy.

   Ta klasa udostępnia łatwy dostęp do obiektu obrazu i funkcje dla elementu wyświetlanego przez niestandardowe właściwości obrazu.

- Wsparcie dla właściwości typu **LPPICTUREDISP**, jest implementowane za pomocą funkcji Get/Set.

   Za pomocą widoku klas, które można szybko dodać właściwość niestandardową lub właściwości, która obsługuje typ obrazu. Aby uzyskać więcej informacji na temat dodawania właściwości formantu ActiveX, za pomocą widoku klas, zobacz artykuł [kontrolki ActiveX MFC: Właściwości](../mfc/mfc-activex-controls-properties.md).

- Strona właściwości, która manipuluje właściwość obrazu lub właściwości formantu.

   Ta strona właściwości jest częścią grupy stron właściwości standardowych dostępna dla kontrolki ActiveX. Aby uzyskać więcej informacji na stronach właściwości kontrolki ActiveX, zobacz artykuł [kontrolki ActiveX MFC: Używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)

##  <a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a> Implementowanie właściwości obrazu niestandardowego w kontrolce ActiveX

Po wykonaniu czynności opisanych w tej sekcji formant może wyświetlić obrazy wybrany przez użytkownika. Użytkownik może zmienić wyświetlany obraz, używając strony właściwości, pokazuje bieżący obraz, który znajduje się przycisk przeglądania, który umożliwia użytkownikowi wybierz różnych obrazów.

Niestandardowe właściwości obrazu jest implementowany przy użyciu procesu podobny do wykonywania innych właściwości, a różnica, możliwe, że niestandardowa właściwość musi obsługiwać typ obrazu. Ponieważ element właściwości obrazu, musi zostać narysowany przez formant ActiveX, liczba uzupełnienia i modyfikacje należy do właściwości przed można zaimplementować w pełni.

Aby zaimplementować niestandardowy właściwości obrazu, wykonaj następujące czynności:

- [Dodawanie kodu do projektu kontroli](#_core_additions_to_your_control_project).

   Standardowy obraz właściwości identyfikator strony, składowa danych klasy typu `CPictureHolder`i niestandardowe właściwości typu **LPPICTUREDISP** przy użyciu Get/Set implementacja musi zostać dodany.

- [Zmodyfikuj kilka funkcji w klasie kontrolki](#_core_modifications_to_your_control_project).

   Te modyfikacje zostaną nawiązać kilka funkcji, które są odpowiedzialne za rysunek formantu ActiveX.

##  <a name="_core_additions_to_your_control_project"></a> Dodatki do projektu kontroli

Aby dodać identyfikator strony właściwości dla standardowej strony właściwości obrazu, Wstaw następujący wiersz po BEGIN_PROPPAGEIDS — makro w pliku implementacji (. CPP):

[!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

Za pomocą jednej, należy zwiększyć wartość parametru liczba BEGIN_PROPPAGEIDS — makro. Ilustruje poniższy wiersz, to:

[!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

Aby dodać `CPictureHolder` element członkowski danych do klasy formantu, Wstaw następujący wiersz w chronionych sekcji deklaracji klasy formantu w pliku nagłówka (. GODZ.):

[!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

Nie jest konieczne nazwanie swoje element członkowski danych *m_pic*; wystarczy dowolną nazwę.

Następnie dodaj właściwość niestandardowa, która obsługuje typ obrazu:

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Aby dodać właściwość obrazu niestandardowego za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. Z menu skrótów wybierz polecenie **Dodaj** i następnie **Dodaj właściwość**.

1. W **nazwa właściwości** wpisz nazwę właściwości. Na przykład do celów `ControlPicture` jest używany w ramach tej procedury.

1. W **typ właściwości** wybierz opcję **elementu IPictureDisp** <strong>\*</strong> dla typu właściwości.

1. Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.

1. Wpisz unikatowe nazwy, Pobierz i ustaw funkcji lub zaakceptuj domyślne nazwy. (W tym przykładzie domyślne nazwy `GetControlPicture` i `SetControlPicture` są używane.)

9. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący kod między komentarze mapy wysyłania do formantu nagłówka (. H) plik:

[!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

Ponadto, następujący kod został wstawiony w mapie wysyłania implementacji kontroli (. Plik CPP):

[!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

Dodaj właściwość dodaje także następujące funkcje dwie klasy zastępczej w pliku implementacji:

[!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
>  Nazwy klas i funkcji sterowania mogą różnić się od powyższego przykładu.

###  <a name="_core_modifications_to_your_control_project"></a> Modyfikacje projektu kontroli

Po dokonaniu niezbędnych dodatki do projektu kontroli, musisz zmodyfikować kilka funkcji, które wpływają na renderowanie formantu ActiveX. Te funkcje `OnResetState`, `OnDraw`, oraz funkcji pobierania/ustawiania niestandardowej właściwości obrazu, znajdują się w pliku implementacji. (Należy pamiętać, że w tym przykładzie Klasa sterowania nosi nazwę `CSampleCtrl`, `CPictureHolder` element członkowski danych jest nazywany *m_pic*, i nazwę właściwości obrazu niestandardowego `ControlPicture`.)

W kontrolce `OnResetState` funkcji, Dodaj następujący wiersz opcjonalne po wywołaniu `COleControl::OnResetState`:

[!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

Obraz kontrolki to ustawienie puste obrazu.

Aby narysować obraz poprawnie, wywołania [CPictureHolder::Render](../mfc/reference/cpictureholder-class.md#render) w kontrolce `OnDraw` funkcji. Zmodyfikuj funkcję, aby można było podobne do następującego przykładu:

[!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

W funkcji Get właściwość obrazu niestandardowego formantu Dodaj następujący wiersz:

[!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

W funkcji ustawiania właściwości obrazu niestandardowego formantu Dodaj następujące wiersze:

[!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

Właściwości obrazu muszą być wykonane trwały, więc, że informacje dodane w czasie projektowania pojawią się w czasie wykonywania. Dodaj następujący wiersz do `COleControl`— w klasie pochodnej `DoPropExchange` funkcji:

[!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
>  Nazwy klas i funkcji mogą różnić się od powyższego przykładu.

Po zakończeniu zmiany należy ponownie skompilować projekt, aby zastosować nowe funkcje niestandardowe właściwości obrazu i użyj kontener testu, aby przetestować nową właściwość. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat dostępu do kontenera testu.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: Używanie czcionek](../mfc/mfc-activex-controls-using-fonts.md)<br/>
[Kontrolki ActiveX MFC: Strony właściwości](../mfc/mfc-activex-controls-property-pages.md)
