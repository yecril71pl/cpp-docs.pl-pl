---
title: "CSocket — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
dev_langs: C++
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ae8a30697783b478e9ffdb1c247f52d7b9f2ac2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csocket-class"></a>CSocket — klasa
Pochodną `CAsyncSocket`dziedziczy jego hermetyzacja interfejsu API systemu Windows Sockets i reprezentuje wyższym poziomie abstrakcji niż `CAsyncSocket` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSocket : public CAsyncSocket  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSocket::CSocket](#csocket)|Konstruuje `CSocket` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSocket::Attach](#attach)|Dołącza **GNIAZDA** dojścia do `CSocket` obiektu.|  
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Anuluje blokowania połączenie, które jest obecnie w toku.|  
|[CSocket::Create](#create)|Tworzy gniazda.|  
|[CSocket::FromHandle](#fromhandle)|Zwraca wskaźnik do `CSocket` obiekt, na podstawie **GNIAZDA** obsługi.|  
|[CSocket::IsBlocking](#isblocking)|Określa, czy wywołanie blokowania jest w toku.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSocket::OnMessagePending](#onmessagepending)|Wywołuje się, by proces komunikatów oczekujących podczas oczekiwania na blokadzie wywołania do wykonania.|  
  
## <a name="remarks"></a>Uwagi  
 `CSocket`działa z klasami `CSocketFile` i `CArchive` do zarządzania wysyłania i odbierania danych.  
  
 A `CSocket` obiekt zapewnia także blokuje, co jest niezbędne do działania synchroniczne `CArchive`. Blokowanie funkcje, takie jak `Receive`, `Send`, `ReceiveFrom`, `SendTo`, i `Accept` (wszystkie odziedziczone z `CAsyncSocket`), nie zwracać `WSAEWOULDBLOCK` błąd w `CSocket`. Zamiast tego należy te funkcje zaczekać, aż do zakończenia operacji. Ponadto wywołanie oryginalnego zostanie zamknięty z powodu błędu `WSAEINTR` Jeśli `CancelBlockingCall` jest wywoływana, gdy jeden z tych funkcji jest zablokowana.  
  
 Umożliwia `CSocket` obiekt, należy wywołać konstruktora, następnie wywołaj `Create` utworzyć podstawową `SOCKET` obsługi (typu `SOCKET`). Parametry domyślne `Create` utworzyć gniazda strumienia, ale jeśli nie używasz gniazda z `CArchive` obiektu, można określić parametr zamiast tego utworzyć gniazda datagram lub powiązania do określonego portu można utworzyć gniazda serwera. Połączenie gniazda klienta przy użyciu `Connect` po stronie klienta i `Accept` po stronie serwera. Następnie utwórz `CSocketFile` obiektów i powiązać ją do `CSocket` obiektu w `CSocketFile` konstruktora. Następnie należy utworzyć `CArchive` obiekt do wysyłania i jeden do odbierania danych (w razie potrzeby), następnie skojarzyć je z `CSocketFile` obiektu w `CArchive` konstruktora. Po zakończeniu komunikacji zniszczyć `CArchive`, `CSocketFile`, i `CSocket` obiektów. `SOCKET` — Typ danych jest opisana w artykule [Windows Sockets: tła](../../mfc/windows-sockets-background.md).  
  
 Jeśli używasz `CArchive` z `CSocketFile` i `CSocket`, może wystąpić sytuacja, gdy `CSocket::Receive` wprowadza pętlę (przez `PumpMessages(FD_READ)`) oczekiwania na żądanej ilości bajtów. Wynika to z faktu Windows sockets Zezwalaj tylko jedno wywołanie ustawiania dla jednego powiadomienia FD_READ, ale `CSocketFile` i `CSocket` Zezwalaj na wiele wywołań otrzymanych na FD_READ. Jeśli otrzymasz FD_READ, gdy nie ma żadnych danych do odczytu, aplikacja zawiesza się. Jeśli nigdy nie otrzymasz innej FD_READ, aplikacja przestaje komunikacji za pośrednictwem gniazda.  
  
 Można rozwiązać ten problem w następujący sposób. W `OnReceive` metody klasy gniazda, wywołanie `CAsyncSocket::IOCtl(FIONREAD, ...)` przed wywołaniem `Serialize` metody klasy wiadomości gdy oczekiwane dane mają być odczytane z gniazda jest większy niż jeden pakiet TCP (maksymalna jednostka transmisji ze średnim sieci zazwyczaj co najmniej 1096 bajtów). Jeśli rozmiar danych dostępne jest mniejsza niż jest to potrzebne, poczekaj, aż wszystkie dane odebrania, a następnie uruchomienie operacji odczytu.  
  
 W poniższym przykładzie `m_dwExpected` jest przybliżoną liczbę bajtów, które użytkownik zamierza odbierania. Zakłada się, że należy zadeklarować go w innym miejscu w kodzie.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]  
  
> [!NOTE]
>  Korzystając z gniazda MFC w dodatkowej wątków w aplikacji statycznie połączone MFC, należy wywołać `AfxSocketInit` w każdym wątku, który używa sockets zainicjować biblioteki gniazd. Domyślnie `AfxSocketInit` jest wywoływany tylko w podstawowym wątku.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets w MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: jak gniazda z archiwami pracy](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: Sekwencja operacji](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: przykład gniazd korzystających z archiwów](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxsock.h  
  
##  <a name="attach"></a>CSocket::Attach  
 Wywołanie tej funkcji Członkowskich, aby dołączyć `hSocket` dojścia do `CSocket` obiektu.  
  
```  
BOOL Attach(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parametry  
 `hSocket`  
 Zawiera dojścia do gniazda.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie.  
  
### <a name="remarks"></a>Uwagi  
 **GNIAZDA** dojścia jest przechowywany w obiekcie [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) element członkowski danych.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]  
  
 [!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]  
  
##  <a name="cancelblockingcall"></a>CSocket::CancelBlockingCall  
 Wywołanie tej funkcji elementu członkowskiego, aby anulować blokowania wywołań w toku.  
  
```  
void CancelBlockingCall();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja umożliwia anulowanie oczekujących operacji blokowania, dla tego gniazda. Oryginalny blokowania wywołanie zakończy się tak szybko, jak to możliwe z powodu błędu **WSAEINTR**.  
  
 W przypadku zablokowania **Connect** operacji implementacji usługi Windows Sockets spowoduje przerwanie blokowania wywołania jak to możliwe, ale może nie być możliwe w dla zasobów gniazda do zwolnienia aż do zakończenia połączenia (i następnie został zresetowany) lub upłynął limit czasu. To może być widoczny tylko wtedy, gdy aplikacja próbuje natychmiast, aby otworzyć nowe gniazdo (jeśli gniazda nie są dostępne) lub nawiązywania połączenia z tym samym węzłem równorzędnym.  
  
 Anulowanie żadnej operacji innych niż **Akceptuj** można pozostawić gniazdo w stanie nieokreślonym. Jeśli aplikacja anuluje operacji blokowania na gnieździe, jedyną operacją, która aplikacja może zależeć od możliwość wykonania w gnieździe jest wywołanie **Zamknij**, mimo że inne operacje może działać na niektórych Windows Sockets implementacje. Przenośność maksymalną wymaganych aplikacji, musi być zachować ostrożność i nie zależą od operacji po anulowania.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="create"></a>CSocket::Create  
 Wywołanie **Utwórz** funkcji członkowskiej po konstruowania obiektu gniazda, aby utworzyć gniazda systemu Windows i dołączyć go.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nSocketPort`  
 Określonego portu do użycia z gniazda lub 0, jeśli chcesz MFC, aby wybrać port.  
  
 `nSocketType`  
 **SOCK_STREAM** lub **SOCK_DGRAM**.  
  
 `lpszSocketAddress`  
 Wskaźnik do ciąg zawierający adres sieciowy połączone gniazdo, liczbę kropkami, na przykład "128.56.22.8". Przekazywanie **NULL** ciągu dla tego parametru oznacza **CSocket —** wystąpienia powinna nasłuchiwać aktywność klienta na wszystkich interfejsach sieciowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie `GetLastError`.  
  
### <a name="remarks"></a>Uwagi  
 **Utwórz** następnie wywołuje **powiązać** można powiązać gniazda do określonego adresu. Obsługiwane są następujące typy gniazda:  
  
- **SOCK_STREAM** zapewnia sekwencjonowania, strumienie bajtów niezawodne, dwukierunkowe, opartego na połączeniach. Używa protokołu Transmission Control Protocol (TCP) dla rodziny adresu internetowego.  
  
- **SOCK_DGRAM** obsługuje datagramy są bez połączenia, zawodne buforów stała długość maksymalną (zazwyczaj jest to mała). Używa protokołu UDP (User Datagram) dla systemów z rodziny adresu internetowego. Aby użyć tej opcji, nie mogą używać gniazda z `CArchive` obiektu.  
  
    > [!NOTE]
    >  **Akceptuj** funkcji członkowskiej przyjmuje odwołanie do nowy, pusty `CSocket` obiektu jako jego parametr. Należy utworzyć ten obiekt przed wywołaniem **Akceptuj**. Należy pamiętać, że jeśli ten obiekt gniazda trafia zakresu, zamyka połączenie. Nie wywołuj **Utwórz** dla tego nowego obiektu gniazda.  
  
 Aby uzyskać więcej informacji na temat gniazd strumienia i datagram, zobacz artykuły [Windows Sockets: tła](../../mfc/windows-sockets-background.md), [Windows Sockets: porty i adresy gniazd](../../mfc/windows-sockets-ports-and-socket-addresses.md), i [Windows Sockets: przy użyciu Gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="csocket"></a>CSocket::CSocket  
 Konstruuje `CSocket` obiektu.  
  
```  
CSocket();
```  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu konstrukcji, należy wywołać **Utwórz** funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="fromhandle"></a>CSocket::FromHandle  
 Zwraca wskaźnik do `CSocket` obiektu.  
  
```  
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parametry  
 `hSocket`  
 Zawiera dojścia do gniazda.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CSocket` obiekt, lub **NULL** w przypadku nie `CSocket` obiekt dołączony do `hSocket`.  
  
### <a name="remarks"></a>Uwagi  
 Gdy **GNIAZDA** obsługi, jeśli `CSocket` obiekt nie jest dołączony do uchwytu, zwraca funkcja członkowska **NULL** i nie tworzy tymczasowy obiekt.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="isblocking"></a>CSocket::IsBlocking  
 Wywołaj tę funkcję elementu członkowskiego, aby określić, czy wywołanie blokowania jest w toku.  
  
```  
BOOL IsBlocking();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli blokuje gniazda; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="onmessagepending"></a>CSocket::OnMessagePending  
 Przesłonić tę funkcję elementu członkowskiego, aby znaleźć określone wiadomości z systemu Windows i zareagować w Twoje gniazda.  
  
```  
virtual BOOL OnMessagePending();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli komunikat został obsłużony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jest to zaawansowane możliwym do zastąpienia.  
  
 Wywołania framework `OnMessagePending` podczas gniazda jest przekazywania komunikatów systemu Windows, aby zapewnić możliwość postępowania w przypadku wiadomości znaczenie dla aplikacji. Przykłady użycia `OnMessagePending`, zapoznaj się z artykułem [Windows Sockets: wyprowadzanie z klas gniazd](../../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Casyncsocket — klasa](../../mfc/reference/casyncsocket-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Casyncsocket — klasa](../../mfc/reference/casyncsocket-class.md)   
 [Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
