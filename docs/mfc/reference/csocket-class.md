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
ms.openlocfilehash: 3f0a7a9a90250ede7b112cfbd9bc1ca14d583356
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318191"
---
# <a name="csocket-class"></a>Klasa CSocket

Wywodzi się z `CAsyncSocket`, dziedziczy jego hermetyzacji interfejsu API windows sockets i `CAsyncSocket` reprezentuje wyższy poziom abstrakcji niż obiekt.

## <a name="syntax"></a>Składnia

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|Konstruuje `CSocket` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSocket::Dołącz](#attach)|Dołącza uchwyt SOCKET do `CSocket` obiektu.|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Anuluje połączenie blokujące, które jest obecnie w toku.|
|[CSocket::Tworzenie](#create)|Tworzy gniazdo.|
|[CSocket::OdHandle](#fromhandle)|Zwraca wskaźnik do `CSocket` obiektu, biorąc pod uwagę uchwyt SOCKET.|
|[CSocket::Blokowanie](#isblocking)|Określa, czy trwa połączenie blokujące.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|Wywoływana do przetwarzania oczekujących wiadomości podczas oczekiwania na zakończenie połączenia blokującego.|

## <a name="remarks"></a>Uwagi

`CSocket`współpracuje z `CSocketFile` `CArchive` klasami oraz zarządza wysyłaniem i odbieraniem danych.

Obiekt `CSocket` zapewnia również blokowanie, co jest niezbędne do `CArchive`synchronicznego działania . Funkcje blokowania, `Receive` `Send`takie `ReceiveFrom` `SendTo`jak `Accept` , , , `CAsyncSocket`i (wszystkie `WSAEWOULDBLOCK` odziedziczone po ), nie zwracają błędu w `CSocket`. Zamiast tego te funkcje poczekaj, aż operacja zostanie zakończona. Ponadto oryginalne wywołanie zakończy się z błędem WSAEINTR, jeśli `CancelBlockingCall` jest wywoływana, gdy jedna z tych funkcji jest blokowanie.

Aby użyć `CSocket` obiektu, wywołaj konstruktora, a następnie wywołaj, `Create` aby utworzyć podstawowy uchwyt SOCKET (typ SOCKET). Domyślne parametry `Create` tworzenia gniazda strumienia, ale jeśli nie `CArchive` używasz gniazda z obiektem, można określić parametr, aby utworzyć gniazdo datagramu zamiast lub powiązać z określonym portem, aby utworzyć gniazdo serwera. Połącz się z `Connect` gniazdem klienta `Accept` przy użyciu po stronie klienta i po stronie serwera. Następnie utwórz `CSocketFile` obiekt i `CSocket` skojarz go `CSocketFile` z obiektem w konstruktorze. Następnie utwórz `CArchive` obiekt do wysyłania i jeden do odbierania danych `CSocketFile` (w `CArchive` razie potrzeby), a następnie skojarzyć je z obiektem w konstruktorze. Po zakończeniu komunikacji zniszcz `CArchive`program `CSocketFile`, `CSocket` i obiekty. Typ danych SOCKET jest opisany w artykule [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

Podczas korzystania `CArchive` `CSocketFile` z `CSocket`i , może `CSocket::Receive` wystąpić sytuacja, w `PumpMessages(FD_READ)`której wchodzi w pętli (by) oczekiwanie na żądaną ilość bajtów. Dzieje się tak, ponieważ gniazda systemu Windows zezwalają tylko `CSocketFile` `CSocket` na jedno wywołanie recv na powiadomienie FD_READ, ale zezwalają na wiele wywołań recv na FD_READ. Jeśli otrzymasz FD_READ, gdy nie ma żadnych danych do odczytu, aplikacja zawiesza się. Jeśli nigdy nie otrzymasz innego FD_READ, aplikacja przestaje komunikować się za pośrednictwem gniazda.

Można rozwiązać ten problem w następujący sposób. W `OnReceive` metodzie klasy gniazda `CAsyncSocket::IOCtl(FIONREAD, ...)` wywołać przed `Serialize` wywołaniem metody klasy wiadomości, gdy oczekiwane dane do odczytu z gniazda przekracza rozmiar jednego pakietu TCP (maksymalna jednostka transmisji medium sieciowego, zwykle co najmniej 1096 bajtów). Jeśli rozmiar dostępnych danych jest mniejszy niż jest to potrzebne, poczekaj na odebranie wszystkich danych, a dopiero potem rozpocznij operację odczytu.

W poniższym `m_dwExpected` przykładzie jest przybliżona liczba bajtów, które użytkownik oczekuje, aby otrzymać. Zakłada się, że deklarujesz go w innym miejscu w kodzie.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
> Podczas korzystania z gniazd MFC w wątkach pomocniczych w statycznie połączonej aplikacji MFC, należy wywołać `AfxSocketInit` w każdym wątku, który używa gniazd do inicjowania bibliotek gniazd. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku podstawowym.

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows w MFC](../../mfc/windows-sockets-in-mfc.md), Gniazda systemu [Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md), [Gniazda systemu Windows: Jak działają gniazda z archiwami](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Gniazda systemu Windows: Sekwencja operacji](../../mfc/windows-sockets-sequence-of-operations.md), Gniazda systemu [Windows: Przykład gniazd za pomocą archiwów](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Casyncsocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsock.h

## <a name="csocketattach"></a><a name="attach"></a>CSocket::Dołącz

Wywołanie tej funkcji `hSocket` elementu członkowskiego, aby dołączyć dojście do `CSocket` obiektu.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket (własówka)*<br/>
Zawiera uchwyt do gniazda.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja zakończy się pomyślnie.

### <a name="remarks"></a>Uwagi

Uchwyt SOCKET jest przechowywany w [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) element członkowski danych obiektu.

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

## <a name="csocketcancelblockingcall"></a><a name="cancelblockingcall"></a>CSocket::CancelBlockingCall

Wywołanie tej funkcji elementu członkowskiego, aby anulować wywołanie blokowania aktualnie w toku.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Uwagi

Ta funkcja anuluje wszelkie zaległe blokowanie dla tego gniazda. Oryginalne wywołanie blokowania zakończy się tak szybko, jak to możliwe z błędem WSAEINTR.

W przypadku operacji `Connect` blokowania implementacja Windows Sockets zakończy wywołanie blokowania tak szybko, jak to możliwe, ale może nie być możliwe zwolnienie zasobów gniazda, dopóki połączenie nie zostanie zakończone (a następnie zresetowane) lub przesunie limit czasu. Jest to prawdopodobnie zauważalne tylko wtedy, gdy aplikacja natychmiast próbuje otworzyć nowe gniazdo (jeśli nie są dostępne gniazda) lub połączyć się z tym samym elementem równorzędnym.

Anulowanie dowolnej operacji `Accept` innej niż może pozostawić gniazdo w stanie nieokreślonym. Jeśli aplikacja anuluje operację blokowania na gnieździe, jedyną operacją, która aplikacja może `Close`zależeć od możliwości wykonania na gnieździe, jest wywołanie , chociaż inne operacje mogą działać w niektórych implementacjach windows sockets. Jeśli chcesz maksymalną przenośność dla aplikacji, należy uważać, aby nie polegać na wykonywaniu operacji po anulowaniu.

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcreate"></a><a name="create"></a>CSocket::Tworzenie

Wywołanie **Create** funkcji elementu członkowskiego po skonstruowaniu obiektu gniazda, aby utworzyć gniazdo systemu Windows i dołączyć go.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Określonego portu, który ma być używany z gniazdem lub 0, jeśli chcesz, aby MFC wybrać port.

*nSocketType*<br/>
SOCK_STREAM lub SOCK_DGRAM.

*lpszSocketAddress*<br/>
Wskaźnik do ciągu zawierającego adres sieciowy podłączonego gniazda, numer kropkowany, taki jak "128.56.22.8". Przekazywanie ciągu NULL dla tego `CSocket` parametru wskazuje, że wystąpienie powinno nasłuchiwanie aktywności klienta we wszystkich interfejsach sieciowych.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod `GetLastError`błędu można pobrać, wywołując .

### <a name="remarks"></a>Uwagi

`Create`następnie `Bind` wywołuje powiązanie gniazda z określonym adresem. Obsługiwane są następujące typy gniazd:

- SOCK_STREAM Zapewnia sekwencjonowane, niezawodne, dwukierunkowe strumienie bajtów oparte na połączeniu. Używa protokołu TCP (Transmission Control Protocol) dla rodziny adresów internetowych.

- SOCK_DGRAM Obsługuje datagramy, które są bezłącznymi, zawodne bufory o stałej (zazwyczaj małej) maksymalnej długości. Używa protokołu UDP (User Datagram Protocol) dla rodziny adresów internetowych. Aby użyć tej opcji, nie należy `CArchive` używać gniazda z obiektem.

    > [!NOTE]
    >  Funkcja `Accept` elementu członkowskiego przyjmuje odwołanie do `CSocket` nowego, pustego obiektu jako parametru. Należy skonstruować ten obiekt `Accept`przed wywołaniem . Należy pamiętać, że jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostanie zamknięte. Nie należy `Create` wywoływać tego nowego obiektu gniazda.

Aby uzyskać więcej informacji na temat gniazd strumienia i datagramu, zobacz artykuły [Gniazda systemu Windows: Tło](../../mfc/windows-sockets-background.md), Gniazda systemu [Windows: Porty i gniazda adresy](../../mfc/windows-sockets-ports-and-socket-addresses.md)oraz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcsocket"></a><a name="csocket"></a>CSocket::CSocket

Konstruuje `CSocket` obiekt.

```
CSocket();
```

### <a name="remarks"></a>Uwagi

Po zakończeniu budowy należy `Create` wywołać funkcję elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketfromhandle"></a><a name="fromhandle"></a>CSocket::OdHandle

Zwraca wskaźnik do `CSocket` obiektu.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket (własówka)*<br/>
Zawiera uchwyt do gniazda.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CSocket` obiektu lub NULL, jeśli `CSocket` do *hSocket*nie jest dołączony żaden obiekt .

### <a name="remarks"></a>Uwagi

Gdy podano dojście `CSocket` SOCKET, jeśli obiekt nie jest dołączony do dojścia, funkcja elementu członkowskiego zwraca wartość NULL i nie tworzy obiektu tymczasowego.

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketisblocking"></a><a name="isblocking"></a>CSocket::Blokowanie

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy trwa wywołanie blokowania.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli gniazdo jest blokowanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketonmessagepending"></a><a name="onmessagepending"></a>CSocket::OnMessagePending

Zastąporzyj tę funkcję elementu członkowskiego, aby wyszukać określone wiadomości z systemu Windows i odpowiedzieć na nie w gnieździe.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość została obsłużona; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jest to zaawansowane zastąpienie.

Struktura wywołuje, `OnMessagePending` gdy gniazdo jest pompowanie wiadomości systemu Windows, aby dać możliwość radzenia sobie z wiadomościami interesujące dla aplikacji. Przykłady użycia można znaleźć `OnMessagePending`w artykule [Gniazda systemu Windows: Pochodne z klas gniazd](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Zobacz też

[Klasa CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
