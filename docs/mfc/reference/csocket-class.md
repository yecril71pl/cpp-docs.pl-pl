---
title: Klasa CSocket | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 170acf3fb9d8cc1e63177a372517cccc8e21b94c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445129"
---
# <a name="csocket-class"></a>CSocket — klasa

Pochodzi od klasy `CAsyncSocket`, dziedziczy jej hermetyzację interfejsu API Windows Sockets i reprezentuje wyższy poziom abstrakcji niż `CAsyncSocket` obiektu.

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
|[CSocket::Dołącz](#attach)|Dołącza dojścia do GNIAZDA `CSocket` obiektu.|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Umożliwia anulowanie wywołania blokowania, która jest obecnie w toku.|
|[CSocket::Create](#create)|Tworzy gniazdo.|
|[CSocket::FromHandle](#fromhandle)|Zwraca wskaźnik do `CSocket` obiektu, biorąc pod uwagę uchwyt GNIAZDA.|
|[CSocket::IsBlocking](#isblocking)|Określa, czy wywołania blokowania jest w toku.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|Wywołuje się, by procesu oczekujących komunikatów podczas oczekiwania na ukończenie wywołania blokowania.|

## <a name="remarks"></a>Uwagi

`CSocket` działa z klasami `CSocketFile` i `CArchive` do zarządzania, wysyłania i odbierania danych.

A `CSocket` obiekt zapewnia także blokowania, co jest niezbędne dla operacji synchronicznych `CArchive`. Blokowanie funkcje, takie jak `Receive`, `Send`, `ReceiveFrom`, `SendTo`, i `Accept` (wszystkie odziedziczone z `CAsyncSocket`), nie zwracają `WSAEWOULDBLOCK` błąd `CSocket`. Zamiast tego te funkcje poczekaj, aż do zakończenia operacji. Ponadto, oryginalnym wywołanie zostanie zakończone z powodu błędu WSAEINTR `CancelBlockingCall` jest wywoływana, gdy jedna z tych funkcji blokuje.

Aby użyć `CSocket` obiektu, wywołaj Konstruktor, następnie wywołać `Create` do utworzenia podstawowego dojścia GNIAZDA (typ GNIAZDA). Parametry domyślne `Create` Tworzenie gniazda strumienia, ale jeśli nie używasz gniazda z `CArchive` obiektu, można określić parametr, aby zamiast tego utworzyć gniazdo datagramu, lub z określonego portu można utworzyć gniazda serwera. Nawiązać połączenie gniazda klienta za pomocą `Connect` po stronie klienta i `Accept` po stronie serwera. Następnie utwórz `CSocketFile` obiektu i skojarz ją z `CSocket` obiektu `CSocketFile` konstruktora. Następnie należy utworzyć `CArchive` obiekt do wysyłania i jeden do odbierania danych (zgodnie z potrzebami), następnie je Skojarz z `CSocketFile` obiektu `CArchive` konstruktora. Po zakończeniu komunikacji zniszczyć `CArchive`, `CSocketFile`, i `CSocket` obiektów. Typ danych GNIAZDA jest opisany w artykule [Windows Sockets: tła](../../mfc/windows-sockets-background.md).

Kiedy używać `CArchive` z `CSocketFile` i `CSocket`, może wystąpić sytuacja, gdzie `CSocket::Receive` wprowadza pętlę (przez `PumpMessages(FD_READ)`) oczekiwania na żądanej ilości bajtów. Jest to spowodowane Windows sockets Zezwalaj tylko jedno wywołanie otrzymanych na powiadomienie FD_READ, ale `CSocketFile` i `CSocket` Zezwalaj na wiele wywołań otrzymanych na FD_READ. Jeśli nie ma żadnych danych do odczytu powoduje FD_READ, aplikacja zawiesza się. Jeśli nigdy nie uzyskasz innej FD_READ, aplikacja przestaje komunikacji za pośrednictwem gniazda.

Ten problem można rozwiązać w następujący sposób. W `OnReceive` metody klasy gniazda, wywołanie `CAsyncSocket::IOCtl(FIONREAD, ...)` przed wywołaniem `Serialize` metody klasy komunikat podczas oczekiwanych danych do odczytu z gniazda jest większy niż jeden pakiet TCP (maksymalna jednostka transmisji z nośnika sieci zazwyczaj co najmniej 1096 bajtów). Jeśli rozmiar danych dostępne jest mniejsza niż jest to potrzebne, poczekaj, aż wszystkie dane w celu odebrania, a dopiero potem zaczynają operacji odczytu.

W poniższym przykładzie `m_dwExpected` jest przybliżona liczba bajtów, które użytkownik oczekuje odbierania. Zakłada się, że trzeba je zadeklarować innym miejscu w kodzie.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  Korzystając z MFC gniazd w pomocnicze wątki w statycznie połączonym aplikacji MFC, należy wywołać `AfxSocketInit` w każdy wątek, który używa gniazda można zainicjować biblioteki gniazda. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku głównym.

Aby uzyskać więcej informacji, zobacz [Windows Sockets w MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: jak gniazda z archiwami](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: Sekwencja operacji przy](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: przykład gniazd korzystających z archiwów](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsock.h

##  <a name="attach"></a>  CSocket::Dołącz

Wywołaj tę funkcję elementu członkowskiego, aby dołączyć `hSocket` uchwytu do `CSocket` obiektu.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Zawiera dojścia do gniazda.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli funkcja się powiedzie.

### <a name="remarks"></a>Uwagi

Uchwyt GNIAZDA są przechowywane w obiekcie [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) element członkowski danych.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall

Wywołaj tę funkcję elementu członkowskiego, aby anulować wywołania blokowania w toku.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia anulowanie żadnych oczekujących operacji blokowania dla tego gniazda. Oryginalny wywołania blokowania utracą ważność tak szybko, jak to możliwe z powodu błędu WSAEINTR.

W przypadku zablokowania `Connect` operacji, implementacja Windows Sockets spowoduje przerwanie działania wywołania blokowania jak tylko to możliwe, ale może nie być możliwe dla zasobów gniazda, które mogą być wprowadzane do momentu połączenia ukończył (i następnie został zresetowany) lub Upłynął limit czasu. Może to być widoczne tylko wtedy, gdy aplikacja próbuje natychmiast, aby otworzyć nowe gniazdo (jeśli gniazda nie są dostępne) lub połączyć się z tym samym węzłem równorzędnym.

Trwa anulowanie wszelkich operacji innych niż `Accept` można pozostawić gniazdo w stanie nieokreślonym. Jeśli aplikacja anuluje operację blokowania na gniazdo, jedyną operacją, która aplikacja może zależeć od możliwości wykonywania w gnieździe jest wywołaniem `Close`, mimo że inne operacje mogą działać na niektóre implementacje Windows Sockets. W razie potrzeby uzyskania maksymalnej przenośności do aplikacji, należy zachować ostrożność i nie są zależne od wykonywanie operacji po anulowania.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>  CSocket::Create

Wywołaj **Utwórz** funkcja elementu członkowskiego po konstruowanie obiektu gniazda, aby utworzyć gniazda Windows i dołączyć go.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Konkretnego portu do użycia z gniazda lub 0, jeśli chcesz, aby MFC, aby wybrać port.

*nSocketType*<br/>
SOCK_STREAM lub SOCK_DGRAM.

*lpszSocketAddress*<br/>
Wskaźnik do ciągu zawierającego adres sieciowy połączone gniazdo, liczbą kropkowana, takie jak "128.56.22.8". Przekazanie wartości NULL ciągu dla tego parametru oznacza `CSocket` wystąpienia powinna nasłuchiwać aktywność klienta na wszystkich interfejsach sieciowych.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie `GetLastError`.

### <a name="remarks"></a>Uwagi

`Create` następnie wywołuje `Bind` powiązać gniazda z określonego adresu. Obsługiwane są następujące typy gniazda:

- Udostępnia SOCK_STREAM sekwencjonowania, strumienie bajtów niezawodnej, dwukierunkowej, opartego na połączeniach. Używa protokołu Transmission Control Protocol (TCP) dla internetowej rodziny adresowej.

- Datagramy obsługuje SOCK_DGRAM są przesyłanie, zawodne buforów stała długość maksymalną (zazwyczaj małego). Używa protokołu UDP (User Datagram) dla internetowej rodziny adresowej. Aby użyć tej opcji, nie można używać gniazda z `CArchive` obiektu.

    > [!NOTE]
    >  `Accept` Funkcja elementu członkowskiego przyjmuje odwołanie do nowy, pusty `CSocket` obiekt jako parametr. Należy utworzyć ten obiekt przed wywołaniem `Accept`. Należy pamiętać, że jeśli ten obiekt gniazda trafia zakresu, zamyka połączenie. Nie wywołuj `Create` dla tego nowego obiektu gniazda.

Aby uzyskać więcej informacji na temat usługi stream i datagram gniazda, zobacz artykuły [Windows Sockets: tła](../../mfc/windows-sockets-background.md), [Windows Sockets: porty i adresy gniazd](../../mfc/windows-sockets-ports-and-socket-addresses.md), i [Windows Sockets: przy użyciu Gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>  CSocket::CSocket

Konstruuje `CSocket` obiektu.

```
CSocket();
```

### <a name="remarks"></a>Uwagi

Po konstrukcji, należy wywołać `Create` funkcja elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>  CSocket::FromHandle

Zwraca wskaźnik do `CSocket` obiektu.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Zawiera dojścia do gniazda.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CSocket` obiekt lub wartość NULL, jeśli ma nie `CSocket` obiekt dołączony do *hSocket*.

### <a name="remarks"></a>Uwagi

Gdy zwracany uchwyt GNIAZDA, jeśli `CSocket` obiektu nie jest dołączony do uchwytu, funkcja elementu członkowskiego zwraca wartość NULL i nie tworzy tymczasowego obiektu.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>  CSocket::IsBlocking

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy wywołania blokowania jest w toku.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli blokuje gniazda; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>  CSocket::OnMessagePending

Zastąpienie tej funkcji elementu członkowskiego, wyszukaj określone wiadomości z Windows i Reaguj na nie w swojej gniazda.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli komunikat został obsłużony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jest to zaawansowany możliwym do zastąpienia.

Struktura wywołuje `OnMessagePending` podczas gniazda jest przekazywanie komunikatów Windows daje możliwość obsługi wiadomości płynących ze swojej aplikacji. Przykłady zastosowania `OnMessagePending`, zapoznaj się z artykułem [Windows Sockets: wyprowadzanie z klas gniazd](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Zobacz też

[Klasa CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
