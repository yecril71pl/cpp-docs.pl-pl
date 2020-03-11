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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890795"
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

Protokół HTTP to jeden z trzech protokołów serwera internetowego implementowanych przez klasy MFC WinInet.

Klasa `CHttpConnection` zawiera Konstruktor i jedna funkcja członkowska [OpenRequest](#openrequest), która zarządza połączeniami z serwerem przy użyciu protokołu HTTP.

Aby komunikować się z serwerem HTTP, należy najpierw utworzyć wystąpienie elementu [CInternetSession](../../mfc/reference/cinternetsession-class.md), a następnie utworzyć obiekt [CHttpConnection](#chttpconnection) . Nie utworzysz bezpośrednio obiektu `CHttpConnection`. Zamiast tego należy wywołać [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), który tworzy obiekt `CHttpConnection` i zwraca do niego wskaźnik.

Aby dowiedzieć się więcej o tym, jak `CHttpConnection` współpracuje z innymi klasami internetowymi MFC, zobacz artykuł [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md). Aby uzyskać więcej informacji na temat łączenia się z serwerami przy użyciu dwóch innych obsługiwanych protokołów internetowych, Gopher i FTP, zobacz klasy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) i [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

##  <a name="chttpconnection"></a>CHttpConnection::CHttpConnection

Ta funkcja członkowska jest wywoływana w celu skonstruowania obiektu `CHttpConnection`.

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
Wskaźnik do obiektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) .

*hConnected*<br/>
Dojście do połączenia internetowego.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*dwContext*<br/>
Identyfikator kontekstu dla obiektu `CInternetConnection`. Aby uzyskać więcej informacji na temat *dwContext*, zobacz sekcję **uwagi** .

*nPort*<br/>
Numer identyfikujący port internetowy dla tego połączenia.

*pstrUserName*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę użytkownika do zalogowania. Jeśli wartość jest równa NULL, wartość domyślna to anonimowe.

*pstrPassword*<br/>
Wskaźnik do ciągu zakończonego wartością null, który określa hasło, które ma być używane do logowania. Jeśli zarówno *pstrPassword* , jak i *pstrUserName* mają wartość null, domyślnym hasłem anonimowym jest nazwa e-mail użytkownika. Jeśli *pstrPassword* ma wartość null lub jest pustym ciągiem, ale *pstrUserName* nie ma wartości null, używane jest puste hasło. W poniższej tabeli opisano zachowanie czterech możliwych ustawień *pstrUserName* i *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nazwa użytkownika wysłana do serwera FTP|Hasło wysyłane do serwera FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL lub ""|NULL lub ""|anonimowe|Nazwa e-mail użytkownika|
|Ciąg o wartości innej niż NULL|NULL lub ""|*pstrUserName*|" "|
|NULL |Ciąg o wartości innej niż NULL|BŁĄD|BŁĄD|
|Ciąg o wartości innej niż NULL|Ciąg o wartości innej niż NULL|*pstrUserName*|*pstrPassword*|

*flagiDW*<br/>
Dowolna kombinacja `INTERNET_FLAG_*` flags. Zapoznaj się z tabelą w sekcji **spostrzeżenia** elementu [CHttpConnection:: OpenRequest](#openrequest) , aby uzyskać opis wartości *flagiDW* .

### <a name="remarks"></a>Uwagi

Nie utworzysz jeszcze `CHttpConnection` bezpośrednio. Zamiast tego należy utworzyć obiekt przez wywołanie [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

##  <a name="openrequest"></a>CHttpConnection::OpenRequest

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
Wskaźnik do ciągu zawierającego czasownik do użycia w żądaniu. Jeśli wartość jest równa NULL, używany jest "GET".

*pstrObjectName*<br/>
Wskaźnik do ciągu zawierającego obiekt docelowy określonego zlecenia. Ten ciąg jest zwykle nazwą pliku, modułem wykonywalnym lub specyfikatorem wyszukiwania.

*pstrReferer*<br/>
Wskaźnik do ciągu, który określa adres (URL) dokumentu, z którego uzyskano adres URL w żądaniu (*pstrObjectName*). Jeśli wartość jest równa NULL, nie określono nagłówka HTTP.

*dwContext*<br/>
Identyfikator kontekstu dla operacji `OpenRequest`. Aby uzyskać więcej informacji na temat *dwContext*, zobacz sekcję Uwagi.

*ppstrAcceptTypes*<br/>
Wskaźnik do tablicy zakończonych znakiem null wskaźników LPCTSTR do ciągów wskazujących typy zawartości akceptowane przez klienta. Jeśli *ppstrAcceptTypes* ma wartość null, serwery interpretują, że klient akceptuje tylko dokumenty typu "text/*" (oznacza to, że tylko dokumenty tekstowe i obrazy lub inne pliki binarne). Typ zawartości jest równoważny zmiennej CGI CONTENT_TYPE, która identyfikuje typ danych dla zapytań, które mają dołączone informacje, takie jak HTTP POST i PUT.

*pstrVersion*<br/>
Wskaźnik do ciągu definiującego wersję protokołu HTTP. W przypadku wartości NULL jest używany protokół "HTTP/1.0".

*flagiDW*<br/>
Dowolna kombinacja INTERNET_ FLAG_ * flags. Zobacz sekcję Uwagi, aby uzyskać opis możliwych wartości *flagiDW* .

*nVerb*<br/>
Liczba skojarzona z typem żądania HTTP. Może to być jeden z następujących modyfikatorów dostępu:

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

Zażądano wskaźnika do obiektu [CHttpFile](../../mfc/reference/chttpfile-class.md) .

### <a name="remarks"></a>Uwagi

*flagiDW* może być jedną z następujących:

|Flaga Internetu|Opis|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Wymusza pobranie żądanego pliku, obiektu lub listy katalogów z serwera pochodzenia, a nie z pamięci podręcznej.|
|INTERNET_FLAG_DONT_CACHE|Nie dodaje zwróconej jednostki do pamięci podręcznej.|
|INTERNET_FLAG_MAKE_PERSISTENT|Dodaje zwróconą jednostkę do pamięci podręcznej jako jednostkę trwałą. Oznacza to, że standardowe czyszczenie pamięci podręcznej, sprawdzanie spójności lub odzyskiwanie pamięci nie może usunąć tego elementu z pamięci podręcznej.|
|INTERNET_FLAG_SECURE|Używa semantyki transakcji zabezpieczonej. Jest ona tłumaczona na użycie protokołu SSL/PCT i ma znaczenie tylko w żądaniach HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Używane tylko z protokołem HTTP, określa, że przekierowania nie należy obsługiwać automatycznie w [CHttpFile:: SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Zastąp domyślne `dwContext`, aby ustawić identyfikator kontekstu na wybraną wartość. Identyfikator kontekstu jest skojarzony z tą konkretną operacją obiektu `CHttpConnection` utworzonego przez obiekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Wartość jest zwracana do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu operacji, z którą została zidentyfikowana. Zapoznaj się z artykułem [internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

Wyjątki mogą być zgłaszane z tą funkcją.

## <a name="see-also"></a>Zobacz także

[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
