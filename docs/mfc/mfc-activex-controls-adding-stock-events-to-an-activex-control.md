---
title: 'Kontrolki ActiveX MFC: dodawanie zdarzeń standardowych do kontrolki ActiveX'
ms.date: 11/04/2016
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
ms.openlocfilehash: a97c08baaf3c11b0436e52bb4fd4ac380999d69a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615588"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Kontrolki ActiveX MFC: dodawanie zdarzeń standardowych do kontrolki ActiveX

Zdarzenia giełdowe różnią się od zdarzeń niestandardowych w tym, że są one automatycznie uruchamiane przez klasę [COleControl](reference/colecontrol-class.md). `COleControl`zawiera wstępnie zdefiniowane funkcje członkowskie, które wyzwalają zdarzenia powstałe w wyniku wykonywania typowych akcji. Niektóre typowe akcje implementowane przez funkcję `COleControl` obejmują pojedyncze kliknięcia kontrolki, zdarzenia klawiatury oraz zmiany stanu przycisków myszy. Wpisy mapy zdarzeń dla zdarzeń giełdowych są zawsze poprzedzane prefiksem EVENT_STOCK.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>Zdarzenia giełdowe obsługiwane przez Kreatora dodawania zdarzenia

`COleControl`Klasa zawiera dziesięć zdarzeń podstawowych wymienionych w poniższej tabeli. Możesz określić żądane zdarzenia w kontrolce za pomocą [Kreatora dodawania zdarzenia](../ide/add-event-wizard.md).

### <a name="stock-events"></a>Zdarzenia giełdowe

|Zdarzenie|Funkcja uruchamiania|Komentarze|
|-----------|---------------------|--------------|
|Kliknij pozycję|**void FireClick ()**|Uruchamiany, gdy kontrolka przechwytuje mysz, zostanie odebrana wiadomość dowolnego **BUTTONUP** (Left, Middle lub right), a przycisk zostanie zwolniony przez kontrolkę. Zdarzenia MouseDown i MouseUp są wykonywane przed tym zdarzeniem.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_CLICK ()**|
|DblClick|**void FireDblClick ()**|Podobne do kliknięcia, ale wywoływane po odebraniu komunikatu **BUTTONDBLCLK** .<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_DBLCLICK ()**|
|Błąd|**void FireError — (SCODE***SCODE* **, LPCSTR** `lpszDescription` **, uint** `nHelpID` **= 0)**        |Uruchamiany w przypadku wystąpienia błędu w kontrolce ActiveX poza zakresem wywołania metody lub dostępu do właściwości.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_ERROREVENT ()**|
|Zdarzenia|**void FireKeyDown (krótkie** `nChar` **, krótkie** `nShiftState` **)**      |Uruchamiany po `WM_SYSKEYDOWN` `WM_KEYDOWN` odebraniu komunikatu lub.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_KEYDOWN ()**|
|KeyPress|**void FireKeyPress (krótki** <strong>\*</strong> `pnChar` **)**    |Uruchamiany po `WM_CHAR` odebraniu komunikatu.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_KEYPRESS ()**|
|KeyUp|**void FireKeyUp (krótkie** `nChar` **, krótkie** `nShiftState` **)**      |Uruchamiany po `WM_SYSKEYUP` `WM_KEYUP` odebraniu komunikatu lub.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_KEYUP ()**|
|MouseDown|**void FireMouseDown (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Uruchamiany w przypadku otrzymania dowolnego **buttonDown** (Left, Middle lub right). Wskaźnik myszy jest przechwytywany natychmiast przed uruchomieniem tego zdarzenia.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_MOUSEDOWN ()**|
|MouseMove|**void FireMouseMove (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Uruchamiany po odebraniu komunikatu WM_MOUSEMOVE.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_MOUSEMOVE ()**|
|MouseUp|**void FireMouseUp (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Uruchamiany w przypadku otrzymania dowolnego **BUTTONUP** (Left, Middle lub right). Przechwytywanie myszy jest uwalniane przed uruchomieniem tego zdarzenia.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_MOUSEUP ()**|
|ReadyStateChange|**void FireReadyStateChange ()**|Uruchamiany, gdy kontrolka przechodzi do następnego stanu gotowości ze względu na ilość odebranych danych.<br /><br /> Wpis mapy zdarzeń: **EVENT_STOCK_READYSTATECHANGE ()**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>Dodawanie zdarzenia giełdowego za pomocą Kreatora dodawania zdarzenia

Dodanie zdarzeń giełdowych wymaga mniejszej ilości pracy niż dodanie zdarzeń niestandardowych, ponieważ wyzwolenie rzeczywistego zdarzenia jest obsługiwane automatycznie przez klasę bazową `COleControl` . Poniższa procedura dodaje zdarzenie podstawowe do kontrolki, która została opracowana za pomocą [Kreatora kontrolek ActiveX MFC](reference/mfc-activex-control-wizard.md). Zdarzenie wywoływane przez naciśnięcie klawisza i jest wyzwalane po naciśnięciu przycisku, a kontrolka jest aktywna. Ta procedura służy również do dodawania innych zdarzeń giełdowych. Zastąp wybraną nazwę zdarzenia podstawowego dla KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Aby dodać wydarzenie na potrzeby giełdowe za pomocą Kreatora dodawania zdarzenia

1. Załaduj projekt kontrolki.

1. W Widok klasy kliknij prawym przyciskiem myszy klasę kontrolki ActiveX, aby otworzyć menu skrótów.

1. W menu skrótów kliknij pozycję **Dodaj** , a następnie kliknij pozycję **Dodaj zdarzenie**.

   Spowoduje to otwarcie Kreatora dodawania zdarzenia.

1. Z listy rozwijanej **Nazwa zdarzenia** wybierz pozycję `KeyPress` .

1. Kliknij przycisk **Zakończ**.

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>Dodaj zmiany kreatora zdarzeń dla zdarzeń giełdowych

Ponieważ zdarzenia giełdowe są obsługiwane przez klasę bazową formantu, Kreator dodawania zdarzeń nie zmienia deklaracji klasy w żaden sposób. Dodaje zdarzenie do mapy zdarzeń kontrolki i tworzy wpis w nim. Plik IDL. Poniższy wiersz jest dodawany do mapy zdarzeń kontrolki, która znajduje się w implementacji klasy kontrolki (. CPP):

[!code-cpp[NVC_MFC_AxUI#5](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

Dodanie tego kodu wyzwala zdarzenie KeyPress po odebraniu komunikatu WM_CHAR, a kontrolka jest aktywna. Zdarzenie KeyPress może być wyzwalane w innym czasie przez wywołanie funkcji uruchamiania (na przykład `FireKeyPress` ) z kodu sterującego.

Kreator dodawania zdarzeń dodaje następujący wiersz kodu do kontrolki. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#6](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Ten wiersz kojarzy zdarzenie KeyPress ze standardowym IDENTYFIKATORem wysyłania i umożliwia kontenerowi przewidzenie zdarzenia KeyPress.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: metody](mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](reference/colecontrol-class.md)
