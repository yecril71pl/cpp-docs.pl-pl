---
title: Klasa CUrl
ms.date: 05/06/2019
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
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: 3468e17b031d0a72bc56d915c689fbe4c78859e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330474"
---
# <a name="curl-class"></a>Klasa CUrl

Ta klasa reprezentuje adres URL. Umożliwia manipulowanie każdym elementem adresu URL niezależnie od innych, niezależnie od tego, czy analizowanie istniejącego ciągu adresu URL lub tworzenie ciągu od podstaw.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CUrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUrl::CUrl](#curl)|Konstruktor.|
|[CUrl::~CUrl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUrl::Kanonizacja](#canonicalize)|Wywołanie tej metody, aby przekonwertować ciąg adresu URL do postaci kanonicznej.|
|[CUrl::Wyczyść](#clear)|Wywołanie tej metody, aby wyczyścić wszystkie pola adresu URL.|
|[CUrl::CrackUrl](#crackurl)|Wywołanie tej metody, aby zdekodować i przeanalizować adres URL.|
|[CUrl::CreateUrl](#createurl)|Wywołanie tej metody, aby utworzyć adres URL.|
|[CUrl::GetExtraInfo](#getextrainfo)|Wywołanie tej metody, aby uzyskać dodatkowe informacje (takie jak *tekst* lub # *tekst)* z adresu URL.|
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Wywołanie tej metody, aby uzyskać długość dodatkowych informacji (takich jak *tekst* lub # *tekst*), aby pobrać z adresu URL.|
|[CUrl::GetHostName](#gethostname)|Wywołanie tej metody, aby uzyskać nazwę hosta z adresu URL.|
|[CUrl::GetHostNameLength](#gethostnamelength)|Wywołanie tej metody, aby uzyskać długość nazwy hosta.|
|[CUrl::GetPassword](#getpassword)|Wywołanie tej metody, aby uzyskać hasło z adresu URL.|
|[CUrl::GetPasswordLength](#getpasswordlength)|Wywołanie tej metody, aby uzyskać długość hasła.|
|[CUrl::GetPortNumber](#getportnumber)|Wywołanie tej metody, aby uzyskać numer portu pod względem ATL_URL_PORT.|
|[CUrl::GetScheme](#getscheme)|Wywołanie tej metody, aby uzyskać schemat adresu URL.|
|[CUrl::GetSchemeName](#getschemename)|Wywołanie tej metody, aby uzyskać nazwę schematu adresu URL.|
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Wywołanie tej metody, aby uzyskać długość nazwy schematu adresu URL.|
|[CUrl::GetUrlLength](#geturllength)|Wywołanie tej metody, aby uzyskać długość adresu URL.|
|[CUrl::GetUrlPath](#geturlpath)|Wywołanie tej metody, aby uzyskać ścieżkę adresu URL.|
|[CUrl::GetUrlPathLength](#geturlpathlength)|Wywołanie tej metody, aby uzyskać długość ścieżki adresu URL.|
|[CUrl::GetUserName](#getusername)|Wywołanie tej metody, aby uzyskać nazwę użytkownika z adresu URL.|
|[CUrl::GetUserNameLength](#getusernamelength)|Wywołanie tej metody, aby uzyskać długość nazwy użytkownika.|
|[CUrl::SetExtraInfo](#setextrainfo)|Wywołanie tej metody, aby ustawić dodatkowe informacje (takie jak *tekst* lub # *tekst)* adresu URL.|
|[CUrl::Nazwa zestawu](#sethostname)|Wywołanie tej metody, aby ustawić nazwę hosta.|
|[CUrl::SetPassword](#setpassword)|Wywołanie tej metody, aby ustawić hasło.|
|[CUrl::SetPortNumber](#setportnumber)|Wywołanie tej metody, aby ustawić numer portu pod względem ATL_URL_PORT.|
|[CUrl::SetScheme](#setscheme)|Wywołanie tej metody, aby ustawić schemat adresu URL.|
|[CUrl::Nazwa zestawu](#setschemename)|Wywołanie tej metody, aby ustawić nazwę schematu adresu URL.|
|[CUrl::SetUrlPath](#seturlpath)|Wywołanie tej metody, aby ustawić ścieżkę adresu URL.|
|[CUrl::Nazwa zestawu](#setusername)|Wywołanie tej metody, aby ustawić nazwę użytkownika.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUrl::operator =](#operator_eq)|Przypisuje określony `CUrl` obiekt do `CUrl` bieżącego obiektu.|

## <a name="remarks"></a>Uwagi

`CUrl`umożliwia manipulowanie polami adresu URL, takimi jak ścieżka lub numer portu. `CUrl`rozumie adresy URL w następującym formularzu:

\<Schemat\<>://>\<UserName: Password>\@ \<HostName\<>: PortNumber>/\<UrlPath>\<ExtraInfo>

(Niektóre pola są opcjonalne). Rozważmy na przykład ten adres URL:

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[CUrl::CrackUrl](#crackurl) analizuje go w następujący sposób:

- Schemat: "http" lub [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- Nazwa użytkownika: "ktoś"

- Hasło: "tajne"

- Nazwa hosta:`www.microsoft.com`" "

- Numer portu: 80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo: "#contents"

Aby manipulować polem UrlPath (na przykład), należy użyć [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength)i [SetUrlPath](#seturlpath). Aby utworzyć pełny ciąg adresu URL, należy użyć [createUrl.](#createurl)

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="curlcanonicalize"></a><a name="canonicalize"></a>CUrl::Kanonizacja

Wywołanie tej metody, aby przekonwertować ciąg adresu URL do postaci kanonicznej.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Flagi, które kontrolują kanonizację. Jeśli nie określono żadnych flag (*dwFlags* = 0), metoda konwertuje \\wszystkie niebezpieczne znaki \\i meta sekwencje (takie jak .,\ .., i ...) do sekwencji ucieczki. *dwFlags* może być jedną z następujących wartości:

- ATL_URL_BROWSER_MODE: Nie koduje ani nie dekoduje znaków po "#" lub "" i nie usuwa końcowego odstępu po "". Jeśli ta wartość nie jest określona, cały adres URL jest zakodowany i końcowe białe spacji jest usuwany.

- ATL_URL _DECODE: Konwertuje wszystkie sekwencje %XX na znaki, w tym sekwencje ucieczki, przed przeanalizowaniem adresu URL.

- ATL_URL _ENCODE_PERCENT: koduje wszelkie napotkane znaki procentowe. Domyślnie znaki procentowe nie są zakodowane.

- ATL_URL _ENCODE_SPACES_ONLY: Koduje tylko spacje.

- ATL_URL _NO_ENCODE: Nie konwertuje niebezpiecznych znaków na sekwencje ucieczki.

- ATL_URL _NO_META: nie usuwa sekwencji meta (takich jak "." i "..") z adresu URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Konwersja do postaci kanonicznej polega na konwersji niebezpiecznych znaków i spacji do sekwencji ucieczki.

## <a name="curlclear"></a><a name="clear"></a>CUrl::Wyczyść

Wywołanie tej metody, aby wyczyścić wszystkie pola adresu URL.

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a>CUrl::CrackUrl

Wywołanie tej metody, aby zdekodować i przeanalizować adres URL.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*lpszurl*<br/>
Adres URL.

*Dwflags*<br/>
Określ ATL_URL_DECODE lub ATL_URL_ESCAPE, aby przekonwertować wszystkie znaki ucieczki w *lpszUrl* na ich rzeczywiste wartości po przeanalizowaniu. (Przed programem Visual C++ 2005 ATL_URL_DECODE przekonwertować wszystkie znaki ucieczki przed analizą).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="curlcreateurl"></a><a name="createurl"></a>CUrl::CreateUrl

Ta metoda tworzy ciąg adresu URL z pól składnika obiektu CUrl.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>Parametry

*lpszurl*<br/>
Bufor ciągu do przechowywania pełnego ciągu adresu URL.

*pdwMaxLength*<br/>
Maksymalna długość buforu ciągu *lpszUrl.*

*Dwflags*<br/>
Określ ATL_URL_ESCAPE, aby przekonwertować wszystkie znaki ucieczki w *lpszUrl* na ich rzeczywiste wartości.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda dołącza swoje poszczególne pola w celu skonstruowania pełnego ciągu adresu URL przy użyciu następującego formatu:

**\<schemat\<>://> użytkownika:\<przekazywanie \@ \<> domeny>:\< \<ścieżka>portu>\<dodatkowe>**

Podczas wywoływania tej metody parametr *pdwMaxLength* powinien początkowo zawierać maksymalną długość buforu ciągu, do którego odwołuje się parametr *lpszUrl.* Wartość parametru *pdwMaxLength* zostanie zaktualizowana o rzeczywistą długość ciągu adresu URL.

### <a name="example"></a>Przykład

Ten przykład pokazuje tworzenie obiektu CUrl i pobieranie jego ciągu adresu URL

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a>CUrl::CUrl

Konstruktor.

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parametry

*urlŻe*<br/>
Obiekt `CUrl` do skopiowania w celu utworzenia adresu URL.

## <a name="curlcurl"></a><a name="dtor"></a>CUrl::~CUrl

Destruktor.

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a>CUrl::GetExtraInfo

Wywołanie tej metody, aby uzyskać dodatkowe informacje (takie jak *tekst* lub # *tekst)* z adresu URL.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg zawierający dodatkowe informacje.

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a>CUrl::GetExtraInfoLength

Wywołanie tej metody, aby uzyskać długość dodatkowych informacji (takich jak *tekst* lub # *tekst*), aby pobrać z adresu URL.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość ciągu zawierającego dodatkowe informacje.

## <a name="curlgethostname"></a><a name="gethostname"></a>CUrl::GetHostName

Wywołanie tej metody, aby uzyskać nazwę hosta z adresu URL.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę hosta.

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a>CUrl::GetHostNameLength

Wywołanie tej metody, aby uzyskać długość nazwy hosta.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość nazwy hosta.

## <a name="curlgetpassword"></a><a name="getpassword"></a>CUrl::GetPassword

Wywołanie tej metody, aby uzyskać hasło z adresu URL.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca hasło.

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a>CUrl::GetPasswordLength

Wywołanie tej metody, aby uzyskać długość hasła.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość hasła.

## <a name="curlgetportnumber"></a><a name="getportnumber"></a>CUrl::GetPortNumber

Wywołanie tej metody, aby uzyskać numer portu.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca numer portu.

## <a name="curlgetscheme"></a><a name="getscheme"></a>CUrl::GetScheme

Wywołanie tej metody, aby uzyskać schemat adresu URL.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [wartość ATL_URL_SCHEME](atl-url-scheme-enum.md) opisującą schemat adresu URL.

## <a name="curlgetschemename"></a><a name="getschemename"></a>CUrl::GetSchemeName

Wywołanie tej metody, aby uzyskać nazwę schematu adresu URL.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę schematu adresu URL (na przykład "http" lub "ftp").

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a>CUrl::GetSchemeNameLength

Wywołanie tej metody, aby uzyskać długość nazwy schematu adresu URL.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość nazwy schematu adresu URL.

## <a name="curlgeturllength"></a><a name="geturllength"></a>CUrl::GetUrlLength

Wywołanie tej metody, aby uzyskać długość adresu URL.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość adresu URL.

## <a name="curlgeturlpath"></a><a name="geturlpath"></a>CUrl::GetUrlPath

Wywołanie tej metody, aby uzyskać ścieżkę adresu URL.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ścieżkę adresu URL.

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a>CUrl::GetUrlPathLength

Wywołanie tej metody, aby uzyskać długość ścieżki adresu URL.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość ścieżki adresu URL.

## <a name="curlgetusername"></a><a name="getusername"></a>CUrl::GetUserName

Wywołanie tej metody, aby uzyskać nazwę użytkownika z adresu URL.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę użytkownika.

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a>CUrl::GetUserNameLength

Wywołanie tej metody, aby uzyskać długość nazwy użytkownika.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość nazwy użytkownika.

## <a name="curloperator-"></a><a name="operator_eq"></a>CUrl::operator =

Przypisuje określony `CUrl` obiekt do `CUrl` bieżącego obiektu.

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parametry

*urlŻe*<br/>
Obiekt `CUrl` do skopiowania do bieżącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do bieżącego obiektu.

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a>CUrl::SetExtraInfo

Wywołanie tej metody, aby ustawić dodatkowe informacje (takie jak *tekst* lub # *tekst)* adresu URL.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>Parametry

*lpszInfo*<br/>
Ciąg zawierający dodatkowe informacje do uwzględnienia w adresie URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="curlsethostname"></a><a name="sethostname"></a>CUrl::Nazwa zestawu

Wywołanie tej metody, aby ustawić nazwę hosta.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>Parametry

*lpszHost (lpszHost)*<br/>
Nazwa hosta.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="curlsetpassword"></a><a name="setpassword"></a>CUrl::SetPassword

Wywołanie tej metody, aby ustawić hasło.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>Parametry

*lpszPass (lpszPass)*<br/>
Hasło.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="curlsetportnumber"></a><a name="setportnumber"></a>CUrl::SetPortNumber

Wywołanie tej metody, aby ustawić numer portu.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>Parametry

*nPrt*<br/>
Numer portu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="curlsetscheme"></a><a name="setscheme"></a>CUrl::SetScheme

Wywołanie tej metody, aby ustawić schemat adresu URL.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>Parametry

*nScheme*<br/>
Jedną z [wartości ATL_URL_SCHEME](atl-url-scheme-enum.md) dla schematu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Schemat można również ustawić według nazwy (patrz [CUrl::SetSchemeName](#setschemename)).

## <a name="curlsetschemename"></a><a name="setschemename"></a>CUrl::Nazwa zestawu

Wywołanie tej metody, aby ustawić nazwę schematu adresu URL.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>Parametry

*lpszSchm*<br/>
Nazwa schematu adresu URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Schemat można również ustawić przy użyciu [stałej ATL_URL_SCHEME](atl-url-scheme-enum.md) (patrz [CUrl::SetScheme](#setscheme)).

## <a name="curlseturlpath"></a><a name="seturlpath"></a>CUrl::SetUrlPath

Wywołanie tej metody, aby ustawić ścieżkę adresu URL.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>Parametry

*lpszPath (lpszPath)*<br/>
Ścieżka adresu URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="curlsetusername"></a><a name="setusername"></a>CUrl::Nazwa zestawu

Wywołanie tej metody, aby ustawić nazwę użytkownika.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>Parametry

*lpszUser*<br/>
Nazwa użytkownika.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)
