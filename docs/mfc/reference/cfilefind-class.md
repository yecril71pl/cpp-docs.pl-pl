---
title: Klasa CFileFind
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: f01aa84593afed5a4f2f102da7d161ad42917080
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373875"
---
# <a name="cfilefind-class"></a>Klasa CFileFind

Wykonuje lokalne wyszukiwania plików i jest klasą podstawową dla [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) i [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), które wykonują wyszukiwania plików internetowych.

## <a name="syntax"></a>Składnia

```
class CFileFind : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|Konstruuje `CFileFind` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileFind::Zamknij](#close)|Zamyka żądanie wyszukiwania.|
|[CFileFind::FindFile](#findfile)|Przeszukuje katalog w poszukiwaniu określonej nazwy pliku.|
|[CFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików z poprzedniego połączenia do [FindFile](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Pobiera czas plik został utworzony.|
|[CFileFind::GetFileName](#getfilename)|Pobiera nazwę, w tym rozszerzenie, znalezionego pliku|
|[CFileFind::GetFilePath](#getfilepath)|Pobiera całą ścieżkę znalezionego pliku.|
|[CFileFind::GetFileTitle](#getfiletitle)|Pobiera tytuł znalezionego pliku. Tytuł nie zawiera rozszerzenia.|
|[CFileFind::GetFileURL](#getfileurl)|Pobiera adres URL, w tym ścieżkę pliku, znalezionego pliku.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Pobiera czas, który plik był ostatnio dostępny.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Pobiera czas plik został ostatnio zmieniony i zapisany.|
|[CFileFind::GetLength](#getlength)|Pobiera długość znalezionego pliku w bajtach.|
|[CFileFind::GetRoot](#getroot)|Pobiera katalog główny znalezionego pliku.|
|[CFileFind::IsArchived](#isarchived)|Określa, czy znaleziony plik jest archiwizowany.|
|[CFileFind::IsCompressed](#iscompressed)|Określa, czy znaleziony plik jest skompresowany.|
|[CFileFind::IsDirectory](#isdirectory)|Określa, czy znaleziony plik jest katalogiem.|
|[CFileFind::IsDots](#isdots)|Określa, czy nazwa znalezionego pliku ma nazwę "." lub "..", wskazując, że w rzeczywistości jest katalogiem.|
|[CFileFind::IsHidden](#ishidden)|Określa, czy znaleziony plik jest ukryty.|
|[CFileFind::IsNormal](#isnormal)|Określa, czy znaleziony plik jest normalny (innymi słowy, nie ma innych atrybutów).|
|[CFileFind::IsReadOnly](#isreadonly)|Określa, czy znaleziony plik jest tylko do odczytu.|
|[CFileFind::System](#issystem)|Określa, czy znaleziony plik jest plikiem systemowym.|
|[CFileFind::IsTemporary](#istemporary)|Określa, czy znaleziony plik jest tymczasowy.|
|[CFileFind::MatchesMask](#matchesmask)|Wskazuje żądane atrybuty pliku, który ma zostać znaleziony.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CFileFind::ZamknijContext](#closecontext)|Zamyka plik określony przez bieżący uchwyt wyszukiwania.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu.|

## <a name="remarks"></a>Uwagi

`CFileFind`zawiera funkcje członkowskie, które rozpoczynają wyszukiwanie, lokalizują plik i zwracają tytuł, nazwę lub ścieżkę pliku. W przypadku wyszukiwania w Internecie funkcja członkowna [GetFileURL](#getfileurl) zwraca adres URL pliku.

`CFileFind`jest klasą podstawową dla dwóch innych klas MFC przeznaczonych do wyszukiwania określonych typów serwerów: `CGopherFileFind` działa specjalnie z serwerami gopher i `CFtpFileFind` współpracuje specjalnie z serwerami FTP. Razem te trzy klasy zapewniają bezproblemowy mechanizm dla klienta, aby znaleźć pliki, niezależnie od protokołu serwera, typu pliku lub lokalizacji, na komputerze lokalnym lub serwerze zdalnym.

Poniższy kod wyliczy wszystkie pliki w bieżącym katalogu, drukując nazwę każdego pliku:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Aby zachować prosty przykład, ten kod używa `cout` klasy Biblioteka standardowa języka C++. Wiersz `cout` można zastąpić wywołaniem `CListBox::AddString`, na przykład, w programie z graficznym interfejsem użytkownika.

Aby uzyskać więcej informacji `CFileFind` na temat używania i innych klas WinInet, zobacz artykuł [Programowanie internetowe z wininet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cfilefindcfilefind"></a><a name="cfilefind"></a>CFileFind::CFileFind

Ta funkcja elementu członkowskiego `CFileFind` jest wywoływana, gdy obiekt jest konstruowany.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindclose"></a><a name="close"></a>CFileFind::Zamknij

Wywołanie tej funkcji elementu członkowskiego, aby zakończyć wyszukiwanie, zresetować kontekst i zwolnić wszystkie zasoby.

```
void Close();
```

### <a name="remarks"></a>Uwagi

Po `Close`wywołaniu , nie trzeba `CFileFind` utworzyć nowe wystąpienie przed wywołaniem [FindFile,](#findfile) aby rozpocząć nowe wyszukiwanie.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindclosecontext"></a><a name="closecontext"></a>CFileFind::ZamknijContext

Zamyka plik określony przez bieżący uchwyt wyszukiwania.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Uwagi

Zamyka plik określony przez bieżącą wartość dojścia wyszukiwania. Zastąd w tej funkcji należy zmienić zachowanie domyślne.

Aby pobrać prawidłowy uchwyt wyszukiwania, należy wywołać funkcje [FindFile](#findfile) lub [FindNextFile](#findnextfile) co najmniej raz. `FindFile` Funkcje `FindNextFile` i funkcje używają uchwytu wyszukiwania do lokalizowania plików o nazwach pasuszych do danej nazwy.

## <a name="cfilefindfindfile"></a><a name="findfile"></a>CFileFind::FindFile

Wywołanie tej funkcji elementu członkowskiego, aby otworzyć wyszukiwanie plików.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Parametry

*pstrName (nazwa pstrname)*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku do znalezienia. Jeśli przekażesz wartość NULL `FindFile` dla *pstrName*\*, powoduje wyszukiwanie symboli wieloznacznych (*.).

*dwUnused*<br/>
Zarezerwowane do `FindFile` polimorficznych z klas pochodnych. Musi być 0.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [Win32 GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Uwagi

Po `FindFile` wywołaniu, aby rozpocząć wyszukiwanie plików, zadzwoń [FindNextFile,](#findnextfile) aby pobrać kolejne pliki. Należy wywołać `FindNextFile` co najmniej raz przed wywołaniem dowolnej z następujących funkcji elementów członkowskich atrybutu:

- [Czas tworzenia](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle (GetFileTitle)](#getfiletitle)

- [Ścieżka GetFilePath](#getfilepath)

- [Plik GetFileURL](#getfileurl)

- [Czas GetLastAccess](#getlastaccesstime)

- [GetLastWriteTime (Czas Pracy)](#getlastwritetime)

- [Getlength](#getlength)

- [Getroot](#getroot)

- [IsArchived (JestArchiwąsek](#isarchived)

- [IsCompressed (IsCompressed)](#iscompressed)

- [IsDirectory (IsDirectory)](#isdirectory)

- [IsDots (IsDots)](#isdots)

- [Ishidden ( Ishidden )](#ishidden)

- [IsNormal (IsNormal)](#isnormal)

- [IsReadOnly](#isreadonly)

- [System IsSystem](#issystem)

- [Istemporary](#istemporary)

- [Maska dopasowuje](#matchesmask)

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindfindnextfile"></a><a name="findnextfile"></a>CFileFind::FindNextFile

Wywołanie tej funkcji członkowskiej, aby kontynuować wyszukiwanie plików z poprzedniego wywołania [findfile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli jest więcej plików; zero, jeśli znaleziony plik jest ostatnim w katalogu lub jeśli wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [Win32 GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Jeśli znaleziony plik jest ostatnim plikiem w katalogu lub jeśli nie `GetLastError` można znaleźć pasujących plików, funkcja zwraca ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Uwagi

Należy wywołać `FindNextFile` co najmniej raz przed wywołaniem dowolnej z następujących funkcji elementów członkowskich atrybutu:

- [Czas tworzenia](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle (GetFileTitle)](#getfiletitle)

- [Ścieżka GetFilePath](#getfilepath)

- [Plik GetFileURL](#getfileurl)

- [Czas GetLastAccess](#getlastaccesstime)

- [GetLastWriteTime (Czas Pracy)](#getlastwritetime)

- [Getlength](#getlength)

- [Getroot](#getroot)

- [IsArchived (JestArchiwąsek](#isarchived)

- [IsCompressed (IsCompressed)](#iscompressed)

- [IsDirectory (IsDirectory)](#isdirectory)

- [IsDots (IsDots)](#isdots)

- [Ishidden ( Ishidden )](#ishidden)

- [IsNormal (IsNormal)](#isnormal)

- [IsReadOnly](#isreadonly)

- [System IsSystem](#issystem)

- [Istemporary](#istemporary)

- [Maska dopasowuje](#matchesmask)

`FindNextFile`zawija funkcję Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindgetcreationtime"></a><a name="getcreationtime"></a>CFileFind::GetCreationTime

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać czas określony plik został utworzony.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pStał z czasem*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierającej czas utworzenia pliku.

*refTime (czas ref)*<br/>
Odwołanie do [obiektu CTime.](../../atl-mfc-shared/reference/ctime-class.md)

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0, jeśli się nie powiedzie. `GetCreationTime`zwraca wartość 0 tylko wtedy, [gdy findnextFile](#findnextfile) nigdy nie został wywołany dla tego `CFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetCreationTime`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

> [!NOTE]
> Nie wszystkie systemy plików używają tej samej semantyki do zaimplementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwróconą przez inne funkcje sygnatury czasowej, jeśli podstawowy system plików lub serwer nie obsługuje zachowania atrybutu czasu. Zobacz [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury, aby uzyskać informacje o formatach czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej lokalnej do komputera, gdy plik znajduje się. Aby uzyskać więcej informacji, zobacz interfejs API Systemu Plików Systemu Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetfilename"></a><a name="getfilename"></a>CFileFind::GetFileName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę znalezionego pliku.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa ostatnio znalezionego pliku.

### <a name="remarks"></a>Uwagi

Musisz wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem GetFileName.

`GetFileName`jest jedną `CFileFind` z trzech funkcji członkowskich, które zwracają jakąś formę nazwy pliku. Na poniższej liście opisano trzy i ich różnice:

- `GetFileName`zwraca nazwę pliku, łącznie z rozszerzeniem. Na przykład `GetFileName` wywołanie wygenerowania komunikatu użytkownika o pliku *c:\myhtml\myfile.txt* zwraca nazwę pliku *myfile.txt*.

- [GetFilePath](#getfilepath) zwraca całą ścieżkę dla pliku. Na przykład `GetFilePath` wywołanie wygenerowania wiadomości użytkownika o pliku *c:\myhtml\myfile.txt* zwraca ścieżkę pliku *c:\myhtml\myfile.txt*.

- [GetFileTitle](#getfiletitle) zwraca nazwę pliku, z wyłączeniem rozszerzenia pliku. Na przykład `GetFileTitle` wywołanie wygenerowania komunikatu użytkownika o pliku *c:\myhtml\myfile.txt* zwraca tytuł pliku *myfile*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

## <a name="cfilefindgetfilepath"></a><a name="getfilepath"></a>CFileFind::GetFilePath

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać pełną ścieżkę określonego pliku.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka określonego pliku.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetFilePath`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

`GetFilePath`jest jedną `CFileFind` z trzech funkcji członkowskich, które zwracają jakąś formę nazwy pliku. Na poniższej liście opisano trzy i ich różnice:

- [GetFileName](#getfilename) zwraca nazwę pliku, łącznie z rozszerzeniem. Na przykład `GetFileName` wywołanie wygenerowania komunikatu użytkownika o pliku *c:\myhtml\myfile.txt* zwraca nazwę pliku *myfile.txt*.

- `GetFilePath`zwraca całą ścieżkę dla pliku. Na przykład `GetFilePath` wywołanie wygenerowania `c:\myhtml\myfile.txt` komunikatu użytkownika `c:\myhtml\myfile.txt`o pliku zwraca ścieżkę pliku .

- [GetFileTitle](#getfiletitle) zwraca nazwę pliku, z wyłączeniem rozszerzenia pliku. Na przykład `GetFileTitle` wywołanie wygenerowania komunikatu użytkownika o pliku *c:\myhtml\myfile.txt* zwraca tytuł pliku *myfile*.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetfiletitle"></a><a name="getfiletitle"></a>CFileFind::GetFileTitle

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać tytuł znalezionego pliku.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Wartość zwracana

Tytuł pliku.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetFileTitle`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

`GetFileTitle`jest jedną `CFileFind` z trzech funkcji członkowskich, które zwracają jakąś formę nazwy pliku. Na poniższej liście opisano trzy i ich różnice:

- [GetFileName](#getfilename) zwraca nazwę pliku, łącznie z rozszerzeniem. Na przykład `GetFileName` wywołanie wygenerowania komunikatu użytkownika o pliku *c:\myhtml\myfile.txt* zwraca nazwę pliku *myfile.txt*.

- [GetFilePath](#getfilepath) zwraca całą ścieżkę dla pliku. Na przykład `GetFilePath` wywołanie wygenerowania wiadomości użytkownika o pliku *c:\myhtml\myfile.txt* zwraca ścieżkę pliku *c:\myhtml\myfile.txt*.

- `GetFileTitle`zwraca nazwę pliku, z wyłączeniem rozszerzenia pliku. Na przykład `GetFileTitle` wywołanie wygenerowania komunikatu użytkownika o pliku *c:\myhtml\myfile.txt* zwraca tytuł pliku *myfile*.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetfileurl"></a><a name="getfileurl"></a>CFileFind::GetFileURL

Wywołanie tej funkcji elementu członkowskiego, aby pobrać określony adres URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Wartość zwracana

Pełny adres URL.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetFileURL`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

`GetFileURL`jest podobny do funkcji członkowskiej [GetFilePath](#getfilepath), z `file://path`tą różnicą, że zwraca adres URL w formularzu . Na przykład `GetFileURL` wywołanie, aby uzyskać pełny adres URL dla `file://c:\myhtml\myfile.txt` *myfile.txt* zwraca adres URL .

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać czas, który został ostatnio dostępny dla określonego pliku.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parametry

*refTime (czas ref)*<br/>
Odwołanie do [obiektu CTime.](../../atl-mfc-shared/reference/ctime-class.md)

*pStał z czasem*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierającej czas ostatniego dostępu do pliku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0, jeśli się nie powiedzie. `GetLastAccessTime`zwraca wartość 0 tylko wtedy, [gdy findnextFile](#findnextfile) nigdy nie został wywołany dla tego `CFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetLastAccessTime`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

> [!NOTE]
> Nie wszystkie systemy plików używają tej samej semantyki do zaimplementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwróconą przez inne funkcje sygnatury czasowej, jeśli podstawowy system plików lub serwer nie obsługuje zachowania atrybutu czasu. Zobacz [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury, aby uzyskać informacje o formatach czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej lokalnej do komputera, gdy plik znajduje się. Aby uzyskać więcej informacji, zobacz interfejs API Systemu Plików Systemu Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CFileFind::GetLastWriteTime

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać ostatni raz plik został zmieniony.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pStał z czasem*<br/>
Wskaźnik do struktury [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) zawierający czas, w której plik został ostatnio zapisany.

*refTime (czas ref)*<br/>
Odwołanie do [obiektu CTime.](../../atl-mfc-shared/reference/ctime-class.md)

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0, jeśli się nie powiedzie. `GetLastWriteTime`zwraca wartość 0 tylko wtedy, [gdy findnextFile](#findnextfile) nigdy nie został wywołany dla tego `CFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetLastWriteTime`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

> [!NOTE]
> Nie wszystkie systemy plików używają tej samej semantyki do zaimplementowania sygnatury czasowej zwracanej przez tę funkcję. Ta funkcja może zwracać tę samą wartość zwróconą przez inne funkcje sygnatury czasowej, jeśli podstawowy system plików lub serwer nie obsługuje zachowania atrybutu czasu. Zobacz [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury, aby uzyskać informacje o formatach czasu. W niektórych systemach operacyjnych zwracany czas znajduje się w strefie czasowej lokalnej do komputera, gdy plik znajduje się. Aby uzyskać więcej informacji, zobacz interfejs API Systemu Plików Systemu Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetlength"></a><a name="getlength"></a>CFileFind::GetLength

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać długość znalezionego pliku w bajtach.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość znalezionego pliku w bajtach.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetLength`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

`GetLength`używa struktury Win32 [WIN32_FIND_DATA,](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) aby uzyskać i zwrócić wartość rozmiaru pliku w bajtach.

> [!NOTE]
> Od MFC 7.0 `GetLength` obsługuje 64-bitowe typy całkowite. Wcześniej istniejący kod utworzony za pomocą tej nowszej wersji biblioteki może spowodować ostrzeżenia o obcięciem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

## <a name="cfilefindgetroot"></a><a name="getroot"></a>CFileFind::GetRoot

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać katalog główny znalezionego pliku.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Wartość zwracana

Katalog główny aktywnego wyszukiwania.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetRoot`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Ta funkcja elementu członkowskiego zwraca specyfikator dysku i nazwę ścieżki używane do rozpoczęcia wyszukiwania. Na przykład wywołanie [FindFile](#findfile) z `*.dat` wynikami w `GetRoot` zwracaniu pustego ciągu. Przechodzenie ścieżki, `c:\windows\system\*.dll`takie `FindFile` jak `GetRoot` , `c:\windows\system\`do wyników zwracających .

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindisarchived"></a><a name="isarchived"></a>CFileFind::IsArchived

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy znaleziony plik jest zarchiwizowany.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacje oznaczają plik archiwum, którego kopię zapasową ma być archiwizowane lub usuwane, z FILE_ATTRIBUTE_ARCHIVE atrybutem pliku zidentyfikowanym w strukturze [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)

Przed wywołaniem `IsArchived`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Zobacz element członkowski funkcji [MatchesMask,](#matchesmask) aby uzyskać pełną listę atrybutów plików.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindiscompressed"></a><a name="iscompressed"></a>CFileFind::IsCompressed

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy znaleziony plik jest skompresowany.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Skompresowany plik jest oznaczony FILE_ATTRIBUTE_COMPRESSED, atrybutem pliku zidentyfikowanym w strukturze [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) W przypadku pliku ten atrybut wskazuje, że wszystkie dane w pliku są kompresowane. W przypadku katalogu ten atrybut wskazuje, że kompresja jest wartością domyślną dla nowo utworzonych plików i podkatalogów.

Przed wywołaniem `IsCompressed`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Zobacz element członkowski funkcji [MatchesMask,](#matchesmask) aby uzyskać pełną listę atrybutów plików.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindisdirectory"></a><a name="isdirectory"></a>CFileFind::IsDirectory

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy znaleziony plik jest katalogiem.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Plik, który jest katalogiem jest oznaczony FILE_ATTRIBUTE_DIRECTORY atrybut pliku zidentyfikowany w strukturze [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)

Przed wywołaniem `IsDirectory`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Zobacz element członkowski funkcji [MatchesMask,](#matchesmask) aby uzyskać pełną listę atrybutów plików.

### <a name="example"></a>Przykład

Ten mały program powtarza każdy katalog na C:\ i drukuje nazwę katalogu.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

## <a name="cfilefindisdots"></a><a name="isdots"></a>CFileFind::IsDots

Wywołanie tej funkcji elementu członkowskiego, aby przetestować dla bieżącego katalogu i nadrzędnych znaczników katalogu podczas iteracji za pośrednictwem plików.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli znaleziony plik ma nazwę "." lub "..", co oznacza, że znaleziony plik jest w rzeczywistości katalogiem. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `IsDots`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindishidden"></a><a name="ishidden"></a>CFileFind::IsHidden

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy znaleziony plik jest ukryty.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ukryte pliki, oznaczone FILE_ATTRIBUTE_HIDDEN, atrybut pliku zidentyfikowany w [strukturze WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Ukryty plik nie znajduje się w zwykłej liście katalogów.

Przed wywołaniem `IsHidden`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Zobacz element członkowski funkcji [MatchesMask,](#matchesmask) aby uzyskać pełną listę atrybutów plików.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindisnormal"></a><a name="isnormal"></a>CFileFind::IsNormal

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy znaleziony plik jest normalnym plikiem.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pliki oznaczone FILE_ATTRIBUTE_NORMAL, atrybut pliku zidentyfikowany w strukturze [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Normalny plik nie ma innych atrybutów ustawionych. Wszystkie inne atrybuty plików zastępują ten atrybut.

Przed wywołaniem `IsNormal`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Zobacz element członkowski funkcji [MatchesMask,](#matchesmask) aby uzyskać pełną listę atrybutów plików.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindisreadonly"></a><a name="isreadonly"></a>CFileFind::IsReadOnly

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy znaleziony plik jest tylko do odczytu.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Plik tylko do odczytu jest oznaczony FILE_ATTRIBUTE_READONLY, atrybut pliku zidentyfikowany w [strukturze WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Aplikacje mogą odczytać taki plik, ale nie mogą do niego zapisać ani usunąć.

Przed wywołaniem `IsReadOnly`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Zobacz element członkowski funkcji [MatchesMask,](#matchesmask) aby uzyskać pełną listę atrybutów plików.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindissystem"></a><a name="issystem"></a>CFileFind::System

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy znaleziony plik jest plikiem systemowym.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Plik systemowy jest oznaczony FILE_ATTRIBUTE_SYSTEM, atrybut pliku zidentyfikowany w strukturze [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Plik systemowy jest częścią lub jest używany wyłącznie przez system operacyjny.

Przed wywołaniem `IsSystem`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Zobacz element członkowski funkcji [MatchesMask,](#matchesmask) aby uzyskać pełną listę atrybutów plików.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindistemporary"></a><a name="istemporary"></a>CFileFind::IsTemporary

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy znaleziony plik jest plikiem tymczasowym.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Plik tymczasowy jest oznaczony FILE_ATTRIBUTE_TEMPORARY, atrybutem pliku zidentyfikowanym w strukturze [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Plik tymczasowy jest używany do przechowywania tymczasowego. Aplikacje powinny zapisywać do pliku tylko wtedy, gdy jest to absolutnie konieczne. Większość danych pliku pozostaje w pamięci bez opróżnienia na nośnik, ponieważ plik zostanie wkrótce usunięty.

Przed wywołaniem `IsTemporary`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

Zobacz element członkowski funkcji [MatchesMask,](#matchesmask) aby uzyskać pełną listę atrybutów plików.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

## <a name="cfilefindm_ptm"></a><a name="m_ptm"></a>CFileFind::m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

## <a name="cfilefindmatchesmask"></a><a name="matchesmask"></a>CFileFind::MatchesMask

Wywołanie tej funkcji elementu członkowskiego, aby przetestować atrybuty pliku w znalezionym pliku.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*Dwmask*<br/>
Określa jeden lub więcej atrybutów plików, zidentyfikowanych w strukturze [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) dla znalezionego pliku. Aby wyszukać wiele atrybutów, użyj operatora or (&#124;). Dopuszczalna jest dowolna kombinacja następujących atrybutów:

- FILE_ATTRIBUTE_ARCHIVE Plik jest plikiem archiwum. Aplikacje używają tego atrybutu do oznaczania plików do tworzenia kopii zapasowych lub usuwania.

- FILE_ATTRIBUTE_COMPRESSED Plik lub katalog jest skompresowany. W przypadku pliku oznacza to, że wszystkie dane w pliku są kompresowane. W przypadku katalogu oznacza to, że kompresja jest wartością domyślną dla nowo utworzonych plików i podkatalogów.

- FILE_ATTRIBUTE_DIRECTORY Plik jest katalogiem.

- FILE_ATTRIBUTE_NORMAL Plik nie ma ustawionego żadnych innych atrybutów. Ten atrybut jest prawidłowy tylko wtedy, gdy jest używany samodzielnie. Wszystkie inne atrybuty plików zastępują ten atrybut.

- FILE_ATTRIBUTE_HIDDEN Plik jest ukryty. Nie należy go włączać do zwykłej listy katalogów.

- FILE_ATTRIBUTE_READONLY Plik jest tylko do odczytu. Aplikacje mogą odczytać plik, ale nie mogą go zapisać ani usunąć.

- FILE_ATTRIBUTE_SYSTEM Plik jest częścią lub jest używany wyłącznie przez system operacyjny.

- FILE_ATTRIBUTE_TEMPORARY Plik jest używany do przechowywania tymczasowego. Aplikacje powinny zapisywać do pliku tylko wtedy, gdy jest to absolutnie konieczne. Większość danych pliku pozostaje w pamięci bez opróżnienia na nośnik, ponieważ plik zostanie wkrótce usunięty.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [Win32 GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Uwagi

Przed wywołaniem `MatchesMask`połączenia należy zadzwonić do [findnextFile](#findnextfile) co najmniej raz.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)<br/>
[Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
