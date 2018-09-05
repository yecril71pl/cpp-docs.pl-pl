---
title: Klasa cUrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
dev_langs:
- C++
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0babb0932fc059a91fd8da79f649039bcaebc457
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753736"
---
# <a name="curl-class"></a>Klasa cUrl

Ta klasa reprezentuje adres URL. Umożliwia on manipulowanie każdy element adresu URL, niezależnie od innych, czy analiza kodu istniejącego adresu URL ciąg lub tworzenia ciągu od podstaw.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CUrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUrl::CUrl](#curl)|Konstruktor.|
|[CUrl:: ~ CUrl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUrl::Canonicalize](#canonicalize)|Wywołaj tę metodę, aby przekonwertować forma kanoniczna ciągu adresu URL.|
|[CUrl::Clear](#clear)|Wywołaj tę metodę, aby wyczyścić wszystkie pola adresu URL.|
|[CUrl::CrackUrl](#crackurl)|Wywołaj tę metodę w celu zdekodowania i przeanalizować adresu URL.|
|[CUrl::CreateUrl](#createurl)|Wywołaj tę metodę, aby utworzyć adres URL.|
|[CUrl::GetExtraInfo](#getextrainfo)|Wywołaj tę metodę, aby uzyskać dodatkowe informacje (takie jak *tekstu* lub # *tekstu*) z adresu URL.|
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Wywołaj tę metodę w celu uzyskania długości dodatkowych informacji (takich jak *tekstu* lub # *tekstu*) można pobrać z adresu URL.|
|[CUrl::GetHostName](#gethostname)|Wywołaj tę metodę można pobrać nazwy hosta z adresu URL.|
|[CUrl::GetHostNameLength](#gethostnamelength)|Wywołaj tę metodę w celu uzyskania długości nazwy hosta.|
|[CUrl::GetPassword](#getpassword)|Wywołaj tę metodę, aby uzyskać hasło z adresu URL.|
|[CUrl::GetPasswordLength](#getpasswordlength)|Wywołaj tę metodę w celu uzyskania długości hasła.|
|[CUrl::GetPortNumber](#getportnumber)|Wywołaj tę metodę, aby uzyskać numer portu w zakresie ATL_URL_PORT.|
|[CUrl::GetScheme](#getscheme)|Wywołaj tę metodę, aby pobrać schemat adresu URL.|
|[CUrl::GetSchemeName](#getschemename)|Wywołaj tę metodę, aby uzyskać nazwę schematu URL.|
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Wywołaj tę metodę, aby pobrać długość nazwy schematu URL.|
|[CUrl::GetUrlLength](#geturllength)|Wywołaj tę metodę, aby uzyskać długość adresu URL.|
|[CUrl::GetUrlPath](#geturlpath)|Wywołaj tę metodę, aby uzyskać ścieżkę adresu URL.|
|[CUrl::GetUrlPathLength](#geturlpathlength)|Wywołaj tę metodę w celu uzyskania długości ścieżki adresu URL.|
|[CUrl::GetUserName](#getusername)|Wywołaj tę metodę, aby uzyskać nazwę użytkownika z adresu URL.|
|[CUrl::GetUserNameLength](#getusernamelength)|Wywołaj tę metodę w celu uzyskania długości nazwy użytkownika.|
|[CUrl::SetExtraInfo](#setextrainfo)|Wywołanie tej metody, aby ustawić informacje dodatkowe (takie jak *tekstu* lub # *tekstu*) adresu URL.|
|[CUrl::SetHostName](#sethostname)|Wywołaj tę metodę, aby ustawić nazwę hosta.|
|[CUrl::SetPassword](#setpassword)|Wywołaj tę metodę, aby ustawić hasło.|
|[CUrl::SetPortNumber](#setportnumber)|Wywołaj tę metodę, aby ustawić numer portu w zakresie ATL_URL_PORT.|
|[CUrl::SetScheme](#setscheme)|Wywołaj tę metodę, aby ustawić schemat adresu URL.|
|[CUrl::SetSchemeName](#setschemename)|Wywołaj tę metodę, aby ustawić nazwę schematu URL.|
|[CUrl::SetUrlPath](#seturlpath)|Wywołaj tę metodę, aby ustawić ścieżkę adresu URL.|
|[CUrl::SetUserName](#setusername)|Wywołaj tę metodę, aby ustawić nazwę użytkownika.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUrl::operator =](#operator_eq)|Przypisuje określonego `CUrl` obiekt do bieżącego `CUrl` obiektu.|

## <a name="remarks"></a>Uwagi

`CUrl` Służy do modyfikowania pola adresu URL, takich jak ścieżki lub numer portu. `CUrl` Określa adresy URL o następującej postaci:

\<Schemat > ://\<UserName >:\<hasło > @\<nazwa hosta >:\<numer_portu > /\<UrlPath >\<ExtraInfo >

(Niektóre pola są opcjonalne). Na przykład rozważmy ten adres URL:

http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents

[CUrl::CrackUrl](#crackurl) analizuje je w następujący sposób:

- Schemat: "http" lub [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- Nazwa użytkownika: "ktoś"

- Hasło: "wpis tajny"

- Nazwa hosta: "www.microsoft.com"

- Numer_portu: 80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo: "#contents"

W celu modyfikowania pola UrlPath (na przykład), należy użyć [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength), i [SetUrlPath](#seturlpath). Należy użyć [CreateUrl](#createurl) do utworzenia całego ciągu adresu URL.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

##  <a name="canonicalize"></a>  CUrl::Canonicalize

Wywołaj tę metodę, aby przekonwertować forma kanoniczna ciągu adresu URL.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*Flagidw*  
Flagi sterujące kanoniczną. Jeśli nie określono żadnych flag (*Flagidw* = 0), Metoda ta konwertuje wszystkich niebezpiecznych znaków i sekwencji meta (takie jak \\., \.., i \\...) jako znak ucieczki dla sekwencji. *Flagidw* może być jedną z następujących wartości:

- ATL_URL_BROWSER_MODE: Nie jest w stanie kodowania lub dekodowania znaków po "#" lub "" i nie powoduje usunięcia odstępu po "". Jeśli ta wartość nie jest określona, cały adres URL jest zaszyfrowana i końcowe biały znak zostanie usunięta.

- ATL_URL _DECODE: konwertuje wszystkie % XX sekwencje znaków, w tym sekwencje ucieczki, aby adres URL jest analizowany.

- ATL_URL _ENCODE_PERCENT: koduje wszystkie znaki procentu napotkano. Domyślnie nie są kodowane procentu.

- ATL_URL _ENCODE_SPACES_ONLY: koduje tylko spacje.

- ATL_URL _NO_ENCODE: nie konwertuje niebezpieczne znaki na sekwencje ucieczki.

- ATL_URL _NO_META: nie powoduje usunięcia meta sekwencji (takie jak "."i"..") z adresu URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Konwertowanie na forma kanoniczna obejmuje konwersję niebezpiecznych znaków i spacji na sekwencje ucieczki.

##  <a name="clear"></a>  CUrl::Clear

Wywołaj tę metodę, aby wyczyścić wszystkie pola adresu URL.

```
inline void Clear() throw();
```

##  <a name="crackurl"></a>  CUrl::CrackUrl

Wywołaj tę metodę w celu zdekodowania i przeanalizować adresu URL.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*lpszUrl*  
Adres URL.

*Flagidw*  
Określ ATL_URL_DECODE lub ATL_URL_ESCAPE przekonwertować wszystkie znaki ucieczki w *lpszUrl* rzeczywistych wartości po analizie. (Przed Visual C++ 2005, ATL_URL_DECODE przekonwertować wszystkie znaki ucieczki przed analizą.)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="createurl"></a>  CUrl::CreateUrl

Ta metoda konstrukcje ciągu adresu URL z obiektem programu CUrl składnika pól.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>Parametry

*lpszUrl*  
Buforu ciągu do przechowywania całego ciągu adresu URL.

*pdwMaxLength*  
Maksymalna długość *lpszUrl* buforu ciągu.

*Flagidw*  
Określ ATL_URL_ESCAPE do konwersji wszystkich znaków ucieczki w *lpszUrl* rzeczywistych wartości.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda dołącza jej poszczególne pola w celu utworzenia całego ciągu adresu URL w następującym formacie:

**\<Schemat > ://\<użytkownika >:\<przekazać > @\<domeny >:\<port >\<ścieżka >\<dodatkowe >**

Po wywołaniu tej metody *pdwMaxLength* parametr początkowo musi zawierać maksymalną długość buforu ciągu odwołuje się *lpszUrl* parametru. Wartość *pdwMaxLength* parametr zostanie zaktualizowany o rzeczywistej długości ciągu adresu URL.

### <a name="example"></a>Przykład

W przykładzie pokazano tworzenie obiektu programu CUrl i pobierania jej ciągu adresu URL

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

##  <a name="curl"></a>  CUrl::CUrl

Konstruktor.

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parametry

*urlThat*  
`CUrl` Obiektu do skopiowania do utworzenia adresu URL.

##  <a name="dtor"></a>  CUrl:: ~ CUrl

Destruktor.

```
~CUrl() throw();
```

##  <a name="getextrainfo"></a>  CUrl::GetExtraInfo

Wywołaj tę metodę, aby uzyskać dodatkowe informacje (takie jak *tekstu* lub # *tekstu*) z adresu URL.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg zawierający dodatkowe informacje.

##  <a name="getextrainfolength"></a>  CUrl::GetExtraInfoLength

Wywołaj tę metodę w celu uzyskania długości dodatkowych informacji (takich jak *tekstu* lub # *tekstu*) można pobrać z adresu URL.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość ciągu zawierającego dodatkowe informacje.

##  <a name="gethostname"></a>  CUrl::GetHostName

Wywołaj tę metodę można pobrać nazwy hosta z adresu URL.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę hosta.

##  <a name="gethostnamelength"></a>  CUrl::GetHostNameLength

Wywołaj tę metodę w celu uzyskania długości nazwy hosta.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca długość nazwy hosta.

##  <a name="getpassword"></a>  CUrl::GetPassword

Wywołaj tę metodę, aby uzyskać hasło z adresu URL.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca hasło.

##  <a name="getpasswordlength"></a>  CUrl::GetPasswordLength

Wywołaj tę metodę w celu uzyskania długości hasła.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość hasła.

##  <a name="getportnumber"></a>  CUrl::GetPortNumber

Wywołaj tę metodę w celu uzyskania numeru portu.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca numer portu.

##  <a name="getscheme"></a>  CUrl::GetScheme

Wywołaj tę metodę, aby pobrać schemat adresu URL.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [ATL_URL_SCHEME](atl-url-scheme-enum.md) wartości opisujące schemat adresu URL.

##  <a name="getschemename"></a>  CUrl::GetSchemeName

Wywołaj tę metodę, aby uzyskać nazwę schematu URL.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę schemat adresu URL (na przykład "http" lub "ftp").

##  <a name="getschemenamelength"></a>  CUrl::GetSchemeNameLength

Wywołaj tę metodę, aby pobrać długość nazwy schematu URL.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość nazwy schematu URL.

##  <a name="geturllength"></a>  CUrl::GetUrlLength

Wywołaj tę metodę, aby uzyskać długość adresu URL.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość adresu URL.

##  <a name="geturlpath"></a>  CUrl::GetUrlPath

Wywołaj tę metodę, aby uzyskać ścieżkę adresu URL.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ścieżkę adresu URL.

##  <a name="geturlpathlength"></a>  CUrl::GetUrlPathLength

Wywołaj tę metodę w celu uzyskania długości ścieżki adresu URL.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość ścieżki adresu URL.

##  <a name="getusername"></a>  CUrl::GetUserName

Wywołaj tę metodę, aby uzyskać nazwę użytkownika z adresu URL.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę użytkownika.

##  <a name="getusernamelength"></a>  CUrl::GetUserNameLength

Wywołaj tę metodę w celu uzyskania długości nazwy użytkownika.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość nazwy użytkownika.

##  <a name="operator_eq"></a>  CUrl::operator =

Przypisuje określonego `CUrl` obiekt do bieżącego `CUrl` obiektu.

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parametry

*urlThat*  
`CUrl` Obiektu do skopiowania do bieżącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do bieżącego obiektu.

##  <a name="setextrainfo"></a>  CUrl::SetExtraInfo

Wywołanie tej metody, aby ustawić informacje dodatkowe (takie jak *tekstu* lub # *tekstu*) adresu URL.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>Parametry

*lpszInfo*  
Ciąg zawierający dodatkowe informacje, aby uwzględnić w adresie URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="sethostname"></a>  CUrl::SetHostName

Wywołaj tę metodę, aby ustawić nazwę hosta.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>Parametry

*lpszHost*  
Nazwa hosta.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="setpassword"></a>  CUrl::SetPassword

Wywołaj tę metodę, aby ustawić hasło.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>Parametry

*lpszPass*  
Hasło.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="setportnumber"></a>  CUrl::SetPortNumber

Wywołaj tę metodę, aby ustawić numer portu.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>Parametry

*nPrt*  
Numer portu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="setscheme"></a>  CUrl::SetScheme

Wywołaj tę metodę, aby ustawić schemat adresu URL.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>Parametry

*nScheme*  
Jedną z [ATL_URL_SCHEME](atl-url-scheme-enum.md) wartości dla schematu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Schemat można również ustawić według nazwy (zobacz [CUrl::SetSchemeName](#setschemename)).

##  <a name="setschemename"></a>  CUrl::SetSchemeName

Wywołaj tę metodę, aby ustawić nazwę schematu URL.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>Parametry

*lpszSchm*  
Nazwa schematu URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Schemat można również ustawić za pomocą [ATL_URL_SCHEME](atl-url-scheme-enum.md) stałych (zobacz [CUrl::SetScheme](#setscheme)).

##  <a name="seturlpath"></a>  CUrl::SetUrlPath

Wywołaj tę metodę, aby ustawić ścieżkę adresu URL.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>Parametry

*lpszPath*  
Ścieżka adresu URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="setusername"></a>  CUrl::SetUserName

Wywołaj tę metodę, aby ustawić nazwę użytkownika.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>Parametry

*lpszUser*  
Nazwa użytkownika.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)
