---
title: 'Formanty MFC ActiveX: Strony właściwości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 81d28a7c5fdb48201cc1f4f2998fd0904749445d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-property-pages"></a>Kontrolki ActiveX MFC: strony właściwości
Strony właściwości umożliwiają użytkownikowi formantu ActiveX wyświetlanie i zmiana właściwości formantu ActiveX. Te właściwości są dostępne przez okno dialogowe właściwości formantu, który zawiera jeden lub więcej stron właściwości, które zapewniają dostosowany interfejs graficzny służący do wyświetlania i edytowania właściwości formantu.  
  
 Strony właściwości formantu ActiveX są wyświetlane na dwa sposoby:  
  
-   Gdy zlecenie właściwości formantu (**OLEIVERB_PROPERTIES**) jest wywołane, formantu Otwiera właściwości modalne okno dialogowe zawiera strony właściwości formantu.  
  
-   Kontener można wyświetlić własny niemodalne okno dialogowe, pokazujący strony właściwości zaznaczonego formantu.  
  
 Okno dialogowe właściwości (przedstawiono na poniższej ilustracji) składa się z obszaru wyświetlania bieżącej strony właściwości karty do przełączania między strony właściwości, a kolekcja przyciski umożliwiające wykonywanie typowych zadań, takich jak zamknięciu okna dialogowego strony właściwości Anuluje zmiany wprowadzone lub od razu stosowania zmian do formantu ActiveX.  
  
 ![Okno dialogowe właściwości dla Circ3](../mfc/media/vc373i1.gif "vc373i1")  
Okno dialogowe właściwości  
  
 W tym artykule omówiono tematów związanych z używanie stron właściwości formantu ActiveX. Należą do nich następujące elementy:  
  
-   [Implementowanie domyślną stronę właściwości dla formantu ActiveX](#_core_implementing_the_default_property_page)  
  
-   [Dodawanie formantów do strony właściwości](#_core_adding_controls_to_a_property_page)  
  
-   [Dostosowywanie funkcji DoDataExchange](#_core_customizing_the_dodataexchange_function)  
  
 Aby uzyskać więcej informacji na używanie stron właściwości formantu ActiveX zobacz następujące artykuły:  
  
-   [Kontrolki ActiveX MFC: dodawanie dodatkowej niestandardowej strony właściwości](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 Informacje na używanie arkuszy właściwości w aplikacji MFC niż formantu ActiveX, zobacz [arkusze właściwości](../mfc/property-sheets-mfc.md).  
  
##  <a name="_core_implementing_the_default_property_page"></a> Implementowanie domyślnej strony właściwości  
 Użycie Kreator kontrolek ActiveX do tworzenia projektu kontroli, Kreator kontrolek ActiveX udostępnia klasy strony właściwości domyślnej dla formantu pochodzące z [COlePropertyPage klasy](../mfc/reference/colepropertypage-class.md). Początkowo tej strony właściwości jest pusta, ale można dodać do niego żadnych kontrolka okna dialogowego lub zbiór kontrolek. Ponieważ Kreator kontrolek ActiveX tworzy tylko jedną właściwość klasy strony domyślnie klasy strony właściwości dodatkowe (również pochodną `COlePropertyPage`) musi być utworzony przy użyciu widoku klasy. Aby uzyskać więcej informacji dotyczących tej procedury, zobacz [kontrolki ActiveX MFC: Dodawanie strony właściwości niestandardowego innego](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).  
  
 Implementowanie właściwości strony (w tym przypadku wartość domyślna) jest procesem trzech etapów:  
  
#### <a name="to-implement-a-property-page"></a>Aby zaimplementować strony właściwości  
  
1.  Dodaj `COlePropertyPage`-pochodnej klasy projektu kontroli. Jeżeli projekt został utworzony za pomocą Kreatora formantu ActiveX (w tym przypadku), domyślną klasę strony właściwości już istnieje.  
  
2.  Użyj edytora okien dialogowych, aby dodać wszystkie formanty do szablonu strony właściwości.  
  
3.  Dostosowywanie `DoDataExchange` funkcji `COlePropertyPage`-klasy do wymiany wartości między właściwości kontrolki strony i kontrolki ActiveX.  
  
 Na przykład celów, w poniższych procedurach Użyj prostego formantu (o nazwie "Test"). Przykład został utworzony przy użyciu Kreatora formantów ActiveX i zawiera tylko podstawowe właściwości podpisu.  
  
##  <a name="_core_adding_controls_to_a_property_page"></a> Dodawanie formantów do strony właściwości  
  
#### <a name="to-add-controls-to-a-property-page"></a>Aby dodać kontrolki do strony właściwości  
  
1.  Otwórz projekt kontroli Otwórz widok zasobów.  
  
2.  Kliknij dwukrotnie **okna dialogowego** ikona katalogu.  
  
3.  Otwórz **IDD_PROPPAGE_SAMPLE** okno dialogowe.  
  
     Kreator kontrolek ActiveX dołącza nazwę projektu w celu identyfikator okna dialogowego, w tym przypadku próbki.  
  
4.  Przeciągnij i upuść wybrany formant z przybornika do obszaru okno dialogowe.  
  
5.  Na przykład tekst etykiety formantu "podpis:" i okno edycji z **IDC_CAPTION** identyfikator są wystarczające.  
  
6.  Kliknij przycisk **zapisać** na pasku narzędzi, aby zapisać zmiany.  
  
 Teraz, interfejs użytkownika został zmodyfikowany, należy połączyć w tym polu edycji właściwości podpisu. Odbywa się w poniższej sekcji, edytując `CSamplePropPage::DoDataExchange` funkcji.  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a> Dostosowywanie funkcji DoDataExchange  
 Strony właściwości [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) funkcja umożliwia link wartości właściwości strony rzeczywiste wartości właściwości w formancie. Do ustanawiania łącza, zamapuj pola strony właściwości odpowiednie do ich właściwości kontroli.  
  
 Te mapowania są implementowane przy użyciu strony właściwości **ddp_ —** funkcji. **Ddp_ —** funkcje działają podobnie **DDX_** funkcji używanych w standardowych oknach dialogowych MFC, z jednym wyjątkiem. Oprócz odwołanie do zmiennej członkowskiej **ddp_ —** funkcje pobierać nazwa właściwości formantu. Poniżej przedstawiono typowe wpisu w `DoDataExchange` funkcji dla strony właściwości.  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 Ta funkcja umożliwia skojarzenie stronę właściwości `m_caption` zmiennej członkowskiej, z tekstem, przy użyciu `DDP_TEXT` funkcji.  
  
 Po dodaje formantu strony właściwości, należy ustanowić powiązanie właściwości kontrolki strony `IDC_CAPTION`, i przy użyciu właściwości rzeczywistą kontrolę podpis, **ddp_text —** działać zgodnie z powyższym opisem.  
  
 [Strony właściwości](../mfc/reference/property-pages-mfc.md) są dostępne dla innych typów formantu okna dialogowego, takich jak pola wyboru, przyciski radiowe i pola listy. Poniższa tabela zawiera listę całego zestawu strony właściwości **ddp_ —** funkcji i ich celów:  
  
### <a name="property-page-functions"></a>Funkcje strony właściwości  
  
|Nazwa funkcji|Ta funkcja służy do link|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|Indeks zaznaczony ciąg w polu kombi z właściwością formantu.|  
|`DDP_CBString`|Zaznaczony ciąg w polu kombi z właściwością formantu. Zaznaczony ciąg może rozpoczynać się od tych samych liter jako wartość właściwości, ale nie musi być zgodne go całkowicie.|  
|`DDP_CBStringExact`|Zaznaczony ciąg w polu kombi z właściwością formantu. Zaznaczony ciąg i wartość ciągu właściwości muszą być całkowicie zgodne.|  
|`DDP_Check`|Pole wyboru z właściwością formantu.|  
|`DDP_LBIndex`|Indeks zaznaczony ciąg w polu listy z właściwością formantu.|  
|`DDP_LBString`|Zaznaczony ciąg w polu listy z właściwością formantu. Zaznaczony ciąg może rozpoczynać się od tych samych liter jako wartość właściwości, ale nie musi być zgodne go całkowicie.|  
|`DDP_LBStringExact`|Zaznaczony ciąg w polu listy z właściwością formantu. Zaznaczony ciąg i wartość ciągu właściwości muszą być całkowicie zgodne.|  
|`DDP_Radio`|Przycisk radiowy z właściwością formantu.|  
|**Ddp_text —**|Tekst z właściwością formantu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Klasa COlePropertyPage](../mfc/reference/colepropertypage-class.md)
