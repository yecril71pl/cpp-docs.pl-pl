---
title: 'Formanty MFC ActiveX: dodawanie właściwości standardowych'
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 16bdfddf0c028bc6a312767844b38c58c942d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364665"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Formanty MFC ActiveX: dodawanie właściwości standardowych

Właściwości magazynowe różnią się od właściwości niestandardowych tym, `COleControl`że są już zaimplementowane przez klasę . `COleControl`zawiera wstępnie zdefiniowane funkcje członkowskie, które obsługują typowe właściwości formantu. Niektóre typowe właściwości obejmują podpis formantu i kolory pierwszego planu i tła. Aby uzyskać informacje na temat innych właściwości zapasów, zobacz [Właściwości zapasów obsługiwane przez Kreatora dodawania właściwości](#_core_stock_properties_supported_by_classwizard) w dalszej części tego artykułu. Wpisy mapy wysyłki dla właściwości magazynowych są zawsze poprzedzone DISP_STOCKPROP.

W tym artykule opisano sposób dodawania właściwości magazynu (w tym przypadku caption) do formantu ActiveX za pomocą Kreatora dodawania właściwości i wyjaśniono wynikające z tego modyfikacje kodu. Tematy obejmują:

- [Dodawanie właściwości magazynu za pomocą Kreatora dodawania właściwości](#_core_using_classwizard_to_add_a_stock_property)

- [Dodawanie zmian Kreatora właściwości dla właściwości magazynowych](#_core_classwizard_changes_for_stock_properties)

- [Właściwości magazynowe obsługiwane przez Kreatora dodawania właściwości](#_core_stock_properties_supported_by_classwizard)

- [Właściwości magazynowe i powiadomienia](#_core_stock_properties_and_notification)

- [Właściwości kolorów](#_core_color_properties)

    > [!NOTE]
    >  Formanty niestandardowe języka Visual Basic zazwyczaj mają właściwości, takie jak Góra, Lewy, Szerokość, Wysokość, Wyrównaj, Tag, Nazwa, TabIndex, TabStop i Nadrzędny. Kontenery kontroli ActiveX są jednak odpowiedzialne za implementowanie tych właściwości formantu i dlatego formanty ActiveX nie powinny obsługiwać tych właściwości.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>Dodawanie właściwości magazynu za pomocą Kreatora dodawania właściwości

Dodawanie właściwości magazynu wymaga mniej kodu niż dodawanie właściwości niestandardowych, ponieważ `COleControl`obsługa właściwości jest obsługiwana automatycznie przez program . Poniższa procedura pokazuje dodanie akcji Caption właściwości do struktury kontroli ActiveX i może również służyć do dodawania innych właściwości magazynu. Zastąp nazwę wybranej właściwości magazynu caption.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Aby dodać właściwość Podpis zapasów za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

   Spowoduje to otwarcie [Kreatora dodawania właściwości](../ide/names-add-property-wizard.md).

1. W polu **Nazwa właściwości** kliknij pozycję **Podpis**.

1. Kliknij przycisk **Zakończ**.

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>Dodawanie zmian kreatora właściwości dla właściwości magazynowych

Ponieważ `COleControl` obsługuje właściwości zapasów, Kreator dodawania właściwości nie zmienia deklaracji klasy w żaden sposób; dodaje właściwość do mapy wysyłki. Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłki formantu, który znajduje się w implementacji (. CPP):

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

Następujący wiersz jest dodawany do opisu interfejsu formantu (. idl) plik:

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Ten wiersz przypisuje caption właściwości określonego identyfikatora. Należy zauważyć, że właściwość jest powiązana i zażąda uprawnień z bazy danych przed zmodyfikowaniem wartości.

Dzięki temu caption właściwość dostępna dla użytkowników formantu. Aby użyć wartości właściwości magazynu, należy uzyskać dostęp do `COleControl` zmiennej elementu członkowskiego lub funkcji elementu członkowskiego klasy podstawowej. Aby uzyskać więcej informacji na temat tych zmiennych członkowskich i funkcji członkowskich, zobacz następną sekcję Właściwości zapasów obsługiwane przez Kreatora dodawania właściwości.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>Właściwości zapasów obsługiwane przez Kreatora dodawania właściwości

Klasa `COleControl` zawiera dziewięć właściwości magazynowych. Właściwości można dodać za pomocą Kreatora dodawania właściwości.

|Właściwość|Wpis mapy wysyłki|Jak uzyskać dostęp do wartości|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|Wartość dostępna `m_sAppearance`jako .|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|Wartość dostępna `GetBackColor`za pomocą połączenia .|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|Wartość dostępna `m_sBorderStyle`jako .|
|`Caption`|DISP_STOCKPROP_CAPTION( )|Wartość dostępna `InternalGetText`za pomocą połączenia .|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|Wartość dostępna `m_bEnabled`jako .|
|`Font`|DISP_STOCKPROP_FONT( )|Zobacz artykuł [MFC ActiveX Formanty: Korzystanie z czcionek](../mfc/mfc-activex-controls-using-fonts.md) do użycia.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|Wartość dostępna `GetForeColor`za pomocą połączenia .|
|`hWnd`|DISP_STOCKPROP_HWND( )|Wartość dostępna `m_hWnd`jako .|
|`Text`|DISP_STOCKPROP_TEXT( )|Wartość dostępna `InternalGetText`za pomocą połączenia . Ta właściwość jest `Caption`taka sama jak , z wyjątkiem nazwy właściwości.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Wartość dostępna `m_lReadyState` jako lub`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>Właściwości magazynowe i powiadomienia

Większość właściwości zapasów mają funkcje powiadomień, które mogą być zastąpione. Na przykład po `BackColor` każdej zmianie właściwości `OnBackColorChanged` wywoływana jest funkcja (funkcja elementu członkowskiego klasy kontrolnej). Domyślna implementacja `COleControl`(w) wywołuje `InvalidateControl`. Zastąd w tej funkcji należy zastąpić, jeśli w odpowiedzi na tę sytuację należy podjąć dodatkowe działania.

## <a name="color-properties"></a><a name="_core_color_properties"></a>Właściwości koloru

Podczas malowania `ForeColor` formantu można używać zapasów i `BackColor` właściwości lub własnych niestandardowych właściwości kolorów. Aby użyć właściwości color, należy wywołać [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) funkcji elementu członkowskiego. Parametry tej funkcji są wartością właściwości color i opcjonalnym uchwytem palety. Zwracana wartość jest wartością **COLORREF,** która może być `SetTextColor` przekazywana do funkcji GDI, takich jak i `CreateSolidBrush`.

Wartości kolorów dla `ForeColor` zapasów i `BackColor` właściwości są dostępne `GetForeColor` przez `GetBackColor` wywołanie albo funkcji, odpowiednio.

Poniższy przykład pokazuje przy użyciu tych dwóch właściwości koloru podczas malowania formantu. Inicjuje tymczasową zmienną `CBrush` **COLORREF** i `TranslateColor`obiekt z `ForeColor` wywołaniami: `BackColor` jeden przy użyciu właściwości, a drugi przy użyciu właściwości. Obiekt `CBrush` tymczasowy jest następnie używany do malowania prostokąta formantu, a `ForeColor` kolor tekstu jest ustawiany przy użyciu właściwości.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
