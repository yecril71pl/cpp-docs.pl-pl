---
title: 'Formanty MFC ActiveX: Używanie obrazów w formancie ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LPPICTUREDISP
dev_langs:
- C++
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 356d7acd67747f4310ed0e4f564df7d1533e88ed
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930651"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>Kontrolki ActiveX MFC: używanie obrazów w kontrolce ActiveX
W tym artykule opisano typowe typ obrazu oraz jak ją wdrożyć w formantu ActiveX. Tematy obejmują:  
  
-   [Przegląd właściwości niestandardowego obrazu](#_core_overview_of_custom_picture_properties)  
  
-   [Implementowanie właściwości obrazu niestandardowego formantu ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)  
  
-   [Dodawanie do projektu kontroli](#_core_additions_to_your_control_project)  
  
##  <a name="_core_overview_of_custom_picture_properties"></a> Przegląd właściwości niestandardowego obrazu  
 Typ obrazu jest jednym z grupy typów wspólnych dla niektórych formantów ActiveX. Typ obrazu obsługuje metapliki, map bitowych lub ikony i umożliwia użytkownikowi określenie obraz do wyświetlenia w formancie ActiveX. Niestandardowe właściwości obrazu są implementowane za pomocą obiektu obrazu i funkcje Get i Set, które umożliwiają sterowanie dostępem użytkowników do właściwości obrazu. Użytkownicy kontroli dostępu do niestandardowej właściwości obrazu za pomocą giełdowych strona właściwości obrazu.  
  
 Oprócz standardowych typ obrazu czcionek i kolorów są również dostępne typy. Aby uzyskać więcej informacji na temat używania standardowy typ czcionki formantu ActiveX, zobacz artykuł [kontrolki ActiveX MFC: przy użyciu czcionek](../mfc/mfc-activex-controls-using-fonts.md).  
  
 Klasy formantów ActiveX podać kilka składników, których można używać do implementowania właściwość obrazu w formancie. Składniki te obejmują:  
  
-   [CPictureHolder](../mfc/reference/cpictureholder-class.md) klasy.  
  
     Ta klasa zapewnia łatwy dostęp do obiektu obrazu oraz funkcji dla elementu wyświetlane przez niestandardowe właściwości obrazu.  
  
-   Obsługa dla właściwości typu **LPPICTUREDISP**, zaimplementowanym funkcje Get i Set.  
  
     Korzystając z widoku klasy można szybko dodać niestandardowe właściwości lub właściwości, która obsługuje typ obrazu. Aby uzyskać więcej informacji na temat dodawania właściwości formantu ActiveX z widoku klasy, zobacz artykuł [kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md).  
  
-   Strony właściwości manipuluje właściwości obrazu lub właściwości formantu.  
  
     Ta strona właściwości jest częścią grupy stron właściwości standardowych dostępne dla formantów ActiveX. Aby uzyskać więcej informacji na stronach właściwości formantu ActiveX, zobacz artykuł [kontrolki ActiveX MFC: przy użyciu strony właściwości zasobów](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
##  <a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a> Implementowanie właściwości obrazu niestandardowego formantu ActiveX  
 Po wykonaniu czynności opisanych w tej sekcji formantu można wyświetlić obrazy wybrany przez użytkownika. Użytkownik może zmienić wyświetlany obraz, używając strony właściwości, który pokazuje bieżący obraz i ma przycisk Przeglądaj, który umożliwia użytkownikowi wybierz różnych obrazów.  
  
 Niestandardowe właściwości obrazu jest implementowane za pomocą proces podobny do wykonywania innych właściwości główną różnicą, że właściwość niestandardowa musi obsługiwać typ obrazu. Ponieważ przez formant ActiveX musi zostać narysowany element właściwości obrazu, liczba dodatki i zmiany muszą być wprowadzane do właściwości przed można zaimplementować pełni.  
  
 Aby zaimplementować niestandardowe właściwości obrazu, wykonaj następujące czynności:  
  
-   [Dodaj do projektu kontroli kodu](#_core_additions_to_your_control_project).  
  
     Standardowe właściwości strony identyfikator obrazu, elementu członkowskiego danych typu `CPictureHolder`i niestandardowe właściwości typu **LPPICTUREDISP** z Get/Set implementacji musi zostać dodany.  
  
-   [Modyfikowanie kilka funkcji w Twojej klasy kontrolki](#_core_modifications_to_your_control_project).  
  
     Te modyfikacje zostaną wprowadzone do kilka funkcji, które są odpowiedzialne za rysunek formantu ActiveX.  
  
##  <a name="_core_additions_to_your_control_project"></a> Dodawanie do projektu kontroli  
 Aby dodać identyfikator strony właściwości dla standardowej strony właściwości obrazu, wstaw poniższy wiersz po begin_proppageids — makro w pliku implementacji (. CPP):  
  
 [!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]  
  
 Parametr liczba begin_proppageids — makro należy również zwiększyć o jeden. Następujący wiersz przedstawiono to:  
  
 [!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]  
  
 Aby dodać `CPictureHolder` element członkowski danych klasy formantu Wstaw następujący wiersz w sekcji chronionych deklaracja klasy formantu w pliku nagłówka (. H):  
  
 [!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]  
  
 Nie jest konieczne nazwanie elementów członkowskich danych *m_pic*; wystarczy dowolną nazwę.  
  
 Następnie Dodaj właściwości niestandardowej, która obsługuje typ obrazu:  
  
#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Aby dodać właściwość obrazu niestandardowego za pomocą Kreatora dodawania właściwości  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  Z menu skrótów wybierz **Dodaj** , a następnie **Dodaj właściwość**.  
  
5.  W **nazwa właściwości** wpisz nazwę właściwości. Na przykład w celach `ControlPicture` jest używany w tej procedurze.  
  
6.  W **typ właściwości** wybierz opcję **IPictureDisp\***  dla typu właściwości.  
  
7.  Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.  
  
8.  Wpisz unikatowe nazwy Get i ustawić funkcji lub zaakceptuj nazwę domyślną. (W tym przykładzie domyślne nazwy `GetControlPicture` i `SetControlPicture` są używane.)  
  
9. Kliknij przycisk **Zakończ**.  
  
 Kreator dodawania właściwości dodaje następujący kod między komentarze mapy wysyłania do formantu nagłówka (. H) plików:  
  
 [!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]  
  
 Ponadto następujący kod została umieszczona w implementacji formantu mapy wysyłania (. Pliku CPP):  
  
 [!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]  
  
 Kreator dodawania właściwości dodaje również następujące funkcje dwóch stub w pliku implementacji:  
  
 [!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]  
  
> [!NOTE]
>  Nazwy klas i funkcji kontroli mogą różnić się od powyższego przykładu.  
  
###  <a name="_core_modifications_to_your_control_project"></a> Zmiany do projektu kontroli  
 Po dokonaniu niezbędnych dodatki do projektu kontroli, należy zmodyfikować kilka funkcji, które mają wpływ na renderowanie formantu ActiveX. Te funkcje `OnResetState`, `OnDraw`, oraz funkcje Get i Set właściwości niestandardowych obrazów, znajdują się w pliku implementacji. (Należy pamiętać, że w tym przykładzie klasa kontroli jest nazywana `CSampleCtrl`, `CPictureHolder` nosi nazwę elementu członkowskiego danych *m_pic*, i nazwa właściwości niestandardowego obrazu jest `ControlPicture`.)  
  
 W formancie `OnResetState` działać, Dodaj następujący wiersz opcjonalne po wywołaniu `COleControl::OnResetState`:  
  
 [!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]  
  
 Obraz formantu to ustawienie puste obrazu.  
  
 Aby poprawnie narysować obraz, wywoływania [CPictureHolder::Render](../mfc/reference/cpictureholder-class.md#render) w formancie `OnDraw` funkcji. Modyfikowanie funkcji, aby przypominały w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]  
  
 W funkcji Get właściwości obrazu niestandardowego formantu Dodaj następujący wiersz:  
  
 [!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]  
  
 W funkcji ustawiania właściwości obrazu niestandardowego formantu Dodaj następujące wiersze:  
  
 [!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]  
  
 Właściwości obrazu muszą być wprowadzane trwałe, dzięki czemu informacje dodane w czasie projektowania będzie wyświetlana w czasie wykonywania. Dodaj następujący wiersz do `COleControl`— w klasie pochodnej `DoPropExchange` funkcji:  
  
 [!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]  
  
> [!NOTE]
>  Nazwy klas i funkcji mogą różnić się od powyższego przykładu.  
  
 Po zakończeniu zmiany należy ponownie skompiluj projekt włączać nowe funkcje niestandardowe właściwości obrazu i użyć kontenera testu, aby przetestować nową właściwość. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat sposobu dostępu kontener testu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: Używanie czcionek](../mfc/mfc-activex-controls-using-fonts.md)   
 [Kontrolki ActiveX MFC: strony właściwości](../mfc/mfc-activex-controls-property-pages.md)

