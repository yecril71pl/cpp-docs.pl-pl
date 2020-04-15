---
title: Klasa CHttpConnection
ms.date: 03/27/2019
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: af402b532b3aba28bdfefea5afa67331765db4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351818"
---
# <a name="chttpconnection-class"></a>Klasa CHttpConnection

Zarządza połączeniem z serwerem HTTP.

## <a name="syntax"></a>Składnia

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHttpConnection::CHttpConnection](#chttpconnection)|Tworzy obiekt `CHttpConnection`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|Otwiera żądanie HTTP.|

## <a name="remarks"></a>Uwagi

HTTP jest jednym z trzech protokołów serwera internetowego zaimplementowanych przez klasy MFC WinInet.

Klasa `CHttpConnection` zawiera konstruktora i jedną funkcję elementu [członkowskiego, OpenRequest](#openrequest), która zarządza połączeniami z serwerem z protokołem HTTP.

Aby komunikować się z serwerem HTTP, należy najpierw utworzyć [wystąpienie CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie utworzyć obiekt [CHttpConnection.](#chttpconnection) Nigdy nie `CHttpConnection` tworzysz obiektu bezpośrednio; zamiast, wywołać [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection) `CHttpConnection` , który tworzy obiekt i zwraca wskaźnik do niego.

Aby dowiedzieć `CHttpConnection` się więcej o tym, jak działa z innymi klasami MFC Internet, zobacz artykuł [Programowanie internetowe z WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji na temat łączenia się z serwerami przy użyciu dwóch pozostałych obsługiwanych protokołów internetowych, gopher i FTP, zobacz klasy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) i [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Połączenie międzysystemowe CInternet](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>CHttpConnection::CHttpConnection

Ta funkcja elementu członkowskiego `CHttpConnection` jest wywoływana do konstruowania obiektu.

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

*pSesja*<br/>
Wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.

*hPołączone*<br/>
Dojście do połączenia internetowego.

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*Dwcontext*<br/>
Identyfikator kontekstu `CInternetConnection` obiektu. Aby uzyskać więcej informacji na temat *dwContext*, zobacz **uwagi** sekcji.

*Nport*<br/>
Numer identyfikujący port internetowy dla tego połączenia.

*pstrUserName*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa nazwę użytkownika do logowania. Jeśli null, wartość domyślna jest anonimowa.

*pstr Hasło*<br/>
Wskaźnik do ciągu zakończonego wartością null, który określa hasło używane do logowania. Jeśli zarówno *pstrPassword,* jak i *pstrUserName* mają wartość NULL, domyślnym anonimowym hasłem jest nazwa e-mail użytkownika. Jeśli *pstrPassword* ma wartość NULL lub pusty ciąg, ale *pstrUserName* nie ma wartości NULL, używane jest puste hasło. W poniższej tabeli opisano zachowanie czterech możliwych ustawień *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstr Hasło*|Nazwa użytkownika wysłana do serwera FTP|Hasło wysłane do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL lub " " "|NULL lub " " "|"anonimowy"|Nazwa e-mail użytkownika|
|Ciąg nienawiązany|NULL lub " " "|*pstrUserName*|" "|
|NULL |Ciąg nienawiązany|BŁĄD|BŁĄD|
|Ciąg nienawiązany|Ciąg nienawiązany|*pstrUserName*|*pstr Hasło*|

*Dwflags*<br/>
Dowolna `INTERNET_FLAG_*` kombinacja flag. Zobacz tabelę w sekcji **Uwagi** [CHttpConnection::OpenRequest](#openrequest) opis wartości *dwFlags.*

### <a name="remarks"></a>Uwagi

Nigdy nie `CHttpConnection` tworzysz bezpośrednio. Zamiast tego można utworzyć obiekt, wywołując [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a>CHttpConnection::OpenRequest

Wywołanie tej funkcji członkowskiej, aby otworzyć połączenie HTTP.

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

*pstrVerb (wład.*<br/>
Wskaźnik do ciągu zawierającego zlecenie do użycia w żądaniu. Jeśli używana jest wartość NULL, używana jest wartość "GET".

*pstrObjectName (nazwa pstrObjectName)*<br/>
Wskaźnik do ciągu zawierającego obiekt docelowy określonego zlecenia. Ten ciąg jest zazwyczaj nazwa pliku, moduł wykonywalny lub specyfikator wyszukiwania.

*pstrReferer ( pstrReferer )*<br/>
Wskaźnik do ciągu, który określa adres (URL) dokumentu, z którego uzyskano adres URL w żądaniu (*pstrObjectName*). Jeśli null, nie określono nagłówka HTTP.

*Dwcontext*<br/>
Identyfikator kontekstu `OpenRequest` dla operacji. Aby uzyskać więcej informacji na temat *dwContext*, zobacz uwagi sekcji.

*ppstrAcceptTypes (Typy odpowiedzi na osekła)*<br/>
Wskaźnik do tablicy zakończonej wartością null wskaźników LPCTSTR do ciągów wskazujących typy zawartości zaakceptowane przez klienta. Jeśli *ppstrAcceptTypes* ma wartość NULL, serwery interpretują, że klient akceptuje tylko dokumenty typu "text/*" (czyli tylko dokumenty tekstowe, a nie obrazy lub inne pliki binarne). Typ zawartości jest odpowiednikiem zmiennej CGI CONTENT_TYPE, która identyfikuje typ danych dla kwerend, które mają dołączone informacje, takie jak HTTP POST i PUT.

*pstrVersion (wersja pstrVersion)*<br/>
Wskaźnik do ciągu definiującego wersję HTTP. Jeśli null, "HTTP/1.0" jest używany.

*Dwflags*<br/>
Dowolna kombinacja flag INTERNET_ FLAG_*. Zobacz uwagi sekcji opis możliwych *dwFlags* wartości.

*nWerb*<br/>
Numer skojarzony z typem żądania HTTP. Może być jedną z następujących czynności:

|Typ żądania HTTP|*Wartość nVerb*|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Wartość zwracana

Żądany wskaźnik do żądanego obiektu [CHttpFile.](../../mfc/reference/chttpfile-class.md)

### <a name="remarks"></a>Uwagi

*dwFlags* może być jedną z następujących czynności:

|Flaga internetowa|Opis|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Wymusza pobieranie żądanego pliku, obiektu lub listy katalogów z serwera pochodzenia, a nie z pamięci podręcznej.|
|INTERNET_FLAG_DONT_CACHE|Nie dodaje zwróconej jednostki do pamięci podręcznej.|
|INTERNET_FLAG_MAKE_PERSISTENT|Dodaje zwróconą encję do pamięci podręcznej jako jednostkę trwałą. Oznacza to, że standardowe oczyszczanie pamięci podręcznej, sprawdzanie spójności lub wyrzucanie elementów bezużytecznych nie można usunąć tego elementu z pamięci podręcznej.|
|INTERNET_FLAG_SECURE|Używa semantyki bezpiecznych transakcji. Przekłada się na używanie protokołu SSL/PCT i ma znaczenie tylko w żądaniach HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Używane tylko z protokołem HTTP, określa, że przekierowania nie powinny być obsługiwane automatycznie w [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Zastąd `dwContext` w polu domyślnym należy ustawić identyfikator kontekstu na wartość według wyboru. Identyfikator kontekstu jest skojarzony z tą `CHttpConnection` określoną operacją obiektu utworzonego przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Wartość jest zwracana do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan operacji, z którą jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

Z tą funkcją mogą być generowane wyjątki.

## <a name="see-also"></a>Zobacz też

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
