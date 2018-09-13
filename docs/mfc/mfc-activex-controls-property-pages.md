---
title: 'Kontrolki ActiveX MFC: Strony właściwości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4d61c1b0d7fb7174bdf7df0c811b0159ece02d
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535240"
---
# <a name="mfc-activex-controls-property-pages"></a>Kontrolki ActiveX MFC: strony właściwości
Strony właściwości umożliwiają użytkownik formantu ActiveX do wyświetlania i zmieniania właściwości formantu ActiveX. Te właściwości są dostępne za pomocą kontrolki okno dialogowe właściwości, która zawiera jedną lub więcej stron właściwości, które zapewniają dostosowany interfejs graficzny służący do wyświetlania i edytowania właściwości formantu.  

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).
  
 Strony właściwości kontrolki ActiveX są wyświetlane na dwa sposoby:  
  
-   Gdy zlecenie właściwości kontrolki (**OLEIVERB_PROPERTIES**) jest wywołana, otwierania kontrolki właściwości modalne okno dialogowe zawiera strony właściwości formantu.  
  
-   Kontener można wyświetlać swój własny niemodalnego okna dialogowego, który pokazuje strony właściwości wybranej kontrolki.  
  
 Okno dialogowe właściwości (zilustrowane na poniższym rysunku) składa się z obszaru wyświetlania bieżącej strony właściwości karty do przełączania między stronami właściwości i zbiór przyciski umożliwiające wykonywanie typowych zadań, takich jak zamyka okno dialogowe strony właściwości anulowanie wszelkich zmian wprowadzonych, lub od razu stosowania zmian do formantu ActiveX.  
  
 ![Okno dialogowe właściwości Circ3](../mfc/media/vc373i1.gif "vc373i1")  
Okno dialogowe właściwości  
  
 W tym artykule opisano tematów związanych z używanie stron właściwości formantu ActiveX. Należą do nich następujące elementy:  
  
-   [Implementowanie domyślną stronę właściwości dla formantu ActiveX](#_core_implementing_the_default_property_page)  
  
-   [Dodawanie kontrolek do strony właściwości](#_core_adding_controls_to_a_property_page)  
  
-   [Dostosowywanie funkcji DoDataExchange](#_core_customizing_the_dodataexchange_function)  
  
 Aby uzyskać więcej informacji na temat używania stron właściwości w kontrolce ActiveX zobacz następujące artykuły:  
  
-   [Kontrolki ActiveX MFC: dodawanie dodatkowej niestandardowej strony właściwości](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 Aby uzyskać informacje na używanie arkuszy właściwości w aplikacji innych niż kontrolki ActiveX MFC, zobacz [arkusze właściwości](../mfc/property-sheets-mfc.md).  
  
##  <a name="_core_implementing_the_default_property_page"></a> Implementowanie domyślna strona właściwości  
 Jeśli używasz kreatora kontrolek ActiveX do utworzenia projektu kontrolki, Kreator kontrolek ActiveX przewiduje domyślnej klasy strony właściwości formant pochodzące z [klasa COlePropertyPage](../mfc/reference/colepropertypage-class.md). Początkowo tej strony właściwości jest pusta, ale można dodać żadnych kontrolka okna dialogowego lub zestaw formantów do niego. Ponieważ Kreator kontrolek ActiveX powoduje utworzenie tylko jednej właściwości klasy strony domyślnie klasy strony właściwości dodatkowych (również pochodzącego z `COlePropertyPage`) musi zostać utworzona za pomocą widoku klas. Aby uzyskać więcej informacji na temat tej procedury, zobacz [kontrolki ActiveX MFC: Dodawanie strony właściwości niestandardowego innego](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).  
  
 Implementowanie właściwości strony (w tym przypadku wartość domyślna) to proces trzech kroków:  
  
#### <a name="to-implement-a-property-page"></a>Aby zaimplementować strony właściwości  
  
1.  Dodaj `COlePropertyPage`-klasy pochodnej projektu kontroli. Jeśli projekt został utworzony przy użyciu Kreatora kontrolek ActiveX (tak jak w tym przypadku), klasy strony właściwości domyślnej jest już istnieje.  
  
2.  Użyj edytora okien dialogowych, aby dodać formanty do szablonu strony właściwości.  
  
3.  Dostosowywanie `DoDataExchange` funkcji `COlePropertyPage`-klasy do wymiany wartości z zakresu od właściwości kontrolki strony i kontrolki ActiveX.  
  
 Na przykład celów, w poniższych procedurach Użyj prostego formantu (o nazwie "Przykładowy"). Przykład został utworzony przy użyciu Kreatora kontrolek ActiveX i zawiera tylko podstawowe właściwości podpisu.  
  
##  <a name="_core_adding_controls_to_a_property_page"></a> Dodawanie kontrolek do strony właściwości  
  
#### <a name="to-add-controls-to-a-property-page"></a>Aby dodać formanty do strony właściwości  
  
1.  Za pomocą formantu projektu open Otwórz widok zasobów.  
  
2.  Kliknij dwukrotnie **okna dialogowego** ikonę katalogu.  
  
3.  Otwórz okno dialogowe IDD_PROPPAGE_SAMPLE.  
  
     Kreator kontrolek ActiveX dołącza nazwę projektu do końca identyfikator okna dialogowego, w tym przypadku próbki.  
  
4.  Przeciągnij i upuść wybranej kontrolki z przybornika do obszaru okno dialogowe.  
  
5.  Na przykład kontrolka etykiety tekst "podpis:" i formant pola edycji o identyfikatorze odpowiadającym IDC_CAPTION są wystarczające.  
  
6.  Kliknij przycisk **Zapisz** na pasku narzędzi, aby zapisać zmiany.  
  
 Teraz, gdy interfejs użytkownika został zmodyfikowany, musisz utworzyć link pole edycji za pomocą właściwości podpisu. Odbywa się w poniższej sekcji, edytując `CSamplePropPage::DoDataExchange` funkcji.  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a> Dostosowywanie funkcji DoDataExchange  
 Strony właściwości [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) funkcja pozwala połączyć wartości strony właściwości przy użyciu rzeczywistych wartości właściwości w formancie. Aby ustanowić łącza, musisz zamapować pola strony odpowiedniej właściwości do ich właściwości odpowiedni formant.  
  
 Te mapowania są implementowane za pomocą strony właściwości **ddp_ —** funkcji. **Ddp_ —** funkcje działają podobnie jak **funkcje DDX_** funkcji używanych w standardowych oknach dialogowych MFC, z jednym wyjątkiem. Oprócz odwołanie do zmiennej składowej **ddp_ —** funkcje przyjmuje nazwę właściwości kontrolki. Poniżej przedstawiono typowe wpisu w `DoDataExchange` funkcji na stronie właściwości.  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 Ta funkcja kojarzy na stronie właściwości *m_caption* zmiennej członkowskiej z podpisem, przy użyciu `DDP_TEXT` funkcji.  
  
 Po utworzeniu strony właściwości kontrolki wstawione, należy ustanowić łącze między właściwości rzeczywistego formantu, formant strony właściwości, IDC_CAPTION oraz podpisu, używając `DDP_Text` działać zgodnie z powyższym opisem.  
  
 [Strony właściwości](../mfc/reference/property-pages-mfc.md) są dostępne dla innych typów kontrolki okna dialogowego, takie jak pola wyboru i przyciski radiowe i pola listy. W poniższej tabeli przedstawiono cały zestaw właściwości strony **ddp_ —** funkcji i ich celów:  
  
### <a name="property-page-functions"></a>Funkcje strony właściwości  
  
|Nazwa funkcji|Ta funkcja służy do link|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|Indeks zaznaczonego ciągu w polu kombi z właściwością kontrolki.|  
|`DDP_CBString`|Zaznaczony ciąg w polu kombi z właściwością kontrolki. Zaznaczony ciąg może rozpoczynać się od tych samych liter jako wartość właściwości, ale nie musi być zgodna go całkowicie.|  
|`DDP_CBStringExact`|Zaznaczony ciąg w polu kombi z właściwością kontrolki. Zaznaczony ciąg i wartość ciągu dla właściwości muszą być zgodne.|  
|`DDP_Check`|Pole wyboru z właściwością kontrolki.|  
|`DDP_LBIndex`|Indeks zaznaczonego ciągu w polu listy, z właściwością kontrolki.|  
|`DDP_LBString`|Zaznaczony ciąg w polu listy, z właściwością kontrolki. Zaznaczony ciąg może rozpoczynać się od tych samych liter jako wartość właściwości, ale nie musi być zgodna go całkowicie.|  
|`DDP_LBStringExact`|Zaznaczony ciąg w polu listy, z właściwością kontrolki. Zaznaczony ciąg i wartość ciągu dla właściwości muszą być zgodne.|  
|`DDP_Radio`|Przycisk radiowy z właściwością kontrolki.|  
|`DDP_Text`|Tekst z właściwością kontrolki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Klasa COlePropertyPage](../mfc/reference/colepropertypage-class.md)
