---
title: Klasa CHttpFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e9af23bb74ba8e96f29a5b7cc4139d2932df8c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="chttpfile-class"></a>Klasa CHttpFile
Udostępnia funkcje do żądania i odczytywać pliki na serwerze HTTP.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CHttpFile : public CInternetFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHttpFile::CHttpFile](#chttpfile)|Tworzy `CHttpFile` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Dodaje nagłówki żądania wysyłane do serwera HTTP.|  
|[CHttpFile::EndRequest](#endrequest)|Kończy żądanie wysłane do serwera HTTP o [SendRequestEx](#sendrequestex) funkcję elementu członkowskiego.|  
|[CHttpFile::GetFileURL](#getfileurl)|Pobiera adres URL dla określonego pliku.|  
|[CHttpFile::GetObject](#getobject)|Pobiera obiekt docelowy zlecenia żądanie do serwera HTTP.|  
|[CHttpFile::GetVerb](#getverb)|Pobiera czasownika, który został użyty w żądaniu skierowanym do serwera HTTP.|  
|[CHttpFile::QueryInfo](#queryinfo)|Zwraca nagłówki odpowiedzi lub żądanie z serwera HTTP.|  
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Pobiera kod stanu skojarzony z żądaniem HTTP i umieszczenie ich w podane `dwStatusCode` parametru.|  
|[CHttpFile::SendRequest](#sendrequest)|Wysyła żądanie do serwera HTTP.|  
|[CHttpFile::SendRequestEx](#sendrequestex)|Wysyła żądanie do serwera HTTP przy użyciu [zapisu](../../mfc/reference/cinternetfile-class.md#write) lub [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) metody `CInternetFile`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli sesja Internet odczytuje dane z serwera HTTP, należy utworzyć wystąpienie `CHttpFile`.  
  
 Aby dowiedzieć się więcej na temat `CHttpFile` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders  
 Wywołanie tej funkcji elementu członkowskiego, aby dodać jeden lub więcej nagłówków żądań HTTP na żądanie HTTP dojścia.  
  
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
 `pstrHeaders`  
 Wskaźnik do ciąg zawierający nagłówek lub nagłówków, aby dołączyć do żądania. Każdy nagłówek musi być zakończona pary CR/LF.  
  
 `dwFlags`  
 Zmienia semantykę nowe nagłówki. Może to być jedna z następujących czynności:  
  
- `HTTP_ADDREQ_FLAG_COALESCE`Scala nagłówków o takiej samej nazwie, za pomocą flagi, aby dodać pierwszy nagłówek znaleziono do kolejnych nagłówka. Na przykład "Zaakceptuj: tekst / *" następuje "Zaakceptuj: audio /\*" powoduje utworzenie pojedynczego nagłówka "Zaakceptuj: tekst /\*audio /\*". Jest wywoływania aplikacji w celu zapewnienia spójnego schematu względem danych otrzymywanych przez żądania wysyłane z nagłówkami scalone lub osobnych.  
  
- `HTTP_ADDREQ_FLAG_REPLACE`Wykonuje Usuń i Dodaj zastąpienie bieżącego nagłówka. Nazwa nagłówka będzie służyć do usunięcia bieżącego nagłówka i zostanie użyta wartość pełne Aby dodać nowy nagłówek. Jeśli wartość nagłówka jest pusta i nagłówek zostanie znaleziony, zostanie ono usunięte. Jeśli nie jest pusta, zostanie zastąpiony wartość nagłówka.  
  
- `HTTP_ADDREQ_FLAG_ADD_IF_NEW`Dodaje nagłówek tylko, jeśli jeszcze nie istnieje. Jeśli istnieje, zwracany jest błąd.  
  
- `HTTP_ADDREQ_FLAG_ADD`Używane z ZAMIEŃ. Dodaje nagłówek, jeśli nie istnieje.  
  
 `dwHeadersLen`  
 Długość w znakach, z `pstrHeaders`. Jeśli jest to L-1, następnie `pstrHeaders` muszą być zakończony zerem i długość jest kolumną obliczaną.  
  
 `str`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który zawiera nagłówek żądania lub nagłówków do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 `AddRequestHeaders`Dołącza nagłówki dodatkowych, w dowolnym formacie Obsługa żądania HTTP. Jest przeznaczony do użytku przez zaawansowane klientów, którzy potrzebują szczegółową kontrolę nad dokładne żądanie wysłane do serwera HTTP.  
  
> [!NOTE]
>  Aplikacja może przekazać wiele nagłówków w `pstrHeaders` lub `str` dla `AddRequestHeaders` wywołanie przy użyciu `HTTP_ADDREQ_FLAG_ADD` lub `HTTP_ADDREQ_FLAG_ADD_IF_NEW`. Jeśli aplikacja próbuje usunąć lub zamienić nagłówka przy użyciu **HTTP_ADDREQ_FLAG_REMOVE** lub `HTTP_ADDREQ_FLAG_REPLACE`, można podać tylko jeden nagłówek w `lpszHeaders`.  
  
##  <a name="chttpfile"></a>CHttpFile::CHttpFile  
 Ta funkcja elementu członkowskiego jest wywoływana w celu utworzenia `CHttpFile` obiektu.  
  
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
 `hFile`  
 Dojście do pliku internetowych.  
  
 `hSession`  
 Dojście do sesji Internetu.  
  
 *pstrObject*  
 Wskaźnik do ciągu zawierającego `CHttpFile` obiektu.  
  
 `pstrServer`  
 Wskaźnik do ciąg zawierający nazwę serwera.  
  
 `pstrVerb`  
 Wskaźnik do ciąg zawierający metody, które będą używane podczas wysyłania żądania. Może być **POST**, **HEAD**, lub `GET`.  
  
 dwContext  
 Identyfikator kontekstu `CHttpFile` obiektu. Zobacz **uwagi** uzyskać więcej informacji dotyczących tego parametru.  
  
 `pConnection`  
 Wskaźnik do [CHttpConnection](../../mfc/reference/chttpconnection-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie skonstruować `CHttpFile` obiektu bezpośrednio; zamiast wywoływać [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) zamiast tego.  
  
 Wartość domyślna dla `dwContext` są wysyłane przez MFC do `CHttpFile` obiekt z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CHttpFile` obiektu. Podczas wywoływania `CInternetSession::OpenURL` lub `CHttpConnection` do skonstruowania `CHttpFile` obiektu, można zastąpić domyślną ustawioną wartość wybrane identyfikator kontekstu. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którym zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="endrequest"></a>CHttpFile::EndRequest  
 Wywołanie tej funkcji Członkowskich do zakończenia żądania wysyłane do serwera HTTP o [SendRequestEx](#sendrequestex) funkcję elementu członkowskiego.  
  
```  
BOOL EndRequest(
    DWORD dwFlags = 0,  
    LPINTERNET_BUFFERS lpBuffIn = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Flagi opisujące operację. Listę odpowiednich flagi, zawiera [HttpEndRequest](http://msdn.microsoft.com/library/windows/desktop/aa384230) w zestawie Windows SDK.  
  
 `lpBuffIn`  
 Wskaźnik do zainicjowane [INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132) opisujący buforu wejściowego używany dla tej operacji.  
  
 `dwContext`  
 Identyfikator kontekstu `CHttpFile` operacji. Aby uzyskać więcej informacji o tym parametrze, zobacz uwagi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. Jeśli połączenie nie powiedzie się, należy określić przyczynę niepowodzenia, sprawdzając zgłoszenia [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wartość domyślna dla `dwContext` są wysyłane przez MFC do `CHttpFile` obiekt z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CHttpFile` obiektu. Podczas wywoływania [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection](../../mfc/reference/chttpconnection-class.md) do skonstruowania `CHttpFile` obiektu, można zastąpić domyślną ustawioną wartość wybrane identyfikator kontekstu. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którym zostanie zidentyfikowana. Zobacz artykuł [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="getfileurl"></a>CHttpFile::GetFileURL  
 Wywołanie tej funkcji członkowskich można pobrać nazwy pliku HTTP jako adres URL.  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający adres URL odwołuje się do zasobów skojarzona z tym plikiem.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji Członkowskich dopiero po pomyślnym nawiązaniu połączenia z [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getobject"></a>CHttpFile::GetObject  
 Wywołanie tej funkcji Członkowskich nazwy obiektów skojarzonych z tym `CHttpFile`.  
  
```  
CString GetObject() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający nazwę obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji Członkowskich dopiero po pomyślnym nawiązaniu połączenia z [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getverb"></a>CHttpFile::GetVerb  
 Wywołanie tej funkcji Członkowskich uzyskanie HTTP zlecenia (lub metody) skojarzony z tym `CHttpFile`.  
  
```  
CString GetVerb() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający nazwę zlecenie HTTP (lub metody).  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji Członkowskich dopiero po pomyślnym nawiązaniu połączenia z [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="queryinfo"></a>CHttpFile::QueryInfo  
 Wywołanie tej funkcji Członkowskich zwracać odpowiedzi lub nagłówki żądań z żądania HTTP.  
  
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
 `dwInfoLevel`  
 Kombinacja atrybutu z zapytania i następujące flagi, które określają typ żądanych informacji:  
  
- **HTTP_QUERY_CUSTOM** znajduje nazwę nagłówka i zwraca tę wartość w `lpvBuffer` w danych wyjściowych. **HTTP_QUERY_CUSTOM** zgłasza wyjątek potwierdzenia, jeśli nie zostanie odnaleziony nagłówka.  
  
- **HTTP_QUERY_FLAG_REQUEST_HEADERS** zwykle aplikacja odwołuje się nagłówki odpowiedzi, ale aplikacja także zbadać nagłówki żądania przy użyciu tej flagi.  
  
- **HTTP_QUERY_FLAG_SYSTEMTIME** dla tych nagłówków, którego wartość jest ciągiem daty/godziny, takie jak "Ostatniej modyfikacji-czasu," Ta flaga zwraca wartość nagłówka jako standardowa Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury, która nie wymaga Aplikacja do analizy danych. Jeśli używasz tej flagi, warto użyć `SYSTEMTIME` przesłonić funkcji.  
  
- **HTTP_QUERY_FLAG_NUMBER** dla tych nagłówków, którego wartość jest liczbą, takie jak kod stanu tej flagi zwraca dane jako 32-bitową liczbą.  
  
 Zobacz **uwagi** sekcja zawiera listę możliwych wartości.  
  
 `lpvBuffer`  
 Wskaźnik do buforu, który odbiera dane.  
  
 `lpdwBufferLength`  
 Na wejściu wskazuje to na wartość zawierającą długości buforu danych w liczbie znaków lub bajtów. Zobacz **uwagi** sekcji, aby uzyskać szczegółowe informacje na temat tego parametru.  
  
 `lpdwIndex`  
 Wskaźnik do indeksu nagłówka liczony od zera. Może być **NULL**. Użyj tej flagi wyliczyć wiele nagłówków o takiej samej nazwie. W danych wejściowych `lpdwIndex` wskazuje indeks określony nagłówek do zwrócenia. W danych wyjściowych `lpdwIndex` wskazuje indeks następnego nagłówka. Jeśli nie można odnaleźć następnego indeksu, **ERROR_HTTP_HEADER_NOT_FOUND** jest zwracany.  
  
 `str`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiektu odbierającego zwrócone informacje.  
  
 `dwIndex`  
 Wartość indeksu. Zobacz `lpdwIndex`.  
  
 *pSysTime*  
 Wskaźnik do Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji Członkowskich dopiero po pomyślnym nawiązaniu połączenia z [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Możesz pobrać następujące typy danych z `QueryInfo`:  
  
-   ciągi (ustawienie domyślne)  
  
- `SYSTEMTIME`(dla "danych:" "Data wygaśnięcia:" etc, nagłówki)  
  
- `DWORD`(dla **STATUS_CODE**, **CONTENT_LENGTH**itp.)  
  
 Po ciągu są zapisywane w buforze, a funkcja członkowska zakończy się powodzeniem, `lpdwBufferLength` zawiera długość ciągu znakami pomniejszonej o 1 dla przerywanie **NULL** znaków.  
  
 Możliwe `dwInfoLevel` wartości to:  
  
- **HTTP_QUERY_MIME_VERSION**  
  
- **HTTP_QUERY_CONTENT_TYPE**  
  
- **HTTP_QUERY_CONTENT_TRANSFER_ENCODING**  
  
- **HTTP_QUERY_CONTENT_ID**  
  
- **HTTP_QUERY_CONTENT_DESCRIPTION**  
  
- **HTTP_QUERY_CONTENT_LENGTH**  
  
- **HTTP_QUERY_ALLOWED_METHODS**  
  
- **HTTP_QUERY_PUBLIC_METHODS**  
  
- **HTTP_QUERY_DATE**  
  
- **HTTP_QUERY_EXPIRES**  
  
- **HTTP_QUERY_LAST_MODIFIED**  
  
- **HTTP_QUERY_MESSAGE_ID**  
  
- **HTTP_QUERY_URI**  
  
- **HTTP_QUERY_DERIVED_FROM**  
  
- **HTTP_QUERY_LANGUAGE**  
  
- **HTTP_QUERY_COST**  
  
- **HTTP_QUERY_WWW_LINK**  
  
- **HTTP_QUERY_PRAGMA**  
  
- **HTTP_QUERY_VERSION**  
  
- **HTTP_QUERY_STATUS_CODE**  
  
- **HTTP_QUERY_STATUS_TEXT**  
  
- **HTTP_QUERY_RAW_HEADERS**  
  
- **HTTP_QUERY_RAW_HEADERS_CRLF**  
  
##  <a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode  
 Wywołanie tej funkcji członkowskich można pobrać kodu stan skojarzony z żądaniem HTTP i umieszczenie go w podane `dwStatusCode` parametru.  
  
```  
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwStatusCode`  
 Odwołanie do kodu stanu. Kody stanu oznaczający powodzenie lub niepowodzenie żądane zdarzenie. Zobacz **uwagi** wyboru opisy kodów stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji Członkowskich dopiero po pomyślnym nawiązaniu połączenia z [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Kody stanu HTTP należą do grup oznaczający powodzenie lub Niepowodzenie żądania. Poniższe tabele przedstawiają grup kodów stanu i najbardziej typowe kody stanu HTTP.  
  
|Grupa|Znaczenie|  
|-----------|-------------|  
|200-299|Powodzenie|  
|300-399|Informacje|  
|400-499|Błąd żądania|  
|500-599|Błąd serwera|  
  
 Typowe kody stanu HTTP:  
  
|Kod stanu|Znaczenie|  
|-----------------|-------------|  
|200|Adres URL znajduje się, sposób przekazywania|  
|400|Żądanie niezrozumiałe|  
|404|Żądany adres URL nie znaleźć.|  
|405|Serwer nie obsługuje żądanego — metoda|  
|500|Nieznany błąd serwera|  
|503|Osiągnięto pojemności serwera|  
  
##  <a name="sendrequest"></a>CHttpFile::SendRequest  
 Wywołanie tej funkcji Członkowskich, aby wysłać żądania do serwera HTTP.  
  
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
 `pstrHeaders`  
 Wskaźnik do ciąg zawierający nazwę nagłówków do wysłania.  
  
 `dwHeadersLen`  
 Długość nagłówków identyfikowane przez `pstrHeaders`.  
  
 `lpOptional`  
 Opcjonalnymi danymi wysłać natychmiast po nagłówki żądania. Jest to zazwyczaj używane do **POST** i **PUT** operacji. Może to być **NULL** Jeśli nie ma żadnych opcjonalne danych do wysyłania.  
  
 *dwOptionalLen*  
 Długość `lpOptional`.  
  
 `strHeaders`  
 Ciąg zawierający nazwę nagłówki dla żądania wysyłane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. Jeśli połączenie nie powiedzie się, należy określić przyczynę niepowodzenia, sprawdzając zgłoszenia [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
##  <a name="sendrequestex"></a>CHttpFile::SendRequestEx  
 Wywołanie tej funkcji Członkowskich, aby wysłać żądania do serwera HTTP.  
  
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
 *dwTotalLen*  
 Liczba bajtów do wysłania w żądaniu.  
  
 `dwFlags`  
 Flagi opisujące operację. Listę odpowiednich flagi, zawiera [HttpSendRequestEx](http://msdn.microsoft.com/library/windows/desktop/aa384318) w zestawie Windows SDK.  
  
 `dwContext`  
 Identyfikator kontekstu `CHttpFile` operacji. Aby uzyskać więcej informacji o tym parametrze, zobacz uwagi.  
  
 `lpBuffIn`  
 Wskaźnik do zainicjowane [INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132) opisujący buforu wejściowego używany dla tej operacji.  
  
 *lpBuffOut*  
 Wskaźnik do zainicjowane **INTERNET_BUFFERS** opisujący buforu wyjściowego używany dla tej operacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie. Jeśli połączenie nie powiedzie się, należy określić przyczynę niepowodzenia, sprawdzając zgłoszenia [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja umożliwia aplikacji do przesyłania danych za pomocą [zapisu](../../mfc/reference/cinternetfile-class.md#write) i [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) metody `CInternetFile`. Należy znać długość danych do wysyłania przed wywołaniem albo zastąpienie tej funkcji. Pierwszy zastąpienie umożliwia określenie długości danych, które chcesz wysyłać. Drugi zastąpienie akceptuje wskaźniki do **INTERNET_BUFFERS** struktur, które mogą być używane do opisywania buforu szczegółowo.  
  
 Po zapisaniu zawartości do pliku, należy wywołać [EndRequest](#endrequest) aby zakończyć operację.  
  
 Wartość domyślna dla `dwContext` są wysyłane przez MFC do `CHttpFile` obiekt z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CHttpFile` obiektu. Podczas wywoływania [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection](../../mfc/reference/chttpconnection-class.md) do skonstruowania `CHttpFile` obiektu, można zastąpić domyślną ustawioną wartość wybrane identyfikator kontekstu. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którym zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
### <a name="example"></a>Przykład  
 Fragmentu kodu wysyła zawartość ciągu o nazwie MFCISAPI biblioteki DLL. Biblioteki DLL na serwerze hosta lokalnego. Gdy w tym przykładzie użyto tylko jedno wywołanie `WriteString`, dopuszczalny jest użycie wielu wywołań do wysyłania danych w blokach.  
  
 [!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Cgopherfile — klasa](../../mfc/reference/cgopherfile-class.md)   
 [Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)
