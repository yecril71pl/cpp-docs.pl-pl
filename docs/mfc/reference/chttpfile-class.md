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
ms.openlocfilehash: ff050a89a10c68c639c141891dd51b1b2d58e105
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915997"
---
# <a name="chttpfile-class"></a>Klasa CHttpFile

Oferuje funkcje do żądania i odczytywania plików na serwerze HTTP.

## <a name="syntax"></a>Składnia

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|`CHttpFile` Tworzy obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Dodaje nagłówki do żądania wysyłanego do serwera HTTP.|
|[CHttpFile::EndRequest](#endrequest)|Zamyka żądanie wysyłane do serwera HTTP za pomocą funkcji składowej [SendRequestEx](#sendrequestex) .|
|[CHttpFile::GetFileURL](#getfileurl)|Pobiera adres URL dla określonego pliku.|
|[CHttpFile::GetObject](#getobject)|Pobiera obiekt docelowy zlecenia w żądaniu do serwera HTTP.|
|[CHttpFile:: getverb](#getverb)|Pobiera czasownik, który został użyty w żądaniu do serwera HTTP.|
|[CHttpFile::QueryInfo](#queryinfo)|Zwraca nagłówek odpowiedzi lub żądania z serwera HTTP.|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Pobiera kod stanu skojarzony z żądaniem http i umieszcza go w dostarczonym `dwStatusCode` parametrze.|
|[CHttpFile::SendRequest](#sendrequest)|Wysyła żądanie do serwera HTTP.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Wysyła żądanie do serwera HTTP przy użyciu metod `CInternetFile` [Write](../../mfc/reference/cinternetfile-class.md#write) lub [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) .|

## <a name="remarks"></a>Uwagi

Jeśli sesja internetowa odczytuje dane z serwera HTTP, należy utworzyć wystąpienie `CHttpFile`.

Aby dowiedzieć się więcej `CHttpFile` o tym, jak działa z innymi klasami internetowymi MFC, zobacz artykuł [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

##  <a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders

Wywołaj tę funkcję elementu członkowskiego, aby dodać jeden lub więcej nagłówków żądań HTTP do dojścia żądania HTTP.

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

*pstrHeaders*<br/>
Wskaźnik do ciągu zawierającego nagłówek lub nagłówki, które mają zostać dołączone do żądania. Każdy nagłówek musi być zakończony przez parę CR/LF.

*flagiDW*<br/>
Modyfikuje semantykę nowych nagłówków. Może to być jeden z następujących elementów:

- HTTP_ADDREQ_FLAG_COALESCE Scala nagłówki o tej samej nazwie przy użyciu flagi, aby dodać pierwszy nagłówek znaleziony do kolejnego nagłówka. Na przykład "Zaakceptuj: tekst\*/", po którym następuje "Akceptuj: audio/\*" powoduje utworzenie pojedynczego nagłówka "Akceptuj: text/\*, audio/\*". Jest do aplikacji wywołującej, aby zapewnić spójny schemat w odniesieniu do danych odbieranych przez żądania wysyłane z dołączonymi lub oddzielnymi nagłówkami.

- HTTP_ADDREQ_FLAG_REPLACE wykonuje usuwanie i Dodawanie, aby zastąpić bieżący nagłówek. Nazwa nagłówka zostanie użyta w celu usunięcia bieżącego nagłówka, a w celu dodania nowego nagłówka zostanie użyta pełna wartość. Jeśli nagłówek-wartość jest pusta, a nagłówek zostanie znaleziony, zostanie usunięty. Jeśli nie jest pusty, wartość nagłówka zostanie zastąpiona.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW dodaje tylko nagłówek, jeśli jeszcze nie istnieje. Jeśli taki istnieje, zwracany jest błąd.

- HTTP_ADDREQ_FLAG_ADD używany z zastępowaniem. Dodaje nagłówek, jeśli nie istnieje.

*dwHeadersLen*<br/>
Długość (w znakach) elementu *pstrHeaders*. Jeśli jest to-1L, zakłada się, że *pstrHeaders* jest zakończony zerem i długość jest obliczana.

*str*<br/>
Odwołanie do obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierającego nagłówek lub nagłówki żądania do dodania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

`AddRequestHeaders`dołącza dodatkowe nagłówki w formacie wolnym do dojścia żądania HTTP. Jest ona przeznaczona do użycia przez zaawansowanych klientów, którzy potrzebują szczegółowej kontroli nad dokładnym żądaniem wysyłanym do serwera HTTP.

> [!NOTE]
>  Aplikacja może przekazać wiele nagłówków w *pstrHeaders* lub *str* dla `AddRequestHeaders` wywołania przy użyciu HTTP_ADDREQ_FLAG_ADD lub HTTP_ADDREQ_FLAG_ADD_IF_NEW. Jeśli aplikacja podejmie próbę usunięcia lub zamiany nagłówka przy użyciu HTTP_ADDREQ_FLAG_REMOVE lub HTTP_ADDREQ_FLAG_REPLACE, w *lpszHeaders*można dostarczyć tylko jeden nagłówek.

##  <a name="chttpfile"></a>CHttpFile::CHttpFile

Ta funkcja członkowska jest wywoływana w celu `CHttpFile` skonstruowania obiektu.

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

*hFile*<br/>
Dojście do pliku internetowego.

*hSession*<br/>
Dojście do sesji internetowej.

*pstrObject*<br/>
Wskaźnik do ciągu zawierającego `CHttpFile` obiekt.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*pstrVerb*<br/>
Wskaźnik do ciągu zawierającego metodę, która ma być używana podczas wysyłania żądania. Może to być POST, szef lub GET.

*dwContext*<br/>
Identyfikator kontekstu dla `CHttpFile` obiektu. Aby uzyskać więcej informacji o tym parametrze, zobacz **uwagi** .

*pConnection*<br/>
Wskaźnik do obiektu [CHttpConnection](../../mfc/reference/chttpconnection-class.md) .

### <a name="remarks"></a>Uwagi

`CHttpFile` Obiekt nigdy nie jest skonstruowany bezpośrednio, zamiast tego należy wywołać [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) .

Wartość domyślna `dwContext` dla jest wysyłana przez `CHttpFile` MFC do obiektu z obiektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) , który utworzył `CHttpFile` obiekt. Podczas wywoływania `CInternetSession::OpenURL` lub `CHttpConnection` do konstruowania `CHttpFile` obiektu, można zastąpić ustawienie domyślne, aby ustawić identyfikator kontekstu na wybraną wartość. Identyfikator kontekstu jest zwracany do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu obiektu, z którym został zidentyfikowany. Zapoznaj się [z artykułem internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

##  <a name="endrequest"></a>CHttpFile::EndRequest

Wywołaj tę funkcję elementu członkowskiego, aby zakończyć żądanie wysłane do serwera HTTP za pomocą funkcji składowej [SendRequestEx](#sendrequestex) .

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Flagi opisujące operację. Aby uzyskać listę odpowiednich flag, zobacz [HttpEndRequest](/windows/desktop/api/wininet/nf-wininet-httpendrequesta) w Windows SDK.

*lpBuffIn*<br/>
Wskaźnik do zainicjowanej [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-internet_buffersa) , który opisuje bufor wejściowy używany do operacji.

*dwContext*<br/>
Identyfikator kontekstu dla `CHttpFile` operacji. Aby uzyskać więcej informacji o tym parametrze, zobacz uwagi.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie zakończy się niepowodzeniem, ustal przyczynę niepowodzenia, badając zgłoszony obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Uwagi

Wartość domyślna parametru *dwContext* jest wysyłana przez MFC do `CHttpFile` obiektu z obiektu [](../../mfc/reference/cinternetsession-class.md) `CHttpFile` CInternetSession, który utworzył obiekt. W przypadku wywołania [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection](../../mfc/reference/chttpconnection-class.md) `CHttpFile` w celu skonstruowania obiektu można zastąpić wartość domyślną, aby ustawić identyfikator kontekstu na wybraną przez siebie zawartość. Identyfikator kontekstu jest zwracany do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu obiektu, z którym został zidentyfikowany. Zapoznaj [się z artykułem internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

##  <a name="getfileurl"></a>CHttpFile::GetFileURL

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę pliku HTTP jako adres URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający adres URL odwołujący się do zasobu skojarzonego z tym plikiem.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego tylko po pomyślnym wywołaniu [SendRequest](#sendrequest) lub `CHttpFile` obiektu, który został pomyślnie utworzony przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getobject"></a>CHttpFile:: GetObject

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę skojarzonego z `CHttpFile`nim obiektu.

```
CString GetObject() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający nazwę obiektu.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego tylko po pomyślnym wywołaniu [SendRequest](#sendrequest) lub `CHttpFile` obiektu, który został pomyślnie utworzony przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getverb"></a>CHttpFile:: getverb

Wywołaj tę funkcję elementu członkowskiego, aby pobrać czasownik HTTP (lub metodę) `CHttpFile`skojarzoną z tym elementem.

```
CString GetVerb() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający nazwę czasownika http (lub metody).

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego tylko po pomyślnym wywołaniu [SendRequest](#sendrequest) lub `CHttpFile` obiektu, który został pomyślnie utworzony przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="queryinfo"></a>CHttpFile::QueryInfo

Wywołaj tę funkcję elementu członkowskiego, aby zwrócić odpowiedź lub nagłówki żądań z żądania HTTP.

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

*dwInfoLevel*<br/>
Kombinacja atrybutu do zapytania i następujących flag, które określają typ żądanych informacji:

- HTTP_QUERY_CUSTOM odnajduje nazwę nagłówka i zwraca tę wartość w *lpvBuffer* w danych wyjściowych. HTTP_QUERY_CUSTOM zgłasza potwierdzenie, jeśli nagłówek nie zostanie znaleziony.

- HTTP_QUERY_FLAG_REQUEST_HEADERS zazwyczaj aplikacja wysyła zapytanie do nagłówków odpowiedzi, ale aplikacja może również wysyłać zapytania do nagłówków żądań za pomocą tej flagi.

- HTTP_QUERY_FLAG_SYSTEMTIME dla tych nagłówków, których wartością jest ciąg daty/godziny, taki jak "godzina ostatniej modyfikacji," Ta flaga zwraca wartość nagłówka jako standardową strukturę [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) Win32, która nie wymaga, aby aplikacja mogła analizować dane. Jeśli używasz tej flagi, możesz chcieć użyć `SYSTEMTIME` przesłonięcia funkcji.

- HTTP_QUERY_FLAG_NUMBER dla tych nagłówków, których wartość jest liczbą, taką jak kod stanu, ta flaga zwraca dane jako liczbę 32-bitową.

Listę możliwych wartości można znaleźć w sekcji **uwagi** .

*lpvBuffer*<br/>
Wskaźnik do buforu, który odbiera informacje.

*lpdwBufferLength*<br/>
We wpisie wskazuje wartość zawierającą długość buforu danych w postaci liczby znaków lub bajtów. Zobacz sekcję **uwagi** , aby uzyskać bardziej szczegółowe informacje o tym parametrze.

*lpdwIndex*<br/>
Wskaźnik na indeks nagłówka liczony od zera. Może mieć wartość NULL. Użyj tej flagi, aby wyliczyć wiele nagłówków o tej samej nazwie. Na wejściu *lpdwIndex* wskazuje indeks określonego nagłówka do zwrócenia. W danych wyjściowych *lpdwIndex* wskazuje indeks następnego nagłówka. Jeśli nie można znaleźć następnego indeksu, zwracany jest ERROR_HTTP_HEADER_NOT_FOUND.

*str*<br/>
Odwołanie do obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) otrzymującego zwrócone informacje.

*dwIndex*<br/>
Wartość indeksu. Zobacz *lpdwIndex*.

*pSysTime*<br/>
Wskaźnik do struktury [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) Win32.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego tylko po pomyślnym wywołaniu [SendRequest](#sendrequest) lub `CHttpFile` obiektu, który został pomyślnie utworzony przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Następujące typy danych można pobrać z `QueryInfo`:

- ciągi (wartość domyślna)

- `SYSTEMTIME`(dla "dane:" "wygasa:" itd.)

- DWORD (dla STATUS_CODE, CONTENT_LENGTH itd.)

Gdy ciąg jest zapisywana w buforze, a funkcja członkowska powiedzie się `lpdwBufferLength` , zawiera długość ciągu znaków minus 1 dla kończącego znaku null.

Możliwe wartości *dwInfoLevel* obejmują:

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

##  <a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać kod stanu skojarzony z żądaniem HTTP i umieść go w podanym parametrze *dwStatusCode* .

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parametry

*dwStatusCode*<br/>
Odwołanie do kodu stanu. Kody stanu wskazują na powodzenie lub niepowodzenie żądanego zdarzenia. Zobacz **uwagi** , aby wybrać opisy kodów stanu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego tylko po pomyślnym wywołaniu [SendRequest](#sendrequest) lub `CHttpFile` obiektu, który został pomyślnie utworzony przez [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Kody stanu HTTP znajdują się w grupach wskazujących powodzenie lub niepowodzenie żądania. W poniższych tabelach przedstawiono grupy kodów stanu i Najczęstsze kody stanu HTTP.

|Grupa|Znaczenie|
|-----------|-------------|
|200-299|Powodzenie|
|300-399|Informacje|
|400-499|Błąd żądania|
|500-599|Błąd serwera|

Typowe kody stanu HTTP:

|Kod stanu|Znaczenie|
|-----------------|-------------|
|200|Zlokalizowany adres URL, transmisja następuje|
|400|Niezrozumiałe żądanie|
|404|Nie znaleziono żądanego adresu URL|
|405|Serwer nie obsługuje żądanej metody|
|500|Nieznany błąd serwera|
|503|Osiągnięto pojemność serwera|

##  <a name="sendrequest"></a>CHttpFile::SendRequest

Wywołaj tę funkcję elementu członkowskiego, aby wysłać żądanie do serwera HTTP.

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

*pstrHeaders*<br/>
Wskaźnik do ciągu zawierającego nazwę nagłówków do wysłania.

*dwHeadersLen*<br/>
Długość nagłówków identyfikowanych przez *pstrHeaders*.

*lpOptional*<br/>
Wszystkie opcjonalne dane do wysłania natychmiast po nagłówkach żądań. Jest to zwykle używane dla operacji POST i PUT. Może to być wartość NULL, jeśli nie ma żadnych opcjonalnych danych do wysłania.

*dwOptionalLen*<br/>
Długość *lpOptional*.

*strHeaders*<br/>
Ciąg zawierający nazwę nagłówków dla wysyłanego żądania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie zakończy się niepowodzeniem, ustal przyczynę niepowodzenia, badając zgłoszony obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) .

##  <a name="sendrequestex"></a>CHttpFile::SendRequestEx

Wywołaj tę funkcję elementu członkowskiego, aby wysłać żądanie do serwera HTTP.

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

*dwTotalLen*<br/>
Liczba bajtów do wysłania w żądaniu.

*flagiDW*<br/>
Flagi opisujące operację. Aby uzyskać listę odpowiednich flag, zobacz [HttpSendRequestEx](/windows/desktop/api/wininet/nf-wininet-httpsendrequestexa) w Windows SDK.

*dwContext*<br/>
Identyfikator kontekstu dla `CHttpFile` operacji. Aby uzyskać więcej informacji o tym parametrze, zobacz uwagi.

*lpBuffIn*<br/>
Wskaźnik do zainicjowanej [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-internet_buffersa) , który opisuje bufor wejściowy używany do operacji.

*lpBuffOut*<br/>
Wskaźnik do zainicjowanej INTERNET_BUFFERS, który opisuje bufor wyjściowy używany dla operacji.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera. Jeśli wywołanie zakończy się niepowodzeniem, ustal przyczynę niepowodzenia, badając zgłoszony obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia aplikacji wysyłanie danych przy użyciu metod `CInternetFile` [Write](../../mfc/reference/cinternetfile-class.md#write) i [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) . Musisz znać długość danych do wysłania przed wywołaniem przesłonięcia tej funkcji. Pierwsze zastąpienie pozwala określić długość danych, które chcesz wysłać. Drugie zastąpienie akceptuje wskaźniki do struktur INTERNET_BUFFERS, które mogą być używane do opisywania buforu w bardzo szczegółowy sposób.

Po zapisaniu zawartości w pliku Wywołaj [EndRequest](#endrequest) , aby zakończyć operację.

Wartość domyślna parametru *dwContext* jest wysyłana przez MFC do `CHttpFile` obiektu z obiektu [](../../mfc/reference/cinternetsession-class.md) `CHttpFile` CInternetSession, który utworzył obiekt. W przypadku wywołania [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection](../../mfc/reference/chttpconnection-class.md) `CHttpFile` w celu skonstruowania obiektu można zastąpić wartość domyślną, aby ustawić identyfikator kontekstu na wybraną przez siebie zawartość. Identyfikator kontekstu jest zwracany do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu obiektu, z którym został zidentyfikowany. Zapoznaj się [z artykułem internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

### <a name="example"></a>Przykład

Ten fragment kodu wysyła zawartość ciągu do biblioteki DLL o nazwie MFCISAPI. DLL na serwerze LOCALHOST. Chociaż w tym przykładzie użyto tylko jednego wywołania `WriteString`do, akceptowalne jest użycie wielu wywołań do wysyłania danych w blokach.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)
