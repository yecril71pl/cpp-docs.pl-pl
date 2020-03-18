---
title: Klasa CGopherConnection
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: f5d655aa7fd2eb9e41c15c60a71492c24ba43c43
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418588"
---
# <a name="cgopherconnection-class"></a>Klasa CGopherConnection

Zarządza połączeniem z serwerem internetowym gopher.

> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind``CGopherLocator` i ich członkowie są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą nadal działały na wcześniejszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Konstruuje obiekt `CGopherConnection`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CGopherConnection:: islocatorer](#createlocator)|Tworzy obiekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) , aby znaleźć pliki na serwerze gopher.|
|[CGopherConnection:: GetAttribute](#getattribute)|Pobiera informacje o atrybutach o obiekcie gopher.|
|[CGopherConnection:: OpenFile](#openfile)|Otwiera plik gopher.|

## <a name="remarks"></a>Uwagi

Usługa gopher jest jedną z trzech usług internetowych uznawanych przez klasy MFC WinInet.

Klasa `CGopherConnection` zawiera konstruktora i trzech dodatkowych funkcji Członkowskich, które zarządzają usługą gopher: [OpenFile](#openfile) [, coclass i](#createlocator) [GetAttribute](#getattribute).

Aby komunikować się z serwerem internetowym gopher, należy najpierw utworzyć wystąpienie elementu [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie wywołać [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), który tworzy obiekt `CGopherConnection` i zwraca do niego wskaźnik. Nie utworzysz bezpośrednio obiektu `CGopherConnection`.

Aby dowiedzieć się więcej o tym, jak `CGopherConnection` współpracuje z innymi klasami internetowymi MFC, zobacz artykuł [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji o korzystaniu z dwóch innych obsługiwanych usług internetowych, FTP i HTTP, zobacz klasy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

##  <a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

Ta funkcja członkowska jest wywoływana w celu skonstruowania obiektu `CGopherConnection`.

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

*pSession*<br/>
Wskaźnik do powiązanego obiektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) .

*hConnected*<br/>
Dojście systemu Windows bieżącej sesji internetowej.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera FTP.

*dwContext*<br/>
Identyfikator kontekstu dla operacji. *dwContext* identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Wartość domyślna to 1; można jednak jawnie przypisać określony identyfikator kontekstu dla operacji. Obiekt i wszystkie wykonane zadania zostaną skojarzone z tym IDENTYFIKATORem kontekstu.

*pstrUserName*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę użytkownika do zalogowania. Jeśli wartość jest równa NULL, wartość domyślna to anonimowe.

*pstrPassword*<br/>
Wskaźnik do ciągu zakończonego wartością null, który określa hasło, które ma być używane do logowania. Jeśli zarówno *pstrPassword* , jak i *pstrUserName* mają wartość null, domyślnym hasłem anonimowym jest nazwa e-mail użytkownika. Jeśli *pstrPassword* ma wartość null (lub ciąg pusty), ale *pstrUserName* nie ma wartości null, używane jest puste hasło. W poniższej tabeli opisano zachowanie czterech możliwych ustawień *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nazwa użytkownika wysłana do serwera FTP|Hasło wysyłane do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL lub ""|NULL lub ""|anonimowe|Nazwa e-mail użytkownika|
|Ciąg o wartości innej niż NULL|NULL lub ""|*pstrUserName*|" "|
|Pusty ciąg o wartości innej niż NULL|BŁĄD|BŁĄD||
|Ciąg o wartości innej niż NULL|Ciąg o wartości innej niż NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Numer identyfikujący port TCP/IP, który ma być używany na serwerze.

### <a name="remarks"></a>Uwagi

Nie utworzysz jeszcze `CGopherConnection` bezpośrednio. Zamiast tego należy wywołać [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), który tworzy obiekt `CGopherConnection` i zwraca do niego wskaźnik.

##  <a name="createlocator"></a>CGopherConnection:: islocatorer

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć lokalizator gopher, aby znaleźć lub zidentyfikować plik na serwerze gopher.

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

*pstrDisplayString*<br/>
Wskaźnik do ciągu zawierającego nazwę dokumentu lub katalogu gopher do pobrania. Jeśli parametr *pstrDisplayString* ma wartość null, zwracany jest domyślny katalog dla serwera gopher.

*pstrSelectorString*<br/>
Wskaźnik do ciągu selektora, który ma zostać wysłany do serwera gopher w celu pobrania elementu. *pstrSelectorString* może mieć wartość null.

*dwGopherType*<br/>
Określa, czy *pstrSelectorString* odwołuje się do katalogu lub dokumentu, oraz czy żądanie dotyczy gopher lub gopher +. Zobacz atrybuty struktury [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) w Windows SDK.

*pstrLocator*<br/>
Wskaźnik do ciągu identyfikujący plik do otwarcia. Zazwyczaj ten ciąg jest zwracany z wywołania do [CGopherFileFind:: Getlocatorer](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera gopher.

*nPort*<br/>
Numer identyfikujący port internetowy dla tego połączenia.

### <a name="return-value"></a>Wartość zwrócona

Obiekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

### <a name="remarks"></a>Uwagi

Statyczna wersja funkcji członkowskiej wymaga określenia serwera, podczas gdy wersja niestatyczna używa nazwy serwera z obiektu połączenia.

Aby można było pobrać informacje z serwera gopher, aplikacja musi najpierw uzyskać lokalizator gopher. Aplikacja musi następnie traktować lokalizator jako token nieprzezroczysty (oznacza to, że aplikacja może używać lokalizatora, ale nie musi bezpośrednio manipulować ani porównywać). Zwykle aplikacja używa lokalizatora dla wywołań funkcji składowej [CGopherFileFind:: FindFile —](../../mfc/reference/cgopherfilefind-class.md#findfile) w celu pobrania określonej informacji.

##  <a name="getattribute"></a>CGopherConnection:: GetAttribute

Wywołaj tę funkcję elementu członkowskiego, aby pobrać określone informacje o atrybucie dotyczące elementu z serwera gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odwołanie do obiektu [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*strRequestedAttributes*<br/>
Rozdzielany spacjami ciąg określający nazwy żądanych atrybutów.

*strResult*<br/>
Odwołanie do elementu [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który odbiera typ lokalizatora.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

##  <a name="openfile"></a>CGopherConnection:: OpenFile

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć plik na serwerze gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odwołanie do obiektu [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*flagiDW*<br/>
Dowolna kombinacja INTERNET_FLAG_ * flags. Aby uzyskać więcej informacji na INTERNET_FLAG_ flagi\*, zobacz [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) .

*pstrView*<br/>
Wskaźnik do ciągu widoku pliku. Jeśli na serwerze istnieje kilka widoków pliku, ten parametr określa, który widok plików ma zostać otwarty. Jeśli *pstrView* ma wartość null, używany jest domyślny widok plików.

*dwContext*<br/>
Identyfikator kontekstu dla otwieranego pliku. Aby uzyskać więcej informacji na temat *dwContext*, zobacz **uwagi** .

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu [CGopherFile](../../mfc/reference/cgopherfile-class.md) , który ma zostać otwarty.

### <a name="remarks"></a>Uwagi

Zastąp wartości domyślne *dwContext* , aby ustawić identyfikator kontekstu na wybraną wartość. Identyfikator kontekstu jest skojarzony z tą konkretną operacją obiektu `CGopherConnection` utworzonego przez obiekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Wartość jest zwracana do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu operacji, z którą jest identyfikowany. Zapoznaj się z artykułem [internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="see-also"></a>Zobacz też

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CInternetSession](../../mfc/reference/cinternetsession-class.md)
