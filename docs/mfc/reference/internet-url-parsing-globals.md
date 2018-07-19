---
title: Internet adresu URL funkcje globalne do analizowania i Pomocnicy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.isapi
dev_langs:
- C++
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 839e07db88edf8b1bb007a6aedfe90c94732c784
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335734"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet adresu URL funkcje globalne do analizowania i pomocnikami
Gdy klient wysyła zapytanie do serwera internetowego, można użyć jednego adresu URL, funkcje globalne do analizowania można wyodrębnić informacji o kliencie. Funkcje pomocnicze zapewniają inne funkcje internetowe.
  
## <a name="internet-url-parsing-globals"></a>Funkcje globalne do analizowania internetowych adresów URL  
  
|||  
|-|-|  
|[Afxparseurl —](#afxparseurl)|Analizuje ciąg adresu URL i zwraca typ usługi i jego składników.|  
|[Afxparseurlex —](#afxparseurlex)|Analizuje ciąg adresu URL i zwraca typ usługi i jego składników, a także podanie nazwy użytkownika i hasła.|  

## <a name="other-internet-helpers"></a>Inne pomocników Internet
|||
|-|-|
|[Afxthrowinternetexception —](#afxthrowinternetexception)|Zgłasza wyjątek związane połączenie z Internetem.|
|[Afxgetinternethandletype —](#afxgetinternethandletype)|Określa typ dojścia internetowego.|
  
##  <a name="afxparseurl"></a>  Afxparseurl —  
 Tym globalnego jest używany w [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
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
 Wskaźnik do ciągu zawierającego adres URL do przeanalizowania.  
  
 *dwServiceType*  
 Wskazuje typ usługi w Internecie. Dopuszczalne są następujące wartości:  
  
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
  
 *strServer*  
 Pierwszy segment adresu URL następującego typu usługi.  
  
 *strObject*  
 Obiekt, który adres URL odwołuje się do (mogą być puste).  
  
 *nPort*  
 Określone serwera lub obiekt części adresu URL, jeśli istnieje jeden.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli adres URL został pomyślnie przetworzona; w przeciwnym razie 0, jeśli jest pusta lub nie zawiera znany typ usługi internetowe.  
  
### <a name="remarks"></a>Uwagi  
 On analizuje ciąg adresu URL i zwraca typ usługi i jego składników.  
  
 Na przykład `AfxParseURL` analizuje adresy URL formularzy *service://server/dir/dir/object.ext:port* i zwraca jego składniki przechowywany w następujący sposób:  
  
 *strServer* == "server"  
  
 *strObject* == "/ dir/dir/object/object.ext"  
  
 *nPort* == #port  
  
 *dwServiceType* == #service  
  
> [!NOTE]
>  Aby wywołać tę funkcję, projekt musi zawierać AFXINET. H.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxinet.h  
  
##  <a name="afxparseurlex"></a>  Afxparseurlex —  
 Ta funkcja globalna jest rozszerzona wersja [afxparseurl —](#afxparseurl) i jest używana w [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
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
 Wskaźnik do ciągu zawierającego adres URL do przeanalizowania.  
  
 *dwServiceType*  
 Wskazuje typ usługi w Internecie. Dopuszczalne są następujące wartości:  
  
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
  
 *strServer*  
 Pierwszy segment adresu URL następującego typu usługi.  
  
 *strObject*  
 Obiekt, który adres URL odwołuje się do (mogą być puste).  
  
 *nPort*  
 Określone serwera lub obiekt części adresu URL, jeśli istnieje jeden.  
  
 *strUsername*  
 Odwołanie do `CString` obiekt zawierający nazwę użytkownika.  
  
 *strPassword*  
 Odwołanie do `CString` obiekt zawierający hasło użytkownika.  
  
 *Flagidw*  
 Flagi, kontrolowanie sposobu analizowania adresu URL. Może być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|ICU_DECODE|Konwertowanie sekwencji unikowych XX % znaków.|  
|ICU_NO_ENCODE|Nie można konwertować niebezpiecznych znaków do sekwencji unikowej.|  
|ICU_NO_META|Nie usuwaj sekwencje metadanych (na przykład wzorzec "\". i "\"..) z adresu URL.|  
|ICU_ENCODE_SPACES_ONLY|Kodowanie tylko spacje.|  
|ICU_BROWSER_MODE|Nie kodowania i dekodowania znaki po znaku "#" lub "i nie usuwaj odstępu po". Jeśli ta wartość nie jest określona, cały adres URL jest zaszyfrowana i końcowe biały znak zostanie usunięta.|  
  
 Jeśli użytkownik korzysta z domyślnych MFC, czyli bez flag funkcji konwertuje wszystkich niebezpiecznych znaków i sekwencji meta (takie jak \\., \.., i \\...) jako znak ucieczki dla sekwencji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli adres URL został pomyślnie przetworzona; w przeciwnym razie 0, jeśli jest pusta lub nie zawiera znany typ usługi internetowe.  
  
### <a name="remarks"></a>Uwagi  
 On analizuje ciąg adresu URL i zwraca typ usługi i jego składników, a także podanie nazwy użytkownika i hasła. Flagi wskazują, jak niebezpiecznych znaków są obsługiwane.  
  
> [!NOTE]
>  Aby wywołać tę funkcję, projekt musi zawierać AFXINET. H.  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxinet.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
 
## <a name="afxgetinternethandletype"></a>  Afxgetinternethandletype —
Funkcja ta globalnej można ustalić typu dojścia internetowego.  
   
### <a name="syntax"></a>Składnia  
  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );  
```
### <a name="parameters"></a>Parametry  
 *hQuery*  
 Dojście do wykonywania zapytań w Internecie.  
   
### <a name="return-value"></a>Wartość zwracana  
 Dowolne typy usług internetowych, które są zdefiniowane przez WININET. H. Zobacz sekcję Spostrzeżenia, aby listę tych usług internetowych. Jeśli uchwyt ma wartość NULL lub nie został rozpoznany, funkcja zwraca AFX_INET_SERVICE_UNK.  
   
### <a name="remarks"></a>Uwagi  
 Poniższa lista zawiera możliwe typy internetowych zwracany przez `AfxGetInternetHandleType`.  
  
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
>  Aby wywołać tę funkcję, projekt musi zawierać AFXINET. H.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Afxparseurl —](internet-url-parsing-globals.md#afxparseurl)
 
## <a name="afxthrowinternetexception"></a>  Afxthrowinternetexception —
Zgłasza wyjątek Internet.  
   
### <a name="syntax"></a>Składnia    
```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );  
```
### <a name="parameters"></a>Parametry  
 *dwContext*  
 Identyfikator kontekstu dla operacji, które spowodowały błąd. Wartość domyślna *dwContext* pierwotnie określono w [CInternetSession](cinternetsession-class.md) i jest przekazywany do [CInternetConnection](cinternetconnection-class.md)— i [CInternetFile](cinternetfile-class.md)-klas pochodnych. Dla określonej operacji wykonywanych na połączenia lub pliku, zwykle zastąpienia domyślnej z *dwContext* samodzielnie. Ta wartość jest następnie zwracany do [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) do identyfikowania stan określonej operacji. 
  
 *dwError*  
 Błąd, który spowodował wyjątek.  
   
### <a name="remarks"></a>Uwagi  
 Odpowiedzialność za ustalenie jego przyczyny, w oparciu o kod błędu systemu operacyjnego.  
  
> [!NOTE]
>  Aby wywołać tę funkcję, projekt musi zawierać AFXINET. H.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Klasa CInternetException](cinternetexception-class.md)   
 [THROW](#throw)
 

