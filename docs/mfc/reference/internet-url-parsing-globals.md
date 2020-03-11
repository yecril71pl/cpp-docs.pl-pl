---
title: Globals i pomocnicy analizowania internetowych adresów URL
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 310e4ffb3fc207d874e97ba1fac65f6f8cb41a31
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865811"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Globals i pomocnicy analizowania internetowych adresów URL

Gdy klient wysyła zapytanie do serwera internetowego, można użyć jednej z Globals analizy adresów URL, aby wyodrębnić informacje o kliencie. Funkcje pomocnika zapewniają inne funkcje internetowe.

## <a name="internet-url-parsing-globals"></a>Funkcje globalne do analizowania internetowych adresów URL

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Analizuje ciąg adresu URL i zwraca typ usługi i jej składniki.|
|[AfxParseURLEx](#afxparseurlex)|Analizuje ciąg adresu URL i zwraca typ usługi i jej składników, a także podanie nazwy użytkownika i hasła.|

## <a name="other-internet-helpers"></a>Inni pomocnicy Internetu

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Zgłasza wyjątek związany z połączeniem internetowym.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Określa typ dojścia internetowego.|

##  <a name="afxparseurl"></a>AfxParseURL

Ta globalna jest używana w [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>Parametry

*pstrURL*<br/>
Wskaźnik do ciągu zawierającego adres URL do przeanalizowania.

*dwServiceType*<br/>
Wskazuje typ usługi internetowej. Dopuszczalne są następujące wartości:

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
Pierwszy segment adresu URL następującego po typie usługi.

*strObject*<br/>
Obiekt, do którego odwołuje się adres URL (może być pusty).

*nPort*<br/>
Określana na podstawie fragmentów adresu URL serwera lub obiektu (jeśli istnieje).

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli adres URL został pomyślnie przeanalizowany; w przeciwnym razie wartość 0, jeśli jest pusta lub nie zawiera znanego typu usługi internetowej.

### <a name="remarks"></a>Uwagi

Analizuje on ciąg adresu URL i zwraca typ usługi i jej składniki.

Na przykład `AfxParseURL` analizuje adresy URL formularza *Service://Server/dir/dir/Object.ext:Port* i zwraca jego składniki przechowywane w następujący sposób:

*strServer* = = "serwer"

*strObject* = = "/dir/dir/Object/Object.ext"

*NPort* = = #port

*dwServiceType* = = #service

> [!NOTE]
>  Aby wywołać tę funkcję, projekt musi zawierać AFXINET. C.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxinet. h

##  <a name="afxparseurlex"></a>AfxParseURLEx

Ta funkcja globalna to rozszerzona wersja [AfxParseURL](#afxparseurl) i jest używana w [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*pstrURL*<br/>
Wskaźnik do ciągu zawierającego adres URL do przeanalizowania.

*dwServiceType*<br/>
Wskazuje typ usługi internetowej. Dopuszczalne są następujące wartości:

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
Pierwszy segment adresu URL następującego po typie usługi.

*strObject*<br/>
Obiekt, do którego odwołuje się adres URL (może być pusty).

*nPort*<br/>
Określana na podstawie fragmentów adresu URL serwera lub obiektu (jeśli istnieje).

*strUsername*<br/>
Odwołanie do obiektu `CString` zawierającego nazwę użytkownika.

*strPassword*<br/>
Odwołanie do obiektu `CString` zawierającego hasło użytkownika.

*flagiDW*<br/>
Flagi kontrolujące sposób analizowania adresu URL. Może być kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|ICU_DECODE|Konwertuj sekwencje ucieczki% XX na znaki.|
|ICU_NO_ENCODE|Nie należy konwertować niebezpiecznych znaków na sekwencję ucieczki.|
|ICU_NO_META|Nie usuwaj sekwencji meta (takich jak "\." i "\..") z adresu URL.|
|ICU_ENCODE_SPACES_ONLY|Zakoduj tylko spacje.|
|ICU_BROWSER_MODE|Nie Koduj ani Dekoduj znaków po znaku "#" lub "" i nie usuwaj odstępu kończącego po elemencie "". Jeśli ta wartość nie jest określona, cały adres URL jest zakodowany, a końcowy biały znak jest usuwany.|

Jeśli używasz domyślnej biblioteki MFC, która nie ma flag, funkcja konwertuje wszystkie niebezpieczne znaki i meta sekwencje (takie jak \\., \... i \\...) na sekwencje ucieczki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli adres URL został pomyślnie przeanalizowany; w przeciwnym razie wartość 0, jeśli jest pusta lub nie zawiera znanego typu usługi internetowej.

### <a name="remarks"></a>Uwagi

Analizuje on ciąg adresu URL i zwraca typ usługi i jej składników, a także podanie nazwy użytkownika i hasła. Flagi wskazują, w jaki sposób są obsługiwane niebezpieczne znaki.

> [!NOTE]
>  Aby wywołać tę funkcję, projekt musi zawierać AFXINET. C.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxinet. h

## <a name="afxgetinternethandletype"></a>AfxGetInternetHandleType

Użyj tej funkcji globalnej, aby określić typ dojścia internetowego.

### <a name="syntax"></a>Składnia

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parametry

*hQuery*<br/>
Dojście do zapytania internetowego.

### <a name="return-value"></a>Wartość zwracana

Wszystkie typy usług internetowych zdefiniowane przez usługę WININET. C. Zapoznaj się z sekcją uwagi, aby zapoznać się z listą tych usług internetowych. Jeśli dojście ma wartość NULL lub nie jest rozpoznawane, funkcja zwraca AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Uwagi

Poniższa lista zawiera możliwe typy internetowe zwrócone przez `AfxGetInternetHandleType`.

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
>  Aby wywołać tę funkcję, projekt musi zawierać AFXINET. C.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

## <a name="afxthrowinternetexception"></a>AfxThrowInternetException

Zgłasza wyjątek internetowy.

### <a name="syntax"></a>Składnia

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parametry

*dwContext*<br/>
Identyfikator kontekstu dla operacji, która spowodowała błąd. Wartość domyślna *dwContext* jest określana pierwotnie w [CInternetSession](cinternetsession-class.md) i jest przenoszona do klas pochodnych [CInternetConnection](cinternetconnection-class.md)i [CInternetFile](cinternetfile-class.md). Dla określonych operacji wykonywanych w ramach połączenia lub pliku zwykle zastępuje się wartością domyślną *dwContext* . Ta wartość jest następnie zwracana do [CInternetSession:: OnStatusCallback](cinternetsession-class.md#onstatuscallback) w celu zidentyfikowania stanu określonej operacji.

*Elemencie*<br/>
Błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Użytkownik jest odpowiedzialny za określenie przyczyny na podstawie kodu błędu systemu operacyjnego.

> [!NOTE]
>  Aby wywołać tę funkcję, projekt musi zawierać AFXINET. C.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

## <a name="see-also"></a>Zobacz także

[Makra i Globals](mfc-macros-and-globals.md)<br/>
[Klasa CInternetException](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
