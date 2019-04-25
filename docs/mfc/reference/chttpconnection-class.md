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
ms.openlocfilehash: 1941af1e16a897235dd90db509d6ed29c2d9a875
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237573"
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
|[CHttpConnection::CHttpConnection](#chttpconnection)|Tworzy `CHttpConnection` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|Otwiera żądanie HTTP.|

## <a name="remarks"></a>Uwagi

HTTP jest jednym z trzech protokołów serwera internetowego zaimplementowanych przez klasy MFC WinInet.

Klasa `CHttpConnection` zawiera konstruktora, a funkcja jednego członka [OpenRequest](#openrequest), który zarządza połączenia z serwerem przy użyciu protokołu HTTP.

Aby komunikować się z serwerem HTTP, należy najpierw utworzyć wystąpienie [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie utwórz [CHttpConnection](#chttpconnection) obiektu. Nigdy nie twórz `CHttpConnection` obiektu bezpośrednio, zamiast zaproszenia [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), co powoduje utworzenie `CHttpConnection` obiektu i zwraca wskaźnik do niego.

Aby dowiedzieć się więcej o tym, jak `CHttpConnection` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji na temat nawiązywania połączenia z serwerami przy użyciu innych dwa obsługiwanych protokołów internetowych, gopher FTP, zobacz klasy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) i [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

##  <a name="chttpconnection"></a>  CHttpConnection::CHttpConnection

Ta funkcja członkowska jest wywoływana, aby skonstruować `CHttpConnection` obiektu.

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

*pSession*<br/>
Wskaźnik do [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu.

*hConnected*<br/>
Dojście do połączenia internetowego.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*dwContext*<br/>
Identyfikator kontekstu `CInternetConnection` obiektu. Aby uzyskać więcej informacji na temat *dwContext*, zobacz **uwagi** sekcji.

*nPort*<br/>
Numer identyfikacyjny portu internetowego dla tego połączenia.

*pstrUserName*<br/>
Wskaźnik na ciąg zakończony znakiem null, określający nazwę użytkownika do logowania. Jeśli ma wartość NULL, wartość domyślna jest anonimowy.

*pstrPassword*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa hasło używane do logowania. Jeśli oba *pstrPassword* i *pstrUserName* mają wartość NULL, domyślne hasło anonimowe to nazwa adres e-mail użytkownika. Jeśli *pstrPassword* ma wartość NULL lub pusty ciąg, ale *pstrUserName* nie ma wartości NULL, puste hasło jest używane. W poniższej tabeli opisano zachowanie cztery ustawienia możliwe *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nazwa użytkownika jest wysyłane do serwera FTP|Hasła przesyłanych do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Wartość NULL lub ""|Wartość NULL lub ""|"anonimowy"|Nazwa e-mail użytkownika|
|Ciąg znaków innych niż NULL|Wartość NULL lub ""|*pstrUserName*|" "|
|NULL |Ciąg znaków innych niż NULL|BŁĄD|BŁĄD|
|Ciąg znaków innych niż NULL|Ciąg znaków innych niż NULL|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Dowolną kombinację `INTERNET_FLAG_*` flag. Zobacz tabelę w **uwagi** części [CHttpConnection::OpenRequest](#openrequest) opis *Flagidw* wartości.

### <a name="remarks"></a>Uwagi

Nigdy nie twórz `CHttpConnection` bezpośrednio. Zamiast tworzenia obiektu przez wywołanie [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

##  <a name="openrequest"></a>  CHttpConnection::OpenRequest

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć połączenie HTTP.

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

*pstrVerb*<br/>
Wskaźnik do ciągu zawierającego zlecenia do użycia w żądaniu. Jeśli ma wartość NULL, używana jest "GET".

*pstrObjectName*<br/>
Wskaźnik do ciągu zawierającego obiekt docelowy określone zlecenie. Ten ciąg jest zazwyczaj nazwę pliku, module pliku wykonywalnego lub specyfikator wyszukiwania.

*pstrReferer*<br/>
Wskaźnik do ciągu, który określa adres (URL) dokumentu, z którego adres URL w żądaniu (*pstrObjectName*) zostały pobrane. Jeśli ma wartość NULL, jest określona bez nagłówka HTTP.

*dwContext*<br/>
Identyfikator kontekstu `OpenRequest` operacji. Aby uzyskać więcej informacji na temat *dwContext*, zobacz sekcję Uwagi.

*ppstrAcceptTypes*<br/>
Wskaźnik do tablicą zakończoną znakiem null LPCTSTR wskaźnikami do ciągów wskazująca typów zawartości zaakceptowane przez klienta. Jeśli *ppstrAcceptTypes* ma wartość NULL, serwery interpretacji, czy klient akceptuje tylko dokumenty typu "text / *" (oznacza to, tekstu tylko dokumenty i obrazy i inne pliki binarne). Typ zawartości jest równoważne do typ_zawartości zmiennej CGI, który identyfikuje typ danych dla zapytania, które zostały dołączone informacje, takie jak żądania HTTP POST i PUT.

*pstrVersion*<br/>
Wskaźnik do ciągu Definiowanie wersji protokołu HTTP. Jeśli ma wartość NULL, jest używany "HTTP/1.0".

*dwFlags*<br/>
Dowolna kombinacja flag INTERNET_ FLAG_ *. Zobacz sekcję Spostrzeżenia, aby uzyskać opis możliwości *Flagidw* wartości.

*nVerb*<br/>
Liczba skojarzony typ żądania HTTP. Może to być jeden z następujących elementów:

|Typ żądania HTTP|*nVerb* wartość|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CHttpFile](../../mfc/reference/chttpfile-class.md) żądanego obiektu.

### <a name="remarks"></a>Uwagi

*Flagidw* może być jedną z następujących czynności:

|Flaga Internet|Opis|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Serwera podrzędnego wymusza pobrania żądanego pliku, obiekt lub listy zawartości katalogu z serwera pochodzenia, ale nie z pamięci podręcznej.|
|INTERNET_FLAG_DONT_CACHE|Nie można dodać zwróconą jednostkę do pamięci podręcznej.|
|INTERNET_FLAG_MAKE_PERSISTENT|Dodaje zwróconą jednostkę do pamięci podręcznej jako trwałe jednostki. Oznacza to, że czyszczenie pamięci podręcznej standardowe, sprawdzania spójności lub wyrzucania elementów bezużytecznych nie można usunąć tego elementu z pamięci podręcznej.|
|INTERNET_FLAG_SECURE|Używa bezpiecznego semantyki transakcji. Przekłada się przy użyciu protokołu SSL/PCT i tylko ma sensu w żądaniach HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Używany tylko za pośrednictwem protokołu HTTP, określa, że przekierowań nie powinny być obsługiwane automatycznie w [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Zastąp `dwContext` domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest skojarzony z tym działania związane z `CHttpConnection` obiekt utworzony przez jego [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu. Zwracana jest wartość [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) do udostępniania informacji o stanie operacji za pomocą którego jest identyfikowana. Zapoznaj się z artykułem [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.

Za pomocą tej funkcji mogą być zgłaszane wyjątki.

## <a name="see-also"></a>Zobacz także

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
