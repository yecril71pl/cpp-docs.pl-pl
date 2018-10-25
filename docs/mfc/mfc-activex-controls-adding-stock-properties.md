---
title: 'Kontrolki ActiveX MFC: Dodawanie właściwości standardowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 038d33a81d96067089eb55affbad6991a62d129f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055206"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Kontrolki ActiveX MFC: dodawanie właściwości standardowych

Właściwości podstawowe różnią się od właściwości niestandardowe, w tym, że są one już zaimplementowany przez klasę `COleControl`. `COleControl` zawiera funkcje Członkowskie wstępnie zdefiniowanych, obsługujące typowe właściwości kontrolki. Niektóre typowe właściwości obejmują formantu podpisu i kolory pierwszego planu i tła. Aby uzyskać informacji na temat innych właściwości podstawowe, zobacz [Stock właściwości obsługiwane przez Kreatora dodawania właściwości](#_core_stock_properties_supported_by_classwizard) w dalszej części tego artykułu. Wpisy mapy wysyłania akcji, które właściwości mają zawsze prefiks przez DISP_STOCKPROP.

Ten artykuł zawiera opis sposobu dodawania właściwości standardowych (w tym przypadku podpis) do formantu ActiveX, za pomocą Kreatora dodawania właściwości i wyjaśnia wynikowy modyfikacji kodu. Tematy obejmują:

- [Dodawanie właściwości standardowych przy użyciu Kreatora dodawania właściwości](#_core_using_classwizard_to_add_a_stock_property)

- [Dodaj Kreatora właściwości zmiany właściwości podstawowe](#_core_classwizard_changes_for_stock_properties)

- [Właściwości podstawowe obsługiwane przez Kreatora dodawania właściwości](#_core_stock_properties_supported_by_classwizard)

- [Właściwości podstawowe i powiadomienia](#_core_stock_properties_and_notification)

- [Właściwości koloru](#_core_color_properties)

    > [!NOTE]
    >  Niestandardowe formanty Visual Basic zazwyczaj mają właściwości, takie jak górnej, po lewej stronie, szerokość, wysokość, wyrównanie, Tag, nazwa, TabIndex, TabStop i nadrzędnej. Kontenery kontrolek ActiveX, jednak są odpowiedzialne za wykonanie tych właściwości formantu, a w związku z tym formantów ActiveX nie powinien obsługiwać tych właściwości.

##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> Za pomocą Dodaj Kreatora właściwości, aby dodać właściwości standardowych

Dodawanie właściwości standardowych wymaga mniejszej ilości kodu niż dodawanie właściwości niestandardowych, ponieważ obsługa właściwość odbywa się automatycznie przez `COleControl`. Poniższa procedura pokazuje Dodawanie zapasów właściwości podpisu Framework formant ActiveX i można także dodać inne właściwości podstawowe. Zastąp nazwę wybranej właściwości podstawowe dla podpisu.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Aby dodać podstawowe właściwości podpisu przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie [Kreator dodawania właściwości](../ide/names-add-property-wizard.md).

1. W **nazwa właściwości** kliknij **podpis**.

1. Kliknij przycisk **Zakończ**.

##  <a name="_core_classwizard_changes_for_stock_properties"></a> Dodaj zmiany Kreatora właściwości dla właściwości podstawowe

Ponieważ `COleControl` deklaracji klasy, w żaden sposób nie zmienia się obsługuje właściwości podstawowe, Kreator dodawania właściwości; dodaje właściwość do mapy wysyłania. Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania formantu, który znajduje się w implementacji (. Plik CPP):

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

Następujący wiersz jest dodawany do kontroli nad opis interfejsu (. Plik IDL):

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Ten wiersz przypisuje właściwości podpisu określonym identyfikatorem. Zwróć uwagę, że właściwość jest możliwej do wiązania i zażąda uprawnień z bazy danych przed zmodyfikowaniem wartość.

Dzięki temu właściwości podpisu dostępne dla użytkowników kontrolki. Aby użyć wartości właściwości podstawowych, dostęp do zmiennej elementu członkowskiego lub funkcji składowej typu `COleControl` klasy bazowej. Aby uzyskać więcej informacji na temat tych zmiennych składowych i składowych zobacz następną sekcję, Stock właściwości obsługiwane przez Kreatora dodawania właściwości.

##  <a name="_core_stock_properties_supported_by_classwizard"></a> Podstawowy właściwości obsługiwanych przez Kreator dodawania właściwości

`COleControl` Klasa udostępnia dziewięć właściwości podstawowe. Można dodać właściwości, które mają za pomocą Kreatora dodawania właściwości.

|Właściwość|Wpis mapy wysyłania|Jak uzyskać dostęp do wartości|
|--------------|------------------------|-------------------------|
|`Appearance`|(DISP_STOCKPROP_APPEARANCE)|Dostępne jako wartość `m_sAppearance`.|
|`BackColor`|(DISP_STOCKPROP_BACKCOLOR)|Wartość dostępna poprzez wywołanie `GetBackColor`.|
|`BorderStyle`|(DISP_STOCKPROP_BORDERSTYLE)|Dostępne jako wartość `m_sBorderStyle`.|
|`Caption`|(DISP_STOCKPROP_CAPTION)|Wartość dostępna poprzez wywołanie `InternalGetText`.|
|`Enabled`|(DISP_STOCKPROP_ENABLED)|Dostępne jako wartość `m_bEnabled`.|
|`Font`|(DISP_STOCKPROP_FONT)|Zapoznaj się z artykułem [kontrolki ActiveX MFC: przy użyciu czcionek](../mfc/mfc-activex-controls-using-fonts.md) do użycia.|
|`ForeColor`|(DISP_STOCKPROP_FORECOLOR)|Wartość dostępna poprzez wywołanie `GetForeColor`.|
|`hWnd`|(DISP_STOCKPROP_HWND)|Dostępne jako wartość `m_hWnd`.|
|`Text`|(DISP_STOCKPROP_TEXT)|Wartość dostępna poprzez wywołanie `InternalGetText`. Ta właściwość jest taka sama jak `Caption`, z wyjątkiem nazwy właściwości.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Dostępne jako wartość `m_lReadyState` lub `GetReadyState`|

##  <a name="_core_stock_properties_and_notification"></a> Właściwości podstawowe i powiadomienia

Większość właściwości podstawowe mają funkcje powiadomień, które mogą zostać zastąpione. Na przykład, gdy `BackColor` właściwość zostanie zmieniona, `OnBackColorChanged` nosi nazwę funkcji (funkcji składowej klasy kontrolki). Domyślna implementacja (w `COleControl`) wywołań `InvalidateControl`. Należy przesłonić tę funkcję, jeśli chcesz wykonać dodatkowe akcje w odpowiedzi na tę sytuację.

##  <a name="_core_color_properties"></a> Właściwości koloru

Można użyć zasobów `ForeColor` i `BackColor` właściwości lub własnych właściwości niestandardowego koloru, gdy malowanie kontrolki. Aby użyć właściwości color, należy wywołać [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) funkcja elementu członkowskiego. Parametry tej funkcji są wartości właściwości koloru i obsługują opcjonalne palety. Wartość zwracana jest **COLORREF** wartość, która może być przekazywany do interfejsu GDI funkcje, takie jak `SetTextColor` i `CreateSolidBrush`.

Wartości kolorów dla zasobu `ForeColor` i `BackColor` właściwości są dostępne, wywołując jedną `GetForeColor` lub `GetBackColor` funkcji odpowiednio.

Poniższy przykład pokazuje, za pomocą właściwości tych dwóch kolorów, gdy malowanie kontrolki. Inicjuje tymczasowego **COLORREF** zmiennej i `CBrush` obiektu z wywołaniami `TranslateColor`: ją przy użyciu `ForeColor` właściwości i inne using `BackColor` właściwości. Tymczasowe `CBrush` obiekt jest następnie używany do malowania w prostokącie kontrolki, a kolor tekstu można ustawić przy użyciu `ForeColor` właściwości.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
