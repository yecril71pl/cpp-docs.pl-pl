---
title: Klasa CFtpFileFind
ms.date: 05/28/2020
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
ms.openlocfilehash: e53e16f738f0436cbd02074c10ca24dbcc9d0fd8
ms.sourcegitcommit: 426e327c9f7c3a3b02300e3f924f9786d62958e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84206235"
---
# <a name="cftpfilefind-class"></a>Klasa CFtpFileFind

Pomoc dla wyszukiwania w pliku internetowym w przypadku serwerów FTP.

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
|[CFtpFileFind:: FindFile —](#findfile)|Znajduje plik na serwerze FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików od poprzedniego wywołania do [FindFile —](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Pobiera adres URL, łącznie z ścieżką, znalezionego pliku.|

## <a name="remarks"></a>Uwagi

`CFtpFileFind`obejmuje funkcje członkowskie, które rozpoczynają wyszukiwanie, odszukają plik i zwracają adres URL lub inne opisowe informacje o pliku.

Inne klasy MFC przeznaczone do przeszukiwania Internetu i plików lokalnych obejmują [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) i [CFileFind](../../mfc/reference/cfilefind-class.md). W połączeniu z programem `CFtpFileFind` te klasy zapewniają bezproblemowy mechanizm do znajdowania określonych plików, niezależnie od protokołu serwera lub typu pliku (komputera lokalnego lub serwera zdalnego). Nie istnieje klasa MFC do wyszukiwania na serwerach HTTP, ponieważ protokół HTTP nie obsługuje bezpośredniego manipulowania plikami wymaganego do wyszukiwania.

Aby uzyskać więcej informacji na temat sposobu użycia `CFtpFileFind` i innych klas WinInet, zobacz artykuł [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Przykład

Poniższy kod ilustruje sposób wyliczania wszystkich plików w bieżącym katalogu serwera FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind

Ta funkcja członkowska jest wywoływana w celu skonstruowania `CFtpFileFind` obiektu.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pConnection*<br/>
Wskaźnik do `CFtpConnection` obiektu. Połączenie FTP można uzyskać, wywołując [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Identyfikator kontekstu dla `CFtpFileFind` obiektu. Aby uzyskać więcej informacji, zobacz następujące **uwagi**.

### <a name="remarks"></a>Uwagi

Wartość domyślna parametru *dwContext* jest wysyłana przez MFC do `CFtpFileFind` obiektu z obiektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) , który utworzył `CFtpFileFind` obiekt. Można zastąpić ustawienie domyślne, aby ustawić identyfikator kontekstu na wybraną wartość. Identyfikator kontekstu jest zwracany do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) w celu udostępnienia stanu obiektu, z którym został zidentyfikowany. Zapoznaj się z artykułem [internetowym pierwsze kroki: WinInet](../../mfc/wininet-basics.md) , aby uzyskać więcej informacji na temat identyfikatora kontekstu.

### <a name="example"></a>Przykład

  Zapoznaj się z przykładem w omówieniu klasy wcześniej w tym temacie.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind:: FindFile —

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć plik FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parametry

*pstrName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do znalezienia. Jeśli wartość jest równa NULL, wywołanie wykona wyszukiwanie przy użyciu symboli wieloznacznych (*).

*flagiDW*<br/>
Flagi opisujące, jak obsłużyć tę sesję. Flagi te można łączyć z operatorem bitowym or (&#124;) i są następujące:

- `INTERNET_FLAG_RELOAD`Pobierz dane z przewodu, nawet jeśli są buforowane lokalnie. Jest to flaga domyślna.

- `INTERNET_FLAG_DONT_CACHE`Nie Buforuj danych lokalnie ani w żadnej bramie.

- `INTERNET_FLAG_RAW_DATA`Zastąp wartość domyślną, aby zwracała dane pierwotne (struktury [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) dla protokołu FTP).

- `INTERNET_FLAG_SECURE`Zabezpiecza transakcje w sieci przy użyciu SSL lub PCT. Ta flaga ma zastosowanie tylko do żądań HTTP.

- `INTERNET_FLAG_EXISTING_CONNECT`Jeśli to możliwe, ponownie Użyj istniejących połączeń z serwerem w celu uzyskania nowych `FindFile` żądań zamiast tworzenia nowej sesji dla każdego żądania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, wywołaj [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)funkcji Win32.

### <a name="remarks"></a>Uwagi

Po wywołaniu programu `FindFile` w celu pobrania pierwszego pliku FTP można wywołać [FindNextFile](#findnextfile) w celu pobrania kolejnych plików FTP.

### <a name="example"></a>Przykład

  Zobacz wcześniejszy przykład w tym temacie.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind::FindNextFile

Wywołaj tę funkcję elementu członkowskiego, aby kontynuować wyszukiwanie plików rozpoczęte za pomocą wywołania funkcji składowej [FindFile —](#findfile) .

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli istnieje więcej plików; zero, jeśli znaleziony plik jest ostatnim z nich w katalogu lub wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, wywołaj [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)funkcji Win32. Jeśli znaleziony plik to ostatni plik w katalogu lub nie można znaleźć pasujących plików, `GetLastError` Funkcja zwraca ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Uwagi

Należy wywołać tę funkcję co najmniej raz przed wywołaniem dowolnej funkcji atrybutów (zobacz [CFileFind:: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`Zawija funkcję Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Przykład

  Zapoznaj się z przykładem znajdującym się wcześniej w tym temacie.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind::GetFileURL

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać adres URL określonego pliku.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Wartość zwracana

Plik i ścieżka lokalizatora zasobów uniwersalnych (URL).

### <a name="remarks"></a>Uwagi

`GetFileURL`jest podobna do funkcji składowej [CFileFind:: GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath) z wyjątkiem tego, że zapewnia ona wynik w formacie adresu URL. Podobnie jak w przypadku `CFileFind::GetFilePath` , wynik nie zawiera nazwy pliku. Na przykład `file1.txt` znajdujący się w `//moose/dir/file1.txt:` zwracaniu `ftp://moose/dir/` .

## <a name="see-also"></a>Zobacz także

[Klasa CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
