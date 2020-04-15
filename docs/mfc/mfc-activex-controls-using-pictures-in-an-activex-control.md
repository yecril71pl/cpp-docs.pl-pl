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
ms.openlocfilehash: 1f78823f39417ff6928a1b915d83507bc1ac9526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358296"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>Formanty MFC ActiveX: używanie obrazów w formancie ActiveX

W tym artykule opisano typ typ obrazu i jak go zaimplementować w formancie ActiveX. Tematy obejmują:

- [Omówienie niestandardowych właściwości obrazu](#_core_overview_of_custom_picture_properties)

- [Implementowanie właściwości niestandardowego obrazu w formancie ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [Dodatki do projektu sterowania](#_core_additions_to_your_control_project)

## <a name="overview-of-custom-picture-properties"></a><a name="_core_overview_of_custom_picture_properties"></a>Omówienie niestandardowych właściwości obrazu

Typ obrazu jest jedną z grup typów wspólnych dla niektórych formantów ActiveX. Typ obrazu obsługuje metaplików, bitmap lub ikon i umożliwia użytkownikowi określenie obrazu, który ma być wyświetlany w formancie ActiveX. Właściwości Obraz niestandardowy są implementowane przy użyciu obiektu obrazu i funkcji Get/Set, które umożliwiają użytkownikowi kontroli dostęp do właściwości Picture. Użytkownicy kontroluj dostęp do niestandardowej właściwości Obraz za pomocą strony właściwości Zdjęcie.

Oprócz standardowego typu obrazu dostępne są również typy czcionki i kolor. Aby uzyskać więcej informacji na temat używania standardowego typu czcionki w formancie ActiveX, zobacz artykuł [MFC ActiveX Controls: Using Fonts](../mfc/mfc-activex-controls-using-fonts.md).

Klasy formantu ActiveX zawierają kilka składników, których można użyć do zaimplementowania Picture właściwości w formancie. Składniki te obejmują:

- [CPictureHolder](../mfc/reference/cpictureholder-class.md) klasy.

   Ta klasa zapewnia łatwy dostęp do obiektu obrazu i funkcji elementu wyświetlanego przez niestandardową właściwość Picture.

- Obsługa właściwości typu **LPPICTUREDISP**, zaimplementowana za pomocą funkcji Get/Set.

   Za pomocą widoku klasy można szybko dodać właściwość niestandardową lub właściwości, która obsługuje typ obrazu. Aby uzyskać więcej informacji na temat dodawania właściwości formantu ActiveX za pomocą widoku klasy, zobacz artykuł [MFC ActiveX Controls: Properties](../mfc/mfc-activex-controls-properties.md).

- Strona właściwości, która manipuluje właściwością lub właściwościami Picture formantu.

   Ta strona właściwości jest częścią grupy stron właściwości magazynowych dostępnych dla formantów ActiveX. Aby uzyskać więcej informacji na temat stron właściwości formantu ActiveX, zobacz artykuł [Kontrolki MFC ActiveX: Korzystanie ze stron właściwości stockowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)

## <a name="implementing-a-custom-picture-property-in-your-activex-control"></a><a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a>Implementowanie właściwości niestandardowego obrazu w formancie ActiveX

Po wykonaniu kroków opisanych w tej sekcji formant może wyświetlać obrazy wybrane przez użytkownika. Użytkownik może zmienić wyświetlany obraz za pomocą strony właściwości, która pokazuje bieżący obraz i ma przycisk Przeglądaj, który umożliwia użytkownikowi wybranie różnych obrazów.

Niestandardowa właściwość Picture jest implementowana przy użyciu procesu podobnego do procesu używanego do implementowania innych właściwości, główną różnicą jest to, że właściwość niestandardowa musi obsługiwać typ Obrazu. Ponieważ element Picture właściwości muszą być rysowane przez ActiveX kontroli, szereg uzupełnień i modyfikacji muszą być wprowadzone do właściwości, zanim będzie można w pełni zaimplementować.

Aby zaimplementować niestandardową właściwość Picture, należy wykonać następujące czynności:

- [Dodaj kod do projektu kontrolnego](#_core_additions_to_your_control_project).

   Należy dodać standardowy identyfikator strony właściwości `CPictureHolder`Picture, element członkowski danych typu i właściwość niestandardową typu **LPPICTUREDISP** z implementacją Get/Set.

- [Zmodyfikuj kilka funkcji w klasie sterowania](#_core_modifications_to_your_control_project).

   Te modyfikacje zostaną wprowadzone do kilku funkcji, które są odpowiedzialne za rysowanie formantu ActiveX.

## <a name="additions-to-your-control-project"></a><a name="_core_additions_to_your_control_project"></a>Dodatki do projektu sterowania

Aby dodać identyfikator strony właściwości dla standardowej strony właściwości Picture, wstaw następujący wiersz po BEGIN_PROPPAGEIDS makra w pliku implementacji formantu (. CPP):

[!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

Należy również zwiększać parametr liczby BEGIN_PROPPAGEIDS makra o jeden. Poniższy wiersz ilustruje to:

[!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

Aby dodać `CPictureHolder` element członkowski danych do klasy formantu, wstaw następujący wiersz w sekcji chronionej deklaracji klasy formantu w pliku nagłówka formantu (. H):

[!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

Nie jest konieczne nazywanie danych *m_pic;* wystarczy każda nazwa.

Następnie dodaj niestandardową właściwość obsługującą typ obrazu:

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Aby dodać niestandardową właściwość obrazu za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. Z menu skrótów wybierz polecenie **Dodaj,** a następnie **dodaj właściwość**.

1. W polu **Nazwa właściwości** wpisz nazwę właściwości. Na przykład w `ControlPicture` tej procedurze jest używana.

1. W polu **Typ właściwości** wybierz pozycję **IPictureDisp** <strong>\*</strong> dla typu właściwości.

1. W przypadku **typu implementacji**kliknij pozycję **Pobierz/Ustaw metody**.

1. Wpisz unikatowe nazwy funkcji Pobierz i Ustaw lub zaakceptuj nazwy domyślne. (W tym przykładzie `GetControlPicture` nazwy `SetControlPicture` domyślne są używane).

1. Kliknij przycisk **Zakończ**.

Kreator dodawania właściwości dodaje następujący kod między komentarzami mapy wysyłki w nagłówku formantu (. H) plik:

[!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

Ponadto na mapie wysyłki implementacji formantu wstawiono następujący kod (. CPP):

[!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

Kreator dodawania właściwości dodaje również następujące dwie funkcje skrótowe w pliku implementacji formantu:

[!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
> Nazwa klasy kontroli i funkcji może różnić się od powyższego przykładu.

### <a name="modifications-to-your-control-project"></a><a name="_core_modifications_to_your_control_project"></a>Modyfikacje projektu sterowania

Po dokonaniu niezbędnych dodatków do projektu sterowania, należy zmodyfikować kilka funkcji, które wpływają na renderowanie formantu ActiveX. Te funkcje `OnDraw`, `OnResetState`i Get/Set funkcje niestandardowego Picture właściwości, znajdują się w pliku implementacji formantu. (Należy zauważyć, że w tym `CSampleCtrl`przykładzie nazywa się klasa kontrolna `CPictureHolder` , element członkowski danych jest nazywany *m_pic*, a niestandardowa nazwa właściwości obrazu to `ControlPicture`.)

W funkcji `OnResetState` sterowania dodaj następujący wiersz opcjonalny `COleControl::OnResetState`po wywołaniu do:

[!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

Spowoduje to ustawienie obrazu formantu na pusty obraz.

Aby narysować obraz poprawnie, nawiązać połączenie z [CPictureHolder::Render](../mfc/reference/cpictureholder-class.md#render) w funkcji sterowania. `OnDraw` Zmodyfikuj funkcję tak, aby przypominała następujący przykład:

[!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

W funkcji Pobierz właściwości niestandardowego obrazu formantu dodaj następujący wiersz:

[!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

W funkcji Ustaw niestandardowej właściwości Obraz formantu dodaj następujące wiersze:

[!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

Właściwość obrazu musi być trwałe, tak aby informacje dodane w czasie projektowania będą wyświetlane w czasie wykonywania. Dodaj następujący wiersz `COleControl`do funkcji klasy `DoPropExchange` pochodnej:

[!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
> Nazwy klas i funkcji mogą różnić się od powyższego przykładu.

Po zakończeniu modyfikacji odbuduj projekt, aby włączyć nowe funkcje niestandardowej właściwości Picture i użyj kontenera testowego, aby przetestować nową właściwość. Zobacz [testowanie właściwości i zdarzenia z kontenerem testowym,](../mfc/testing-properties-and-events-with-test-container.md) aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: używanie czcionek](../mfc/mfc-activex-controls-using-fonts.md)<br/>
[Kontrolki ActiveX MFC: strony właściwości](../mfc/mfc-activex-controls-property-pages.md)
