---
title: Klasa CHttpFile
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: cba3ba7d86577703de2bf5709d66bbd5e0298863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368392"
---
# <a name="chttpfile-class"></a>Klasa CHttpFile

Udostępnia funkcje żądania i odczytywania plików na serwerze HTTP.

## <a name="syntax"></a>Składnia

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|Tworzy obiekt `CHttpFile`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Dodaje nagłówki do żądania wysłanego do serwera HTTP.|
|[CHttpFile::EndRequest](#endrequest)|Kończy żądanie wysłane do serwera HTTP za pomocą funkcji członkowskiej [SendRequestEx.](#sendrequestex)|
|[CHttpFile::GetFileURL](#getfileurl)|Pobiera adres URL dla określonego pliku.|
|[CHttpFile::GetObject](#getobject)|Pobiera obiekt docelowy zlecenia w żądaniu do serwera HTTP.|
|[CHttpFile::GetVerb](#getverb)|Pobiera zlecenie, który został użyty w żądaniu do serwera HTTP.|
|[CHttpFile::QueryInfo](#queryinfo)|Zwraca nagłówki odpowiedzi lub żądania z serwera HTTP.|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Pobiera kod stanu skojarzony z żądaniem HTTP i `dwStatusCode` umieszcza go w dostarczonym parametrze.|
|[CHttpFile::WyślijRequest](#sendrequest)|Wysyła żądanie do serwera HTTP.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Wysyła żądanie do serwera HTTP przy użyciu metod `CInternetFile` [zapisu](../../mfc/reference/cinternetfile-class.md#write) lub [writestring](../../mfc/reference/cinternetfile-class.md#writestring) .|

## <a name="remarks"></a>Uwagi

Jeśli sesja internetowa odczytuje dane z serwera HTTP, `CHttpFile`należy utworzyć wystąpienie programu .

Aby dowiedzieć `CHttpFile` się więcej o tym, jak działa z innymi klasami MFC Internet, zobacz artykuł [Programowanie internetowe z WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

[Cstdiofile](../../mfc/reference/cstdiofile-class.md)

[Cinternetfile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders

Wywołanie tej funkcji elementu członkowskiego, aby dodać jeden lub więcej nagłówków żądań HTTP do dojścia żądania HTTP.

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>Parametry

*pstrHeaders (głowice)*<br/>
Wskaźnik do ciągu zawierającego nagłówek lub nagłówki do dołączenia do żądania. Każdy nagłówek musi zostać zakończony parą CR/LF.

*Dwflags*<br/>
Modyfikuje semantykę nowych nagłówków. Może być jedną z następujących czynności:

- HTTP_ADDREQ_FLAG_COALESCE Scala nagłówki o tej samej nazwie, używając flagi, aby dodać pierwszy nagłówek znaleziony do następnego nagłówka. Na przykład "Accept:\*text/ ", a następnie\*"Accept: audio/ " powoduje utworzenie\*pojedynczego\*nagłówka "Accept: text/ , audio/ ". To do aplikacji wywołującej, aby zapewnić spójny schemat w odniesieniu do danych otrzymanych przez żądania wysyłane z coalesced lub oddzielnych nagłówków.

- HTTP_ADDREQ_FLAG_REPLACE Wykonuje usunięcie i dodanie w celu zastąpienia bieżącego nagłówka. Nazwa nagłówka będzie używana do usuwania bieżącego nagłówka, a pełna wartość zostanie użyta do dodania nowego nagłówka. Jeśli wartość nagłówka jest pusta, a nagłówek zostanie znaleziony, zostanie on usunięty. Jeśli nie jest pusty, wartość nagłówka jest zastępowany.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW Nagłówek jest dodany tylko wtedy, gdy jeszcze nie istnieje. Jeśli istnieje, zwracany jest błąd.

- HTTP_ADDREQ_FLAG_ADD używany z replace. Dodaje nagłówek, jeśli nie istnieje.

*dwHeadersLen (Łańczy)*<br/>
Długość, w postaci, *pstrHeaders*. Jeśli jest to -1L, a następnie *pstrHeaders* zakłada się zero-zakończone i długość jest obliczany.

*Str*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu zawierającego nagłówek żądania lub nagłówki, które mają zostać dodane.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

`AddRequestHeaders`dołącza dodatkowe nagłówki w wolnym formacie do dojścia żądania HTTP. Jest on przeznaczony do użytku przez zaawansowanych klientów, którzy potrzebują szczegółowej kontroli nad dokładnym żądaniem wysłanym do serwera HTTP.

> [!NOTE]
> Aplikacja może przekazać wiele nagłówków w *pstrHeaders* lub *str* dla `AddRequestHeaders` wywołania przy użyciu HTTP_ADDREQ_FLAG_ADD lub HTTP_ADDREQ_FLAG_ADD_IF_NEW. Jeśli aplikacja próbuje usunąć lub zastąpić nagłówek za pomocą HTTP_ADDREQ_FLAG_REMOVE lub HTTP_ADDREQ_FLAG_REPLACE, tylko jeden nagłówek może być dostarczony w *lpszHeaders*.

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a>CHttpFile::CHttpFile

Ta funkcja elementu członkowskiego `CHttpFile` jest wywoływana do konstruowania obiektu.

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>Parametry

*hFile (plik)*<br/>
Dojście do pliku internetowego.

*hSession (wysiew)*<br/>
Dojście do sesji internetowej.

*pstrObject (łak.)*<br/>
Wskaźnik do ciągu zawierającego `CHttpFile` obiekt.

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*pstrVerb (wład.*<br/>
Wskaźnik do ciągu zawierającego metodę, która ma być używana podczas wysyłania żądania. Może być POST, HEAD lub GET.

*Dwcontext*<br/>
Identyfikator kontekstu `CHttpFile` obiektu. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat tego parametru.

*pZkładanie*<br/>
Wskaźnik do obiektu [CHttpConnection.](../../mfc/reference/chttpconnection-class.md)

### <a name="remarks"></a>Uwagi

Nigdy nie `CHttpFile` konstruujesz obiektu bezpośrednio; zamiast tego wywołaj [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection::OpenRequest.](../../mfc/reference/chttpconnection-class.md#openrequest)

Wartość domyślna `dwContext` jest wysyłana przez `CHttpFile` MFC do obiektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu, który utworzył `CHttpFile` obiekt. Podczas `CInternetSession::OpenURL` wywoływania `CHttpConnection` lub `CHttpFile` konstruowania obiektu, można zastąpić domyślne, aby ustawić identyfikator kontekstu do wartości wybranej. Identyfikator kontekstu jest zwracany do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan obiektu, z którym jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="chttpfileendrequest"></a><a name="endrequest"></a>CHttpFile::EndRequest

Wywołanie tej funkcji elementu członkowskiego, aby zakończyć żądanie wysłane do serwera HTTP z funkcją elementu członkowskiego [SendRequestEx.](#sendrequestex)

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Flagi opisujące operację. Aby uzyskać listę odpowiednich flag, zobacz [HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) w zestawie Windows SDK.

*lpBuffIn (lpBuffIn)*<br/>
Wskaźnik do zainicjowanego [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) opisującego bufor wejściowy używany do operacji.

*Dwcontext*<br/>
Identyfikator kontekstu `CHttpFile` dla operacji. Zobacz Uwagi, aby uzyskać więcej informacji na temat tego parametru.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, należy określić przyczynę błędu, badając zgłoszony [obiekt CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Uwagi

Wartość domyślna dla *dwContext* jest wysyłana przez MFC do `CHttpFile` obiektu z `CHttpFile` [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu, który utworzył obiekt. Podczas wywoływania [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection](../../mfc/reference/chttpconnection-class.md) do konstruowania `CHttpFile` obiektu, można zastąpić domyślny, aby ustawić identyfikator kontekstu do wartości wybranej. Identyfikator kontekstu jest zwracany do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan obiektu, z którym jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a>CHttpFile::GetFileURL

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę pliku HTTP jako adres URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający adres URL odwołujący się do zasobu skojarzonego z tym plikiem.

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego należy używać tylko po `CHttpFile` pomyślnym wywołaniu [sendrequest](#sendrequest) lub na obiekcie pomyślnie utworzonym przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetobject"></a><a name="getobject"></a>CHttpFile::GetObject

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać `CHttpFile`nazwę obiektu skojarzonego z tym .

```
CString GetObject() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający nazwę obiektu.

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego należy używać tylko po `CHttpFile` pomyślnym wywołaniu [sendrequest](#sendrequest) lub na obiekcie pomyślnie utworzonym przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetverb"></a><a name="getverb"></a>CHttpFile::GetVerb

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać zlecenie `CHttpFile`HTTP (lub metoda) skojarzone z tym .

```
CString GetVerb() const;
```

### <a name="return-value"></a>Wartość zwracana

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający nazwę zlecenia HTTP (lub metody).

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego należy używać tylko po `CHttpFile` pomyślnym wywołaniu [sendrequest](#sendrequest) lub na obiekcie pomyślnie utworzonym przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a>CHttpFile::QueryInfo

Wywołanie tej funkcji elementu członkowskiego, aby zwrócić odpowiedzi lub żądania nagłówków z żądania HTTP.

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>Parametry

*dwInfoLevel (Na poziomie nieszczegowym)*<br/>
Kombinacja atrybutu do kwerendy i następujące flagi, które określają typ żądanych informacji:

- HTTP_QUERY_CUSTOM Znajduje nazwę nagłówka i zwraca tę wartość w *lpvBuffer* na danych wyjściowych. HTTP_QUERY_CUSTOM zgłasza asercja, jeśli nie zostanie znaleziony nagłówek.

- HTTP_QUERY_FLAG_REQUEST_HEADERS Zazwyczaj aplikacja wysyła kwerendy do nagłówków odpowiedzi, ale aplikacja może również wysyłać zapytania do nagłówków żądań przy użyciu tej flagi.

- HTTP_QUERY_FLAG_SYSTEMTIME Dla tych nagłówków, których wartość jest ciągiem daty/godziny, takim jak "Last-Modified-Time", ta flaga zwraca wartość nagłówka jako standardową strukturę [SystemuTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) systemu Win32, która nie wymaga od aplikacji analizowania danych. Jeśli używasz tej flagi, można `SYSTEMTIME` użyć zastąpienia funkcji.

- HTTP_QUERY_FLAG_NUMBER Dla tych nagłówków, których wartość jest liczbą, takich jak kod stanu, ta flaga zwraca dane jako liczbę 32-bitową.

Zobacz **uwagi** sekcji listy możliwych wartości.

*lpvBuffer*<br/>
Wskaźnik do buforu, który odbiera informacje.

*lpdwBufferLength*<br/>
Przy wprowadzaniu wskazuje to wartość zawierającą długość buforu danych w liczbie znaków lub bajtów. Zobacz **uwagi** sekcji bardziej szczegółowe informacje na temat tego parametru.

*lpdwIndex*<br/>
Wskaźnik do indeksu nagłówka opartego na wartości zero. Może mieć wartość NULL. Ta flaga służy do wyliczanie wielu nagłówków o tej samej nazwie. Na danych wejściowych *lpdwIndex* wskazuje indeks określonego nagłówka do zwrócenia. Na wyjściu *lpdwIndex* wskazuje indeks następnego nagłówka. Jeśli nie można odnaleźć następnego indeksu, zwracany jest ERROR_HTTP_HEADER_NOT_FOUND.

*Str*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu odbierania zwracanych informacji.

*dwIndex (np.*<br/>
Wartość indeksu. Zobacz *lpdwIndex*.

*pSysCzas*<br/>
Wskaźnik do struktury [Systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) Systemu Win32.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego należy używać tylko po `CHttpFile` pomyślnym wywołaniu [sendrequest](#sendrequest) lub na obiekcie pomyślnie utworzonym przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Następujące typy danych można pobrać `QueryInfo`z:

- ciągi znaków (domyślnie)

- `SYSTEMTIME`(dla "Data:" "Wygasa:" itp., nagłówki)

- DWORD (dla STATUS_CODE, CONTENT_LENGTH itp.)

Gdy ciąg jest zapisywany w buforze, a `lpdwBufferLength` funkcja elementu członkowskiego powiedzie się, zawiera długość ciągu w znakach minus 1 dla kończącego się znaku NULL.

Możliwe *wartości dwInfoLevel* obejmują:

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać kod stanu skojarzony z żądaniem HTTP i umieścić go w dostarczonym parametru *dwStatusCode.*

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parametry

*kod dwStatusCode*<br/>
Odwołanie do kodu stanu. Kody stanu wskazują powodzenie lub niepowodzenie żądanego zdarzenia. Zobacz **Uwagi** dotyczące wyboru opisów kodów stanu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego należy używać tylko po `CHttpFile` pomyślnym wywołaniu [sendrequest](#sendrequest) lub na obiekcie pomyślnie utworzonym przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Kody stanu HTTP należą do grup wskazujących na powodzenie lub niepowodzenie żądania. W poniższych tabelach opisano grupy kodów stanu i najczęściej spotykane kody stanu HTTP.

|Grupa|Znaczenie|
|-----------|-------------|
|200-299|Powodzenie|
|300-399|Informacje|
|400-499|Błąd żądania|
|500-599|Błąd serwera|

Typowe kody stanu HTTP:

|Kod stanu|Znaczenie|
|-----------------|-------------|
|200|Adres URL znajduje się, transmisja następuje|
|400|Niezrozumiała prośba|
|404|Nie znaleziono żądanego adresu URL|
|405|Serwer nie obsługuje żądanej metody|
|500|Nieznany błąd serwera|
|503|Osiągnięto pojemność serwera|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a>CHttpFile::WyślijRequest

Wywołanie tej funkcji członkowskiej, aby wysłać żądanie do serwera HTTP.

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>Parametry

*pstrHeaders (głowice)*<br/>
Wskaźnik do ciągu zawierającego nazwę nagłówków do wysłania.

*dwHeadersLen (Łańczy)*<br/>
Długość nagłówków identyfikowanych przez *pstrHeaders*.

*lpOuchylnik*<br/>
Wszelkie opcjonalne dane do wysłania natychmiast po nagłówkach żądania. Jest to zwykle używane dla operacji POST i PUT. Może to być null, jeśli nie ma żadnych opcjonalnych danych do wysłania.

*dwOptionalLen (500)*<br/>
Długość *lpOptional*.

*strHeaders ( strHeaders )*<br/>
Ciąg zawierający nazwę nagłówków dla wysyłanego żądania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, należy określić przyczynę błędu, badając zgłoszony [obiekt CInternetException.](../../mfc/reference/cinternetexception-class.md)

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a>CHttpFile::SendRequestEx

Wywołanie tej funkcji członkowskiej, aby wysłać żądanie do serwera HTTP.

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*dwTotalLen (DotalLen)*<br/>
Liczba bajtów do wysłania w żądaniu.

*Dwflags*<br/>
Flagi opisujące operację. Aby uzyskać listę odpowiednich flag, zobacz [HttpSendRequestEx](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) w zestawie Windows SDK.

*Dwcontext*<br/>
Identyfikator kontekstu `CHttpFile` dla operacji. Zobacz Uwagi, aby uzyskać więcej informacji na temat tego parametru.

*lpBuffIn (lpBuffIn)*<br/>
Wskaźnik do zainicjowanego [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) opisującego bufor wejściowy używany do operacji.

*lpBuffOut (lpBuffOut)*<br/>
Wskaźnik do zainicjowanego INTERNET_BUFFERS opisującego bufor wyjściowy używany do operacji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli się powiedzie. Jeśli wywołanie nie powiedzie się, należy określić przyczynę błędu, badając zgłoszony [obiekt CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia aplikacji wysyłanie danych przy użyciu metod `CInternetFile` [zapisu](../../mfc/reference/cinternetfile-class.md#write) i [zapisu.](../../mfc/reference/cinternetfile-class.md#writestring) Musisz znać długość danych do wysłania przed wywołaniem albo zastąpienie tej funkcji. Pierwsze zastąpienie umożliwia określenie długości danych, które chcesz wysłać. Drugie zastąpienie akceptuje wskaźniki do INTERNET_BUFFERS struktur, które mogą służyć do opisywania buforu bardzo szczegółowo.

Po zapisaniu zawartości do pliku, wywołać [EndRequest,](#endrequest) aby zakończyć operację.

Wartość domyślna dla *dwContext* jest wysyłana przez MFC do `CHttpFile` obiektu z `CHttpFile` [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu, który utworzył obiekt. Podczas wywoływania [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection](../../mfc/reference/chttpconnection-class.md) do konstruowania `CHttpFile` obiektu, można zastąpić domyślny, aby ustawić identyfikator kontekstu do wartości wybranej. Identyfikator kontekstu jest zwracany do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan obiektu, z którym jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

### <a name="example"></a>Przykład

Ten fragment kodu wysyła zawartość ciągu do biblioteki DLL o nazwie MFCISAPI. Biblioteka DLL na serwerze LOCALHOST. W tym przykładzie użyto `WriteString`tylko jednego wywołania , przy użyciu wielu wywołań do wysyłania danych w blokach jest dopuszczalne.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)
