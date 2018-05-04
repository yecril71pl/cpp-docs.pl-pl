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
ms.openlocfilehash: afb0f7abc079d699cfcf682356b88b9cc8aa2bb9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="curl-class"></a>Klasa cUrl
Ta klasa reprezentuje adres URL. Umożliwia manipulowania każdy element adresu URL, niezależnie od innych, czy podczas analizowania istniejący adres URL ciągu lub tworzenia ciągu od początku.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
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
|[CUrl::Canonicalize](#canonicalize)|Wywołaj tę metodę, aby przekonwertować ciągu adresu URL w formie kanonicznej.|  
|[CUrl::Clear](#clear)|Wywołanie tej metody, aby wyczyścić wszystkie pola adresu URL.|  
|[CUrl::CrackUrl](#crackurl)|Wywołaj tę metodę w celu zdekodowania i przeanalizować adresu URL.|  
|[CUrl::CreateUrl](#createurl)|Wywołaj tę metodę, aby utworzyć adres URL.|  
|[CUrl::GetExtraInfo](#getextrainfo)|Wywołanie tej metody, aby uzyskać dodatkowe informacje (takie jak *tekst* lub # *tekst*) z adresu URL.|  
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Wywołanie tej metody, aby uzyskać dodatkowe informacje o długości (takich jak *tekst* lub # *tekst*) można pobrać z adresu URL.|  
|[CUrl::GetHostName](#gethostname)|Wywołanie tej metody można pobrać nazwy hosta z adresu URL.|  
|[CUrl::GetHostNameLength](#gethostnamelength)|Wywołaj tę metodę, aby pobrać długości nazwy hosta.|  
|[CUrl::GetPassword](#getpassword)|Wywołaj tę metodę w celu pobrania hasła z adresu URL.|  
|[CUrl::GetPasswordLength](#getpasswordlength)|Wywołaj tę metodę, aby pobrać długości hasła.|  
|[CUrl::GetPortNumber](#getportnumber)|Wywołanie tej metody, aby uzyskać numer portu w zakresie ATL_URL_PORT.|  
|[CUrl::GetScheme](#getscheme)|Wywołaj tę metodę, aby pobrać schemat adresu URL.|  
|[CUrl::GetSchemeName](#getschemename)|Wywołaj tę metodę, aby uzyskać adres URL nazwy schematu.|  
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Wywołanie tej metody można uzyskać długości nazwy schemat adresu URL.|  
|[CUrl::GetUrlLength](#geturllength)|Wywołanie tej metody, aby uzyskać długość adresu URL.|  
|[CUrl::GetUrlPath](#geturlpath)|Wywołanie tej metody można uzyskać ścieżki adresu URL.|  
|[CUrl::GetUrlPathLength](#geturlpathlength)|Wywołanie tej metody, aby uzyskać długość ścieżki adresu URL.|  
|[CUrl::GetUserName](#getusername)|Wywołanie tej metody można uzyskać nazwy użytkownika z adresu URL.|  
|[CUrl::GetUserNameLength](#getusernamelength)|Wywołanie tej metody, aby uzyskać długość nazwy użytkownika.|  
|[CUrl::SetExtraInfo](#setextrainfo)|Wywołanie tej metody można ustawić dodatkowe informacje (takie jak *tekst* lub # *tekst*) adresu URL.|  
|[CUrl::SetHostName](#sethostname)|Wywołanie tej metody można ustawić nazwy hosta.|  
|[CUrl::SetPassword](#setpassword)|Wywołaj tę metodę, aby ustawić hasło.|  
|[CUrl::SetPortNumber](#setportnumber)|Wywołaj tę metodę, aby ustawić numer portu w zakresie ATL_URL_PORT.|  
|[CUrl::SetScheme](#setscheme)|Wywołaj tę metodę, aby ustawić schemat adresu URL.|  
|[CUrl::SetSchemeName](#setschemename)|Wywołaj tę metodę, aby ustawić adres URL nazwy schematu.|  
|[CUrl::SetUrlPath](#seturlpath)|Wywołaj tę metodę, aby ustawić ścieżkę adresu URL.|  
|[CUrl::SetUserName](#setusername)|Wywołaj tę metodę, aby ustawić nazwę użytkownika.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CUrl::operator =](#operator_eq)|Przypisuje określonego `CUrl` obiektu do bieżącego `CUrl` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CUrl` Służy do manipulowania pola Adres URL, takie jak ścieżka lub numer portu. `CUrl` rozumie, adresy URL mają następującą postać:  
  
 \<Schemat > ://\<nazwa użytkownika >:\<hasło > @\<nazwa_hosta >:\<numer_portu > /\<UrlPath >\<ExtraInfo >  
  
 (Niektóre pola są opcjonalne). Rozważmy na przykład tego adresu URL:  
  
 http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents  
  
 [CUrl::CrackUrl](#crackurl) analizuje go w następujący sposób:  
  
-   Schemat: "http" lub [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)  
  
-   Nazwa użytkownika: "ktoś"  
  
-   Hasło: "klucz tajny"  
  
-   Nazwa hosta: "www.microsoft.com"  
  
-   Numer_portu: 80  
  
-   UrlPath: "visualc/stuff.htm"  
  
-   ExtraInfo: "#contents"  
  
 W celu manipulowania UrlPath pola (na przykład), należy użyć [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength), i [SetUrlPath](#seturlpath). Należy użyć [CreateUrl](#createurl) Aby utworzyć pełny ciąg adresu URL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="canonicalize"></a>  CUrl::Canonicalize  
 Wywołaj tę metodę, aby przekonwertować ciągu adresu URL w formie kanonicznej.  
  
```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Flagi, które kontrolują zapewniania kanoniczności. Jeśli nie określono żadnych flag ( `dwFlags` = 0), metoda konwertuje wszystkie znaki niebezpieczne i meta sekwencje (takich jak \\., \.., i \\...) ucieczki sekwencji. `dwFlags` Może to być jedna z następujących wartości:  
  
-   ATL_URL_BROWSER_MODE: Nie kodowania lub dekodowania znaków po "#" lub "" i nie powoduje usunięcia końcu spację po "". Jeśli ta wartość nie jest określona, cały adres URL jest zakodowany i usunięciu wiodących znaków odstępu.  
  
-   ATL_URL _DECODE: konwertuje wszystkie sekwencje XX % znaków, w tym sekwencji unikowych przed analizowania adresu URL.  
  
-   ATL_URL _ENCODE_PERCENT: koduje wszelkie znaki procentu napotkano. Domyślnie nie są kodowane procentu.  
  
-   ATL_URL _ENCODE_SPACES_ONLY: koduje tylko spacje.  
  
-   ATL_URL _NO_ENCODE: nie konwertuje sekwencje specjalne znaków niebezpieczne.  
  
-   ATL_URL _NO_META: nie powoduje usunięcia meta sekwencje (takich jak "."i"..") z adresu URL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Konwertowanie na forma kanoniczna polega na konwertowaniu znaki niebezpieczne i spacje sekwencji ucieczki.  
  
##  <a name="clear"></a>  CUrl::Clear  
 Wywołanie tej metody, aby wyczyścić wszystkie pola adresu URL.  
  
```
inline void Clear() throw();
```  
  
##  <a name="crackurl"></a>  CUrl::CrackUrl  
 Wywołaj tę metodę w celu zdekodowania i przeanalizować adresu URL.  
  
```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszUrl`  
 Adres URL.  
  
 `dwFlags`  
 Określ ATL_URL_DECODE lub ATL_URL_ESCAPE, aby przekonwertować wszystkie znaki specjalne w `lpszUrl` rzeczywistych wartości po analizie. (Przed Visual C++ 2005, ATL_URL_DECODE przekonwertować wszystkie znaki ucieczki przed analizą.)  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
##  <a name="createurl"></a>  CUrl::CreateUrl  
 Ta metoda tworzy ciągu adresu URL z pola składnika obiektu CUrl.  
  
```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszUrl*  
 Bufor ciągu do przechowywania pełny ciąg adresu URL.  
  
 `pdwMaxLength`  
 Maksymalna długość *lpszUrl* buforu ciągu.  
  
 `dwFlags`  
 Określ ATL_URL_ESCAPE można przekonwertować wszystkie znaki specjalne w *lpszUrl* rzeczywiste wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dołącza jego poszczególnych pól, aby utworzyć pełny ciąg adresu URL w następującym formacie:  
  
 **\<Schemat > ://\<użytkownika >:\<przekazać > @\<domeny >:\<port >\<ścieżka >\<dodatkowych >**  
  
 Podczas wywoływania tej metody `pdwMaxLength` parametr początkowo musi zawierać maksymalną długość buforu ciągu odwołuje się *lpszUrl* parametru. Wartość `pdwMaxLength` parametru zostaną zaktualizowane rzeczywista długość ciągu adresu URL.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano tworzenie obiektu CUrl i pobierania jej ciągu adresu URL  
  
 [!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]  
  
##  <a name="curl"></a>  CUrl::CUrl  
 Konstruktor.  
  
```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `urlThat`  
 `CUrl` Obiektu można skopiować do tworzenia adresu URL.  
  
##  <a name="dtor"></a>  CUrl:: ~ CUrl  
 Destruktor.  
  
```
~CUrl() throw();
```  
  
##  <a name="getextrainfo"></a>  CUrl::GetExtraInfo  
 Wywołanie tej metody, aby uzyskać dodatkowe informacje (takie jak *tekst* lub # *tekst*) z adresu URL.  
  
```
inline LPCTSTR GetExtraInfo() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg zawierający dodatkowe informacje.  
  
##  <a name="getextrainfolength"></a>  CUrl::GetExtraInfoLength  
 Wywołanie tej metody, aby uzyskać dodatkowe informacje o długości (takich jak *tekst* lub # *tekst*) można pobrać z adresu URL.  
  
```
inline DWORD GetExtraInfoLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca długość ciągu zawierający dodatkowe informacje.  
  
##  <a name="gethostname"></a>  CUrl::GetHostName  
 Wywołanie tej metody można pobrać nazwy hosta z adresu URL.  
  
```
inline LPCTSTR GetHostName() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nazwę hosta.  
  
##  <a name="gethostnamelength"></a>  CUrl::GetHostNameLength  
 Wywołaj tę metodę, aby pobrać długości nazwy hosta.  
  
```
inline DWORD GetHostNameLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca długość nazwy hosta.  
  
##  <a name="getpassword"></a>  CUrl::GetPassword  
 Wywołaj tę metodę w celu pobrania hasła z adresu URL.  
  
```
inline LPCTSTR GetPassword() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca hasło.  
  
##  <a name="getpasswordlength"></a>  CUrl::GetPasswordLength  
 Wywołaj tę metodę, aby pobrać długości hasła.  
  
```
inline DWORD GetPasswordLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca długość hasła.  
  
##  <a name="getportnumber"></a>  CUrl::GetPortNumber  
 Wywołanie tej metody, aby uzyskać numer portu.  
  
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
 Wywołaj tę metodę, aby uzyskać adres URL nazwy schematu.  
  
```
inline LPCTSTR GetSchemeName() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nazwę schemat adresu URL (na przykład "http" lub "ftp").  
  
##  <a name="getschemenamelength"></a>  CUrl::GetSchemeNameLength  
 Wywołanie tej metody można uzyskać długości nazwy schemat adresu URL.  
  
```
inline DWORD GetSchemeNameLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca długość nazwy schemat adresu URL.  
  
##  <a name="geturllength"></a>  CUrl::GetUrlLength  
 Wywołanie tej metody, aby uzyskać długość adresu URL.  
  
```
inline DWORD GetUrlLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca długość adresu URL.  
  
##  <a name="geturlpath"></a>  CUrl::GetUrlPath  
 Wywołanie tej metody można uzyskać ścieżki adresu URL.  
  
```
inline LPCTSTR GetUrlPath() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ścieżkę adresu URL.  
  
##  <a name="geturlpathlength"></a>  CUrl::GetUrlPathLength  
 Wywołanie tej metody, aby uzyskać długość ścieżki adresu URL.  
  
```
inline DWORD GetUrlPathLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca długość ścieżki adresu URL.  
  
##  <a name="getusername"></a>  CUrl::GetUserName  
 Wywołanie tej metody można uzyskać nazwy użytkownika z adresu URL.  
  
```
inline LPCTSTR GetUserName() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nazwę użytkownika.  
  
##  <a name="getusernamelength"></a>  CUrl::GetUserNameLength  
 Wywołanie tej metody, aby uzyskać długość nazwy użytkownika.  
  
```
inline DWORD GetUserNameLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca długość nazwy użytkownika.  
  
##  <a name="operator_eq"></a>  CUrl::operator =  
 Przypisuje określonego `CUrl` obiektu do bieżącego `CUrl` obiektu.  
  
```
CUrl& operator= (const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `urlThat`  
 `CUrl` Obiekt ma zostać skopiowany do bieżącego obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do bieżącego obiektu.  
  
##  <a name="setextrainfo"></a>  CUrl::SetExtraInfo  
 Wywołanie tej metody można ustawić dodatkowe informacje (takie jak *tekst* lub # *tekst*) adresu URL.  
  
```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszInfo*  
 Ciąg zawierający dodatkowe informacje, aby uwzględnić w adresie URL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
##  <a name="sethostname"></a>  CUrl::SetHostName  
 Wywołanie tej metody można ustawić nazwy hosta.  
  
```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszHost`  
 Nazwa hosta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
##  <a name="setpassword"></a>  CUrl::SetPassword  
 Wywołaj tę metodę, aby ustawić hasło.  
  
```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPass*  
 Hasło.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
##  <a name="setportnumber"></a>  CUrl::SetPortNumber  
 Wywołaj tę metodę, aby ustawić numer portu.  
  
```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nPrt*  
 Numer portu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
##  <a name="setscheme"></a>  CUrl::SetScheme  
 Wywołaj tę metodę, aby ustawić schemat adresu URL.  
  
```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nScheme`  
 Jeden z [ATL_URL_SCHEME](atl-url-scheme-enum.md) wartości schematu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Można również ustawić schemat według nazwy (zobacz [CUrl::SetSchemeName](#setschemename)).  
  
##  <a name="setschemename"></a>  CUrl::SetSchemeName  
 Wywołaj tę metodę, aby ustawić adres URL nazwy schematu.  
  
```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSchm*  
 Nazwa schematu URL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Schemat można również ustawić za pomocą [ATL_URL_SCHEME](atl-url-scheme-enum.md) stałych (zobacz [CUrl::SetScheme](#setscheme)).  
  
##  <a name="seturlpath"></a>  CUrl::SetUrlPath  
 Wywołaj tę metodę, aby ustawić ścieżkę adresu URL.  
  
```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPath`  
 Ścieżka adresu URL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
##  <a name="setusername"></a>  CUrl::SetUserName  
 Wywołaj tę metodę, aby ustawić nazwę użytkownika.  
  
```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszUser*  
 Nazwa użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../atl/reference/atl-classes.md)
