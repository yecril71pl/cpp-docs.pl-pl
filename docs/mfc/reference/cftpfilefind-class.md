---
title: Klasa CFtpFileFind
ms.date: 11/04/2016
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: cf4afb4a683c2d0cf5f2977107d02ee300a53cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373752"
---
# <a name="cftpfilefind-class"></a>Klasa CFtpFileFind

Pomaga w wyszukiwaniu plików internetowych serwerów FTP.

## <a name="syntax"></a>Składnia

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Konstruuje `CFtpFileFind` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Znajduje plik na serwerze FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików z poprzedniego połączenia do [FindFile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Pobiera adres URL, w tym ścieżkę, znalezionego pliku.|

## <a name="remarks"></a>Uwagi

`CFtpFileFind`zawiera funkcje członkowskie, które rozpoczynają wyszukiwanie, lokalizują plik i zwracają adres URL lub inne opisowe informacje o pliku.

Inne klasy MFC przeznaczone do wyszukiwania w Internecie i lokalnie to [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) i [CFileFind](../../mfc/reference/cfilefind-class.md). Wraz `CFtpFileFind`z programem , klasy te zapewniają bezproblemowy mechanizm znajdowania określonych plików przez klienta, niezależnie od protokołu serwera lub typu pliku (komputera lokalnego lub serwera zdalnego). Należy zauważyć, że nie ma klasy MFC do wyszukiwania na serwerach HTTP, ponieważ protokół HTTP nie obsługuje bezpośredniej manipulacji plikami wymaganych do wyszukiwania.

Aby uzyskać więcej informacji `CFtpFileFind` na temat używania i innych klas WinInet, zobacz artykuł [Programowanie internetowe z wininet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak wyliczyć wszystkie pliki w bieżącym katalogu serwera FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfilefind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind

Ta funkcja elementu członkowskiego `CFtpFileFind` jest wywoływana do konstruowania obiektu.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pZkładanie*<br/>
Wskaźnik do `CFtpConnection` obiektu. Połączenie FTP można uzyskać, wywołując [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*Dwcontext*<br/>
Identyfikator kontekstu `CFtpFileFind` obiektu. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat tego parametru.

### <a name="remarks"></a>Uwagi

Wartość domyślna dla *dwContext* jest wysyłana przez MFC do `CFtpFileFind` obiektu z `CFtpFileFind` [CInternetSession](../../mfc/reference/cinternetsession-class.md) obiektu, który utworzył obiekt. Można zastąpić domyślne, aby ustawić identyfikator kontekstu do wartości wybranej. Identyfikator kontekstu jest zwracany do [CInternetSession::OnStatusCallback,](../../mfc/reference/cinternetsession-class.md#onstatuscallback) aby zapewnić stan obiektu, z którym jest identyfikowany. Zobacz artykuł [Pierwsze kroki internetowe: WinInet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

### <a name="example"></a>Przykład

  Zobacz przykład w omówienie klasy wcześniej w tym temacie.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind::FindFile

Wywołanie tej funkcji elementu członkowskiego, aby znaleźć plik FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parametry

*pstrName (nazwa pstrname)*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do znalezienia. Jeśli null, wywołanie wykona wyszukiwanie symboli wieloznacznych (*).

*Dwflags*<br/>
Flagi opisujące sposób obsługi tej sesji. Flagi te mogą być łączone z operatorem or bitowego (&#124;) i są następujące:

- INTERNET_FLAG_RELOAD Pobierz dane z przewodu, nawet jeśli jest on buforowany lokalnie. Jest to flaga domyślna.

- INTERNET_FLAG_DONT_CACHE Nie buforuj danych lokalnie ani w żadnych bramkach.

- INTERNET_FLAG_RAW_DATA Zastąp domyślnie, aby zwrócić nieprzetworzone dane [(WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktur ftp).

- INTERNET_FLAG_SECURE zabezpiecza transakcje w sieci za pomocą secure sockets layer lub PCT. Ta flaga ma zastosowanie tylko do żądań HTTP.

- INTERNET_FLAG_EXISTING_CONNECT Jeśli to możliwe, ponownie użyć istniejących połączeń `FindFile` z serwerem dla nowych żądań zamiast tworzenia nowej sesji dla każdego żądania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [Win32 GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Uwagi

Po `FindFile` wywołaniu, aby pobrać pierwszy plik FTP, można wywołać [FindNextFile,](#findnextfile) aby pobrać kolejne pliki FTP.

### <a name="example"></a>Przykład

  Zobacz wcześniejszy przykład w tym temacie.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind::FindNextFile

Wywołanie tej funkcji elementu członkowskiego, aby kontynuować wyszukiwanie plików rozpoczęte wywołaniem funkcji elementu członkowskiego [FindFile.](#findfile)

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli jest więcej plików; zero, jeśli znaleziony plik jest ostatnim w katalogu lub jeśli wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [Win32 GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Jeśli znaleziony plik jest ostatnim plikiem w katalogu lub jeśli nie `GetLastError` można znaleźć pasujących plików, funkcja zwraca ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Uwagi

Należy wywołać tę funkcję co najmniej raz przed wywołaniem dowolnej funkcji atrybutu (zobacz [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`zawija funkcję Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Przykład

  Zobacz przykład wcześniej w tym temacie.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind::GetFileURL

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać adres URL określonego pliku.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Wartość zwracana

Plik i ścieżka uniwersalnego lokalizatora zasobów (URL).

### <a name="remarks"></a>Uwagi

`GetFileURL`jest podobny do funkcji członkowskiej [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), z `ftp://moose/dir/file.txt`tą różnicą, że zwraca adres URL w formularzu .

## <a name="see-also"></a>Zobacz też

[Klasa CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
