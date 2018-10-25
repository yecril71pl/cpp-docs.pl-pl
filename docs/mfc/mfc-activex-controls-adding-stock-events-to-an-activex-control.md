---
title: 'Kontrolki ActiveX MFC: Dodawanie zdarzeń standardowych do kontrolki ActiveX | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 3bf023dbc52ccac7311a62aba1a290b1a03190dd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060562"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Kontrolki ActiveX MFC: dodawanie zdarzeń standardowych do kontrolki ActiveX

Zdarzeń standardowych różnią się od zdarzenia niestandardowe, w tym, że są one uruchamiane automatycznie przez klasę [COleControl](../mfc/reference/colecontrol-class.md). `COleControl` zawiera funkcje Członkowskie wstępnie zdefiniowanych, które wyzwolenie zdarzenia wynikające z typowych akcji. Niektóre typowe akcje implementowany przez `COleControl` obejmują jedną — i double - clicks na kontrolki, zdarzenia klawiatury i zmiany w stanie przycisków myszy. Zdarzenie mapy zapisów akcji, które zdarzenia są zawsze poprzedzone event_stock — prefiks.

##  <a name="_core_stock_events_supported_by_classwizard"></a> Podstawowy zdarzenia obsługiwane przez Kreator dodawania zdarzenia

`COleControl` Klasa udostępnia dziesięciu standardowych zdarzeń, wymienione w poniższej tabeli. Można określić zdarzeń w sieci za pomocą kontrolki [Kreator dodawania zdarzenia](../ide/add-event-wizard.md).

### <a name="stock-events"></a>Podstawowe zdarzenia

|Zdarzenie|Wyzwalanie funkcji|Komentarze|
|-----------|---------------------|--------------|
|Kliknij|**void (fireclick —)**|Wywoływane, gdy kontrolka przechwytuje mysz, wszelkie **BUTTONUP** (lewy, środkowy lub prawy) wiadomość zostaje odebrana i zwolnieniu przycisku kontrolki. Stock MouseDown i MouseUp zdarzeń odbywa się przed tym zdarzeniem.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_click —)**|
|DblClick|**void (firedblclick —)**|Podobne, a następnie kliknij ale wyzwalane, gdy **BUTTONDBLCLK** wiadomość zostaje odebrana.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_dblclick —)**|
|Błąd|**fireerror — void (SCODE***scode* **, LPCSTR** `lpszDescription` **, UINT**`nHelpID`**= 0)**|Wywoływane, gdy wystąpi błąd w obrębie formant ActiveX poza zakres dostępu metody wywołania lub właściwość.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_errorevent —)**|
|KeyDown|**firekeydown — void (krótki** `nChar` **, krótkich**`nShiftState`**)**|Wywoływane, gdy `WM_SYSKEYDOWN` lub `WM_KEYDOWN` wiadomość zostaje odebrana.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_keydown —)**|
|KeyPress|**firekeypress — void (krótki** <strong>\*</strong> `pnChar` **)**|Wywoływane, gdy `WM_CHAR` wiadomość zostaje odebrana.<br /><br /> Wpisu mapowania zdarzeń: **(EVENT_STOCK_KEYPRESS)**|
|KeyUp|**firekeyup — void (krótki** `nChar` **, krótkich**`nShiftState`**)**|Wywoływane, gdy `WM_SYSKEYUP` lub `WM_KEYUP` wiadomość zostaje odebrana.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_keyup —)**|
|MouseDown|**firemousedown — void (krótki** `nButton` **, krótkich** `nShiftState` **, float***x* **, float** *y***)**|Wywoływane, jeśli istnieje **BUTTONDOWN** (po lewej stronie, środka lub do prawej) została odebrana. Przycisk myszy jest przechwytywany bezpośrednio przed wykonaniem to zdarzenie jest wywoływane.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_mousedown —)**|
|MouseMove|**firemousemove — void (krótki** `nButton` **, krótkich** `nShiftState` **, float***x* **, float** *y***)**|Wywoływane, gdy WM_MOUSEMOVE wiadomość zostaje odebrana.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_mousemove —)**|
|MouseUp|**firemouseup — void (krótki** `nButton` **, krótkich** `nShiftState` **, float***x* **, float** *y***)**|Wywoływane, jeśli istnieje **BUTTONUP** (po lewej stronie, środka lub do prawej) została odebrana. Przechwytywanie myszy jest zwalniany, zanim to zdarzenie jest wywoływane.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_mouseup —)**|
|ReadyStateChange|**void (FireReadyStateChange)**|Wywoływane, gdy przejściu kontrolki do następnego stanu gotowości ze względu na ilość danych odebranych.<br /><br /> Wpisu mapowania zdarzeń: **event_stock_readystatechange —)**|

##  <a name="_core_adding_a_stock_event_using_classwizard"></a> Dodawanie zdarzeń standardowych przy użyciu Kreator dodawania zdarzenia

Dodawanie zdarzeń standardowych wymaga mniej pracy niż dodawanie zdarzeń niestandardowych, ponieważ uruchomieniem rzeczywistego zdarzenia jest obsługiwane automatycznie przez klasę bazową `COleControl`. Poniższa procedura dodaje zdarzenie do formantu, który został utworzony przy użyciu [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md). Zdarzenia KeyPress, wywoływana jest uruchamiana, gdy zostanie naciśnięty klawisz i sterowania jest aktywna. Tej procedury można również dodać inne podstawowe zdarzenia. Zastąp nazwę wybranego zdarzenie KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Aby dodać podstawowe zdarzenia KeyPress przy użyciu Kreatora dodawania zdarzenia

1. Załaduj projekt formantu.

1. W widoku klas kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów klasy kontrolki ActiveX.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodawanie zdarzenia**.

   Spowoduje to otwarcie Kreatora dodawania zdarzenia.

1. W **Nazwa zdarzenia** listy rozwijanej wybierz `KeyPress`.

1. Kliknij przycisk **Zakończ**.

##  <a name="_core_classwizard_changes_for_stock_events"></a> Dodaj zmiany w zdarzeniu kreatora dla zdarzeń dotyczących zapasów

Ponieważ zdarzeń standardowych są obsługiwane przez klasę bazową kontrolki, Kreator dodawania zdarzenia nie zmienia się deklaracją klasy w dowolny sposób. Dodaje zdarzenie do mapy zdarzeń formantów i sprawia, że wpis w jego. Plik IDL. Następujący wiersz zostanie dodany do mapy zdarzeń formantu, znajduje się w implementacji klasy formantu (. Plik CPP):

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

Dodając ten kod wyzwala zdarzenia KeyPress po otrzymaniu komunikat WM_CHAR i sterowania jest aktywna. Zdarzenia KeyPress, uruchamiane w innym czasie przez wywołanie funkcji jego uruchomieniu którego (na przykład `FireKeyPress`) z kodem kontroli.

Kreator dodawania zdarzenia dodaje następujący wiersz kodu do formantu. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Ten wiersz kojarzy zdarzenie KeyPress za pomocą jego Identyfikatora wysyłania standardowego i umożliwia kontener, aby przewidywać zdarzenia KeyPress.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
