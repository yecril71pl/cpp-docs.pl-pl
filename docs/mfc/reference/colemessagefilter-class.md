---
title: Klasa COleMessageFilter | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85161e7f3dd752c6df27afedf6276f8823e7ec6e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="colemessagefilter-class"></a>Klasa COleMessageFilter
Zarządza współbieżności wymagane przez interakcji w aplikacji OLE.  
  
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
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Umieszcza aplikacji w stanie zajęty.|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Włącza i wyłącza okno dialogowe, które pojawia się po nazwie aplikacja jest zajęta.|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Włącza i wyłącza okno dialogowe, który jest wyświetlany, gdy nie odpowiada nazwie aplikacji.|  
|[COleMessageFilter::EndBusyState](#endbusystate)|Kończy zajęty stan aplikacji.|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Metoda wywoływana przez platformę do przetwarzania komunikatów, gdy wywołanie OLE jest w toku.|  
|[COleMessageFilter::Register](#register)|Rejestruje filtr komunikatu w systemie OLE biblioteki dll.|  
|[COleMessageFilter::Revoke](#revoke)|Wycofanie filtr komunikatu rejestracji w systemie OLE biblioteki dll.|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Określa zajęty aplikacji odpowiedź na wywołania OLE.|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Określa, jak długo aplikacja oczekuje na odpowiedź na wywołania OLE.|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|Określa odpowiedź aplikacja wywołująca aplikację zajęty.|  
  
## <a name="remarks"></a>Uwagi  
 `COleMessageFilter` Klasy jest przydatne w visual edycji aplikacje kontenera i serwera, a także aplikacje automatyzacji OLE. Dla aplikacji serwerowych, które są wywoływane tej klasy można zastosować "zajęty", aby przychodzące wywołania z innych aplikacji kontenera są anulowane lub ponowione później. Ta klasa można również określić działanie podejmowane przez aplikacja wywołująca po nazwie aplikacja jest zajęta.  
  
 Użycie wspólnych jest dla aplikacji serwera wywołać [BeginBusyState](#beginbusystate) i [EndBusyState](#endbusystate) po jest niebezpieczne dla dokumentu lub innych dostępny obiekt OLE mają zostać zniszczone. Tych wywołań w [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) podczas aktualizowania interfejsu użytkownika.  
  
 Domyślnie `COleMessageFilter` obiekt został przydzielony po zainicjowaniu aplikacji. Mogą być pobierane z [afxolegetmessagefilter —](application-control.md#afxolegetmessagefilter).  
  
 Jest to klasa zaawansowane; rzadko występuje konieczność pracę z nią bezpośrednio.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="beginbusystate"></a>  COleMessageFilter::BeginBusyState  
 Wywołanie tej funkcji, aby rozpocząć stanu zajętości.  
  
```  
virtual void BeginBusyState();
```  
  
### <a name="remarks"></a>Uwagi  
 Działa w połączeniu z [EndBusyState](#endbusystate) kontrolować stan zajęty aplikacji. Funkcja [SetBusyReply](#setbusyreply) określa odpowiedź aplikacji do wywoływania aplikacji, gdy jest zajęty.  
  
 `BeginBusyState` i `EndBusyState` wywołań zwiększyć i zmniejszyć, licznik, który określa, czy aplikacja jest zajęta. Na przykład dwa wywołań `BeginBusyState` i jedno wywołanie `EndBusyState` nadal doprowadzi do stanu zajętości. Aby anulować zajęty stanu, należy wywołać `EndBusyState` taką samą liczbę razy `BeginBusyState` została wywołana.  
  
 Domyślnie platformę przechodzi do stanu zajętości podczas przetwarzanie w stanie bezczynności, które jest wykonywane przez [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Gdy aplikacja jest obsługa **ON_COMMANDUPDATEUI** powiadomienia, połączenia przychodzące są obsługiwane później, po zakończeniu przetwarzanie w stanie bezczynności.  
  
##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter  
 Tworzy `COleMessageFilter` obiektu.  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog  
 Włącza i wyłącza okna dialogowego zajęty, które jest wyświetlane, gdy wygaśnie opóźnienie komunikatów oczekujących (zobacz [SetRetryReply](#setretryreply)) podczas wywołania OLE.  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnableBusy*  
 Określa, czy okno dialogowe "zajęty" jest włączona.  
  
##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog  
 Włącza i wyłącza okno dialogowe "nie odpowiada", która jest wyświetlana, jeśli trwa oczekiwanie na wiadomość klawiatury lub myszy podczas OLE wywołania i wywołania został przekroczony.  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnableNotResponding*  
 Określa, czy okno dialogowe "nie odpowiada" jest włączona.  
  
##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState  
 Wywołanie tej funkcji do końca stanu zajętości.  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>Uwagi  
 Działa w połączeniu z [BeginBusyState](#beginbusystate) kontrolować stan zajęty aplikacji. Funkcja [SetBusyReply](#setbusyreply) określa odpowiedź aplikacji do wywoływania aplikacji, gdy jest zajęty.  
  
 `BeginBusyState` i `EndBusyState` wywołań zwiększyć i zmniejszyć, licznik, który określa, czy aplikacja jest zajęta. Na przykład dwa wywołań `BeginBusyState` i jedno wywołanie `EndBusyState` nadal doprowadzi do stanu zajętości. Aby anulować zajęty stanu, należy wywołać `EndBusyState` taką samą liczbę razy `BeginBusyState` została wywołana.  
  
 Domyślnie platformę przechodzi do stanu zajętości podczas przetwarzanie w stanie bezczynności, które jest wykonywane przez [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Gdy aplikacja jest obsługa `ON_UPDATE_COMMAND_UI` powiadomienia, połączenia przychodzące są obsługiwane, po zakończeniu przetwarzanie w stanie bezczynności.  
  
##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending  
 Metoda wywoływana przez platformę do przetwarzania komunikatów, gdy wywołanie OLE jest w toku.  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Wskaźnik do oczekujących komunikatów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Gdy aplikacja wywołująca oczekuje na połączenie, należy wykonać, struktura wywołuje `OnMessagePending` za pomocą wskaźnika do oczekujących komunikatów. Domyślnie wywołuje platformę `WM_PAINT` komunikaty, dzięki czemu aktualizacji okna może wystąpić podczas wywołania, która jest zbyt długi czas.  
  
 Filtr komunikatu musi zarejestrować za pomocą wywołania [zarejestrować](#register) przed może zostać uaktywniony.  
  
##  <a name="register"></a>  COleMessageFilter::Register  
 Rejestruje filtr komunikatu w systemie OLE biblioteki dll.  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Filtr komunikatu nie ma znaczenia, chyba że został on zarejestrowany na systemowej biblioteki dll. Zazwyczaj kod inicjujący aplikacji rejestruje filtr komunikatów aplikacji. Powinny zostać odwołane innych filtr komunikatu, zarejestrowane przez aplikację, zanim program zakończy przez wywołanie do [odwołać](#revoke).  
  
 Filtr komunikatu domyślnej struktury jest automatycznie zarejestrowane podczas inicjowania i odwołane po zakończeniu.  
  
##  <a name="revoke"></a>  COleMessageFilter::Revoke  
 Wycofanie poprzedniej rejestracji wykonywane przez wywołanie do [zarejestrować](#register).  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Uwagi  
 Zanim program zakończy, powinny zostać odwołane filtr komunikatu.  
  
 Domyślny filtr komunikat, który jest tworzony i automatycznie zarejestrowane przez platformę, automatycznie został odwołany.  
  
##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply  
 Ta funkcja ustawia aplikacji "zajęty odpowiedzi."  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>Parametry  
 *nBusyReply*  
 Wartość z zakresu od `SERVERCALL` wyliczenia, która jest zdefiniowana w COMPOBJ. H. Może mieć jeden z następujących wartości:  
  
- **SERVERCALL_ISHANDLED** aplikacja może akceptować połączeń, ale może zakończyć się niepowodzeniem podczas przetwarzania określonego połączenia.  
  
- **SERVERCALL_REJECTED** aplikacja prawdopodobnie nigdy nie będzie mógł przetworzyć wywołania.  
  
- **SERVERCALL_RETRYLATER** aplikacji jest tymczasowo w stanie, w którym nie można przetworzyć wywołania.  
  
### <a name="remarks"></a>Uwagi  
 [BeginBusyState](#beginbusystate) i [EndBusyState](#endbusystate) funkcje kontroli aplikacji stanu zajętości.  
  
 Gdy wniosku zajęty wywołanie `BeginBusyState`, odpowiada wywołania z bibliotek DLL systemu OLE z wartością określona przez ustawienie ostatniego `SetBusyReply`. Aplikacja wywołująca używa zajęty odpowiedź do określenia, jakie działanie do wykonania.  
  
 Domyślnie jest zajęty odpowiedzi **SERVERCALL_RETRYLATER**. Odpowiedź ta powoduje, że aplikacja wywołująca ponowić próbę połączenia możliwie jak.  
  
##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay  
 Określa, jak długo aplikacja wywołująca czeka na odpowiedź o nazwie aplikacji przed podjęciem dalszych działań.  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>Parametry  
 `nTimeout`  
 Wyrażony w milisekundach czas opóźnienia oczekujących komunikatów.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja działa w połączeniu z [SetRetryReply](#setretryreply).  
  
##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply  
 Określa akcję aplikacja wywołująca po odebraniu odpowiedzi zajęty z aplikacji o nazwie.  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nRetryReply`  
 Liczba milisekund między kolejnymi próbami.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku aplikacji o nazwie oznacza, że jest zajęty, aplikacja wywołująca może zadecydować o poczekaj, aż serwer nie jest już zajęty, aby ponowić próbę teraz lub spróbuj ponownie po upływie określonego czasu. Może również zdecydować je anulować całkowicie.  
  
 Odpowiedź wywołującego jest kontrolowany przez funkcje `SetRetryReply` i [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply` Określa, jak długo aplikacja wywołująca powinna czekać między kolejnymi próbami dla danego połączenia. `SetMessagePendingDelay` Określa, jak długo aplikacja wywołująca czeka na odpowiedź z serwera przed podjęciem dalszych działań.  
  
 Zwykle wartości domyślne są dozwolone i nie muszą zostać zmienione. Platformę ponowi próbę połączenia co `nRetryReply` milisekund, dopóki wywołania przechodzi przez lub opóźnienia komunikatów oczekujących utracił ważność. Wartość 0 dla `nRetryReply` określa natychmiastowego ponawiania i - 1 oznacza anulowania wywołania.  
  
 Gdy opóźnienie komunikatów oczekujących utracił ważność, OLE "zajęty okna dialogowego" (zobacz [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) jest wyświetlana, dzięki czemu użytkownik może anulować lub ponów próbę połączenia. Wywołanie [EnableBusyDialog](#enablebusydialog) Aby włączyć lub wyłączyć tego okna dialogowego.  
  
 Gdy oczekuje komunikatów klawiatury lub myszy podczas wywołania i wywołania upłynął limit czasu (przekroczony opóźnienie komunikatów oczekujących), wyświetlane jest okno dialogowe "nie odpowiada". Wywołanie [EnableNotRespondingDialog](#enablenotrespondingdialog) Aby włączyć lub wyłączyć tego okna dialogowego. Zwykle ten stan spraw wskazuje, że coś niepowodzenia, i użytkownik otrzymuje będzie cierpliwy.  
  
 Okna dialogowe są wyłączone, bieżący "Ponów odpowiedzi" jest zawsze używana w przypadku wywołań zajęty aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
