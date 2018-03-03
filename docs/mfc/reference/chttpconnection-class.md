---
title: Klasa CHttpConnection | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
dev_langs:
- C++
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a5236a4a957c742074a1305ba2d4359da3ed967
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="chttpconnection-class"></a>Klasa CHttpConnection
Zarządza nawiązanie połączenia z serwerem HTTP.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CHttpConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHttpConnection::CHttpConnection](#chttpconnection)|Tworzy `CHttpConnection` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHttpConnection::OpenRequest](#openrequest)|Otwiera żądanie HTTP.|  
  
## <a name="remarks"></a>Uwagi  
 HTTP jest jednym z trzech protokoły serwera Internet implementowane przez klasy MFC WinInet.  
  
 Klasa `CHttpConnection` zawiera konstruktora i funkcja jednego członka [OpenRequest](#openrequest), który zarządza połączeń z serwerem z protokołem HTTP.  
  
 Do komunikacji z serwerem HTTP, należy najpierw utworzyć wystąpienie [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie utwórz [CHttpConnection](#_mfc_chttpconnection) obiektu. Nigdy nie twórz `CHttpConnection` obiektu bezpośrednio; zamiast wywoływać [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), co powoduje `CHttpConnection` obiektu i zwraca wskaźnik do niego.  
  
 Aby dowiedzieć się więcej na temat `CHttpConnection` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji na temat łączenia się z serwerami przy użyciu innych dwa obsługiwanych protokołów internetowych, gopher FTP, zobacz klasy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) i [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="chttpconnection"></a>CHttpConnection::CHttpConnection  
 Ta funkcja elementu członkowskiego jest wywoływana w celu utworzenia `CHttpConnection` obiektu.  
  
```  
CHttpConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CHttpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 1);

 
CHttpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    DWORD dwFlags,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pSession`  
 Wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.  
  
 `hConnected`  
 Dojście do połączenia internetowego.  
  
 `pstrServer`  
 Wskaźnik do ciąg zawierający nazwę serwera.  
  
 `dwContext`  
 Identyfikator kontekstu `CInternetConnection` obiektu. Zobacz **uwagi** uzyskać więcej informacji o `dwContext`.  
  
 `nPort`  
 Liczba, która identyfikuje portu internetowego dla tego połączenia.  
  
 `pstrUserName`  
 Wskaźnik do zerem ciąg, który określa nazwę użytkownika, aby się zalogować. Jeśli **NULL**, wartością domyślną jest anonimowy.  
  
 `pstrPassword`  
 Wskaźnik do zerem ciąg, który określa hasło używane do logowania. Jeśli oba `pstrPassword` i `pstrUserName` są **NULL**, domyślne hasła anonimowego jest nazwa e-mail użytkownika. Jeśli `pstrPassword` jest **NULL** (lub ciąg pusty), ale `pstrUserName` nie jest **NULL**, puste hasło jest używane. W poniższej tabeli opisano zachowanie cztery ustawienia możliwe `pstrUserName` i `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|Nazwa użytkownika jest wysyłane do serwera FTP|Hasło wysłane do serwera FTP|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**Wartość NULL** lub ""|**Wartość NULL** lub ""|"anonymous"|Nazwa e-mail użytkownika|  
|Nie- **NULL** ciągu|**Wartość NULL** lub ""|`pstrUserName`|" "|  
|**Wartość NULL** z systemem innym niż **NULL** ciągu|**BŁĄD**|**BŁĄD**||  
|Nie- **NULL** ciągu|Nie- **NULL** ciągu|`pstrUserName`|`pstrPassword`|  
  
 `dwFlags`  
 Dowolną kombinację **INTERNET_ FLAG_\***  flagi. Zobacz tabelę w **uwagi** sekcji [CHttpConnection::OpenRequest](#openrequest) opis `dwFlags` wartości.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie twórz `CHttpConnection` bezpośrednio. Zamiast tworzenia obiektu przez wywołanie metody [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).  
  
##  <a name="openrequest"></a>CHttpConnection::OpenRequest  
 Wywołanie tej funkcji elementu członkowskiego, aby otworzyć połączenie HTTP.  
  
```  
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,  
    LPCTSTR pstrObjectName,  
    LPCTSTR pstrReferer = NULL,  
    DWORD_PTR dwContext = 1,  
    LPCTSTR* ppstrAcceptTypes = NULL,  
    LPCTSTR pstrVersion = NULL,  
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

 
CHttpFile* OpenRequest(
    int nVerb,  
    LPCTSTR pstrObjectName,  
    LPCTSTR pstrReferer = NULL,  
    DWORD_PTR dwContext = 1,  
    LPCTSTR* ppstrAcceptTypes = NULL,  
    LPCTSTR pstrVersion = NULL,  
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrVerb`  
 Wskaźnik do ciąg zawierający zlecenie do użycia w żądaniu. Jeśli `NULL`, "GET" jest używany.  
  
 `pstrObjectName`  
 Wskaźnik do ciąg zawierający określone zlecenie obiektu docelowego. Zwykle jest to nazwy pliku wykonywalnego modułu i specyfikator wyszukiwania.  
  
 `pstrReferer`  
 Wskaźnik do ciąg określający adres (URL) dokumentu, z którego adres URL w żądaniu ( `pstrObjectName`) został uzyskany. Jeśli `NULL`, określono brak nagłówka HTTP.  
  
 `dwContext`  
 Identyfikator kontekstu `OpenRequest` operacji. Zobacz sekcję uwag, aby uzyskać więcej informacji `dwContext`.  
  
 `ppstrAcceptTypes`  
 Wskaźnik tablicy zerem `LPCTSTR` wskaźniki do ciągów wskazująca typy zawartości zaakceptowane przez klienta. Jeśli `ppstrAcceptTypes` jest `NULL`, serwery zinterpretować, czy klient akceptuje tylko dokumenty typu "tekstu / *" (oznacza to, że tylko dokumenty tekstowe i nie obrazy lub inne pliki binarne). Typ zawartości jest odpowiednikiem typ_zawartości zmiennej CGI, który określa typ danych dla zapytań, które zostały podłączone informacji, takich jak HTTP POST i PUT.  
  
 `pstrVersion`  
 Wskaźnik do ciągu Definiowanie wersji protokołu HTTP. Jeśli `NULL`, służy "HTTP/1.0".  
  
 `dwFlags`  
 Dowolna kombinacja flag INTERNET_ FLAG_ *. Opis możliwości w sekcji uwag `dwFlags` wartości.  
  
 `nVerb`  
 Liczba skojarzone z typem żądania HTTP. Może to być jedna z następujących czynności:  
  
|Typ żądania HTTP|`nVerb`wartość|  
|-----------------------|-------------------|  
|`HTTP_VERB_POST`|0|  
|`HTTP_VERB_GET`|1|  
|`HTTP_VERB_HEAD`|2|  
|`HTTP_VERB_PUT`|3|  
|`HTTP_VERB_LINK`|4|  
|`HTTP_VERB_DELETE`|5|  
|`HTTP_VERB_UNLINK`|6|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CHttpFile](../../mfc/reference/chttpfile-class.md) żądanego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `dwFlags`może to być jedna z następujących czynności:  
  
|Flaga Internet|Opis|  
|-------------------|-----------------|  
|`INTERNET_FLAG_RELOAD`|Wymusi pobieranie żądanego pliku, obiektów lub listy katalogów z serwera pochodzenia, a nie z pamięci podręcznej.|  
|`INTERNET_FLAG_DONT_CACHE`|Nie dodaje zwróconą jednostkę do pamięci podręcznej.|  
|`INTERNET_FLAG_MAKE_PERSISTENT`|Dodaje zwróconą jednostkę do pamięci podręcznej jako trwałe jednostki. Oznacza to, że czyszczenie pamięci podręcznej standardowe, sprawdzania spójności lub wyrzucanie elementów bezużytecznych nie można usunąć tego elementu z pamięci podręcznej.|  
|`INTERNET_FLAG_SECURE`|Używa semantyki bezpiecznego transakcji. To oznacza przy użyciu protokołu SSL/PCT i jest przydatny w żądaniach HTTP tylko|  
|`INTERNET_FLAG_NO_AUTO_REDIRECT`|Używany tylko z protokołu HTTP, określa, że przekierowania nie powinien automatycznie obsługiwany w [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|  
  
 Zastąpienie `dwContext` domyślne, aby skonfigurować identyfikator kontekstu wartości wybrane. Identyfikator kontekstu jest skojarzony z tym działania związane z `CHttpConnection` obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stan operacji, z którą zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
 Może zostać zgłoszony, wyjątki z tej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
