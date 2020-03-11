---
title: Klasa CSocket
ms.date: 11/04/2016
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
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854562"
---
# <a name="csocket-class"></a>Klasa CSocket

Wynika z `CAsyncSocket`, dziedziczy hermetyzację interfejsu API Windows Sockets i reprezentuje wyższy poziom abstrakcji niż obiekt `CAsyncSocket`.

## <a name="syntax"></a>Składnia

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSocket:: CSocket](#csocket)|Konstruuje obiekt `CSocket`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSocket:: Attach](#attach)|Dołącza uchwyt gniazda do `CSocket` obiektu.|
|[CSocket:: CancelBlockingCall](#cancelblockingcall)|Anuluje wywołanie blokujące, które jest aktualnie w toku.|
|[CSocket:: Create](#create)|Tworzy gniazdo.|
|[CSocket:: FromHandle](#fromhandle)|Zwraca wskaźnik do obiektu `CSocket`, w którym znajduje się uchwyt gniazda.|
|[CSocket:: isblocking](#isblocking)|Określa, czy wywołanie blokujące jest w toku.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CSocket:: OnMessagePending](#onmessagepending)|Wywołuje się, by przetworzyć oczekujące komunikaty podczas oczekiwania na ukończenie wywołania blokującego.|

## <a name="remarks"></a>Uwagi

`CSocket` współpracuje z klasami `CSocketFile` i `CArchive` w celu zarządzania wysyłaniem i otrzymywaniem danych.

Obiekt `CSocket` zapewnia również blokowanie, co jest niezbędne do synchronicznej operacji `CArchive`. Funkcje blokowania, takie jak `Receive`, `Send`, `ReceiveFrom`, `SendTo`i `Accept` (wszystkie dziedziczone z `CAsyncSocket`) nie zwracają błędu `WSAEWOULDBLOCK` w `CSocket`. Zamiast tego funkcje te czekają na zakończenie operacji. Ponadto oryginalne wywołanie zakończy się z błędem WSAEINTR, jeśli `CancelBlockingCall` jest wywoływana podczas blokowania jednej z tych funkcji.

Aby użyć obiektu `CSocket`, Wywołaj konstruktora, a następnie Wywołaj `Create`, aby utworzyć podstawowy uchwyt gniazda (gniazdo typu). Domyślne parametry `Create` tworzenia gniazda strumienia, ale jeśli nie korzystasz z gniazda z obiektem `CArchive`, możesz określić parametr, aby utworzyć gniazdo datagramu, lub powiązać z określonym portem, aby utworzyć gniazdo serwera. Połącz się z gniazdem klienckim przy użyciu `Connect` po stronie klienta i `Accept` po stronie serwera. Następnie Utwórz obiekt `CSocketFile` i skojarz go z obiektem `CSocket` w konstruktorze `CSocketFile`. Następnie Utwórz obiekt `CArchive` do wysłania i jeden do odebrania danych (w razie potrzeby), a następnie skojarz je z obiektem `CSocketFile` w konstruktorze `CArchive`. Po zakończeniu komunikacji należy zniszczyć obiekty `CArchive`, `CSocketFile`i `CSocket`. Typ danych gniazda został opisany w artykule [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

W przypadku korzystania z `CArchive` z `CSocketFile` i `CSocket`może wystąpić sytuacja, w której `CSocket::Receive` wprowadza pętlę (przez `PumpMessages(FD_READ)`) oczekiwanie na żądaną ilość bajtów. Wynika to z faktu, że usługa Windows Sockets zezwala tylko na jedno wywołanie odbierania na FD_READ powiadomienia, ale `CSocketFile` i `CSocket` zezwolić na wiele wywołań odbierania na FD_READ. Jeśli otrzymasz FD_READ, gdy nie ma danych do odczytania, aplikacja zawiesza się. Jeśli nie otrzymasz kolejnej FD_READ, aplikacja przestanie komunikować się za pośrednictwem gniazda.

Ten problem można rozwiązać w następujący sposób. W metodzie `OnReceive` klasy Socket Wywołaj `CAsyncSocket::IOCtl(FIONREAD, ...)` przed wywołaniem `Serialize` metody klasy wiadomości, gdy oczekiwane dane, które mają zostać odczytane z gniazda, przekraczają rozmiar jednego pakietu TCP (maksymalna jednostka transmisji nośnika sieciowego, zwykle co najmniej 1096 bajtów). Jeśli rozmiar dostępnych danych jest mniejszy niż jest to konieczne, poczekaj na odebranie wszystkich danych, a następnie uruchom operację odczytu.

W poniższym przykładzie `m_dwExpected` to Przybliżona liczba bajtów, które użytkownik oczekuje na odebranie. Przyjęto założenie, że deklarujesz go w innym miejscu w kodzie.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  W przypadku korzystania z gniazd MFC w wątkach pomocniczych w statycznie połączonej aplikacji MFC należy wywołać `AfxSocketInit` w każdym wątku, który używa gniazd do inicjowania bibliotek gniazd. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku podstawowym.

Aby uzyskać więcej informacji, zobacz [Windows Sockets w MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: jak działają gniazda z archiwami](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: Sekwencja operacji](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: przykład gniazd korzystających z archiwów](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AfxSock. h

##  <a name="attach"></a>CSocket:: Attach

Wywołaj tę funkcję elementu członkowskiego, aby dołączyć dojście `hSocket` do obiektu `CSocket`.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Zawiera uchwyt do gniazda.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie.

### <a name="remarks"></a>Uwagi

Uchwyt gniazda jest przechowywany w elemencie członkowskim danych [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) obiektu.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>CSocket:: CancelBlockingCall

Wywołaj tę funkcję elementu członkowskiego, aby anulować wywołanie blokujące w toku.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Uwagi

Ta funkcja anuluje wszystkie oczekujące operacje blokowania dla tego gniazda. Oryginalne wywołanie blokowania zostanie zakończone najszybciej, jak to możliwe, z błędem WSAEINTR.

W przypadku blokowania operacji `Connect`, implementacja Windows Sockets zakończy wywołanie blokowania najszybciej, jak to możliwe, ale może nie być możliwe do zwolnienia zasobów gniazda do momentu zakończenia połączenia (a następnie zresetowania) lub przekroczenia limitu czasu. Jest to możliwe tylko wtedy, gdy aplikacja natychmiast próbuje otworzyć nowe gniazdo (jeśli nie są dostępne żadne gniazda) lub połączyć się z tym samym węzłem równorzędnym.

Anulowanie operacji innych niż `Accept` może opuścić gniazdo w nieokreślonym stanie. Jeśli aplikacja anuluje operację blokowania w gnieździe, jedyną operacją, która może być możliwa do wykonania w gnieździe, jest wywołanie do `Close`, chociaż inne operacje mogą działać na niektórych implementacjach Windows Sockets. Jeśli życzy sobie maksymalną przenośność aplikacji, należy zachować ostrożność, aby nie zależeć od wykonywania operacji po anulowaniu.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>CSocket:: Create

Wywołaj funkcję **Utwórz** element członkowski po utworzeniu obiektu gniazda, aby utworzyć gniazdo systemu Windows i dołączyć go.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Konkretny port do użycia z gniazdem lub 0, jeśli chcesz, aby MFC wybierał port.

*nSocketType*<br/>
SOCK_STREAM lub SOCK_DGRAM.

*lpszSocketAddress*<br/>
Wskaźnik do ciągu zawierającego adres sieciowy połączonego gniazda, numer kropkowany, taki jak "128.56.22.8". Przekazywanie ciągu o wartości NULL dla tego parametru wskazuje, że wystąpienie `CSocket` powinno nasłuchiwać aktywności klienta na wszystkich interfejsach sieciowych.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a konkretny kod błędu można pobrać, wywołując `GetLastError`.

### <a name="remarks"></a>Uwagi

`Create` następnie wywoła `Bind`, aby powiązać gniazdo z określonym adresem. Obsługiwane są następujące typy gniazd:

- SOCK_STREAM zapewnia sekwencję, niezawodne, dwukierunkowe, oparte na połączeniach strumienie bajtów. Używa Transmission Control Protocol (TCP) dla rodziny adresów internetowych.

- SOCK_DGRAM obsługuje datagramy, które są bezpołączeniowe, niezawodne bufory o stałej (zwykle małych) długości. Używa protokołu UDP (User Datagram Protocol) dla rodziny adresów internetowych. Aby użyć tej opcji, nie należy używać gniazda z obiektem `CArchive`.

    > [!NOTE]
    >  Funkcja członkowska `Accept` pobiera odwołanie do nowego, pustego obiektu `CSocket` jako jego parametru. Należy skonstruować ten obiekt przed wywołaniem `Accept`. Należy pamiętać, że jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostanie zamknięte. Nie wywołuj `Create` dla tego nowego obiektu gniazda.

Aby uzyskać więcej informacji na temat gniazd strumienia i datagramów, zobacz artykuły [Windows Sockets: Background](../../mfc/windows-sockets-background.md), [Windows Sockets: Ports and Socket Addresss](../../mfc/windows-sockets-ports-and-socket-addresses.md)i [Windows Sockets: Using Sockets with archiwa](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>CSocket:: CSocket

Konstruuje obiekt `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Uwagi

Po przygotowaniu należy wywołać funkcję członkowską `Create`.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>CSocket:: FromHandle

Zwraca wskaźnik do obiektu `CSocket`.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Zawiera uchwyt do gniazda.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu `CSocket` lub wartość NULL, jeśli nie ma `CSocket` obiektu dołączonego do *hSocket*.

### <a name="remarks"></a>Uwagi

Gdy dany obiekt `CSocket` nie jest dołączony do dojścia, funkcja członkowska zwraca wartość NULL i nie tworzy obiektu tymczasowego.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>CSocket:: isblocking

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy wywołanie blokujące jest w toku.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli gniazdo blokuje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>CSocket:: OnMessagePending

Przesłoń tę funkcję elementu członkowskiego, aby szukać określonych komunikatów z systemu Windows i odpowiadać na nie w gnieździe.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli komunikat został obsłużony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jest to zaawansowany możliwy do zaawansowania.

Struktura wywołuje `OnMessagePending`, gdy gniazdo prowadzi pompę komunikatów systemu Windows, co pozwala na zaradzenie sobie z wiadomościami interesującymi aplikację. Aby zapoznać się z przykładami użycia `OnMessagePending`, zobacz artykuł [Windows Sockets: wyprowadzanie z klas gniazd](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Aby uzyskać więcej informacji, zobacz [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Zobacz także

[Klasa CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
