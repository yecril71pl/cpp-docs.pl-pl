---
title: 'Formanty MFC ActiveX: używanie obrazów w formancie ActiveX'
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
ms.openlocfilehash: 9eb204dd240ae17421a20b7cddeff56c9a22c19b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618079"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>Formanty MFC ActiveX: używanie obrazów w formancie ActiveX

W tym artykule opisano typowy typ obrazu oraz sposób jego implementacji w formancie ActiveX. Tematy obejmują:

- [Przegląd właściwości obrazu niestandardowego](#_core_overview_of_custom_picture_properties)

- [Implementowanie niestandardowej właściwości obrazu w kontrolce ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [Dodawanie do projektu kontrolki](#_core_additions_to_your_control_project)

## <a name="overview-of-custom-picture-properties"></a><a name="_core_overview_of_custom_picture_properties"></a>Przegląd właściwości obrazu niestandardowego

Typ obrazu to jedna z grup typów wspólnych dla niektórych kontrolek ActiveX. Typ obrazu obsługuje wszystkie pliki, mapy bitowe lub ikony oraz umożliwia użytkownikowi określenie obrazu, który ma być wyświetlany w kontrolce ActiveX. Niestandardowe właściwości obrazu są implementowane przy użyciu obiektu Picture i get/set Functions, które umożliwiają kontrolowanie użytkownikowi dostępu do właściwości obrazu. Kontroluj użytkownikom dostęp do niestandardowej właściwości obrazu przy użyciu strony właściwości obrazu podstawowego.

Oprócz standardowego typu obrazu dostępne są również typy czcionek i kolorów. Aby uzyskać więcej informacji na temat używania standardowego typu czcionki w kontrolce ActiveX, zobacz [kontrolki ActiveX MFC w artykule: Używanie czcionek](mfc-activex-controls-using-fonts.md).

Klasy kontrolek ActiveX udostępniają kilka składników, których można użyć do zaimplementowania właściwości Picture w formancie. Te składniki obejmują:

- Klasa [CPictureHolder](reference/cpictureholder-class.md) .

   Ta klasa zapewnia łatwy dostęp do obiektu obrazu i funkcji dla elementu wyświetlanego przez właściwość obrazu niestandardowego.

- Obsługa właściwości typu **LPPICTUREDISP**wdrożonych za pomocą funkcji get/set.

   Za pomocą Widok klasy można szybko dodać właściwość niestandardową lub właściwości, które obsługują typ obrazu. Aby uzyskać więcej informacji na temat dodawania właściwości kontrolki ActiveX Widok klasy, zobacz [kontrolki ActiveX MFC: właściwości](mfc-activex-controls-properties.md).

- Strona właściwości, która operuje na właściwości obrazu lub właściwości formantu.

   Ta strona właściwości jest częścią grupy stron właściwości podstawowych dostępnych dla formantów ActiveX. Aby uzyskać więcej informacji na temat stron właściwości kontrolki ActiveX, zobacz artykuł [kontrolki ActiveX MFC: używanie stron właściwości podstawowych](mfc-activex-controls-using-stock-property-pages.md)

## <a name="implementing-a-custom-picture-property-in-your-activex-control"></a><a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a>Implementowanie niestandardowej właściwości obrazu w kontrolce ActiveX

Po wykonaniu czynności opisanych w tej sekcji formant może wyświetlać obrazy wybrane przez jego użytkownika. Użytkownik może zmienić wyświetlany obraz przy użyciu strony właściwości, która wyświetla bieżący obraz i ma przycisk przeglądania, który umożliwia użytkownikowi wybieranie różnych zdjęć.

Niestandardowa właściwość obrazu jest implementowana przy użyciu procesu podobnego do używanego do implementowania innych właściwości, główną różnicą, że właściwość niestandardowa musi obsługiwać typ obrazu. Ponieważ element właściwości Picture musi być rysowany przez formant ActiveX, do właściwości należy wprowadzić szereg dodatkowych i modyfikacji, aby można było w pełni zaimplementować.

Aby zaimplementować Właściwość obrazu niestandardowego, należy wykonać następujące czynności:

- [Dodaj kod do projektu kontrolki](#_core_additions_to_your_control_project).

   Należy dodać identyfikator strony właściwości standardowego obrazu, składową danych typu `CPictureHolder` i właściwość niestandardową typu **LPPICTUREDISP** z implementacją get/set.

- [Zmodyfikuj kilka funkcji w klasie kontrolki](#_core_modifications_to_your_control_project).

   Te modyfikacje zostaną wprowadzone do kilku funkcji, które są odpowiedzialne za rysowanie kontrolki ActiveX.

## <a name="additions-to-your-control-project"></a><a name="_core_additions_to_your_control_project"></a>Dodawanie do projektu kontrolki

Aby dodać identyfikator strony właściwości dla standardowej strony właściwości obrazu, Wstaw następujący wiersz po makrze BEGIN_PROPPAGEIDS w pliku implementacji kontroli (. CPP):

[!code-cpp[NVC_MFC_AxPic#1](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

Należy również zwiększyć liczbę parametrów BEGIN_PROPPAGEIDS makra. Poniższy wiersz ilustruje:

[!code-cpp[NVC_MFC_AxPic#2](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

Aby dodać `CPictureHolder` element członkowski danych do klasy kontrolki, Wstaw następujący wiersz w sekcji chronionej deklaracji klasy kontrolki w pliku nagłówkowym formantu (. H):

[!code-cpp[NVC_MFC_AxPic#3](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

Nazwa elementu członkowskiego danych nie jest konieczna *m_pic*; dowolna nazwa będzie wystarczająca.

Następnie Dodaj niestandardową właściwość, która obsługuje typ obrazu:

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Aby dodać niestandardową Właściwość obrazu przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. Z menu skrótów wybierz polecenie **Dodaj** , a następnie **Dodaj właściwość**.

1. W polu **Nazwa właściwości** wpisz nazwę właściwości. Na przykład, `ControlPicture` jest używany w tej procedurze.

1. W polu **Typ właściwości** wybierz pozycję **IPictureDisp** <strong>\*</strong> dla typu właściwości.

1. W obszarze **Typ implementacji**kliknij pozycję **Pobierz/ustaw metody**.

1. Wpisz unikatowe nazwy dla funkcji get i set lub zaakceptuj nazwy domyślne. (W tym przykładzie domyślne nazwy `GetControlPicture` i `SetControlPicture` są używane).

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący kod między komentarzami mapy wysyłania w nagłówku sterowania (. H):

[!code-cpp[NVC_MFC_AxPic#4](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

Ponadto Poniższy kod został wstawiony do mapy wysyłania implementacji kontroli (. CPP):

[!code-cpp[NVC_MFC_AxPic#5](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

Kreator dodawania właściwości dodaje również następujące dwie funkcje zastępcze w pliku implementacji formantu:

[!code-cpp[NVC_MFC_AxPic#6](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
> Nazwy klas i funkcji formantów mogą się różnić od powyższego przykładu.

### <a name="modifications-to-your-control-project"></a><a name="_core_modifications_to_your_control_project"></a>Modyfikacje projektu kontrolki

Po wprowadzeniu niezbędnych uzupełnień do projektu kontrolki należy zmodyfikować kilka funkcji, które wpływają na renderowanie kontrolki ActiveX. Te funkcje, `OnResetState` , `OnDraw` i funkcje get/set właściwości obrazu niestandardowego, znajdują się w pliku implementacji formantu. (Należy zauważyć, że w tym przykładzie Klasa Control jest wywoływana `CSampleCtrl` , `CPictureHolder` element członkowski danych jest nazywany *m_pic*, a nazwa właściwości obrazu niestandardowego to `ControlPicture` ).

W funkcji sterowania `OnResetState` Dodaj następujący opcjonalny wiersz po wywołaniu `COleControl::OnResetState` :

[!code-cpp[NVC_MFC_AxPic#7](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

Spowoduje to ustawienie obrazu kontrolki na pusty obraz.

Aby poprawnie narysować obraz, wykonaj wywołanie [CPictureHolder:: Render](reference/cpictureholder-class.md#render) w `OnDraw` funkcji Control. Zmodyfikuj funkcję w taki sposób, aby wyglądała podobnie jak w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxPic#8](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

W funkcji get właściwości obrazu niestandardowego kontrolki Dodaj następujący wiersz:

[!code-cpp[NVC_MFC_AxPic#9](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

W funkcji ustaw właściwości obrazu niestandardowego kontrolki Dodaj następujące wiersze:

[!code-cpp[NVC_MFC_AxPic#10](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

Właściwość Picture musi być trwała, aby informacje dodane w czasie projektowania były wyświetlane w czasie wykonywania. Dodaj następujący wiersz do `COleControl` funkcji klasy pochodnej `DoPropExchange` :

[!code-cpp[NVC_MFC_AxPic#11](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
> Nazwy klas i funkcji mogą się różnić od powyższego przykładu.

Po zakończeniu modyfikacji ponownie skompiluj projekt, aby uwzględnić nowe funkcje niestandardowej właściwości obrazu i Użyj kontenera testów do przetestowania nowej właściwości. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testów,](testing-properties-and-events-with-test-container.md) Aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: używanie czcionek](mfc-activex-controls-using-fonts.md)<br/>
[Kontrolki ActiveX MFC: strony właściwości](mfc-activex-controls-property-pages.md)
