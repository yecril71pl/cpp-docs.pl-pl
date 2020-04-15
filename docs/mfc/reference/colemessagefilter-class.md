---
title: Klasa COleMessageFilter
ms.date: 11/04/2016
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
ms.openlocfilehash: f6db5f012aedf08edd87980e304e181295bfb953
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374914"
---
# <a name="colemessagefilter-class"></a>Klasa COleMessageFilter

Zarządza współbieżności wymagane przez interakcję aplikacji OLE.

## <a name="syntax"></a>Składnia

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|Konstruuje `COleMessageFilter` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Umieszcza aplikację w stanie zajęty.|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Włącza i wyłącza okno dialogowe, które pojawia się, gdy wywoływana aplikacja jest zajęta.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Włącza i wyłącza okno dialogowe, które pojawia się, gdy wywoływana aplikacja nie odpowiada.|
|[COleMessageFilter::EndBusyState](#endbusystate)|Kończy stan zajęty aplikacji.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Wywoływane przez platformę do przetwarzania komunikatów, gdy trwa wywołanie OLE.|
|[COleMessageFilter::Zarejestruj się](#register)|Rejestruje filtr wiadomości z bibliotekami DLL systemu OLE.|
|[COleMessageFilter::Odwołaj](#revoke)|Odwołuje rejestrację filtru wiadomości z bibliotekami DLL systemu OLE.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Określa odpowiedź zajętej aplikacji na wywołanie OLE.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Określa, jak długo aplikacja czeka na odpowiedź na wywołanie OLE.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|Określa odpowiedź aplikacji wywołującej na zajętą aplikację.|

## <a name="remarks"></a>Uwagi

Klasa `COleMessageFilter` jest przydatna w wizualnej edycji aplikacji serwera i kontenerów, a także aplikacji automatyzacji OLE. W przypadku aplikacji serwera, które są wywoływane, ta klasa może służyć do aplikacji "zajęty", tak aby wywołania przychodzące z innych aplikacji kontenera są anulowane lub ponowione później. Ta klasa może również służyć do określenia akcji, które mają być podjęte przez aplikację wywołującą, gdy wywoływana aplikacja jest zajęta.

Typowe użycie jest dla aplikacji serwera do wywołania [BeginBusyState](#beginbusystate) i [EndBusyState,](#endbusystate) gdy byłoby niebezpieczne dla dokumentu lub innego obiektu ole dostępne zostać zniszczone. Te wywołania są dokonywane w [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) podczas aktualizacji interfejsu użytkownika.

Domyślnie `COleMessageFilter` obiekt jest przydzielany podczas inicjowania aplikacji. Można go pobrać z [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

Jest to klasa zaawansowana; rzadko trzeba z nim pracować bezpośrednio.

Aby uzyskać więcej informacji, zobacz artykuł [Serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a>COleMessageFilter::BeginBusyState

Wywołanie tej funkcji, aby rozpocząć stan zajęty.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Uwagi

Działa w połączeniu z [EndBusyState](#endbusystate) do kontrolowania stanu zajęty aplikacji. Funkcja [SetBusyReply](#setbusyreply) określa odpowiedź aplikacji na wywoływanie aplikacji, gdy jest zajęty.

I `BeginBusyState` `EndBusyState` wywołuje przyrost i dekrementacji, odpowiednio, licznik, który określa, czy aplikacja jest zajęty. Na przykład dwa `BeginBusyState` wywołania i `EndBusyState` jedno wywołanie, aby nadal spowodować stan zajęty. Aby anulować stan zajętości, należy wywołać `EndBusyState` tę samą liczbę razy `BeginBusyState` został wywołany.

Domyślnie struktura przechodzi w stan zajętości podczas bezczynnego przetwarzania, który jest wykonywany przez [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Podczas gdy aplikacja obsługuje powiadomienia ON_COMMANDUPDATEUI, połączenia przychodzące są obsługiwane później, po zakończeniu przetwarzania bezczynnego.

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter

Tworzy obiekt `COleMessageFilter`.

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog

Włącza i wyłącza zajęte okno dialogowe, które jest wyświetlane po wygaśnięciu opóźnienia oczekującego na wiadomość (zobacz [SetRetryReply](#setretryreply)) podczas wywołania OLE.

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableBusy*<br/>
Określa, czy okno dialogowe "zajęty" jest włączone czy wyłączone.

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog

Włącza i wyłącza okno dialogowe "nie odpowiada", które jest wyświetlane, jeśli komunikat klawiatury lub myszy jest oczekujący podczas wywołania OLE i nawiążenie czasu połączenia.

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>Parametry

*bZaponowanie niespozycją*<br/>
Określa, czy okno dialogowe "brak odpowiedzi" jest włączone czy wyłączone.

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a>COleMessageFilter::EndBusyState

Wywołanie tej funkcji, aby zakończyć stan zajęty.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Uwagi

Działa w połączeniu z [BeginBusyState](#beginbusystate) do kontrolowania stanu zajęty aplikacji. Funkcja [SetBusyReply](#setbusyreply) określa odpowiedź aplikacji na wywoływanie aplikacji, gdy jest zajęty.

I `BeginBusyState` `EndBusyState` wywołuje przyrost i dekrementacji, odpowiednio, licznik, który określa, czy aplikacja jest zajęty. Na przykład dwa `BeginBusyState` wywołania i `EndBusyState` jedno wywołanie, aby nadal spowodować stan zajęty. Aby anulować stan zajętości, należy wywołać `EndBusyState` tę samą liczbę razy `BeginBusyState` został wywołany.

Domyślnie struktura przechodzi w stan zajętości podczas bezczynnego przetwarzania, który jest wykonywany przez [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Podczas gdy aplikacja obsługuje powiadomienia ON_UPDATE_COMMAND_UI, połączenia przychodzące są obsługiwane po zakończeniu przetwarzania bezczynnego.

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a>COleMessageFilter::OnMessagePending

Wywoływane przez platformę do przetwarzania komunikatów, gdy trwa wywołanie OLE.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskaźnik do oczekującej wiadomości.

### <a name="return-value"></a>Wartość zwracana

Nonzero na sukces; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Gdy aplikacja wywołująca oczekuje na zakończenie połączenia, struktura `OnMessagePending` wywołuje ze wskaźnikiem do oczekującej wiadomości. Domyślnie struktura wywołuje WM_PAINT komunikatów, dzięki czemu aktualizacje okna może wystąpić podczas wywołania, który zajmuje dużo czasu.

Musisz zarejestrować filtr wiadomości za pomocą wywołania, aby [zarejestrować,](#register) zanim stanie się aktywny.

## <a name="colemessagefilterregister"></a><a name="register"></a>COleMessageFilter::Zarejestruj się

Rejestruje filtr wiadomości z bibliotekami DLL systemu OLE.

```
BOOL Register();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero na sukces; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Filtr wiadomości nie ma wpływu, chyba że jest zarejestrowany w systemowych bibliotekach DLL. Zazwyczaj kod inicjowania aplikacji rejestruje filtr komunikatów aplikacji. Każdy inny filtr wiadomości zarejestrowany przez aplikację powinien zostać odwołany, zanim program zakończy się wywołaniem [Odwołania](#revoke).

Domyślny filtr wiadomości framework jest automatycznie rejestrowany podczas inicjowania i odwoływany po zakończeniu.

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a>COleMessageFilter::Odwołaj

Odwołuje poprzednią rejestrację wykonaną przez wywołanie [rejestracji](#register).

```
void Revoke();
```

### <a name="remarks"></a>Uwagi

Filtr wiadomości powinien zostać odwołany przed zakończeniem programu.

Domyślny filtr wiadomości, który jest tworzony i rejestrowany automatycznie przez platformę, jest również automatycznie odwoływany.

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a>COleMessageFilter::SetBusyReply

Ta funkcja ustawia "zajęty odpowiedzi aplikacji".

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>Parametry

*nBusyReply*<br/>
Wartość z `SERVERCALL` wyliczenia, która jest zdefiniowana w COMPOBJ. H. Może mieć jedną z następujących wartości:

- SERVERCALL_ISHANDLED Aplikacja może akceptować połączenia, ale może zakończyć się niepowodzeniem w przetwarzaniu określonego wywołania.

- SERVERCALL_REJECTED Aplikacja prawdopodobnie nigdy nie będzie w stanie przetworzyć połączenia.

- SERVERCALL_RETRYLATER Aplikacja jest tymczasowo w stanie, w którym nie może przetworzyć wywołania.

### <a name="remarks"></a>Uwagi

[BeginBusyState](#beginbusystate) i [EndBusyState](#endbusystate) funkcje kontroli aplikacji zajęty stan.

Gdy aplikacja została wykonana zajęty wywołaniem do `BeginBusyState`, odpowiada na wywołania z bibliotek DLL systemu `SetBusyReply`OLE z wartością określoną przez ostatnie ustawienie . Aplikacja wywołująca używa tej zajętej odpowiedzi, aby określić, jakie działania należy podjąć.

Domyślnie zajęta odpowiedź jest SERVERCALL_RETRYLATER. Ta odpowiedź powoduje, że aplikacja wywołująca ponowi próbę wywołania tak szybko, jak to możliwe.

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay

Określa, jak długo aplikacja wywołująca czeka na odpowiedź z wywoływanej aplikacji przed podjęciem dalszych działań.

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>Parametry

*nCzas*<br/>
Liczba milisekund opóźnienia oczekującego na wiadomość.

### <a name="remarks"></a>Uwagi

Ta funkcja działa w porozumieniu z [SetRetryReply](#setretryreply).

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a>COleMessageFilter::SetRetryReply

Określa akcję aplikacji wywołującej, gdy odbiera ona zajętą odpowiedź z wywoływaną aplikacją.

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>Parametry

*nRetryReply (Wyredukuj)*<br/>
Liczba milisekund między ponownych prób.

### <a name="remarks"></a>Uwagi

Gdy wywoływana aplikacja wskazuje, że jest zajęta, aplikacja wywołująca może zdecydować, aby poczekać, aż serwer nie jest już zajęty, aby ponowić próbę od razu lub ponowić próbę po określonym przedziale czasu. Może również podjąć decyzję o 60- całkowitego anulowania połączenia.

Odpowiedź wywołującego jest kontrolowana przez `SetRetryReply` funkcje i [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply`określa, jak długo aplikacja wywołująca powinna czekać między ponownych prób dla danego wywołania. `SetMessagePendingDelay`określa, jak długo aplikacja wywołująca czeka na odpowiedź z serwera przed podjęciem dalszych działań.

Zazwyczaj wartości domyślne są dopuszczalne i nie trzeba ich zmieniać. Struktura ponawia każde *wywołanie nRetryReply* milisekundy, dopóki wywołanie nie przejdzie lub opóźnienie oczekujące na wiadomość wygasło. Wartość 0 dla *nRetryReply* określa natychmiastowe ponowienie próby i - 1 określa anulowanie wywołania.

Po upływie opóźnienia oczekującego na wiadomość, OLE "zajęty okno dialogowe" (zobacz [COleBusyDialog)](../../mfc/reference/colebusydialog-class.md)jest wyświetlany, dzięki czemu użytkownik może wybrać, aby anulować lub ponowić próbę wywołania. Wywołanie [EnableBusyDialog,](#enablebusydialog) aby włączyć lub wyłączyć to okno dialogowe.

Gdy wiadomość klawiatury lub myszy jest w toku podczas połączenia i nawisł limit czasu połączenia (przekroczył opóźnienie oczekujące na wiadomość), zostanie wyświetlone okno dialogowe "nie odpowiadanie". Wywołanie [EnableNotRespondingDialog,](#enablenotrespondingdialog) aby włączyć lub wyłączyć to okno dialogowe. Zazwyczaj ten stan rzeczy wskazuje, że coś poszło nie tak, a użytkownik staje się niecierpliwy.

Gdy okna dialogowe są wyłączone, bieżąca odpowiedź "ponów próbę" jest zawsze używana do wywołań zajętych aplikacji.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
