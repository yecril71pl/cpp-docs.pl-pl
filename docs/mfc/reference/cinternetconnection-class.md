---
title: Klasa CInternetConnection
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 6649986f279e010a833b31157922cb4fd1ea8613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372422"
---
# <a name="cinternetconnection-class"></a>Klasa CInternetConnection

Zarządza połączeniem z serwerem internetowym.

## <a name="syntax"></a>Składnia

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Konstruuje `CInternetConnection` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|Pobiera identyfikator kontekstu dla tego obiektu połączenia.|
|[CInternetConnection::GetServerName](#getservername)|Pobiera nazwę serwera skojarzonego z połączeniem.|
|[CInternetConnection::GetSession](#getsession)|Pobiera wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu skojarzonego z połączeniem.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Dojście do sesji internetowej.|

## <a name="remarks"></a>Uwagi

Jest to klasa podstawowa dla klas MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md)i [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Każda z tych klas zapewnia dodatkowe funkcje komunikacji z odpowiednim serwerem FTP, HTTP lub gopher.

Aby komunikować się bezpośrednio z serwerem internetowym, musisz mieć [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu i `CInternetConnection` obiektu.

Aby dowiedzieć się więcej o tym, jak działają klasy WinInet, zobacz artykuł [Programowanie internetowe z wininet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a>CInternetConnection::CInternetConnection

Ta funkcja elementu członkowskiego `CInternetConnection` jest wywoływana podczas tworzenia obiektu.

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pSesja*<br/>
Wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*Nport*<br/>
Numer identyfikujący port internetowy dla tego połączenia.

*Dwcontext*<br/>
Identyfikator kontekstu `CInternetConnection` obiektu. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat *dwContext*.

### <a name="remarks"></a>Uwagi

Nigdy nie `CInternetConnection` nazywasz siebie; zamiast tego wywołać [CInternetSession](../../mfc/reference/cinternetsession-class.md) funkcji elementu członkowskiego dla typu połączenia, które chcesz ustanowić:

- [Cinternetsession::getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

Wartość domyślna dla *dwContext* jest wysyłana przez MFC do obiektu pochodnego `CInternetConnection`z obiektu [CInternetSession,](../../mfc/reference/cinternetsession-class.md) który utworzył obiekt pochodny **InternetConnection.** Wartość domyślna jest ustawiona na 1; jednak można jawnie przypisać identyfikator określonego kontekstu w konstruktorze [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) dla połączenia. Obiekt i wszelkie prace, które wykonuje, będą skojarzone z tym identyfikatorem kontekstu. Identyfikator kontekstu jest zwracany do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan obiektu, z którym jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a>CInternetConnection::GetContext

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać identyfikator kontekstu dla tej sesji.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator kontekstu przypisany do aplikacji.

### <a name="remarks"></a>Uwagi

Identyfikator kontekstu jest pierwotnie określony w [CInternetSession](../../mfc/reference/cinternetsession-class.md) i `CInternetConnection`propaguje do - i [CInternetFile -pochodne](../../mfc/reference/cinternetfile-class.md)klasy, chyba że określono inaczej w wywołaniu funkcji, która otwiera połączenie. Identyfikator kontekstu jest skojarzony z dowolną operacją danego obiektu i identyfikuje informacje o stanie operacji zwrócone przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

Aby uzyskać więcej `GetContext` informacji na temat pracy z innymi klasami WinInet, aby podać informacje o stanie użytkownika, zobacz artykuł [Pierwsze kroki internetowe: WinInet,](../../mfc/wininet-basics.md) aby uzyskać więcej informacji na temat identyfikatora kontekstu.

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a>CInternetConnection::GetServerName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę serwera skojarzonego z tym połączeniem internetowym.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa serwera, z którymi działa ten obiekt połączenia.

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a>CInternetConnection::GetSession

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wskaźnik do `CInternetSession` obiektu, który jest skojarzony z tym połączeniem.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CInternetSession](../../mfc/reference/cinternetsession-class.md) skojarzonego z tym obiektem połączenia internetowego.

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetConnection::operator HINTERNET

Ten operator służy do uzyskania uchwytu na poziomie interfejsu API dla bieżącej sesji internetowej.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
