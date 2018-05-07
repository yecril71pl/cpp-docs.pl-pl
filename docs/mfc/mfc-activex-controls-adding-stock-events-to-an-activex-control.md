---
title: 'Formanty MFC ActiveX: Dodawanie zdarzeń standardowych do formantu ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 210749906391ccdba2e488b75be98264bcba39cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Kontrolki ActiveX MFC: dodawanie zdarzeń standardowych do kontrolki ActiveX
Zdarzeń standardowych różnią się od zdarzeń niestandardowych, są one uruchamiane automatycznie przez klasę [colecontrol —](../mfc/reference/colecontrol-class.md). `COleControl` zawiera funkcji wstępnie zdefiniowanych elementów członkowskich, które wyzwalać zdarzenia wynikające z typowych akcji. Niektóre typowe akcje implementowane przez `COleControl` obejmują jednym - i double - clicks na kontroli, zdarzenia klawiatury i zmiany w stanie przycisku myszy. Wpisy mapy zdarzeń dla standardowych zdarzeń są zawsze poprzedzone **event_stock —** prefiks.  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a> Podstawowy zdarzenia obsługiwane przez Kreator dodawania zdarzenia  
 `COleControl` Klasa udostępnia dziesięć zdarzeń standardowych wymienionych w poniższej tabeli. Można określić zdarzenia w za pomocą formantu [Kreator dodawania zdarzenia](../ide/add-event-wizard.md).  
  
### <a name="stock-events"></a>Zdarzeń standardowych  
  
|Zdarzenie|Wyzwalania — funkcja|Komentarze|  
|-----------|---------------------|--------------|  
|Kliknij|**void (fireclick —)**|Wywoływane, gdy formant przechwytuje mysz, wszystkie **BUTTONUP** (po lewej stronie, średnie lub prawego) komunikat jest odbierany i zwolnieniu przycisku nad formantem. MouseDown giełdowych i zdarzenia MouseUp odbywa się przed tym zdarzeniem.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_click —)**|  
|DblClick|**void (firedblclick —)**|Podobny do kliknij ale wywoływane, gdy **BUTTONDBLCLK** odebrać wiadomości.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_dblclick —)**|  
|Błąd|**void FireError (SCODE***scode* **, LPCSTR** `lpszDescription` **, UINT**`nHelpID`**= 0)** |Uruchamiany po wystąpieniu błędu w formantu ActiveX poza zakres dostępu metody wywołania lub właściwości.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_errorevent —)**|  
|KeyDown|**firekeydown — void (krótka** `nChar` **, krótki**`nShiftState`**)** |Wywoływane, gdy `WM_SYSKEYDOWN` lub `WM_KEYDOWN` odebrać wiadomości.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_keydown —)**|  
|KeyPress|**firekeypress — void (krótka\***`pnChar`**)** |Wywoływane, gdy `WM_CHAR` odebrać wiadomości.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_keypress —)**|  
|KeyUp|**firekeyup — void (krótka** `nChar` **, krótki**`nShiftState`**)** |Wywoływane, gdy `WM_SYSKEYUP` lub `WM_KEYUP` odebrać wiadomości.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_keyup —)**|  
|MouseDown|**firemousedown — void (krótka** `nButton` **, krótki** `nShiftState` **, float***x* **, float** *y***)** |Uruchamiany, jeśli istnieją **BUTTONDOWN** odebraniu (po lewej, środka lub do prawej). Mysz jest przechwytywany bezpośrednio przed to zdarzenie jest wywoływane.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_mousedown —)**|  
|MouseMove|**firemousemove — void (krótka** `nButton` **, krótki** `nShiftState` **, float***x* **, float** *y***)** |Wywoływane, gdy `WM_MOUSEMOVE` odebrać wiadomości.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_mousemove —)**|  
|MouseUp|**firemouseup — void (krótka** `nButton` **, krótki** `nShiftState` **, float***x* **, float** *y***)** |Uruchamiany, jeśli istnieją **BUTTONUP** odebraniu (po lewej, środka lub do prawej). Przechwytywanie myszy jest zwolniony przed to zdarzenie jest wywoływane.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_mouseup —)**|  
|ReadyStateChange|**void (FireReadyStateChange)**|Uruchamiany, gdy formant przejścia do następnego stanu gotowości ze względu na ilość danych otrzymywanych.<br /><br /> Wpisu mapowania zdarzeń: **(event_stock_readystatechange —)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a> Dodawanie zdarzeń standardowych przy użyciu Kreator dodawania zdarzenia  
 Dodawanie zdarzeń standardowych wymaga mniej pracy niż dodawanie zdarzeń niestandardowych, ponieważ uruchamiania rzeczywistego zdarzenia odbywa się automatycznie przez klasę podstawową `COleControl`. Poniższa procedura dodaje zdarzeń standardowych do formantu, który został utworzony przy użyciu [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md). Zdarzenia o nazwie KeyPress generowane, gdy zostanie naciśnięty klawisz i kontrolka jest aktywny. Tę procedurę można również dodać innych standardowych zdarzeń. Zastąp nazwę wybranego standardowych zdarzenia KeyPress.  
  
#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Aby dodać zdarzenie standardowe KeyPress za pomocą Kreatora dodawania zdarzenia  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas kliknij prawym przyciskiem myszy Twojej klasy kontrolki ActiveX, aby otworzyć menu skrótów.  
  
3.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodawanie zdarzenia**.  
  
     Spowoduje to otwarcie Kreatora dodawania zdarzenia.  
  
4.  W **Nazwa zdarzenia** listy rozwijanej wybierz `KeyPress`.  
  
5.  Kliknij przycisk **Zakończ**.  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a> Dodawanie zdarzenia zmiany kreatora dla standardowych zdarzeń  
 Ponieważ standardowych zdarzenia są obsługiwane przez klasę podstawową formantu, Kreator dodawania zdarzenia nie zmienia się z deklaracji klasy, w dowolny sposób. Dodaje zdarzenie do formantu mapy zdarzeń i powoduje, że wpis w jej. Plik IDL. Następujący wiersz zostanie dodany do mapy zdarzeń formantu, znajduje się w implementacji klasy formantu (. Pliku CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 Dodawanie tego kodu wyzwala zdarzenia KeyPress podczas `WM_CHAR` komunikat jest odbierany i kontrolka jest aktywny. Zdarzenia KeyPress mogą być uruchamiane w pozostałych godzinach przez wywołanie jego uruchamiania funkcji (na przykład `FireKeyPress`) z kodem formantu.  
  
 Kreator dodawania zdarzenia dodaje następujący wiersz kodu do formantu. Plik IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 Ten wiersz kojarzy zdarzenia KeyPress z Identyfikatora wysyłania standardowe i umożliwia kontenera do przewidzenia zdarzenia KeyPress.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [Klasa COleControl](../mfc/reference/colecontrol-class.md)
