---
title: Klasa CInternetConnection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
dev_langs:
- C++
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 227637dc042777725692122babe0d4c7b232d578
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037781"
---
# <a name="cinternetconnection-class"></a>Klasa CInternetConnection
Zarządzanie połączeniem internetowym serwerze.  
  
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
|[CInternetConnection::GetServerName](#getservername)|Pobiera nazwę serwera, skojarzone z połączeniem.|  
|[CInternetConnection::GetSession](#getsession)|Pobiera wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiekt skojarzony z tym połączeniem.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Dojście do sesji Internetu.|  
  
## <a name="remarks"></a>Uwagi  
 Jest klasą podstawową dla klas MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md), i [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Każda z tych klas udostępnia dodatkowe funkcje do komunikowania się z odpowiedniego serwera FTP, HTTP lub gopher.  
  
 Aby komunikować się bezpośrednio z serwera internetowego, musisz mieć [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu i `CInternetConnection` obiektu.  
  
 Aby dowiedzieć się więcej o jak WinInet klasy pracy, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection  
 Ta funkcja członkowska jest wywoływane, gdy `CInternetConnection` tworzony jest obiekt.  
  
```  
CInternetConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 *pSession*  
 Wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.  
  
 *pstrServer*  
 Wskaźnik do ciąg zawierający nazwę serwera.  
  
 *nPort*  
 Liczba, która identyfikuje portu internetowego dla tego połączenia.  
  
 *dwContext*  
 Identyfikator kontekstu `CInternetConnection` obiektu. Zobacz **uwagi** uzyskać więcej informacji o *dwContext*.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie należy wywołać `CInternetConnection` ; zamiast tego wywołać [CInternetSession](../../mfc/reference/cinternetsession-class.md) funkcji członkowskiej typu chcesz ustanowić połączenie:  
  
- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)  
  
- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)  
  
- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)  
  
 Wartość domyślna dla *dwContext* są wysyłane przez MFC do `CInternetConnection`-pochodnych obiektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt **InternetConnection**- Obiekt pochodnych. Wartość domyślna jest ustawiona na 1; jednak można jawnie przypisać identyfikatora kontekstu określonych w [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) konstruktora dla połączenia. Obiekt i pracę go nie będą skojarzone z tym identyfikatorem kontekstu. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którym zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="getcontext"></a>  CInternetConnection::GetContext  
 Wywołanie tej funkcji członkowskich można uzyskać Identyfikatora kontekstu dla tej sesji.  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator kontekstu przypisane aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 W pierwotnie został określony identyfikator kontekstu [CInternetSession](../../mfc/reference/cinternetsession-class.md) i propaguje do `CInternetConnection`- i [CInternetFile](../../mfc/reference/cinternetfile-class.md)-pochodzi z klasy, chyba że określono inaczej w wywołaniu funkcji, który zostanie otwarty połączenie. Identyfikator kontekstu jest skojarzony z żadnej operacji danego obiektu i identyfikuje operacji informacje o stanie zwracanych przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).  
  
 Aby uzyskać więcej informacji o tym, jak `GetContext` współpracuje z innymi Wininet — klasy zapewniające informacje o stanie użytkownika, zobacz artykuł [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="getservername"></a>  CInternetConnection::GetServerName  
 Wywołanie tej funkcji członkowskich można odczytać nazwy serwera skojarzonego z tym połączeniem z Internetem.  
  
```  
CString GetServerName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa serwera, w którym pracuje ten obiekt połączenia.  
  
##  <a name="getsession"></a>  CInternetConnection::GetSession  
 Wywołanie tej funkcji Członkowskich otrzymywać wskaźnik do `CInternetSession` obiektu, który został skojarzony z tym połączeniem.  
  
```  
CInternetSession* GetSession() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiekt skojarzony z tym obiektem połączenia internetowego.  
  
##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET  
 Użyj tego operatora, można pobrać uchwytu poziom interfejsu API dla bieżącej sesji Internet.  
  
```  
operator HINTERNET() const;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



