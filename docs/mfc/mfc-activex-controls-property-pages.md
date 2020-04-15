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
ms.openlocfilehash: c31d13e03483f8632f17a526da75ebe8e21bccbf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364567"
---
# <a name="mfc-activex-controls-property-pages"></a>Formanty MFC ActiveX: strony właściwości

Strony właściwości umożliwiają użytkownikowi sterującemu ActiveX wyświetlanie i zmienianie właściwości formantu ActiveX. Dostęp do tych właściwości jest dostępny przez wywołanie okna dialogowego właściwości formantu, które zawiera jedną lub więcej stron właściwości, które zapewniają dostosowany, graficzny interfejs do wyświetlania i edytowania właściwości formantu.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Strony właściwości formantu ActiveX są wyświetlane na dwa sposoby:

- Po wywołaniu zlecenia właściwości formantu (**OLEIVERB_PROPERTIES)** formant otwiera okno dialogowe właściwości modalne, które zawiera strony właściwości formantu.

- Kontener może wyświetlać własne niemodless okno dialogowe, które pokazuje strony właściwości wybranego formantu.

Okno dialogowe właściwości (zilustrowane na poniższym rysunku) składa się z obszaru do wyświetlania bieżącej strony właściwości, kart do przełączania między stronami właściwości oraz kolekcji przycisków wykonujących typowe zadania, takie jak zamykanie okna dialogowego strony właściwości, anulowanie wszelkich wprowadzonych zmian lub natychmiastowe zastosowanie wszelkich zmian do formantu ActiveX.

![Okno dialogowe Właściwości dla programu Circ3](../mfc/media/vc373i1.gif "Okno dialogowe Właściwości dla programu Circ3") <br/>
Okno dialogowe Właściwości

W tym artykule omówiono tematy związane z używaniem stron właściwości w formancie ActiveX. Należą do nich:

- [Implementowanie domyślnej strony właściwości formantu ActiveX](#_core_implementing_the_default_property_page)

- [Dodawanie formantów do strony właściwości](#_core_adding_controls_to_a_property_page)

- [Dostosowywanie funkcji DoDataExchange](#_core_customizing_the_dodataexchange_function)

Aby uzyskać więcej informacji na temat używania stron właściwości w formancie ActiveX, zobacz następujące artykuły:

- [Formanty MFC ActiveX: dodawanie dodatkowej niestandardowej strony właściwości](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)

Aby uzyskać informacje na temat używania arkuszy właściwości w aplikacji MFC innej niż formant ActiveX, zobacz [Arkusze właściwości](../mfc/property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Implementowanie strony właściwości domyślnej

Jeśli do utworzenia projektu sterującego używasz Kreatora sterowania ActiveX, Kreator kontroli ActiveX udostępnia domyślną klasę strony właściwości dla formantu uzyskanego z [klasy COlePropertyPage](../mfc/reference/colepropertypage-class.md). Początkowo ta strona właściwości jest pusta, ale można dodać dowolne kontrolki okna dialogowego lub zestaw formantów do niego. Ponieważ Kreator kontroli ActiveX tworzy domyślnie tylko jedną klasę strony właściwości, `COlePropertyPage`dodatkowe klasy stron właściwości (również pochodzące z ) muszą być tworzone przy użyciu widoku klasy. Aby uzyskać więcej informacji na temat tej procedury, zobacz [Kontrolki MFC ActiveX: Dodawanie innej strony właściwości niestandardowej](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).

Implementowanie strony właściwości (w tym przypadku domyślnie) jest procesem trzyetapowym:

#### <a name="to-implement-a-property-page"></a>Aby zaimplementować stronę właściwości

1. Dodaj `COlePropertyPage`klasę pochodną do projektu sterującego. Jeśli projekt został utworzony za pomocą Kreatora kontroli ActiveX (jak w tym przypadku), domyślna klasa strony właściwości już istnieje.

1. Użyj edytora dialogów, aby dodać wszystkie formanty do szablonu strony właściwości.

1. Dostosuj `DoDataExchange` funkcję klasy `COlePropertyPage`pochodnej, aby wymienić wartości między formantem strony właściwości a formancie ActiveX.

Na przykład następujące procedury używają prostego formantu (o nazwie "Przykład"). Przykład został utworzony przy użyciu Kreatora kontroli ActiveX i zawiera tylko właściwość caption.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Dodawanie kontrolek do strony właściwości

#### <a name="to-add-controls-to-a-property-page"></a>Aby dodać formanty do strony właściwości

1. Po otwarciu projektu sterującego otwórz widok zasobów.

1. Kliknij dwukrotnie ikonę katalogu **dialogowego.**

1. Otwórz okno dialogowe IDD_PROPPAGE_SAMPLE.

   Kreator kontroli ActiveX dołącza nazwę projektu na końcu identyfikatora okna dialogowego, w tym przypadku Sample.

1. Przeciągnij i upuść zaznaczony formant z przybornika na obszar okna dialogowego.

1. W tym przykładzie wystarczy formant etykiety tekstowej "Podpis :" i kontrolka pola edycji z identyfikatorem IDC_CAPTION.

1. Kliknij **pozycję Zapisz** na pasku narzędzi, aby zapisać zmiany.

Teraz, gdy interfejs użytkownika został zmodyfikowany, musisz połączyć pole edycji z caption właściwości. Odbywa się to w poniższej `CSamplePropPage::DoDataExchange` sekcji, edytując funkcję.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Dostosowywanie funkcji DoDataExchange

Strona właściwości [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) funkcja umożliwia łączenie wartości strony właściwości z rzeczywistymi wartościami właściwości w formancie. Aby ustanowić łącza, należy zamapować odpowiednie pola strony właściwości do ich odpowiednich właściwości formantu.

Te mapowania są implementowane przy użyciu strony właściwości **DDP_** funkcji. Funkcje **DDP_** działają jak **funkcje DDX_** używane w standardowych oknach dialogowych MFC, z jednym wyjątkiem. Oprócz odwołania do zmiennej elementu członkowskiego **funkcje DDP_** przyjmują nazwę właściwości control. Poniżej przedstawiono typowy `DoDataExchange` wpis w funkcji dla strony właściwości.

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Ta funkcja kojarzy zmienną *m_caption* elementu członkowskiego strony właściwości z `DDP_TEXT` caption, za pomocą funkcji.

Po wstawieniu formantu strony właściwości należy ustanowić łącze między formantem strony właściwości, IDC_CAPTION `DDP_Text` i właściwość rzeczywistego formantu Caption, przy użyciu funkcji opisanej powyżej.

[Strony właściwości](../mfc/reference/property-pages-mfc.md) są dostępne dla innych typów formantów dialogowych, takich jak pola wyboru, przyciski radiowe i pola listy. W poniższej tabeli wymieniono cały zestaw funkcji **DDP_** funkcji i ich celów:

### <a name="property-page-functions"></a>Funkcje strony właściwości

|Nazwa funkcji|Użyj tej funkcji, aby połączyć|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Indeks wybranego ciągu w polu kombi z właściwością formantu.|
|`DDP_CBString`|Wybrany ciąg w polu kombi z właściwością formantu. Wybrany ciąg może zaczynać się od tych samych liter co wartość właściwości, ale nie musi być w pełni dopasowany.|
|`DDP_CBStringExact`|Wybrany ciąg w polu kombi z właściwością formantu. Wybrany ciąg i wartość ciągu właściwości musi być dokładnie zgodna.|
|`DDP_Check`|Pole wyboru z właściwością formantu.|
|`DDP_LBIndex`|Indeks wybranego ciągu w polu listy z właściwością formantu.|
|`DDP_LBString`|Wybrany ciąg w polu listy z właściwością formantu. Wybrany ciąg może zaczynać się od tych samych liter co wartość właściwości, ale nie musi być w pełni dopasowany.|
|`DDP_LBStringExact`|Wybrany ciąg w polu listy z właściwością formantu. Wybrany ciąg i wartość ciągu właściwości musi być dokładnie zgodna.|
|`DDP_Radio`|Przycisk radiowy z właściwością formantu.|
|`DDP_Text`|Tekst z właściwością formantu.|

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Klasa COlePropertyPage](../mfc/reference/colepropertypage-class.md)
