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
ms.openlocfilehash: 9f17c3ade53ec45ddde654e83c77fe1d817d8495
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275353"
---
# <a name="cinternetconnection-class"></a>Klasa CInternetConnection

Zarządza połączeniem z serwerem Internet.

## <a name="syntax"></a>Składnia

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Konstruuje `CInternetConnection` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|Pobiera identyfikator kontekstu dla tego obiektu połączenia.|
|[CInternetConnection::GetServerName](#getservername)|Pobiera nazwę serwera skojarzonych z tym połączeniem.|
|[CInternetConnection::GetSession](#getsession)|Pobiera wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiekt skojarzony z tym połączeniem.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Dojście do sesji Internetu.|

## <a name="remarks"></a>Uwagi

Jest to klasa podstawowa dla klas MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md), i [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Każda z tych klas udostępnia dodatkowe funkcje do komunikowania się z odpowiednim serwerem FTP, HTTP lub gopher.

Aby komunikować się bezpośrednio z serwerem internetowym, konieczne jest posiadanie [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu i `CInternetConnection` obiektu.

Aby dowiedzieć się więcej na temat sposobu działania klas WinInet, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection

Ta funkcja członkowska jest wywoływana, gdy `CInternetConnection` obiekt zostanie utworzony.

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pSession*<br/>
Wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*nPort*<br/>
Numer identyfikacyjny portu internetowego dla tego połączenia.

*dwContext*<br/>
Identyfikator kontekstu `CInternetConnection` obiektu. Zobacz **uwagi** Aby uzyskać więcej informacji na temat *dwContext*.

### <a name="remarks"></a>Uwagi

Nigdy nie wywołują metody `CInternetConnection` samodzielnie; zamiast tego należy wywołać [CInternetSession](../../mfc/reference/cinternetsession-class.md) funkcji składowej typu chcesz nawiązać połączenie:

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

Wartością domyślną dla *dwContext* są wysyłane przez MFC, aby `CInternetConnection`-pochodzi obiekt z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt **InternetConnection**- Obiekt pochodnych. Wartość domyślna jest ustawiona na 1; Jednakże można jawnie przypisać identyfikator określonego kontekstu, w [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) konstruktora dla połączenia. Obiekt i wszelkie prace, które wykonuje zostanie skojarzona z tym identyfikatorem kontekstu. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którą jest identyfikowany. Zapoznaj się z artykułem [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.

##  <a name="getcontext"></a>  CInternetConnection::GetContext

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać identyfikator kontekstu dla tej sesji.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator kontekstu przypisanych aplikacji.

### <a name="remarks"></a>Uwagi

W pierwotnie określono identyfikator kontekstu [CInternetSession](../../mfc/reference/cinternetsession-class.md) i propaguje do `CInternetConnection`— i [CInternetFile](../../mfc/reference/cinternetfile-class.md)-pochodnych klas, chyba że określono inaczej w wywołaniu funkcji, która zostanie otwarta połączenie. Identyfikator kontekstu jest skojarzony z wszelkich operacji danego obiektu i identyfikuje informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

Aby uzyskać więcej informacji o tym, jak `GetContext` współpracuje z innych klas WinInet, aby zapewnić informacje o stanie użytkownika, zapoznaj się z artykułem [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.

##  <a name="getservername"></a>  CInternetConnection::GetServerName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę serwera, skojarzony z tym połączeniem z Internetem.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa serwera, w którym działa ten obiekt połączenia.

##  <a name="getsession"></a>  CInternetConnection::GetSession

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do `CInternetSession` obiekt, który jest skojarzony z tym połączeniem.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiekt skojarzony z tym obiektem połączenia internetowego.

##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET

Można pobrać uchwytu poziom interfejsu API dla bieżącej sesji Internet, należy użyć tego operatora.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
