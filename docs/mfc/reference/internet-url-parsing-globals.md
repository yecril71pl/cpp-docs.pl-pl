---
title: Internet URL analizowanie globals i pomocników
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 742b381ecb55c433d0f384174b7612fcc21e9716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356617"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet URL analizowanie globals i pomocników

Gdy klient wysyła zapytanie do serwera internetowego, można użyć jednego z globals analizy adresu URL wyodrębnić informacje o kliencie. Funkcje pomocnika zapewniają inne funkcje internetowe.

## <a name="internet-url-parsing-globals"></a>Funkcje globalne do analizowania internetowych adresów URL

|||
|-|-|
|[AfxParseURL (AfxParseURL)](#afxparseurl)|Analizuje ciąg adresu URL i zwraca typ usługi i jej składników.|
|[AfxParseURLEx](#afxparseurlex)|Analizuje ciąg adresu URL i zwraca typ usługi i jej składniki, a także podaje nazwę użytkownika i hasło.|

## <a name="other-internet-helpers"></a>Inni pomocnicy internetowi

|||
|-|-|
|[AfxThrowInternetEkceptacja](#afxthrowinternetexception)|Zgłasza wyjątek związany z połączeniem internetowym.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Określa typ dojścia internetowego.|

## <a name="afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL (AfxParseURL)

Ten globalny jest używany w [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>Parametry

*pstrURL (pstrURL)*<br/>
Wskaźnik do ciągu zawierającego adres URL, który ma być analizowany.

*dwStype usługi*<br/>
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

*strServer (strServer)*<br/>
Pierwszy segment adresu URL po typie usługi.

*strObiject (Obić)*<br/>
Obiekt, do który odwołuje się adres URL (może być pusty).

*Nport*<br/>
Określana na podstawie części serwera lub obiektu adresu URL, jeśli taka istnieje.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli adres URL został pomyślnie przeanalizowany; w przeciwnym razie 0, jeśli jest pusta lub nie zawiera znanego typu usługi internetowej.

### <a name="remarks"></a>Uwagi

Analizuje ciąg adresu URL i zwraca typ usługi i jej składników.

Na przykład `AfxParseURL` analizuje adresy URL formularza *service://server/dir/dir/object.ext:port* i zwraca jego składniki przechowywane w następujący sposób:

*strServer* == "serwer"

*strObject* == "/dir/dir/object/object.ext"

*nPort* == #port

*dwServiceType* == #service

> [!NOTE]
> Aby wywołać tę funkcję, projekt musi zawierać AFXINET. H.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxinet.h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx

Ta funkcja globalna jest rozszerzoną wersją [AfxParseURL](#afxparseurl) i jest używana w [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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

*pstrURL (pstrURL)*<br/>
Wskaźnik do ciągu zawierającego adres URL, który ma być analizowany.

*dwStype usługi*<br/>
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

*strServer (strServer)*<br/>
Pierwszy segment adresu URL po typie usługi.

*strObiject (Obić)*<br/>
Obiekt, do który odwołuje się adres URL (może być pusty).

*Nport*<br/>
Określana na podstawie części serwera lub obiektu adresu URL, jeśli taka istnieje.

*strUsername (strUsername)*<br/>
Odwołanie do `CString` obiektu zawierającego nazwę użytkownika.

*strPassword (hasło)*<br/>
Odwołanie do `CString` obiektu zawierającego hasło użytkownika.

*Dwflags*<br/>
Flagi kontrolujące sposób analizować adres URL. Może być kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|ICU_DECODE|Konwertuj sekwencje ucieczki %XX na znaki.|
|ICU_NO_ENCODE|Nie konwertuj niebezpiecznych znaków na sekwencję ucieczki.|
|ICU_NO_META|Nie usuwaj sekwencji meta (takich jak "\ ." i "\ ..") z adresu URL.|
|ICU_ENCODE_SPACES_ONLY|Koduj tylko spacje.|
|ICU_BROWSER_MODE|Nie należy kodować ani dekodować znaków po "#" lub '' i nie usuwaj końcowych odstępów po ''. Jeśli ta wartość nie jest określona, cały adres URL jest zakodowany i końcowe białe spacji jest usuwany.|

Jeśli używasz domyślnego MFC, który nie jest flagami, funkcja konwertuje \\wszystkie niebezpieczne znaki \\i meta sekwencje (takie jak .,\ .., i ...) do sekwencji ucieczki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli adres URL został pomyślnie przeanalizowany; w przeciwnym razie 0, jeśli jest pusta lub nie zawiera znanego typu usługi internetowej.

### <a name="remarks"></a>Uwagi

Analizuje ciąg adresu URL i zwraca typ usługi i jej składniki, a także podaje nazwę użytkownika i hasło. Flagi wskazują, jak niebezpieczne znaki są obsługiwane.

> [!NOTE]
> Aby wywołać tę funkcję, projekt musi zawierać AFXINET. H.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxinet.h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a>AfxGetInternetHandleType

Ta funkcja globalna służy do określania typu dojścia internetowego.

### <a name="syntax"></a>Składnia

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parametry

*hQuery ( hQuery )*<br/>
Dojście do zapytania internetowego.

### <a name="return-value"></a>Wartość zwracana

Dowolny typ usług internetowych zdefiniowany przez wininet. H. Zobacz uwagi sekcji listy tych usług internetowych. Jeśli dojście ma wartość NULL lub nie jest rozpoznawane, funkcja zwraca AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Uwagi

Poniższa lista zawiera możliwe `AfxGetInternetHandleType`typy Internetu zwracane przez program .

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
> Aby wywołać tę funkcję, projekt musi zawierać AFXINET. H.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a>AfxThrowInternetEkceptacja

Zgłasza wyjątek z Internetu.

### <a name="syntax"></a>Składnia

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parametry

*Dwcontext*<br/>
Identyfikator kontekstu operacji, który spowodował błąd. Wartość domyślna *dwContext* jest określona pierwotnie w [CInternetSession](cinternetsession-class.md) i jest przekazywana do [CInternetConnection](cinternetconnection-class.md)- i [CInternetFile](cinternetfile-class.md)-derived klas. W przypadku określonych operacji wykonywanych na połączeniu lub pliku zwykle zastępuje się wartością domyślną za pomocą własnego *dwContext.* Ta wartość jest następnie zwracana do [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) do identyfikacji stanu określonej operacji.

*dwError ( dwError )*<br/>
Błąd, który spowodował wyjątek.

### <a name="remarks"></a>Uwagi

Użytkownik jest odpowiedzialny za określenie przyczyny na podstawie kodu błędu systemu operacyjnego.

> [!NOTE]
> Aby wywołać tę funkcję, projekt musi zawierać AFXINET. H.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)<br/>
[Klasa CInternetException](cinternetexception-class.md)<br/>
[AfxParseURL (AfxParseURL)](internet-url-parsing-globals.md#afxparseurl)
