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
ms.openlocfilehash: a06891f9413979895175808e109cc4abb7d75e09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224370"
---
# <a name="colemessagefilter-class"></a>Klasa COleMessageFilter

Zarządza współbieżnością wymaganą przez interakcję aplikacji OLE.

## <a name="syntax"></a>Składnia

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|Konstruuje `COleMessageFilter` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Umieszcza ją w stan zajęty.|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Włącza i wyłącza okno dialogowe, który jest wyświetlany, gdy wywoływana aplikacja jest zajęta.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Włącza i wyłącza okno dialogowe, który jest wyświetlany, gdy wywoływana aplikacja nie odpowiada.|
|[COleMessageFilter::EndBusyState](#endbusystate)|Kończy stan zajęty aplikacji.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Metoda wywoływana przez platformę, by przetwarzania komunikatów w trakcie wywołania interfejsu OLE.|
|[COleMessageFilter::Register](#register)|Rejestruje filtr komunikatu z OLE systemowych bibliotek DLL.|
|[COleMessageFilter::Revoke](#revoke)|Odwołuje filtr komunikatu rejestracji w systemie OLE biblioteki dll.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Określa zajęty aplikacji odpowiedź na wywołania interfejsu OLE.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Określa, jak długo aplikacja czeka na odpowiedź na wywołania interfejsu OLE.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|Określa odpowiedź aplikacji wywołującej zajęty aplikacji.|

## <a name="remarks"></a>Uwagi

`COleMessageFilter` Klasa jest przydatna w serwera i kontener aplikacje do edycji wizualnej oraz aplikacje automatyzacji OLE. Dla aplikacji serwera, które są wywoływane są tej klasy można wprowadzić aplikacji "zajęty" Aby wywołań przychodzących od innych aplikacji kontenera zostały anulowane lub ponowione później. Ta klasa można również określić działanie podejmowane przez aplikacji wywołującej, gdy wywoływana aplikacja jest zajęta.

Wspólne użycie jest dla aplikacji serwera wywołać [BeginBusyState](#beginbusystate) i [EndBusyState](#endbusystate) po byłoby niebezpieczne dla dokumentu lub innych OLE dostępne zniszczenia obiektu. Te wywołania są wykonywane w [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) podczas aktualizacji interfejsu użytkownika.

Domyślnie `COleMessageFilter` obiekt jest przydzielany, gdy aplikacja została zainicjowany. Może być pobierany za pomocą [afxolegetmessagefilter —](application-control.md#afxolegetmessagefilter).

Jest to klasa zaawansowane; rzadko potrzebne do pracy z nim bezpośrednio.

Aby uzyskać więcej informacji, zobacz artykuł [serwerów: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="beginbusystate"></a>  COleMessageFilter::BeginBusyState

Wywołaj tę funkcję, aby rozpocząć stan zajęty.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Uwagi

Działa w połączeniu z [EndBusyState](#endbusystate) kontrolować stan zajęty aplikacji. Funkcja [SetBusyReply](#setbusyreply) określa odpowiedź aplikacji do wywoływania aplikacji, gdy jest zajęty.

`BeginBusyState` i `EndBusyState` wywołania zwiększyć i zmniejszyć odpowiednio licznika, która określa, czy aplikacja jest zajęta. Na przykład dwa wywołania `BeginBusyState` i jedno wywołanie `EndBusyState` nadal powodować stan zajęty. Aby anulować stan zajęty, należy wywołać `EndBusyState` taką samą liczbę razy `BeginBusyState` została wywołana.

Domyślnie struktura wprowadza stan zajęty podczas przetwarzanie w stanie bezczynności, które jest wykonywane przez [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Gdy aplikacja obsługuje ON_COMMANDUPDATEUI powiadomienia, połączenia przychodzące są obsługiwane później, po zakończeniu przetwarzanie w stanie bezczynności.

##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter

Tworzy `COleMessageFilter` obiektu.

```
COleMessageFilter();
```

##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog

Włącza i wyłącza zajęty, okno dialogowe, które jest wyświetlany po upływie opóźnienie komunikatów oczekujących (zobacz [SetRetryReply](#setretryreply)) podczas wywołania interfejsu OLE.

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableBusy*<br/>
Określa, czy okno dialogowe "zajęty" jest włączona.

##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog

Włącza i wyłącza "nie odpowiada" okno dialogowe, które jest wyświetlane, jeśli oczekuje komunikatów klawiatury lub myszy podczas OLE wywołania i połączenie przekroczyło limit czasu.

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableNotResponding*<br/>
Określa, czy okno dialogowe "nie odpowiada" jest włączona.

##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState

Wywołaj tę funkcję, aby zakończyć stan zajęty.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Uwagi

Działa w połączeniu z [BeginBusyState](#beginbusystate) kontrolować stan zajęty aplikacji. Funkcja [SetBusyReply](#setbusyreply) określa odpowiedź aplikacji do wywoływania aplikacji, gdy jest zajęty.

`BeginBusyState` i `EndBusyState` wywołania zwiększyć i zmniejszyć odpowiednio licznika, która określa, czy aplikacja jest zajęta. Na przykład dwa wywołania `BeginBusyState` i jedno wywołanie `EndBusyState` nadal powodować stan zajęty. Aby anulować stan zajęty, należy wywołać `EndBusyState` taką samą liczbę razy `BeginBusyState` została wywołana.

Domyślnie struktura wprowadza stan zajęty podczas przetwarzanie w stanie bezczynności, które jest wykonywane przez [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Gdy aplikacja obsługuje powiadomienia ON_UPDATE_COMMAND_UI, połączenia przychodzące są obsługiwane po zakończeniu przetwarzanie w stanie bezczynności.

##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending

Metoda wywoływana przez platformę, by przetwarzania komunikatów w trakcie wywołania interfejsu OLE.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskaźnik do oczekujących komunikatów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera w przypadku powodzenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Gdy aplikacja wywołująca Trwa oczekiwanie na połączenie, należy wykonać, struktura wywołuje `OnMessagePending` ze wskaźnikiem do oczekujących komunikatów. Domyślnie struktura wywołuje komunikaty WM_PAINT tak, aby aktualizacje okna może wystąpić podczas wywołania, która jest zbyt długi czas.

Filtr komunikatu należy zarejestrować za pomocą wywołania [zarejestrować](#register) przed może zostać uaktywniony.

##  <a name="register"></a>  COleMessageFilter::Register

Rejestruje filtr komunikatu z OLE systemowych bibliotek DLL.

```
BOOL Register();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera w przypadku powodzenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Filtr komunikatu nie ma wpływu, chyba że jest on zarejestrowany w systemie biblioteki dll. Zazwyczaj aplikacji kod inicjowania rejestruje filtr komunikatów aplikacji. Powinny zostać odwołane innych filtr komunikatów, zarejestrowane przez aplikację, zanim program zakończy się przez wywołanie [odwołać](#revoke).

Filtr wiadomości domyślnej struktury jest automatycznie rejestrowane podczas inicjowania i odwołane na zakończenie.

##  <a name="revoke"></a>  COleMessageFilter::Revoke

Odwołuje poprzednią rejestrację wykonywana przez wywołanie [zarejestrować](#register).

```
void Revoke();
```

### <a name="remarks"></a>Uwagi

Filtr komunikatu powinny zostać odwołane, zanim program zakończy działanie.

Domyślny filtr komunikatów, który jest utworzony i zarejestrowany automatycznie przez platformę, jest również automatycznie odwoływane.

##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply

Funkcja ta ustawia aplikacji "zajęty odpowiedzi."

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>Parametry

*nBusyReply*<br/>
Wartość z zakresu od `SERVERCALL` wyliczenia, która jest zdefiniowana w COMPOBJ. H. Może mieć jeden z następujących wartości:

- SERVERCALL_ISHANDLED aplikacja może akceptować połączeń, ale może zakończyć się niepowodzeniem podczas przetwarzania konkretnego wywołania.

- SERVERCALL_REJECTED aplikacji prawdopodobnie będzie nigdy nie można przetworzyć wywołania.

- SERVERCALL_RETRYLATER aplikacji jest tymczasowo w stanie, w której nie można przetworzyć wywołania.

### <a name="remarks"></a>Uwagi

[BeginBusyState](#beginbusystate) i [EndBusyState](#endbusystate) funkcje kontrolować stan zajęty aplikacji.

Gdy aplikacja została wprowadzona zagęszczoną w przypadku wywołania `BeginBusyState`, odpowiada na wywołania z OLE systemowych bibliotek DLL z wartością określona przez ostatnie ustawienie `SetBusyReply`. Aplikacja wywołująca używa odpowiedź zajęty, aby określić jaką akcję należy podjąć.

Domyślnie zajęty odpowiedzi jest SERVERCALL_RETRYLATER. Odpowiedź powoduje, że aplikacja wywołująca ponowić próbę połączenia możliwie najszybciej.

##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay

Określa, jak długo aplikacja wywołująca czeka na odpowiedź z aplikacji o nazwie, przed podjęciem dalszych działań.

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>Parametry

*nTimeout*<br/>
Liczba milisekund dla opóźnienia oczekujących komunikatów.

### <a name="remarks"></a>Uwagi

Ta funkcja działa w połączeniu z [SetRetryReply](#setretryreply).

##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply

Określa akcję aplikacji wywołującej, po odebraniu zajęty odpowiedzi z aplikacji o nazwie.

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>Parametry

*nRetryReply*<br/>
Liczba milisekund między kolejnymi próbami.

### <a name="remarks"></a>Uwagi

W przypadku aplikacji o nazwie wskazuje, że jest zajęta, aplikacja wywołująca może zdecydować o poczekaj, aż serwer nie jest już zajęty, aby ponowić próbę następnie od razu lub spróbuj ponownie po upływie określonego czasu. Mogą również wybrać je anulować całkowicie.

Odpowiedź wywołującego jest kontrolowany przez funkcje `SetRetryReply` i [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply` Określa, jak długo aplikacja wywołująca powinna czekać między kolejnymi próbami dla danego wywołania. `SetMessagePendingDelay` Określa, jak długo aplikacja wywołująca czeka na odpowiedź z serwera przed podjęciem dalszych działań.

Zazwyczaj ustawienia domyślne są dopuszczalne i nie muszą zostać zmienione. Struktura ponawia próbę wywołania co *nRetryReply* milisekund do momentu wywołania przechodzi przez lub opóźnienia oczekujących komunikatów utracił ważność. Wartość 0 dla *nRetryReply* określa natychmiastowe ponowienie próby i - 1, określa anulowanie wywołania.

Gdy opóźnienie komunikatów oczekujących utracił ważność, OLE "zajęty, okno dialogowe" (zobacz [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) są wyświetlane tak, że użytkownik może wybrać anulować lub ponowić wywołanie. Wywołaj [EnableBusyDialog](#enablebusydialog) Aby włączyć lub wyłączyć tego okna dialogowego.

Gdy oczekuje komunikatów klawiatury lub myszy podczas wywołania i połączenie przekroczyło limit czasu (przekroczony opóźnienia oczekujących komunikatów), wyświetlane jest okno dialogowe "nie odpowiada". Wywołaj [EnableNotRespondingDialog](#enablenotrespondingdialog) Aby włączyć lub wyłączyć tego okna dialogowego. Zwykle ten stan spraw wskazuje, że Niestety, wystąpił problem, i użytkownik otrzymuje cierpliwy.

Okna dialogowe są wyłączone, bieżący "Ponów próbę wykonania odpowiedzi" jest zawsze używana dla wywołań do aplikacji zajęty.

## <a name="see-also"></a>Zobacz także

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
