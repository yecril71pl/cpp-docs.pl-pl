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
ms.openlocfilehash: 13e8af5ddb3dd5130c864e42383e3bb9ff23b87b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625425"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Formanty MFC ActiveX: dodawanie właściwości standardowych

Właściwości giełdowe różnią się od właściwości niestandardowych w tym, że są już zaimplementowane przez klasę `COleControl` . `COleControl`zawiera wstępnie zdefiniowane funkcje członkowskie, które obsługują wspólne właściwości formantu. Niektóre typowe właściwości obejmują podpis kontrolki i kolor pierwszego planu i tła. Aby uzyskać informacje dotyczące innych właściwości podstawowych, zobacz temat [właściwości podstawowe obsługiwane przez Kreatora dodawania właściwości](#_core_stock_properties_supported_by_classwizard) w dalszej części tego artykułu. Wpisy mapy wysyłania dla właściwości podstawowych są zawsze poprzedzone DISP_STOCKPROP.

W tym artykule opisano, jak dodać właściwość giełdową (w tym przypadku podpis) do kontrolki ActiveX przy użyciu Kreatora dodawania właściwości i objaśniające modyfikacje kodu. Tematy obejmują:

- [Za pomocą Kreatora dodawania właściwości, aby dodać właściwość giełdową](#_core_using_classwizard_to_add_a_stock_property)

- [Dodawanie zmian w Kreatorze właściwości dla właściwości podstawowych](#_core_classwizard_changes_for_stock_properties)

- [Właściwości podstawowe obsługiwane przez Kreatora dodawania właściwości](#_core_stock_properties_supported_by_classwizard)

- [Właściwości i powiadomienia dotyczące akcji](#_core_stock_properties_and_notification)

- [Właściwości koloru](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic kontrolki niestandardowe mają zazwyczaj właściwości takie jak Top, Left, Width, Height, align, tag, Name, TabIndex, TabStop i Parent. Kontenery kontrolek ActiveX są jednak odpowiedzialne za implementację tych właściwości kontroli, dlatego kontrolki ActiveX nie powinny obsługiwać tych właściwości.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>Za pomocą Kreatora dodawania właściwości, aby dodać właściwość giełdową

Dodawanie właściwości podstawowych wymaga mniejszej ilości kodu niż Dodawanie właściwości niestandardowych, ponieważ obsługa właściwości jest obsługiwana automatycznie przez `COleControl` . Poniższa procedura pokazuje dodanie właściwości spisu do struktury formantów ActiveX i może również służyć do dodawania innych właściwości podstawowych. Zastąp wybraną nazwę właściwości giełdy dla podpisu.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Aby dodać właściwość Caption giełdowy przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie [Kreatora dodawania właściwości](../ide/names-add-property-wizard.md).

1. W polu **Nazwa właściwości** kliknij pozycję **podpis**.

1. Kliknij przycisk **Zakończ**.

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>Dodawanie zmian w Kreatorze właściwości dla właściwości podstawowych

Ponieważ `COleControl` obsługuje właściwości podstawowe, Kreator dodawania właściwości nie zmienia deklaracji klasy w jakikolwiek sposób; dodaje właściwość do mapy wysyłania. Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania kontrolki, która znajduje się w implementacji (. CPP):

[!code-cpp[NVC_MFC_AxUI#22](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

Następujący wiersz jest dodawany do opisu interfejsu formantu (. IDL):

[!code-cpp[NVC_MFC_AxUI#23](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Ten wiersz przypisuje Właściwość Caption o określonym IDENTYFIKATORze. Należy zauważyć, że właściwość jest powiązana i będzie żądać uprawnień z bazy danych przed zmodyfikowaniem wartości.

Spowoduje to udostępnienie właściwości Caption użytkownikom formantu. Aby użyć wartości właściwości giełdowej, uzyskaj dostęp do zmiennej składowej lub funkcji członkowskiej `COleControl` klasy bazowej. Aby uzyskać więcej informacji na temat tych zmiennych składowych i funkcji Członkowskich, zobacz następną sekcję, właściwości giełdowe obsługiwane przez Kreatora dodawania właściwości.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>Właściwości podstawowe obsługiwane przez Kreatora dodawania właściwości

`COleControl`Klasa zawiera dziewięć właściwości podstawowych. Możesz dodać odpowiednie właściwości przy użyciu Kreatora dodawania właściwości.

|Właściwość|Wpis mapy wysyłania|Jak uzyskać dostęp do wartości|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE ()|Wartość dostępna jako `m_sAppearance` .|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR ()|Wartość dostępna poprzez wywołanie `GetBackColor` .|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE ()|Wartość dostępna jako `m_sBorderStyle` .|
|`Caption`|DISP_STOCKPROP_CAPTION ()|Wartość dostępna poprzez wywołanie `InternalGetText` .|
|`Enabled`|DISP_STOCKPROP_ENABLED ()|Wartość dostępna jako `m_bEnabled` .|
|`Font`|DISP_STOCKPROP_FONT ()|Zobacz [kontrolki ActiveX MFC w artykule: Używanie czcionek](mfc-activex-controls-using-fonts.md) do użycia.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR ()|Wartość dostępna poprzez wywołanie `GetForeColor` .|
|`hWnd`|DISP_STOCKPROP_HWND ()|Wartość dostępna jako `m_hWnd` .|
|`Text`|DISP_STOCKPROP_TEXT ()|Wartość dostępna poprzez wywołanie `InternalGetText` . Ta właściwość jest taka sama jak `Caption` , z wyjątkiem nazwy właściwości.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE ()|Wartość dostępna jako `m_lReadyState` lub`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>Właściwości i powiadomienia dotyczące akcji

Większość właściwości podstawowych ma funkcje powiadomień, które mogą zostać zastąpione. Na przykład za każdym razem, gdy `BackColor` Właściwość zostanie zmieniona, `OnBackColorChanged` wywoływana jest funkcja (funkcja członkowska klasy kontrolki). Domyślne implementacje (in `COleControl` ) `InvalidateControl` . Zastąp tę funkcję, jeśli chcesz podjąć dodatkowe działania w odpowiedzi na tę sytuację.

## <a name="color-properties"></a><a name="_core_color_properties"></a>Właściwości koloru

`ForeColor` `BackColor` Podczas malowania kontrolki można użyć zasobów i właściwości lub własnych właściwości kolorów niestandardowych. Aby użyć właściwości Color, wywołaj funkcję członkowską [COleControl:: TranslateColor](reference/colecontrol-class.md#translatecolor) . Parametry tej funkcji to wartość właściwości Color i opcjonalnego dojścia do palety. Wartość zwracana jest wartością **COLORREF** , która może być przenoszona do funkcji GDI, takich jak `SetTextColor` i `CreateSolidBrush` .

Wartości koloru dla zasobów `ForeColor` i `BackColor` właściwości są dostępne przez wywołanie `GetForeColor` albo lub `GetBackColor` funkcji.

Poniższy przykład demonstruje użycie tych dwóch właściwości koloru podczas malowania kontrolki. Inicjuje chwilową zmienną **COLORREF** i `CBrush` obiekt z wywołaniami do `TranslateColor` : jeden przy użyciu `ForeColor` właściwości, a drugi przy użyciu `BackColor` właściwości. Obiekt tymczasowy `CBrush` jest następnie używany do malowania prostokąta kontrolki, a kolor tekstu jest ustawiany przy użyciu `ForeColor` właściwości.

[!code-cpp[NVC_MFC_AxUI#24](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](reference/colecontrol-class.md)
