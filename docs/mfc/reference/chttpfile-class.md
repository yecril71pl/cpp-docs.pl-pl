---
title: Klasa CHttpFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 422952ae459d6a6e4d9f768eb111c9c01cfbb5d0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219745"
---
# <a name="chttpfile-class"></a>Klasa CHttpFile
Oferuje funkcje w celu zażądania i odczytania plików na serwerze HTTP.  
  
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
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Dodaje nagłówki żądania wysłanego do serwera HTTP.|  
|[CHttpFile::EndRequest](#endrequest)|Kończy się w przypadku żądania wysyłanego do serwera HTTP o [SendRequestEx](#sendrequestex) funkcja elementu członkowskiego.|  
|[CHttpFile::GetFileURL](#getfileurl)|Pobiera adres URL dla określonego pliku.|  
|[CHttpFile::GetObject](#getobject)|Pobiera obiekt docelowy zlecenie w ramach żądania do serwera HTTP.|  
|[CHttpFile::GetVerb](#getverb)|Pobiera zlecenia, który został użyty w żądaniu skierowanym do serwera HTTP.|  
|[CHttpFile::QueryInfo](#queryinfo)|Zwraca nagłówki żądania lub odpowiedzi z serwera HTTP.|  
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Pobiera kod stanu skojarzony z żądaniem HTTP i umieszcza je w podanym `dwStatusCode` parametru.|  
|[CHttpFile::SendRequest](#sendrequest)|Wysyła żądanie do serwera HTTP.|  
|[CHttpFile::SendRequestEx](#sendrequestex)|Wysyła żądanie do serwera HTTP za pomocą [zapisu](../../mfc/reference/cinternetfile-class.md#write) lub [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) metody `CInternetFile`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli sesja Internet odczytuje dane z serwera HTTP, należy utworzyć wystąpienie `CHttpFile`.  
  
 Aby dowiedzieć się więcej o tym, jak `CHttpFile` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="addrequestheaders"></a>  CHttpFile::AddRequestHeaders  
 Wywołanie tej funkcji elementu członkowskiego, aby dodać jeden lub więcej nagłówków żądania HTTP do żądania HTTP obsługi.  
  
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
 *pstrHeaders*  
 Wskaźnik do ciągu zawierającego nagłówek lub nagłówki, aby dołączyć do żądania. Każdy nagłówek musi się kończyć znakiem pary CR/LF.  
  
 *Flagidw*  
 Zmienia semantykę nowe nagłówki. Może to być jeden z następujących elementów:  
  
- Scala HTTP_ADDREQ_FLAG_COALESCE nagłówki o takiej samej nazwie, przy użyciu flagi, aby dodać pierwszy nagłówek się kolejne nagłówka. Na przykład "Akceptuj: tekst /\*" następuje "Akceptuj: audio /\*" powoduje utworzenie pojedynczego nagłówka "Akceptuj: tekst /\*audio /\*". Jest aplikacji wywołującej, aby zapewnić spójny schemat w odniesieniu do danych otrzymywanych przez żądań wysyłanych z nagłówkami połączonych lub oddzielne.  
  
- HTTP_ADDREQ_FLAG_REPLACE wykonuje Usuń i Dodaj zastąpienie bieżącego nagłówka. Nazwa nagłówka będzie służyć do usunięcia bieżącego nagłówka, a pełną wartość będzie służyć do dodawania nowego nagłówka. Jeśli wartość nagłówka jest pusta, i nagłówek zostanie znaleziony, zostaną usunięte. W przeciwnym razie wartość nagłówka puste, zostanie zastąpiony.  
  
- Dodaje nagłówek HTTP_ADDREQ_FLAG_ADD_IF_NEW tylko, jeśli jeszcze nie istnieje. Jeśli istnieje, zwracany jest błąd.  
  
- HTTP_ADDREQ_FLAG_ADD używane z Zastąp. Dodaje nagłówek, jeśli nie istnieje.  
  
 *dwHeadersLen*  
 Długość w znakach, z *pstrHeaders*. Jeśli jest to wartość-1 L, następnie *pstrHeaders* zostanie uznany za zakończony zerem i długość jest kolumną obliczaną.  
  
 *str*  
 Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który zawiera nagłówek żądania lub nagłówków, które mają zostać dodane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 `AddRequestHeaders` dołącza dodatkowych, formacie nagłówki do realizacji żądania HTTP. Jest przeznaczony do użytku przez zaawansowanych klientów, którzy potrzebują szczegółową kontrolę nad dokładnie żądania wysłanego do serwera HTTP.  
  
> [!NOTE]
>  Aplikację można przekazać wiele nagłówków w *pstrHeaders* lub *str* dla `AddRequestHeaders` wywołać za pomocą HTTP_ADDREQ_FLAG_ADD lub HTTP_ADDREQ_FLAG_ADD_IF_NEW. Jeśli aplikacja próbuje usunąć lub zamienić nagłówek używający HTTP_ADDREQ_FLAG_REMOVE lub HTTP_ADDREQ_FLAG_REPLACE, tylko jeden nagłówek mogą być podawane w *lpszHeaders*.  
  
##  <a name="chttpfile"></a>  CHttpFile::CHttpFile  
 Ta funkcja członkowska jest wywoływana, aby skonstruować `CHttpFile` obiektu.  
  
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
 *hFile —*  
 Dojście do pliku Internet.  
  
 *hSession*  
 Dojście do sesji Internetu.  
  
 *pstrObject*  
 Wskaźnik do ciągu zawierającego `CHttpFile` obiektu.  
  
 *pstrServer*  
 Wskaźnik do ciągu zawierającego nazwę serwera.  
  
 *pstrVerb*  
 Wskaźnik do ciągu zawierającego metodę, która ma być używany podczas wysyłania żądania. Może być POST i HEAD, lub UZYSKAĆ.  
  
 *dwContext*  
 Identyfikator kontekstu `CHttpFile` obiektu. Zobacz **uwagi** uzyskać więcej informacji dotyczących tego parametru.  
  
 *pConnection*  
 Wskaźnik do [CHttpConnection](../../mfc/reference/chttpconnection-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie konstruowania `CHttpFile` obiektu bezpośrednio, zamiast zaproszenia [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) zamiast tego.  
  
 Wartością domyślną dla `dwContext` są wysyłane przez MFC, aby `CHttpFile` obiektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CHttpFile` obiektu. Gdy wywołujesz `CInternetSession::OpenURL` lub `CHttpConnection` do konstruowania `CHttpFile` obiektu, można zastąpić domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którą jest identyfikowany. Zapoznaj się z artykułem [Internet pierwszych kroków: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="endrequest"></a>  CHttpFile::EndRequest  
 Wywołaj tę funkcję elementu członkowskiego, aby zakończyć żądania wysyłane do serwera HTTP o [SendRequestEx](#sendrequestex) funkcja elementu członkowskiego.  
  
```  
BOOL EndRequest(
    DWORD dwFlags = 0,  
    LPINTERNET_BUFFERS lpBuffIn = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 *Flagidw*  
 Flagi opisujące wykonać operację. Aby uzyskać listę flag odpowiednie zobacz [HttpEndRequest](/windows/desktop/api/wininet/nf-wininet-httpendrequesta) w zestawie Windows SDK.  
  
 *lpBuffIn*  
 Wskaźnik do zainicjowane [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa) opisujący buforu wejściowego używany podczas operacji.  
  
 *dwContext*  
 Identyfikator kontekstu `CHttpFile` operacji. Aby uzyskać więcej informacji o tym parametrze, zobacz uwagi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. Jeśli wywołanie zakończy się niepowodzeniem, należy określić przyczynę niepowodzenia, sprawdzając zgłoszony [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wartością domyślną dla *dwContext* są wysyłane przez MFC, aby `CHttpFile` obiektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CHttpFile` obiektu. Gdy wywołujesz [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection](../../mfc/reference/chttpconnection-class.md) do konstruowania `CHttpFile` obiektu, można zastąpić domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którą jest identyfikowany. Zobacz artykuł [Internet pierwszych kroków: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="getfileurl"></a>  CHttpFile::GetFileURL  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę pliku HTTP jako adres URL.  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający adres URL odwołuje się do zasobów skojarzonych z tym plikiem.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji elementu członkowskiego dopiero po pomyślnym wywołaniem [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getobject"></a>  CHttpFile::GetObject  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę obiektu skojarzonego z tym `CHttpFile`.  
  
```  
CString GetObject() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający nazwę obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji elementu członkowskiego dopiero po pomyślnym wywołaniem [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getverb"></a>  CHttpFile::GetVerb  
 Wywołaj tę funkcję elementu członkowskiego HTTP zlecenie (lub metoda) skojarzony z tym `CHttpFile`.  
  
```  
CString GetVerb() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający nazwę czasownik HTTP (lub metoda).  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji elementu członkowskiego dopiero po pomyślnym wywołaniem [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="queryinfo"></a>  CHttpFile::QueryInfo  
 Wywołaj tę funkcję elementu członkowskiego do zwracania odpowiedzi lub nagłówki żądań z żądania HTTP.  
  
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
 *dwInfoLevel*  
 Kombinacja atrybutu do zapytania i następujące flagi określające typ żądane informacje:  
  
- HTTP_QUERY_CUSTOM znajduje nazwę nagłówka i zwraca tę wartość w *lpvBuffer* w danych wyjściowych. HTTP_QUERY_CUSTOM zgłasza potwierdzenie, jeśli nie odnaleziono nagłówka.  
  
- HTTP_QUERY_FLAG_REQUEST_HEADERS zwykle aplikacja wykonuje zapytania nagłówki odpowiedzi, ale aplikacji można także badać nagłówki żądania przy użyciu tej flagi.  
  
- HTTP_QUERY_FLAG_SYSTEMTIME dla tych nagłówków, którego wartość jest ciągiem daty/godziny, np. "Ostatniej modyfikacji — czas," Flaga ta zwraca wartość nagłówka w jako standardowa Win32 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę, która nie wymaga aplikacji przeanalizować dane. Jeśli używasz tej flagi, warto użyć `SYSTEMTIME` przesłonić funkcji.  
  
- Ta flaga HTTP_QUERY_FLAG_NUMBER dla tych nagłówków, którego wartość jest liczbą, np. kod stanu zwraca dane jako wartość liczby 32-bitowej.  
  
 Zobacz **uwagi** sekcja zawiera listę możliwych wartości.  
  
 *lpvBuffer*  
 Wskaźnik do buforu, który otrzymuje informacje.  
  
 *lpdwBufferLength*  
 Przy uruchamianiu wskazuje to na wartość zawierająca długość buforu danych, liczby znaków lub liczbę bajtów. Zobacz **uwagi** sekcji, aby uzyskać szczegółowe informacje o tym parametrze.  
  
 *lpdwIndex*  
 Wskaźnik do indeksu zaczynającego się od zera nagłówka. Może mieć wartości NULL. Użyj tej flagi, aby wyliczyć wiele nagłówków o takiej samej nazwie. W danych wejściowych *lpdwIndex* wskazuje indeks określony nagłówek do zwrócenia. W danych wyjściowych *lpdwIndex* wskazuje indeks następnego nagłówka. Jeśli nie można odnaleźć następnego indeksu, zwracany jest ERROR_HTTP_HEADER_NOT_FOUND.  
  
 *str*  
 Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu odbierającego pobranych informacjach.  
  
 *dwIndex*  
 Wartość indeksu. Zobacz *lpdwIndex*.  
  
 *pSysTime*  
 Wskaźnik do systemu Win32 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji elementu członkowskiego dopiero po pomyślnym wywołaniem [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Możesz pobrać następujące typy danych z `QueryInfo`:  
  
-   ciągi (ustawienie domyślne)  
  
- `SYSTEMTIME` (Aby uzyskać "danych:" "Expires:" nagłówki itd,)  
  
- DWORD (w przypadku STATUS_CODE CONTENT_LENGTH, itp.)  
  
 Ciąg jest zapisywany w buforze, gdy funkcja elementu członkowskiego zakończy się powodzeniem, `lpdwBufferLength` zawiera długość ciągu znaków, minus 1 w przypadku końcowego znaku NULL.  
  
 Możliwe *dwInfoLevel* wartości obejmują:  
  
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
  
##  <a name="queryinfostatuscode"></a>  CHttpFile::QueryInfoStatusCode  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać kod stanu skojarzony z żądaniem HTTP i umieść go w podanym *dwStatusCode* parametru.  
  
```  
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwStatusCode*  
 Odwołanie do kodu stanu. Kody stanu oznaczający powodzenie lub niepowodzenie żądane zdarzenie. Zobacz **uwagi** wyboru opisów kodów stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji elementu członkowskiego dopiero po pomyślnym wywołaniem [wysłanie](#sendrequest) lub na `CHttpFile` pomyślnie utworzony przez obiekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Kody stanu HTTP można podzielić na grupy oznaczający powodzenie lub Niepowodzenie żądania. Poniższe tabele przedstawiają grup kodu stanu i najbardziej typowe kody stanu HTTP.  
  
|Grupa|Znaczenie|  
|-----------|-------------|  
|200-299|Powodzenie|  
|300-399|Informacje|  
|400-499|Błąd żądania|  
|500-599|Błąd serwera|  
  
 Typowe kody stanu HTTP:  
  
|Kod stanu:|Znaczenie|  
|-----------------|-------------|  
|200|Znajduje się adres URL przesyłania jest zgodna|  
|400|Niezrozumiały żądania|  
|404|Żądany adres URL nie znaleziono.|  
|405|Serwer nie obsługuje żądanej metody|  
|500|Nieznany błąd serwera|  
|503|Pojemność serwera osiągnięty|  
  
##  <a name="sendrequest"></a>  CHttpFile::SendRequest  
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
 *pstrHeaders*  
 Wskaźnik do ciągu zawierającego nazwę nagłówki do wysłania.  
  
 *dwHeadersLen*  
 Długość nagłówki identyfikowane przez *pstrHeaders*.  
  
 *lpOptional*  
 Opcjonalnymi danymi wysłać natychmiast po nagłówki żądania. Jest to zazwyczaj używane dla operacji POST i PUT. Może to być wartość NULL, jeśli nie ma żadnych danych opcjonalne do wysłania.  
  
 *dwOptionalLen*  
 Długość *lpOptional*.  
  
 *strHeaders*  
 Ciąg zawierający nazwę nagłówki dla żądania są wysyłane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. Jeśli wywołanie zakończy się niepowodzeniem, należy określić przyczynę niepowodzenia, sprawdzając zgłoszony [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
##  <a name="sendrequestex"></a>  CHttpFile::SendRequestEx  
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
 *dwTotalLen*  
 Liczba bajtów do wysłania w żądaniu.  
  
 *Flagidw*  
 Flagi opisujące wykonać operację. Aby uzyskać listę flag odpowiednie zobacz [HttpSendRequestEx](/windows/desktop/api/wininet/nf-wininet-httpsendrequestexa) w zestawie Windows SDK.  
  
 *dwContext*  
 Identyfikator kontekstu `CHttpFile` operacji. Aby uzyskać więcej informacji o tym parametrze, zobacz uwagi.  
  
 *lpBuffIn*  
 Wskaźnik do zainicjowane [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa) opisujący buforu wejściowego używany podczas operacji.  
  
 *lpBuffOut*  
 Wskaźnik do INTERNET_BUFFERS zainicjowane, opisujący bufor wyjściowy używany podczas operacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie. Jeśli wywołanie zakończy się niepowodzeniem, należy określić przyczynę niepowodzenia, sprawdzając zgłoszony [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja pozwala aplikacji na przesyłanie danych przy użyciu [zapisu](../../mfc/reference/cinternetfile-class.md#write) i [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) metody `CInternetFile`. Długość danych do wysłania przed wywołaniem albo override tę funkcję, musisz znać. Zastąpienie pierwsze pozwala określić długość danych, który chcesz wysłać. Drugi zastąpienie akceptuje wskaźniki do struktur INTERNET_BUFFERS, które mogą być używane do opisywania buforu bardzo szczegółowo.  
  
 Po zapisaniu zawartość do pliku, należy wywołać [EndRequest](#endrequest) o zakończeniu operacji.  
  
 Wartością domyślną dla *dwContext* są wysyłane przez MFC, aby `CHttpFile` obiektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CHttpFile` obiektu. Gdy wywołujesz [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) lub [CHttpConnection](../../mfc/reference/chttpconnection-class.md) do konstruowania `CHttpFile` obiektu, można zastąpić domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którą jest identyfikowany. Zapoznaj się z artykułem [Internet pierwszych kroków: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
### <a name="example"></a>Przykład  
 Ten fragment kodu wysyła zawartość ciągu z biblioteką DLL o nazwie MFCISAPI. Biblioteka DLL na serwerze hosta lokalnego. Chociaż w tym przykładzie użyto tylko jedno wywołanie `WriteString`, korzystając z wielu wywołań do przesyłania danych w blokach jest dopuszczalna.  
  
 [!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Cgopherfile — klasa](../../mfc/reference/cgopherfile-class.md)   
 [Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)
