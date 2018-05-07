---
title: 'Formanty MFC ActiveX: Dodawanie właściwości standardowych | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: c51a2efba3c89b4e216fec96459b14c3d0c637d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Kontrolki ActiveX MFC: dodawanie właściwości standardowych
Właściwości podstawowe różnią się od właściwości niestandardowe, są one już zaimplementowany przez klasę `COleControl`. `COleControl` zawiera funkcje wstępnie zdefiniowanego elementu członkowskiego, które obsługuje wspólne właściwości formantu. Niektóre typowe właściwości obejmują Podpis formantu i kolory pierwszego planu i tła. Uzyskać informacji o innych właściwości podstawowych, zobacz [giełdowych właściwości obsługiwane przez Kreatora dodawania właściwości](#_core_stock_properties_supported_by_classwizard) dalszej części tego artykułu. Wpisy mapy wysyłania dla właściwości podstawowe są zawsze poprzedzone **DISP_STOCKPROP**.  
  
 W tym artykule opisano Dodawanie właściwości standardowych (w tym przypadku podpis) do formantu ActiveX, za pomocą Kreatora dodawania właściwości i opisano wynikowy modyfikacji kodu. Tematy obejmują:  
  
-   [Dodawanie właściwości standardowych przy użyciu Kreatora dodawania właściwości](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [Dodaj Kreatora właściwości zmiany właściwości standardowych](#_core_classwizard_changes_for_stock_properties)  
  
-   [Właściwości podstawowe obsługiwane przez Kreatora dodawania właściwości](#_core_stock_properties_supported_by_classwizard)  
  
-   [Właściwości podstawowe i powiadomienia](#_core_stock_properties_and_notification)  
  
-   [Właściwości kolorów](#_core_color_properties)  
  
    > [!NOTE]
    >  Niestandardowe formanty Visual Basic zwykle mają właściwości, takie jak Top, po lewej, szerokość, wysokość, Wyrównaj, Tag, nazwa, TabIndex, TabStop i nadrzędnego. Kontenery formantów ActiveX, jednak są zobowiązani do wykonania tych właściwości formantu, a w związku z tym formantów ActiveX nie powinna obsługiwać te właściwości.  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> Przy użyciu Dodaj Kreatora właściwości, aby dodać właściwości standardowych  
 Dodawanie właściwości standardowych wymaga mniejsza ilość kodu niż dodawanie właściwości niestandardowych, ponieważ obsługa właściwość odbywa się automatycznie przez `COleControl`. Poniższa procedura pokazuje, dodawanie zapasów właściwości podpisu Framework formantu ActiveX i można także dodać inne właściwości standardowych. Zastąp nazwę wybranej właściwości podstawowych dla podpisu.  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Aby dodać podstawowe właściwości podpisu za pomocą Kreatora dodawania właściwości  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
     Spowoduje to otwarcie [Dodaj Kreatora właściwości](../ide/names-add-property-wizard.md).  
  
5.  W **nazwa właściwości** kliknij **podpis**.  
  
6.  Kliknij przycisk **Zakończ**.  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> Dodaj Kreatora właściwości zostanie zmieniona dla właściwości podstawowe  
 Ponieważ `COleControl` obsługuje właściwości podstawowych, w Kreatorze dodawania właściwości nie zmienia deklaracji klasy, w dowolny sposób; dodaje właściwość do mapy wysyłania. Kreator dodawania właściwości dodaje następujący wiersz do mapy wysyłania formantu, który znajduje się w implementacji (. Pliku CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 Następujący wiersz jest dodawany do formantu opis interfejsu (. Plik IDL):  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 Ten wiersz przypisuje właściwości podpisu określonym identyfikatorem. Zwróć uwagę, że właściwość jest powiązania i będzie żądać uprawnień z bazy danych przed zmodyfikowaniem wartość.  
  
 Dzięki temu właściwości podpisu dostępne dla użytkowników formantu. Aby użyć wartości właściwości standardowych, dostęp do zmiennej członkowskiej lub funkcja członkowska `COleControl` klasy podstawowej. Aby uzyskać więcej informacji o tych zmiennych Członkowskich i funkcji elementów członkowskich zobacz następną sekcję, Stock właściwości obsługiwane przez Kreatora dodawania właściwości.  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> Podstawowy właściwości obsługiwanych przez Dodaj Kreatora właściwości  
 `COleControl` Klasa udostępnia dziewięć właściwości standardowych. Można dodać właściwości, które mają za pomocą Kreatora dodawania właściwości.  
  
|Właściwość|Wpisu mapy wysyłania|Jak wartość dostępu|  
|--------------|------------------------|-------------------------|  
|**Wygląd**|**(DISP_STOCKPROP_APPEARANCE)**|Wartość dostępna jako **m_sAppearance**.|  
|`BackColor`|**(DISP_STOCKPROP_BACKCOLOR)**|Wartość dostępny przez wywołanie metody `GetBackColor`.|  
|`BorderStyle`|**(DISP_STOCKPROP_BORDERSTYLE)**|Wartość dostępna jako **m_sBorderStyle**.|  
|**Podpis**|**(DISP_STOCKPROP_CAPTION)**|Wartość dostępny przez wywołanie metody `InternalGetText`.|  
|**włączone**|**(DISP_STOCKPROP_ENABLED)**|Wartość dostępna jako **m_bEnabled**.|  
|**Czcionki**|**(DISP_STOCKPROP_FONT)**|Zapoznaj się z artykułem [kontrolki ActiveX MFC: przy użyciu czcionek](../mfc/mfc-activex-controls-using-fonts.md) do użycia.|  
|`ForeColor`|**(DISP_STOCKPROP_FORECOLOR)**|Wartość dostępny przez wywołanie metody `GetForeColor`.|  
|**Właściwość hWnd**|**(DISP_STOCKPROP_HWND)**|Wartość dostępna jako `m_hWnd`.|  
|**Tekst**|**(DISP_STOCKPROP_TEXT)**|Wartość dostępny przez wywołanie metody `InternalGetText`. Ta właściwość jest taka sama jak **podpis**, z wyjątkiem nazwy właściwości.|  
|**ReadyState**|**DISP_STOCKPROP_READYSTATE()**|Wartość dostępna jako m_lReadyState lub `GetReadyState`|  
  
##  <a name="_core_stock_properties_and_notification"></a> Właściwości podstawowe i powiadomienia  
 Większość podstawowych właściwości ma funkcje powiadomień, które mogą zostać zastąpione. Na przykład, gdy `BackColor` właściwości zostanie zmieniona, `OnBackColorChanged` wywołaniem funkcji (funkcja członkowska klasy formantu). Domyślna implementacja (w `COleControl`) wywołań `InvalidateControl`. Należy przesłonić tę funkcję, aby podejmować dodatkowe akcje w odpowiedzi na takiej sytuacji.  
  
##  <a name="_core_color_properties"></a> Właściwości kolorów  
 Można użyć zapasów `ForeColor` i `BackColor` właściwości lub własne właściwości niestandardowego koloru, gdy malowanie formantu. Aby użyć właściwości kolor, należy wywołać [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) funkcję elementu członkowskiego. Parametry tej funkcji są wartości właściwości kolorów i dojścia opcjonalne palety. Wartość zwracana jest **COLORREF** wartości, które mogą zostać przekazane do interfejsu GDI funkcji, takich jak `SetTextColor` i `CreateSolidBrush`.  
  
 Wartości kolorów dla zasobu `ForeColor` i `BackColor` właściwości są udostępniane przez wywołanie albo `GetForeColor` lub `GetBackColor` funkcji odpowiednio.  
  
 W poniższym przykładzie pokazano, za pomocą właściwości tych dwóch kolorów, gdy malowanie formantu. Inicjuje on tymczasowej **COLORREF** zmiennej i `CBrush` obiektu wywołania `TranslateColor`: go przy użyciu `ForeColor` właściwości i innych using `BackColor` właściwości. Tymczasowej `CBrush` obiekt jest następnie używany do rysowania prostokącie kontrolki i ustawić kolor tekstu przy użyciu `ForeColor` właściwości.  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: właściwości](../mfc/mfc-activex-controls-properties.md)   
 [Formanty MFC ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [Klasa COleControl](../mfc/reference/colecontrol-class.md)
