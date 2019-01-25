---
title: CGopherFileFind Class
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: dafa313d9d2c7aae13e83a891c79d437ac276e08
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894500"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind Class

Pomoc Internetowych plikach wyszukiwania serwerów gopher.

> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` i ich elementów członkowskich są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą one nadal działały na starszych platformach.

## <a name="syntax"></a>Składnia

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Konstruuje `CGopherFileFind` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Umożliwia znalezienie pliku na serwerze gophera.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików z poprzedniego wywołania [FindFile](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Pobiera godzinę utworzenia określonego pliku.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Pobiera czas, w których nastąpił ostatni dostęp do określonego pliku.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Pobiera czas do ostatniego zapisania określonego pliku.|
|[CGopherFileFind::GetLength](#getlength)|Pobiera długość znaleziony plik, w bajtach.|
|[CGopherFileFind::GetLocator](#getlocator)|Pobierz `CGopherLocator` obiektu.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Pobiera nazwę ekranu gopher.|
|[CGopherFileFind::IsDots](#isdots)|Testuje pod kątem bieżącego katalogu i element nadrzędny znaczników katalogu podczas iteracji w plikach.|

## <a name="remarks"></a>Uwagi

`CGopherFileFind` obejmuje funkcje Członkowskie, które rozpocząć wyszukiwanie, zlokalizuj plik i zwraca adres URL pliku.

Inne klasy MFC, przeznaczony dla Internetu i plik lokalny przeszukiwane [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) i [CFileFind](../../mfc/reference/cfilefind-class.md). Wraz z `CGopherFileFind`, te klasy oferują bezproblemowe mechanizm dla użytkownika znaleźć określone pliki, niezależnie od protokołu serwera, typu pliku i lokalizację (komputer lokalny lub zdalny serwer.) Zwróć uwagę, że żadna z klas MFC do wyszukiwania na serwerach HTTP, ponieważ HTTP nie obsługuje manipulowania bezpośrednie pliku wymaganego przez wyszukiwanie.

> [!NOTE]
> `CGopherFileFind` nie obsługuje następujących funkcji składowej klasy bazowej [CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Ponadto, gdy jest używane z `CGopherFileFind`, `CFileFind` funkcja elementu członkowskiego [IsDots](../../mfc/reference/cfilefind-class.md#isdots) ma zawsze wartość FALSE.

Aby uzyskać więcej informacji o sposobie używania `CGopherFileFind` i innych klasach WinInet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind

Ta funkcja członkowska jest wywoływana, aby skonstruować `CGopherFileFind` obiektu.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pConnection*<br/>
Wskaźnik do [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) obiektu.

*dwContext*<br/>
Identyfikator kontekstu dla tej operacji. Zobacz **uwagi** Aby uzyskać więcej informacji na temat *dwContext*.

### <a name="remarks"></a>Uwagi

Wartością domyślną dla *dwContext* są wysyłane przez MFC, aby `CGopherFileFind` obiektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CGopherFileFind` obiektu. Podczas konstruowania `CGopherFileFind` obiektu, można zastąpić domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którą jest identyfikowany. Zapoznaj się z artykułem [Internet pierwsze kroki: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.

##  <a name="findfile"></a>  CGopherFileFind::FindFile

Wywołaj tę funkcję elementu członkowskiego, aby znaleźć plik gopher.

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odwołanie do [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.

*pstrString*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku.

*dwFlags*<br/>
Flagi opisujące sposób obsługi tej sesji. Prawidłowe flagi są:

- INTERNET_FLAG_RELOAD uzyskać danych z serwera zdalnego, nawet jeśli jest ona buforowana lokalnie.

- INTERNET_FLAG_DONT_CACHE nie buforują dane, lokalnie lub w żadnych bram.

- Żądanie INTERNET_FLAG_SECURE zabezpieczone transakcje w sieci za pomocą Secure Sockets Layer lub procent Ta flaga ma zastosowanie tylko żądania HTTP.

- INTERNET_FLAG_USE_EXISTING, jeśli jest to możliwe, ponowne używanie istniejących połączeń z serwerem dla nowych `FindFile` żądania, zamiast tworzenia nowej sesji dla każdego żądania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Uwagi

Po wywołaniu `FindFile` można pobrać pierwszy obiekt gopher, można wywołać [FindNextFile](#findnextfile) do pobierania plików kolejnych gopher.

##  <a name="findnextfile"></a>  CGopherFileFind::FindNextFile

Wywołaj tę funkcję elementu członkowskiego, aby kontynuować wyszukiwanie plików, uruchomione przy użyciu wywołania do [CGopherFileFind::FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli istnieje więcej plików; zero, jeśli znaleziono pliku jest ostatni z nich w katalogu lub jeśli wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360). Jeśli znaleziono pliku ostatniego pliku w katalogu lub jeśli nie pasujących plików można znaleźć `GetLastError` :: gettotalsize() zwróciło ERROR_NO_MORE_FILES.

##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime

Pobiera czasu utworzenia dla bieżącego pliku.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Wskaźnik do [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury zawierającej czas utworzenia pliku.

*refTime*<br/>
Odwołanie do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; 0 w przypadku niepowodzenia. `GetCreationTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CGopherFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetCreationTime`.

> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki w celu zaimplementowania sygnaturę czasową, zwrócona przez tę funkcję. Ta funkcja może zwrócić tę samą wartość zwracana przez inne funkcje sygnatury czasu, jeśli bazowego systemu plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury, aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacyjnych zwracana godzina jest w czasie lokalnej strefy do maszyny były znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) interfejsu API, aby uzyskać więcej informacji.

##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime

Pobiera czas, w których nastąpił ostatni dostęp do określonego pliku.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parametry

*refTime*<br/>
Odwołanie do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu.

*pTimeStamp*<br/>
Wskaźnik do [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury zawierającej czas ostatniego dostępu do pliku.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; 0 w przypadku niepowodzenia. `GetLastAccessTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CGopherFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastAccessTime`.

> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki w celu zaimplementowania sygnaturę czasową, zwrócona przez tę funkcję. Ta funkcja może zwrócić tę samą wartość zwracana przez inne funkcje sygnatury czasu, jeśli bazowego systemu plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury, aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacyjnych zwracana godzina jest w czasie lokalnej strefy do maszyny były znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) interfejsu API, aby uzyskać więcej informacji.

##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime

Pobiera podczas ostatniego plik został zmieniony.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Wskaźnik do [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury zawierającej czas do ostatniego zapisania pliku.

*refTime*<br/>
Odwołanie do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; 0 w przypadku niepowodzenia. `GetLastWriteTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CGopherFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastWriteTime`.

> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki w celu zaimplementowania sygnaturę czasową, zwrócona przez tę funkcję. Ta funkcja może zwrócić tę samą wartość zwracana przez inne funkcje sygnatury czasu, jeśli bazowego systemu plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury, aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacyjnych zwracana godzina jest w czasie lokalnej strefy do maszyny były znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) interfejsu API, aby uzyskać więcej informacji.

##  <a name="getlength"></a>  CGopherFileFind::GetLength

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać długość w bajtach, znaleziony plik.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość, w bajtach, znaleziony plik.

### <a name="remarks"></a>Uwagi

`GetLength` używa struktury Win32 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) można uzyskać wartość rozmiaru pliku w bajtach.

> [!NOTE]
>  Począwszy od MFC 7.0 `GetLength` obsługuje typy 64-bitową liczbę całkowitą. Wcześniej istniejący kod utworzonych za pomocą tego nowszą wersję biblioteki może spowodować ostrzeżenia obcięcie.

### <a name="example"></a>Przykład

  Zobacz przykład [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (implementacji klasy podstawowej).

##  <a name="getlocator"></a>  CGopherFileFind::GetLocator

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiekt [FindFile](#findfile) używa do znajdowania pliku gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Element `CGopherLocator` obiektu.

##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę ekranu gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa na ekranie gopher.

##  <a name="isdots"></a>  CGopherFileFind::IsDots

Testuje pod kątem bieżącego katalogu i element nadrzędny znaczników katalogu podczas iteracji w plikach.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli znaleziono plik o nazwie "."lub"..", co oznacza, że znaleziony plik jest w rzeczywistości katalogiem. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsDots`.

## <a name="see-also"></a>Zobacz też

[Klasa CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)<br/>
[Klasa CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
