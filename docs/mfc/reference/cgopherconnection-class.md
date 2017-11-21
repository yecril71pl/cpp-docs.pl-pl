---
title: Klasa CGopherConnection | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
dev_langs: C++
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7405ec72a046a482f1b9bd8ddbdb806ba0be5e13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cgopherconnection-class"></a>Klasa CGopherConnection
Zarządza połączenie z serwerem Internet gopher.  
  
> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` i ich elementy członkowskie są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą one nadal działać na starszych platformach.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CGopherConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Konstruuje `CGopherConnection` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGopherConnection::CreateLocator](#createlocator)|Tworzy [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu można znaleźć plików na serwerze gopher.|  
|[CGopherConnection::GetAttribute](#getattribute)|Pobiera informacje o atrybutach dotyczące gopher obiektu.|  
|[CGopherConnection::OpenFile](#openfile)|Otwiera plik gopher.|  
  
## <a name="remarks"></a>Uwagi  
 Usługa gopher jest jednym z trzech usług internetowych, rozpoznaje klas MFC WinInet.  
  
 Klasa `CGopherConnection` zawiera konstruktora i trzy funkcje Członkowskie dodatkowe, które zarządzać usługą gopher: [OpenFile](#openfile), [CreateLocator](#createlocator), i [GetAttribute](#getattribute).  
  
 Do komunikacji z serwerem gopher Internet, należy najpierw utworzyć wystąpienie [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie wywołać [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), co powoduje `CGopherConnection` obiektu i zwraca wskaźnik do niego. Nigdy nie twórz `CGopherConnection` obiekt bezpośrednio.  
  
 Aby dowiedzieć się więcej na temat `CGopherConnection` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md). Więcej informacji o używaniu pozostałe dwa obsługiwane usługi internetowe, FTP i HTTP Zobacz klasy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CGopherConnection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cgopherconnection"></a>CGopherConnection::CGopherConnection  
 Ta funkcja elementu członkowskiego jest wywoływana w celu utworzenia `CGopherConnection` obiektu.  
  
```  
CGopherConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CGopherConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>Parametry  
 `pSession`  
 Wskaźnik do pokrewny [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.  
  
 `hConnected`  
 Dojście systemu Windows w bieżącej sesji Internet.  
  
 `pstrServer`  
 Wskaźnik do ciąg zawierający nazwę serwera FTP.  
  
 `dwContext`  
 Identyfikator kontekstu dla tej operacji. `dwContext`Określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Wartość domyślna jest ustawiona na 1; jednak można jawnie przypisać identyfikator kontekstu określonych dla tej operacji. Obiekt i pracę go nie będą skojarzone z tym identyfikatorem kontekstu.  
  
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
  
 `nPort`  
 Liczba, która identyfikuje port TCP/IP używany na serwerze.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie twórz `CGopherConnection` bezpośrednio. Zamiast wywoływać [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), co powoduje `CGopherConnection` obiektu i zwraca wskaźnik do niego.  
  
##  <a name="createlocator"></a>CGopherConnection::CreateLocator  
 Wywołanie tej funkcji członkowskiej, aby utworzyć Lokalizator gopher można znaleźć lub określić plik na serwerze gopher.  
  
```  
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType);  
  
static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

 
static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,  
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrDisplayString`  
 Wskaźnik do ciąg zawierający nazwę dokumentu gopher lub katalogu, które mają zostać pobrane. Jeśli `pstrDisplayString` parametr jest **NULL**, jest zwracany domyślny katalog gopher serwera.  
  
 `pstrSelectorString`  
 Wskaźnik do ciągu selektor do wysłania na serwer gopher w celu pobrania elementu. `pstrSelectorString`może być **NULL**.  
  
 *dwGopherType*  
 To ustawienie określa, czy `pstrSelectorString` odwołuje się do katalogu lub dokument, i określa, czy żądanie jest gopher lub gopher +. Zobacz atrybuty dla struktury [GOPHER_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa384215) w zestawie Windows SDK.  
  
 `pstrLocator`  
 Wskaźnik do ciąg identyfikujący otworzyć plik. Ogólnie rzecz biorąc, ten ciąg jest zwracana z wywołania [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).  
  
 *pstrServerName*  
 Wskaźnik do ciąg zawierający nazwę serwera gopher.  
  
 `nPort`  
 Liczba identyfikująca portu internetowego dla tego połączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wersji statycznej funkcji członkowskiej, należy określić serwer, a wersja niestatyczna używa nazwy serwera na podstawie obiektu połączenia.  
  
 Aby pobrać informacje z serwera gopher, aplikacja musi najpierw uzyskać lokalizatora gopher. Aplikacji następnie należy traktować jako token nieprzezroczyste Lokalizator (oznacza to, aplikacji można użyć Lokalizator, ale nie bezpośrednio manipulowania lub porównaj je). Zwykle aplikacja używa Lokalizator wywołań [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) funkcji członkowskiej do pobrania konkretnych danych.  
  
##  <a name="getattribute"></a>CGopherConnection::GetAttribute  
 Wywołanie tej funkcji członkowskich można pobrać z serwera gopher określony atrybut informacje o elemencie.  
  
```  
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,  
    CString& strResult,);
```  
  
### <a name="parameters"></a>Parametry  
 `refLocator`  
 Odwołanie do [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.  
  
 *strRequestedAttributes*  
 Ciąg rozdzielonych spacjami Określanie nazw wymaganych atrybutów.  
  
 `strResult`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) odbierająca Typ lokalizatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
##  <a name="openfile"></a>CGopherConnection::OpenFile  
 Wywołanie tej funkcji elementu członkowskiego, aby otworzyć plik na serwerze gopher.  
  
```  
CGopherFile* OpenFile(
    CGopherLocator& refLocator,  
    DWORD dwFlags = 0,  
    LPCTSTR pstrView = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `refLocator`  
 Odwołanie do [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.  
  
 `dwFlags`  
 Dowolna kombinacja flag INTERNET_FLAG_ *. Zobacz [CInternetSession::OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) więcej informacji o INTERNET_FLAG_\* flagi.  
  
 `pstrView`  
 Wskaźnik do ciągu widoku pliku. Jeśli istnieje kilka widoków pliku na serwerze, ten parametr określa, aby otworzyć widok pliku. Jeśli `pstrView` jest **NULL**, widok domyślny plik jest używany.  
  
 `dwContext`  
 Identyfikator kontekstu otwierany plik. Zobacz **uwagi** uzyskać więcej informacji o `dwContext`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [cgopherfile —](../../mfc/reference/cgopherfile-class.md) obiekt, aby go otworzyć.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie `dwContext` domyślne, aby skonfigurować identyfikator kontekstu wartości wybrane. Identyfikator kontekstu jest skojarzony z tym działania związane z `CGopherConnection` obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stan operacji, z którą zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFtpConnection](../../mfc/reference/cftpconnection-class.md)   
 [Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)   
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Klasa CGopherLocator](../../mfc/reference/cgopherlocator-class.md)   
 [Cgopherfile — klasa](../../mfc/reference/cgopherfile-class.md)   
 [Klasa CInternetSession](../../mfc/reference/cinternetsession-class.md)
