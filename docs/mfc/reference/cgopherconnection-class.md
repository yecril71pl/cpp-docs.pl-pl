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
ms.openlocfilehash: d960d566a63531af211592a7a8ae8f1cb35c5958
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300725"
---
# <a name="cgopherconnection-class"></a>Klasa CGopherConnection

Zarządza połączeniem z serwerem Internet gopher.

> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` i ich elementów członkowskich są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą one nadal działały na starszych platformach.

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
|[CGopherConnection::CreateLocator](#createlocator)|Tworzy [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu, aby znaleźć pliki na serwerze gophera.|
|[CGopherConnection::GetAttribute](#getattribute)|Pobiera informacje o atrybutach dotyczące obiektu gopher.|
|[CGopherConnection::OpenFile](#openfile)|Otwiera plik gopher.|

## <a name="remarks"></a>Uwagi

Usługa gopher jest jednym z trzech usług internetowych, które rozpoznają klas MFC WinInet.

Klasa `CGopherConnection` zawiera konstruktora i trzy funkcje Członkowskie dodatkowe, które zarządzać usługą gopher: [OpenFile](#openfile), [CreateLocator](#createlocator), i [GetAttribute](#getattribute).

Aby komunikować się z serwerem Internet gopher, należy najpierw utworzyć wystąpienie [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie wywołaj [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), co powoduje utworzenie `CGopherConnection` obiektu i zwraca wskaźnik do niego. Nigdy nie twórz `CGopherConnection` obiektu bezpośrednio.

Aby dowiedzieć się więcej o tym, jak `CGopherConnection` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md). Więcej informacji o używaniu dla pozostałych obsługiwanych usług internetowych, FTP i HTTP zawiera opis klas [CHttpConnection](../../mfc/reference/chttpconnection-class.md) i [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

##  <a name="cgopherconnection"></a>  CGopherConnection::CGopherConnection

Ta funkcja członkowska jest wywoływana, aby skonstruować `CGopherConnection` obiektu.

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
Wskaźnik do powiązane [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.

*hConnected*<br/>
Uchwyt Windows bieżącej sesji internetowej.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera FTP.

*dwContext*<br/>
Identyfikator kontekstu dla tej operacji. *dwContext* określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Wartość domyślna jest ustawiona na 1; Jednakże można jawnie przypisać identyfikator kontekstu określonego dla operacji. Obiekt i wszelkie prace, które wykonuje zostanie skojarzona z tym identyfikatorem kontekstu.

*pstrUserName*<br/>
Wskaźnik na ciąg zakończony znakiem null, określający nazwę użytkownika, aby zalogować się. Jeśli ma wartość NULL, wartość domyślna jest anonimowy.

*pstrPassword*<br/>
Wskaźnik Określa hasło używane do logowania się w ciąg zakończony znakiem null. Jeśli oba *pstrPassword* i *pstrUserName* mają wartość NULL, domyślne hasło anonimowe to nazwa adres e-mail użytkownika. Jeśli *pstrPassword* ma wartość NULL (lub pustego ciągu), ale *pstrUserName* nie ma wartości NULL, puste hasło jest używane. W poniższej tabeli opisano zachowanie cztery ustawienia możliwe *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nazwa użytkownika jest wysyłane do serwera FTP|Hasła przesyłanych do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Wartość NULL lub ""|Wartość NULL lub ""|"anonimowy"|Nazwa e-mail użytkownika|
|Ciąg znaków innych niż NULL|Wartość NULL lub ""|*pstrUserName*|" "|
|PUSTY ciąg inną niż NULL|BŁĄD|BŁĄD||
|Ciąg znaków innych niż NULL|Ciąg znaków innych niż NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Liczba, która identyfikuje port TCP/IP używany na serwerze.

### <a name="remarks"></a>Uwagi

Nigdy nie twórz `CGopherConnection` bezpośrednio. Zamiast wywoływać [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), co powoduje utworzenie `CGopherConnection` obiektu i zwraca wskaźnik do niego.

##  <a name="createlocator"></a>  CGopherConnection::CreateLocator

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć Lokalizator gopher, aby znaleźć lub określić plik na serwerze gophera.

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
Wskaźnik do ciągu zawierającego nazwę gopher dokumentu lub katalogu, które mają zostać pobrane. Jeśli *pstrDisplayString* parametr ma wartość NULL, jest zwracana domyślny katalog dla serwera gopher.

*pstrSelectorString*<br/>
Wskaźnik do ciągu selektor do wysłania do serwera gopher, aby pobrać element. *pstrSelectorString* może mieć wartości NULL.

*dwGopherType*<br/>
Określa, czy *pstrSelectorString* odwołuje się do katalogu lub dokumentu, oraz tego, czy żądanie jest gopher lub gopher +. Zobacz atrybuty dla struktury [GOPHER_FIND_DATA](/windows/desktop/api/wininet/ns-wininet-gopher_find_dataa) w zestawie Windows SDK.

*pstrLocator*<br/>
Wskaźnik na ciąg, który identyfikuje plik do otwarcia. Ogólnie rzecz biorąc, ten ciąg jest zwracany z wywołania [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera gopher.

*nPort*<br/>
Numer identyfikujący portu internetowego dla tego połączenia.

### <a name="return-value"></a>Wartość zwracana

A [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.

### <a name="remarks"></a>Uwagi

W wersji statycznej funkcji składowej wymaga określenia serwera, nazwę serwera z obiektu połączenia jest używana wersja statyczna.

Aby pobrać informacje z serwera gopher, aplikacji musi najpierw uzyskać lokalizatora gopher. Aplikacja następnie potraktować jako token nieprzezroczyste Lokalizator (oznacza to, że aplikacja użyć Lokalizator, ale nie są bezpośrednio manipulowania lub porównaj je). Zazwyczaj aplikacja używa Lokalizator wywołania [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) funkcja elementu członkowskiego w celu pobrania konkretnych danych.

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

Wywołaj tę funkcję elementu członkowskiego, aby pobrać określony atrybut informacji na temat elementu z serwera gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odwołanie do [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.

*strRequestedAttributes*<br/>
Rozdzielany spacjami ciąg, określanie nazw wymaganych atrybutów.

*strResult*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) , która otrzymuje Typ lokalizatora.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.

##  <a name="openfile"></a>  CGopherConnection::OpenFile

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć plik na serwerze gophera.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odwołanie do [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.

*dwFlags*<br/>
Dowolna kombinacja flag INTERNET_FLAG_ *. Zobacz [CInternetSession::OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) więcej informacji na temat INTERNET_FLAG_\* flag.

*pstrView*<br/>
Wskaźnik do ciągu widok pliku. Jeśli istnieje kilka widoków pliku na serwerze, ten parametr określa widok plików, które można otworzyć. Jeśli *pstrView* ma wartość NULL, jest używany domyślny widok plików.

*dwContext*<br/>
Identyfikator kontekstu otwierany plik. Zobacz **uwagi** Aby uzyskać więcej informacji na temat *dwContext*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CGopherFile](../../mfc/reference/cgopherfile-class.md) obiekt ma zostać otwarty.

### <a name="remarks"></a>Uwagi

Zastąp *dwContext* domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest skojarzony z tym działania związane z `CGopherConnection` obiekt utworzony przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Zwracana jest wartość [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) do udostępniania informacji o stanie operacji za pomocą którego jest identyfikowana. Zapoznaj się z artykułem [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.

## <a name="see-also"></a>Zobacz także

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[Klasa CHttpConnection](../../mfc/reference/chttpconnection-class.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CInternetSession](../../mfc/reference/cinternetsession-class.md)
