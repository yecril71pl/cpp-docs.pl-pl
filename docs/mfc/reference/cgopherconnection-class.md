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
ms.openlocfilehash: eade1a82b674d5ad2e91146559139445ef017180
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373714"
---
# <a name="cgopherconnection-class"></a>Klasa CGopherConnection

Zarządza połączeniem z serwerem internetowym gopher.

> [!NOTE]
> Klasy `CGopherConnection`, `CGopherFile` `CGopherFileFind`, `CGopherLocator` i ich członkowie zostały przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą nadal działać na wcześniejszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Konstruuje `CGopherConnection` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|Tworzy [obiekt CGopherLocator,](../../mfc/reference/cgopherlocator-class.md) aby znaleźć pliki na serwerze gopher.|
|[CGopherConnection::GetAttribute](#getattribute)|Pobiera informacje o atrybutach obiektu gopher.|
|[CGopherConnection::OpenFile](#openfile)|Otwiera plik gopher.|

## <a name="remarks"></a>Uwagi

Usługa gopher jest jedną z trzech usług internetowych rozpoznawanych przez klasy MFC WinInet.

Klasa `CGopherConnection` zawiera konstruktora i trzy dodatkowe funkcje członkowskie, które zarządzają usługą gopher: [OpenFile](#openfile), [CreateLocator](#createlocator)i [GetAttribute](#getattribute).

Aby komunikować się z gopher serwera internetowego, należy najpierw utworzyć [wystąpienie CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie wywołać [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), który tworzy `CGopherConnection` obiekt i zwraca wskaźnik do niego. Nigdy nie `CGopherConnection` tworzysz obiektu bezpośrednio.

Aby dowiedzieć `CGopherConnection` się więcej o tym, jak działa z innymi klasami MFC Internet, zobacz artykuł [Programowanie internetowe z WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji na temat korzystania z pozostałych dwóch obsługiwanych usług internetowych, ftp i HTTP zobacz klasy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Połączenie międzysystemowe CInternet](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

Ta funkcja elementu członkowskiego `CGopherConnection` jest wywoływana do konstruowania obiektu.

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

*pSesja*<br/>
Wskaźnik do powiązanego [obiektu CInternetSession.](../../mfc/reference/cinternetsession-class.md)

*hPołączone*<br/>
Uchwyt systemu Windows bieżącej sesji internetowej.

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera FTP.

*Dwcontext*<br/>
Identyfikator kontekstu dla operacji. *dwContext* identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Wartość domyślna jest ustawiona na 1; jednak można jawnie przypisać identyfikator określonego kontekstu dla operacji. Obiekt i wszelkie prace, które wykonuje, będą skojarzone z tym identyfikatorem kontekstu.

*pstrUserName*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa nazwę użytkownika do logowania. Jeśli null, wartość domyślna jest anonimowa.

*pstr Hasło*<br/>
Wskaźnik do ciągu zakończonego wartością null, który określa hasło używane do logowania. Jeśli zarówno *pstrPassword,* jak i *pstrUserName* mają wartość NULL, domyślnym anonimowym hasłem jest nazwa e-mail użytkownika. Jeśli *pstrPassword* ma wartość NULL (lub pusty ciąg), ale *pstrUserName* nie ma wartości NULL, używane jest puste hasło. W poniższej tabeli opisano zachowanie czterech możliwych ustawień *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstr Hasło*|Nazwa użytkownika wysłana do serwera FTP|Hasło wysłane do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL lub " " "|NULL lub " " "|"anonimowy"|Nazwa e-mail użytkownika|
|Ciąg nienawidkowy|NULL lub " " "|*pstrUserName*|" "|
|Ciąg null nienawidkowy|BŁĄD|BŁĄD||
|Ciąg nienawidkowy|Ciąg nienawidkowy|*pstrUserName*|*pstr Hasło*|

*Nport*<br/>
Liczba identyfikująca port TCP/IP do użycia na serwerze.

### <a name="remarks"></a>Uwagi

Nigdy nie `CGopherConnection` tworzysz bezpośrednio. Zamiast tego wywołaj [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), który tworzy `CGopherConnection` obiekt i zwraca do niego wskaźnik.

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a>CGopherConnection::CreateLocator

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć lokalizator gopher, aby znaleźć lub zidentyfikować plik na serwerze gopher.

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

*pstrDisplayStrowanie*<br/>
Wskaźnik do ciągu zawierającego nazwę dokumentu gopher lub katalogu do pobrania. Jeśli parametr *pstrDisplayString* ma wartość NULL, zwracany jest domyślny katalog serwera gopher.

*pstrSelectorString*<br/>
Wskaźnik do ciągu selektora, który ma zostać wysłany do serwera gopher w celu pobrania elementu. *pstrSelectorStrowanie* może mieć wartość NULL.

*typ dwGopherType*<br/>
Określa, czy *pstrSelectorString* odwołuje się do katalogu lub dokumentu i czy żądanie jest gopher lub gopher+. Zobacz atrybuty [struktury GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) w windows SDK.

*lokalizator pstrLocator*<br/>
Wskaźnik do ciągu identyfikujący plik do otwarcia. Ogólnie rzecz biorąc ten ciąg jest zwracany z wywołania do [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName (nazwa pstrServerName)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera gopher.

*Nport*<br/>
Numer identyfikujący port internetowy dla tego połączenia.

### <a name="return-value"></a>Wartość zwracana

Obiekt [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

### <a name="remarks"></a>Uwagi

Statyczna wersja funkcji elementu członkowskiego wymaga określenia serwera, podczas gdy wersja niestatyczna używa nazwy serwera z obiektu połączenia.

Aby pobrać informacje z serwera gopher, aplikacja musi najpierw uzyskać lokalizator gopher. Aplikacja musi następnie traktować lokalizatora jako nieprzezroczystego tokenu (oznacza to, że aplikacja może używać lokalizatora, ale nie bezpośrednio manipulować lub porównywać go). Zwykle aplikacja używa lokalizatora dla wywołań [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) funkcji elementu członkowskiego, aby pobrać określone informacje.

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a>CGopherConnection::GetAttribute

Wywołanie tej funkcji elementu członkowskiego, aby pobrać określone informacje o atrybutach o elemencie z serwera gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parametry

*reflocator*<br/>
Odwołanie do [obiektu CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*strRequestedAttributes*<br/>
Ciąg rozdzielany przestrzenią określający nazwy żądanych atrybutów.

*strResult (wynik)*<br/>
Odwołanie do [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który odbiera typ lokalizatora.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a>CGopherConnection::OpenFile

Wywołanie tej funkcji elementu członkowskiego, aby otworzyć plik na serwerze gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*reflocator*<br/>
Odwołanie do [obiektu CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*Dwflags*<br/>
Dowolna kombinacja flag INTERNET_FLAG_*. Zobacz [CInternetSession::OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) aby uzyskać więcej\* informacji na temat INTERNET_FLAG_ flag.

*widok pstrView*<br/>
Wskaźnik do ciągu widoku pliku. Jeśli na serwerze istnieje kilka widoków pliku, ten parametr określa, który widok pliku ma być otwarty. Jeśli *pstrView* ma wartość NULL, używany jest domyślny widok pliku.

*Dwcontext*<br/>
Identyfikator kontekstu dla otwieranych plików. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat *dwContext*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CGopherFile](../../mfc/reference/cgopherfile-class.md) obiektu do otwarcia.

### <a name="remarks"></a>Uwagi

Zastąd w ustawieniach domyślnego *dwContext,* aby ustawić identyfikator kontekstu na wartość wybranej. Identyfikator kontekstu jest skojarzony z tą `CGopherConnection` określoną operacją obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan operacji, z którą jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="see-also"></a>Zobacz też

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CInternetSession](../../mfc/reference/cinternetsession-class.md)
