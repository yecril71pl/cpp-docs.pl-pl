---
title: 'Formanty MFC ActiveX: strony właściwości'
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: 3d22085daa503a7c778111718445920f98b98a89
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615443"
---
# <a name="mfc-activex-controls-property-pages"></a>Formanty MFC ActiveX: strony właściwości

Strony właściwości umożliwiają użytkownikowi kontrolki ActiveX wyświetlanie i zmienianie właściwości kontrolki ActiveX. Te właściwości są dostępne przez wywołanie okna dialogowego właściwości kontrolki, które zawiera co najmniej jedną stronę właściwości, która zapewnia dostosowany interfejs graficzny do wyświetlania i edytowania właściwości kontrolki.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

Strony właściwości kontrolki ActiveX są wyświetlane na dwa sposoby:

- Gdy zostanie wywołane zlecenie właściwości kontrolki (**OLEIVERB_PROPERTIES**), formant otwiera okno dialogowe właściwości modalnej zawierające strony właściwości kontrolki.

- Kontener może wyświetlać własne niemodalne okno dialogowe, które wyświetla strony właściwości wybranej kontrolki.

Okno dialogowe właściwości (pokazane na poniższym rysunku) składa się z obszaru do wyświetlania bieżącej strony właściwości, kart do przełączania między stronami właściwości i kolekcji przycisków wykonujących typowe zadania, takie jak zamknięcie okna dialogowego strony właściwości, Anulowanie wszelkich wprowadzonych zmian lub natychmiastowe zastosowanie wszelkich zmian do kontrolki ActiveX.

![Okno dialogowe właściwości dla Circ3](../mfc/media/vc373i1.gif "Okno dialogowe właściwości dla Circ3") <br/>
Okno dialogowe właściwości

W tym artykule opisano tematy związane z korzystaniem ze stron właściwości w kontrolce ActiveX. Należą do nich następujące elementy:

- [Implementowanie domyślnej strony właściwości kontrolki ActiveX](#_core_implementing_the_default_property_page)

- [Dodawanie kontrolek do strony właściwości](#_core_adding_controls_to_a_property_page)

- [Dostosowywanie funkcji DoDataExchange](#_core_customizing_the_dodataexchange_function)

Aby uzyskać więcej informacji na temat używania stron właściwości w kontrolce ActiveX, zobacz następujące artykuły:

- [Formanty MFC ActiveX: dodawanie dodatkowej niestandardowej strony właściwości](mfc-activex-controls-adding-another-custom-property-page.md)

- [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](mfc-activex-controls-using-stock-property-pages.md)

Aby uzyskać informacje na temat używania arkuszy właściwości w aplikacji MFC innej niż Kontrolka ActiveX, zobacz [arkusze właściwości](property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Implementowanie domyślnej strony właściwości

Jeśli do utworzenia projektu kontrolki używasz Kreatora kontrolek ActiveX, Kreator kontrolek ActiveX udostępnia domyślną klasę strony właściwości dla formantu pochodnego od [klasy COlePropertyPage](reference/colepropertypage-class.md). Początkowo ta strona właściwości jest pusta, ale można dodać do niej dowolną kontrolkę okna dialogowego lub zestaw kontrolek. Ponieważ Kreator kontrolek ActiveX tworzy tylko jedną klasę strony właściwości, należy utworzyć dodatkowe klasy stron właściwości (pochodzące również z `COlePropertyPage` ) przy użyciu widok klasy. Aby uzyskać więcej informacji na temat tej procedury, zobacz [kontrolki ActiveX MFC: Dodawanie innej niestandardowej strony właściwości](mfc-activex-controls-adding-another-custom-property-page.md).

Zaimplementowanie strony właściwości (w tym przypadku domyślnie) jest procesem trójwymiarowym:

#### <a name="to-implement-a-property-page"></a>Aby zaimplementować stronę właściwości

1. Dodaj `COlePropertyPage` klasę pochodną do projektu kontrolki. Jeśli projekt został utworzony przy użyciu kreatora kontrolki ActiveX (jak w tym przypadku), domyślna klasa strony właściwości już istnieje.

1. Użyj edytora okien dialogowych, aby dodać kontrolki do szablonu strony właściwości.

1. Dostosuj `DoDataExchange` funkcję `COlePropertyPage` klasy pochodnej do wartości wymiany między kontrolką strony właściwości a kontrolką ActiveX.

Na przykład w poniższych procedurach użyto prostej kontrolki (o nazwie "sample"). Przykład został utworzony za pomocą Kreatora kontrolki ActiveX i zawiera tylko Właściwość Caption.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Dodawanie kontrolek do strony właściwości

#### <a name="to-add-controls-to-a-property-page"></a>Aby dodać kontrolki do strony właściwości

1. Po otwarciu projektu kontrolki Otwórz Widok zasobów.

1. Kliknij dwukrotnie ikonę katalogu **okna dialogowego** .

1. Otwórz okno dialogowe IDD_PROPPAGE_SAMPLE.

   Kreator kontrolek ActiveX dołącza nazwę projektu na końcu identyfikatora okna dialogowego, w tym przypadku przykład.

1. Przeciągnij i upuść wybrany formant z przybornika w obszarze okna dialogowego.

1. W tym przykładzie wystarcza kontrolka etykieta tekstowa "Caption:" i kontrolka pola edycji z identyfikatorem IDC_CAPTION.

1. Kliknij przycisk **Zapisz** na pasku narzędzi, aby zapisać zmiany.

Teraz, gdy interfejs użytkownika został zmodyfikowany, należy połączyć pole edycji z właściwością Caption. W tym celu należy wykonać czynności opisane w poniższej sekcji, edytując `CSamplePropPage::DoDataExchange` funkcję.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Dostosowywanie funkcji DoDataExchange

Strona właściwości [CWnd::D odataexchange](reference/cwnd-class.md#dodataexchange) funkcja umożliwia łączenie wartości strony właściwości z rzeczywistymi wartościami właściwości w formancie. Aby ustanowić linki, należy zamapować odpowiednie pola strony właściwości na odpowiednie właściwości kontrolki.

Te mapowania są implementowane przy użyciu strony właściwości **DDP_** funkcje. **DDP_** funkcje działają podobnie jak funkcje **DDX_** używane w standardowych oknach dialogowych MFC z jednym wyjątkiem. Oprócz odwołania do zmiennej składowej, **DDP_** funkcje przyjmuje nazwę właściwości kontrolki. Poniżej znajduje się typowy wpis w `DoDataExchange` funkcji dla strony właściwości.

[!code-cpp[NVC_MFC_AxUI#31](codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Ta funkcja kojarzy zmienną członkowską *m_caption* strony właściwości z podpisem przy użyciu `DDP_TEXT` funkcji.

Po wstawieniu kontrolki Strona właściwości należy nawiązać połączenie między kontrolką strony właściwości, IDC_CAPTION i rzeczywistą właściwością kontrolki, przy użyciu `DDP_Text` funkcji opisanej powyżej.

[Strony właściwości](reference/property-pages-mfc.md) są dostępne dla innych typów formantów okna dialogowego, takich jak pola wyboru, przyciski radiowe i pola listy. W poniższej tabeli przedstawiono cały zestaw funkcji **DDP_** strony i ich cele:

### <a name="property-page-functions"></a>Funkcje strony właściwości

|Nazwa funkcji|Użyj tej funkcji do łączenia|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Indeks wybranego ciągu w polu kombi z właściwością kontrolki.|
|`DDP_CBString`|Wybrany ciąg w polu kombi z właściwością kontrolki. Wybrany ciąg może rozpoczynać się od tych samych liter co wartość właściwości, ale nie musi być w pełni dopasowany.|
|`DDP_CBStringExact`|Wybrany ciąg w polu kombi z właściwością kontrolki. Wybrany ciąg i wartość ciągu właściwości muszą być dokładnie zgodne.|
|`DDP_Check`|Pole wyboru z właściwością kontrolki.|
|`DDP_LBIndex`|Indeks wybranego ciągu w polu listy z właściwością kontrolki.|
|`DDP_LBString`|Wybrany ciąg w polu listy z właściwością kontrolki. Wybrany ciąg może rozpoczynać się od tych samych liter co wartość właściwości, ale nie musi być w pełni dopasowany.|
|`DDP_LBStringExact`|Wybrany ciąg w polu listy z właściwością kontrolki. Wybrany ciąg i wartość ciągu właściwości muszą być dokładnie zgodne.|
|`DDP_Radio`|Przycisk radiowy z właściwością kontrolki.|
|`DDP_Text`|Tekst z właściwością kontrolki.|

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Klasa COlePropertyPage](reference/colepropertypage-class.md)
