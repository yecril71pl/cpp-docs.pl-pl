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
ms.openlocfilehash: 79cd4fc572e55c67cc5a2cfe3a00e04f2a4a7850
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364685"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Kontrolki ActiveX MFC: dodawanie zdarzeń standardowych do kontrolki ActiveX

Zdarzenia giełdowe różnią się od zdarzeń niestandardowych tym, że są automatycznie uruchamiane przez klasę [COleControl](../mfc/reference/colecontrol-class.md). `COleControl`zawiera wstępnie zdefiniowane funkcje członkowskie, które uruchamiają zdarzenia wynikające ze wspólnych akcji. Niektóre typowe akcje `COleControl` implementowane przez obejmują pojedyncze i dwukrotne kliknięcia formantu, zdarzenia klawiatury i zmiany stanu przycisków myszy. Wpisy mapy zdarzeń dla zdarzeń magazynowych są zawsze poprzedzone prefiksem EVENT_STOCK.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>Zdarzenia giełdowe obsługiwane przez Kreatora dodawania zdarzeń

Klasa `COleControl` zawiera dziesięć zdarzeń giełdowych, wymienionych w poniższej tabeli. Zdarzenia, które mają być określone w formancie, można określić za pomocą [Kreatora dodawania zdarzeń](../ide/add-event-wizard.md).

### <a name="stock-events"></a>Wydarzenia stockowe

|Wydarzenie|Funkcja wypalania|Komentarze|
|-----------|---------------------|--------------|
|Kliknij pozycję|**nieważne FireClick( )**|Uruchamiany, gdy formant przechwytuje myszy, każdy **BUTTONUP** (lewo, środkowy lub prawy) komunikat jest odbierany, a przycisk jest zwalniany za pomocą kontroli. Zdarzenia MouseDown i MouseUp magazynu występują przed tym zdarzeniem.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_CLICK( )**|
|DblClick (właśc.|**void FireDblClick( )**|Podobnie jak Kliknij, ale zwolniony po odebraniu **komunikatu BUTTONDBLCLK.**<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_DBLCLICK( )**|
|Błąd|**void FireError( SCODE scode***scode* **, LPCSTR** `lpszDescription` , **UINT**`nHelpID`**= 0 )**        |Uruchamiany, gdy wystąpi błąd w formancie ActiveX poza zakresem wywołania metody lub dostępu do właściwości.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_ERROREVENT( )**|
|Keydown|**void FireKeyDown( krótki,** `nChar` **krótki)**`nShiftState`**)**      |Uruchamiany `WM_SYSKEYDOWN` po `WM_KEYDOWN` odebraniu lub odebraniu wiadomości.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_KEYDOWN( )**|
|Keypress|**void FireKeyPress(** <strong>\*</strong> `pnChar` **krótki)**    |Uruchamiany `WM_CHAR` po odebraniu wiadomości.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_KEYPRESS( )**|
|Keyup|**void FireKeyUp( krótki,** `nChar` **krótki)**`nShiftState`**)**      |Uruchamiany `WM_SYSKEYUP` po `WM_KEYUP` odebraniu lub odebraniu wiadomości.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_KEYUP( )**|
|Mousedown|**void FireMouseDown(** `nButton` **krótki, krótki** `nShiftState` , **float***x* , **float***y***)**          |Wystrzeliwany, jeśli zostanie **odebrany przycisk BUTTONDOWN** (lewy, środkowy lub prawy). Mysz jest przechwytywany bezpośrednio przed tym zdarzeniem jest uruchamiany.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_MOUSEDOWN( )**|
|Mousemove|**void FireMouseMove(** `nButton` **krótki, krótki** `nShiftState` , **float***x* , **float***y***)**          |Uruchamiany po odebraniu WM_MOUSEMOVE wiadomości.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_MOUSEMOVE( )**|
|Mouseup|**void FireMouseUp(** `nButton` **krótki, krótki** `nShiftState` , **float***x* , **float***y***)**          |Uruchamiany, jeśli zostanie **odebrany przycisk** (lewy, środkowy lub prawy). Przechwytywanie myszy jest zwalniany przed tym zdarzeniem jest uruchamiany.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_MOUSEUP( )**|
|ReadyStateChange (Dania)|**void FireReadyStateChange( )**|Uruchamiane, gdy formant przechodzi do następnego stanu gotowości ze względu na ilość odebranych danych.<br /><br /> Wpis mapy wydarzenia: **EVENT_STOCK_READYSTATECHANGE( )**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>Dodawanie zdarzenia giełdowego za pomocą Kreatora dodawania zdarzeń

Dodawanie zdarzeń magazynowych wymaga mniej pracy niż dodawanie zdarzeń niestandardowych, ponieważ wypalanie rzeczywistego zdarzenia jest obsługiwane automatycznie przez klasę podstawową. `COleControl` Poniższa procedura dodaje zdarzenie giełdowe do formantu opracowanego przy użyciu [Kreatora sterowania MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md). Zdarzenie o nazwie KeyPress uruchamia się po naciśnięciu klawisza i jest aktywne sterowanie. Ta procedura może być również używana do dodawania innych zdarzeń giełdowych. Zastąp nazwę wybranego zdarzenia giełdowego dla KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Aby dodać zdarzenie giełdowe KeyPress za pomocą Kreatora dodawania zdarzeń

1. Załaduj projekt formantu.

1. W widoku klasy kliknij prawym przyciskiem myszy klasę formantu ActiveX, aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj zdarzenie**.

   Spowoduje to otwarcie Kreatora dodawania zdarzeń.

1. Z listy rozwijanej **Nazwa** zdarzenia `KeyPress`wybierz pozycję .

1. Kliknij przycisk **Zakończ**.

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>Dodawanie zmian kreatora zdarzeń dla zdarzeń magazynowych

Ponieważ zdarzenia stockowe są obsługiwane przez klasę podstawową formantu, Kreator dodawania zdarzeń nie zmienia deklaracji klasy w żaden sposób. Dodaje zdarzenie do mapy zdarzeń formantu i wprowadza wpis w jego . IDL. Następujący wiersz jest dodawany do mapy zdarzeń formantu, znajduje się w implementacji klasy kontroli (. CPP):

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

Dodanie tego kodu powoduje wyzywanie zdarzenia KeyPress po odebraniu WM_CHAR i aktywnym formancie. KeyPress zdarzenie może być uruchamiany w innym czasie, `FireKeyPress`wywołując jego funkcji wypalania (na przykład) z wewnątrz kodu sterującego.

Kreator dodawania zdarzeń dodaje następujący wiersz kodu do formantu . Plik IDL:

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Ten wiersz kojarzy zdarzenie KeyPress ze standardowym identyfikatorem wysyłki i umożliwia kontenerowi przewidywanie zdarzenia KeyPress.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
