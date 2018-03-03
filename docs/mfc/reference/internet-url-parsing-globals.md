---
title: Internet adresu URL funkcje globalne do analizowania i pomocnikami | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.isapi
dev_langs:
- C++
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e29ae754e7f5b078c23f0cdf27c0a280cd28b40a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet adresu URL funkcje globalne do analizowania i pomocnikami
Gdy klient wysyła zapytanie do serwera internetowego, można użyć jednego adresu URL, funkcje globalne do analizowania do wyodrębnienia informacji o kliencie. Funkcje pomocy zawierają inne funkcje internetowe.
  
## <a name="internet-url-parsing-globals"></a>Funkcje globalne do analizowania internetowych adresów URL  
  
|||  
|-|-|  
|[Afxparseurl —](#afxparseurl)|Analizuje ciągu adresu URL i zwraca typ usługi i jego składniki.|  
|[Afxparseurlex —](#afxparseurlex)|Analizuje ciągu adresu URL i zwraca typ usługi i jego składników, a także podanie nazwy użytkownika i hasła.|  

## <a name="other-internet-helpers"></a>Inne pomocników Internet
|||
|-|-|
|[Afxthrowinternetexception —](#afxthrowinternetexception)|Zgłasza wyjątek związane z połączeniem internetowym.|
|[Afxgetinternethandletype —](#afxgetinternethandletype)|Określa typ dojścia internetowego.|
  
##  <a name="afxparseurl"></a>Afxparseurl —  
 Tym globalnych jest używany w [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
```   
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,  
    DWORD& dwServiceType,  
    CString& strServer,  
    CString& strObject,  
    INTERNET_PORT& nPort); 
```  
  
### <a name="parameters"></a>Parametry  
 *pstrURL*  
 Wskaźnik do ciąg zawierający adres URL do przeanalizowania.  
  
 `dwServiceType`  
 Wskazuje typ usługi internetowe. Dopuszczalne są następujące wartości:  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 Pierwszy segment adresu URL następującego typu usługi.  
  
 `strObject`  
 Adres URL odwołujące się do obiektu (może być pusty).  
  
 `nPort`  
 Określona z serwera albo obiekt części adresu URL, jeśli albo istnieje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli adres URL został pomyślnie przeanalizowano; w przeciwnym razie wartość 0, jeśli jest pusty lub nie zawiera znanego typu usługi internetowe.  
  
### <a name="remarks"></a>Uwagi  
 Analizuje ciągu adresu URL, a zwraca typ usługi i jego składniki.  
  
 Na przykład `AfxParseURL` analizuje adresów URL w postaci **service://server/dir/dir/object.ext:port** i zwraca jego składniki przechowywane w następujący sposób:  
  
 `strServer`== "server"  
  
 `strObject`== "/ dir/dir/object/object.ext"  
  
 `nPort`== #port  
  
 `dwServiceType`== #service  
  
> [!NOTE]
>  Aby wywołać tę funkcję, projektu musi zawierać AFXINET. H.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxinet.h  
  
##  <a name="afxparseurlex"></a>Afxparseurlex —  
 To jest rozszerzona wersja [afxparseurl —](#afxparseurl) i jest używany w [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
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
 *pstrURL*  
 Wskaźnik do ciąg zawierający adres URL do przeanalizowania.  
  
 `dwServiceType`  
 Wskazuje typ usługi internetowe. Dopuszczalne są następujące wartości:  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 Pierwszy segment adresu URL następującego typu usługi.  
  
 `strObject`  
 Adres URL odwołujące się do obiektu (może być pusty).  
  
 `nPort`  
 Określona z serwera albo obiekt części adresu URL, jeśli albo istnieje.  
  
 *strUsername*  
 Odwołanie do `CString` obiekt zawierający nazwę użytkownika.  
  
 `strPassword`  
 Odwołanie do `CString` obiekt zawierający hasło użytkownika.  
  
 `dwFlags`  
 Flagi, kontrolowanie sposobu przeanalizować adresu URL. Może być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|**ICU_DECODE**|Konwertuj sekwencji unikowych XX % znaków.|  
|**ICU_NO_ENCODE**|Nie można konwertować niebezpieczny znaki wyjścia sekwencji.|  
|**ICU_NO_META**|Nie usuwaj meta sekwencje (na przykład "\". i "\"..) z adresu URL.|  
|**ICU_ENCODE_SPACES_ONLY**|Kodowanie tylko spacje.|  
|**ICU_BROWSER_MODE**|Nie kodowania i dekodowania znaków po "#" lub ", a nie usuwaj końcu spację po". Jeśli ta wartość nie jest określona, cały adres URL jest zakodowany i usunięciu wiodących znaków odstępu.|  
  
 Jeśli użytkownik korzysta z domyślnych MFC, czyli żadnych flag funkcji konwertuje wszystkie znaki niebezpieczne i meta sekwencje (takich jak \\., \.., i \\...) ucieczki sekwencji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli adres URL został pomyślnie przeanalizowano; w przeciwnym razie wartość 0, jeśli jest pusty lub nie zawiera znanego typu usługi internetowe.  
  
### <a name="remarks"></a>Uwagi  
 Analizuje ciągu adresu URL, a zwraca typ usługi i jego składników, a także podanie nazwy użytkownika i hasła. Flagi wskazują, jak niebezpieczne znaki są obsługiwane.  
  
> [!NOTE]
>  Aby wywołać tę funkcję, projektu musi zawierać AFXINET. H.  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxinet.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
 
## <a name="afxgetinternethandletype"></a>Afxgetinternethandletype —
Użyj tej funkcji globalnych można określić typu dojścia internetowego.  
   
### <a name="syntax"></a>Składnia  
  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );  
```
### <a name="parameters"></a>Parametry  
 `hQuery`  
 Dojście do zapytania Internet.  
   
### <a name="return-value"></a>Wartość zwracana  
 Dowolne typy usługi internetowe, zdefiniowane przez WININET. H. Zobacz sekcję uwag listę tych usług internetowych. Jeśli dojście ma wartość NULL lub nie został rozpoznany, funkcja zwraca AFX_INET_SERVICE_UNK.  
   
### <a name="remarks"></a>Uwagi  
 Poniższa lista zawiera możliwych typów Internet zwrócony przez `AfxGetInternetHandleType`.  
  
-   INTERNET_HANDLE_TYPE_INTERNET  
  
-   INTERNET_HANDLE_TYPE_CONNECT_FTP  
  
-   INTERNET_HANDLE_TYPE_CONNECT_GOPHER  
  
-   INTERNET_HANDLE_TYPE_CONNECT_HTTP  
  
-   INTERNET_HANDLE_TYPE_FTP_FIND  
  
-   INTERNET_HANDLE_TYPE_FTP_FIND_HTML  
  
-   INTERNET_HANDLE_TYPE_FTP_FILE  
  
-   INTERNET_HANDLE_TYPE_FTP_FILE_HTML  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FIND  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FILE  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML  
  
-   INTERNET_HANDLE_TYPE_HTTP_REQUEST  
  
> [!NOTE]
>  Aby można było wywołać tę funkcję, projektu musi zawierać AFXINET. H.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Afxparseurl —](internet-url-parsing-globals.md#afxparseurl)
 
## <a name="afxthrowinternetexception"></a>Afxthrowinternetexception —
Zgłasza wyjątek Internet.  
   
### <a name="syntax"></a>Składnia    
```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );  
```
### <a name="parameters"></a>Parametry  
 `dwContext`  
 Identyfikator kontekstu dla operacji, który spowodował błąd. Wartość domyślna `dwContext` pierwotnie określonym w [CInternetSession](cinternetsession-class.md) i jest przekazywana do [CInternetConnection](cinternetconnection-class.md)- i [CInternetFile](cinternetfile-class.md)-klas pochodnych. Dla określonej operacji wykonywanych na połączenie lub pliku, zwykle zastąpić domyślną z `dwContext` własny. Ta wartość jest następnie zwracany do [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) do identyfikowania stan określonej operacji. 
  
 `dwError`  
 Błąd, który spowodował wyjątek.  
   
### <a name="remarks"></a>Uwagi  
 Jest odpowiedzialny za ustalania przyczyny oparte na kod błędu systemu operacyjnego.  
  
> [!NOTE]
>  Aby wywołać tę funkcję, projektu musi zawierać AFXINET. H.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Klasa CInternetException](cinternetexception-class.md)   
 [THROW](#throw)
 

