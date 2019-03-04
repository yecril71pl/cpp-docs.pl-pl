---
title: CFileFind Class
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
ms.openlocfilehash: da08b04b314df4916a290d4929a4cbaac87434d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289926"
---
# <a name="cfilefind-class"></a>CFileFind Class

Wykonuje wyszukiwanie plików lokalnych i jest klasą bazową dla [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) i [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), które wykonują internetowych plikach wyszukiwania.

## <a name="syntax"></a>Składnia

```
class CFileFind : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|Konstruuje `CFileFind` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileFind::Close](#close)|Zamknięcie żądania wyszukiwania.|
|[CFileFind::FindFile](#findfile)|Przeszukuje katalog dla określonej nazwy pliku.|
|[CFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików z poprzedniego wywołania [FindFile](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Pobiera czasu utworzenia pliku.|
|[CFileFind::GetFileName](#getfilename)|Pobiera nazwę, łącznie z rozszerzeniem, pliku, znaleziono|
|[CFileFind::GetFilePath](#getfilepath)|Pobiera pełną ścieżkę pliku, znaleziono.|
|[CFileFind::GetFileTitle](#getfiletitle)|Pobiera tytuł znaleziony plik. Tytuł nie zawiera rozszerzenia.|
|[CFileFind::GetFileURL](#getfileurl)|Pobiera adres URL, łącznie ze ścieżką pliku znalezionego pliku.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Pobiera czas ostatniego dostępu do pliku.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Pobiera czas plik został ostatnio zmieniony i zapisany.|
|[CFileFind::GetLength](#getlength)|Pobiera długość znaleziony plik, w bajtach.|
|[CFileFind::GetRoot](#getroot)|Pobiera katalog główny znaleziony plik.|
|[CFileFind::IsArchived](#isarchived)|Określa, jeśli znaleziono plik zostaje zarchiwizowany.|
|[CFileFind::IsCompressed](#iscompressed)|Określa, jeśli znaleziono plik jest skompresowany.|
|[CFileFind::IsDirectory](#isdirectory)|Określa, czy plik znaleziono katalogu.|
|[CFileFind::IsDots](#isdots)|Określa, czy nazwa znaleziony plik ma nazwę "."lub"..", który wskazuje, że jest w rzeczywistości katalogiem.|
|[CFileFind::IsHidden](#ishidden)|Określa, jeśli znaleziono plik jest ukryty.|
|[CFileFind::IsNormal](#isnormal)|Określa, czy plik znaleziono normalny (innymi słowy, nie ma innych atrybutów).|
|[CFileFind::IsReadOnly](#isreadonly)|Określa, jeśli znaleziono plik jest tylko do odczytu.|
|[CFileFind::IsSystem](#issystem)|Określa, jeśli znaleziono plik jest plikiem systemu.|
|[CFileFind::IsTemporary](#istemporary)|Określa, czy znaleziony plik tymczasowy.|
|[CFileFind::MatchesMask](#matchesmask)|Określa atrybuty pliku odpowiednią pliku, który ma zostać odnaleziona.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Zamykanie pliku określonego przez dojście bieżącego wyszukiwania.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu.|

## <a name="remarks"></a>Uwagi

`CFileFind` obejmuje funkcje Członkowskie, które rozpocząć wyszukiwanie, zlokalizuj plik i zwracają tytuł, nazwa lub ścieżka do pliku. Wyszukiwania w Internecie, funkcja elementu członkowskiego [GetFileURL](#getfileurl) zwraca adres URL pliku.

`CFileFind` Klasa bazowa dla dwóch klas MFC zaprojektowano w celu wyszukiwania typów określonego serwera: `CGopherFileFind` współpracuje w szczególności z serwerów gopher i `CFtpFileFind` współpracuje w szczególności z serwerami FTP. Razem te trzy klasy mechanizm bezproblemowe dla klienta w celu znalezienia plików, niezależnie od tego, czy protokół serwera, typu pliku lub lokalizacji, na komputerze lokalnym lub zdalnym serwerem.

Poniższy kod powoduje wyliczenie wszystkich plików w bieżącym katalogu, drukowanie nazwę każdego pliku:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

W celu uproszczenia w przykładzie, ten kod używa standardowej biblioteki C++ `cout` klasy. `cout` Wiersza może zostać zastąpione wywołanie `CListBox::AddString`, na przykład w programie przy użyciu graficznego interfejsu użytkownika.

Aby uzyskać więcej informacji o sposobie używania `CFileFind` i innych klasach WinInet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cfilefind"></a>  CFileFind::CFileFind

Ta funkcja członkowska jest wywoływana, gdy `CFileFind` obiekt jest konstruowany.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

##  <a name="close"></a>  CFileFind::Close

Wywołaj tę funkcję elementu członkowskiego, aby zakończyć wyszukiwanie, Resetowanie kontekstu i zwolnić wszystkie zasoby.

```
void Close();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `Close`, nie trzeba utworzyć nową `CFileFind` wystąpienia przed wywołaniem [FindFile](#findfile) można rozpocząć nowego wyszukiwania.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

##  <a name="closecontext"></a>  CFileFind::CloseContext

Zamykanie pliku określonego przez dojście bieżącego wyszukiwania.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Uwagi

Zamyka plik określony przez bieżącą wartość dojście do wyszukiwania. Należy przesłonić tę funkcję, aby zmienić zachowanie domyślne.

Należy wywołać [FindFile](#findfile) lub [FindNextFile](#findnextfile) funkcje co najmniej raz, można pobrać uchwytu prawidłowe wyszukiwania. `FindFile` i `FindNextFile` funkcje użyć uchwytu wyszukiwania, aby zlokalizować pliki o nazwach odpowiadających podanej nazwie.

##  <a name="findfile"></a>  CFileFind::FindFile

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć wyszukiwanie plików.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Parametry

*pstrName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku, aby znaleźć. W przypadku przekazania wartości NULL *pstrName*, `FindFile` jest symbol wieloznaczny (*.\*) wyszukiwania.

*dwUnused*<br/>
Zastrzeżone się `FindFile` polimorficznych z klas pochodnych. Musi być równa 0.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Uwagi

Po wywołaniu `FindFile` aby rozpocząć wyszukiwanie plików, należy wywołać [FindNextFile](#findnextfile) do pobierania plików kolejne. Należy wywołać `FindNextFile` co najmniej raz przed wywołaniem żadnego z następujących atrybutów elementów członkowskich:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [Isnormal —](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).

##  <a name="findnextfile"></a>  CFileFind::FindNextFile

Wywołaj tę funkcję elementu członkowskiego, aby kontynuować wyszukiwanie plików z poprzedniego wywołania [FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli istnieje więcej plików; zero, jeśli znaleziono pliku jest ostatni z nich w katalogu lub jeśli wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360). Jeśli znaleziono pliku ostatniego pliku w katalogu lub jeśli nie pasujących plików można znaleźć `GetLastError` :: gettotalsize() zwróciło ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Uwagi

Należy wywołać `FindNextFile` co najmniej raz przed wywołaniem żadnego z następujących atrybutów elementów członkowskich:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [Isnormal —](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile` opakowuje funkcję Win32 [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea).

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).

##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime

Wywołaj tę funkcję elementu członkowskiego, można pobrać czasu utworzenia określonego pliku.

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

Wartość różną od zera, jeśli to się powiedzie; 0 w przypadku niepowodzenia. `GetCreationTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetCreationTime`.

> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki w celu zaimplementowania sygnaturę czasową, zwrócona przez tę funkcję. Ta funkcja może zwrócić tę samą wartość zwracana przez inne funkcje sygnatury czasu, jeśli bazowego systemu plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury, aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacji zwracana godzina jest w czasie lokalnej strefy do maszyny były znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) interfejsu API, aby uzyskać więcej informacji.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="getfilename"></a>  CFileFind::GetFileName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwę pliku, znaleziono.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa pliku ostatnio odnaleziono.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem GetFileName.

`GetFileName` jest jednym z trzech `CFileFind` funkcje Członkowskie, które zwracają jakąś formę nazwy pliku. Na poniższej liście opisano trzy i jak mogą się różnić:

- `GetFileName` Zwraca nazwę pliku, łącznie z rozszerzeniem. Na przykład, wywołanie `GetFileName` wygenerować komunikat użytkowników o pliku *c:\myhtml\myfile.txt* zwraca nazwę *mójplik.txt*.

- [GetFilePath](#getfilepath) zwraca pełną ścieżkę do pliku. Na przykład, wywołanie `GetFilePath` wygenerować komunikat użytkowników o pliku *c:\myhtml\myfile.txt* zwraca ścieżkę pliku *c:\myhtml\myfile.txt*.

- [GetFileTitle](#getfiletitle) zwraca nazwę pliku bez rozszerzenia pliku. Na przykład, wywołanie `GetFileTitle` wygenerować komunikat użytkowników o pliku *c:\myhtml\myfile.txt* zwraca tytuł pliku *myfile*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

##  <a name="getfilepath"></a>  CFileFind::GetFilePath

Wywołaj tę funkcję elementu członkowskiego, aby pobrać pełnej ścieżki pliku.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka określonego pliku.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetFilePath`.

`GetFilePath` jest jednym z trzech `CFileFind` funkcje Członkowskie, które zwracają jakąś formę nazwy pliku. Na poniższej liście opisano trzy i jak mogą się różnić:

- [GetFileName](#getfilename) zwraca nazwę pliku, łącznie z rozszerzeniem. Na przykład, wywołanie `GetFileName` wygenerować komunikat użytkowników o pliku *c:\myhtml\myfile.txt* zwraca nazwę *mójplik.txt*.

- `GetFilePath` Zwraca pełną ścieżkę do pliku. Na przykład, wywołanie `GetFilePath` wygenerować komunikat użytkowników o pliku `c:\myhtml\myfile.txt` zwraca ścieżkę pliku `c:\myhtml\myfile.txt`.

- [GetFileTitle](#getfiletitle) zwraca nazwę pliku bez rozszerzenia pliku. Na przykład, wywołanie `GetFileTitle` wygenerować komunikat użytkowników o pliku *c:\myhtml\myfile.txt* zwraca tytuł pliku *myfile*.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle

Wywołaj tę funkcję elementu członkowskiego, aby pobrać tytuł znaleziony plik.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Wartość zwracana

Tytuł pliku.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetFileTitle`.

`GetFileTitle` jest jednym z trzech `CFileFind` funkcje Członkowskie, które zwracają jakąś formę nazwy pliku. Na poniższej liście opisano trzy i jak mogą się różnić:

- [GetFileName](#getfilename) zwraca nazwę pliku, łącznie z rozszerzeniem. Na przykład, wywołanie `GetFileName` wygenerować komunikat użytkowników o pliku *c:\myhtml\myfile.txt* zwraca nazwę *mójplik.txt*.

- [GetFilePath](#getfilepath) zwraca pełną ścieżkę do pliku. Na przykład, wywołanie `GetFilePath` wygenerować komunikat użytkowników o pliku *c:\myhtml\myfile.txt* zwraca ścieżkę pliku *c:\myhtml\myfile.txt*.

- `GetFileTitle` Zwraca nazwę pliku bez rozszerzenia pliku. Na przykład, wywołanie `GetFileTitle` wygenerować komunikat użytkowników o pliku *c:\myhtml\myfile.txt* zwraca tytuł pliku *myfile*.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

##  <a name="getfileurl"></a>  CFileFind::GetFileURL

Wywołaj tę funkcję elementu członkowskiego, aby pobrać określony adres URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Wartość zwracana

Pełny adres URL.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetFileURL`.

`GetFileURL` jest podobna do funkcji składowej [GetFilePath](#getfilepath), chyba że zwraca adres URL w postaci `file://path`. Na przykład, wywołanie `GetFileURL` można pobrać pełny adres URL dla *mójplik.txt* zwraca adres URL `file://c:\myhtml\myfile.txt`.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime

Wywołaj tę funkcję elementu członkowskiego, aby pobrać czas ostatniego dostępu do określonego pliku.

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

Wartość różną od zera, jeśli to się powiedzie; 0 w przypadku niepowodzenia. `GetLastAccessTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastAccessTime`.

> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki w celu zaimplementowania sygnaturę czasową, zwrócona przez tę funkcję. Ta funkcja może zwrócić tę samą wartość zwracana przez inne funkcje sygnatury czasu, jeśli bazowego systemu plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury, aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacji zwracana godzina jest w czasie lokalnej strefy do maszyny były znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) interfejsu API, aby uzyskać więcej informacji.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime

Wywołaj tę funkcję elementu członkowskiego, można pobrać czasu, gdy plik został zmieniony.

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

Wartość różną od zera, jeśli to się powiedzie; 0 w przypadku niepowodzenia. `GetLastWriteTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CFileFind` obiektu.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastWriteTime`.

> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki w celu zaimplementowania sygnaturę czasową, zwrócona przez tę funkcję. Ta funkcja może zwrócić tę samą wartość zwracana przez inne funkcje sygnatury czasu, jeśli bazowego systemu plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_Find_Data](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury, aby uzyskać informacje na temat formatów czasu. W niektórych systemach operacji zwracana godzina jest w czasie lokalnej strefy do maszyny były znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) interfejsu API, aby uzyskać więcej informacji.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="getlength"></a>  CFileFind::GetLength

Wywołaj tę funkcję elementu członkowskiego, aby pobrać długości znaleziony plik, w bajtach.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość znaleziony plik, w bajtach.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLength`.

`GetLength` używa struktury Win32 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) uzyskać i zwracają wartość rozmiaru pliku w bajtach.

> [!NOTE]
>  Począwszy od MFC 7.0 `GetLength` obsługuje typy 64-bitową liczbę całkowitą. Wcześniej istniejący kod utworzonych za pomocą tego nowszą wersję biblioteki może spowodować ostrzeżenia obcięcie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

##  <a name="getroot"></a>  CFileFind::GetRoot

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać katalogu głównego znaleziony plik.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Wartość zwracana

Katalog główny aktywnego wyszukiwania.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetRoot`.

Ta funkcja elementu członkowskiego zwraca specyfikator dysku i nazwy ścieżki używany, aby rozpocząć wyszukiwanie. Na przykład, wywołanie [FindFile](#findfile) z `*.dat` skutkuje `GetRoot` zwraca pusty ciąg. Przekazanie ścieżki, takich jak `c:\windows\system\*.dll`, `FindFile` wyniki `GetRoot` zwracanie `c:\windows\system\`.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetFileName](#getfilename).

##  <a name="isarchived"></a>  CFileFind::IsArchived

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli znaleziono plik zostaje zarchiwizowany.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacje oznaczyć pliku archiwum, który ma zostać kopii zapasowej lub usunięte z FILE_ATTRIBUTE_ARCHIVE, atrybut pliku, określonej w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury.

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsArchived`.

Zobacz opis funkcji elementu członkowskiego [MatchesMask](#matchesmask) pełną listę atrybutów pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="iscompressed"></a>  CFileFind::IsCompressed

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli znaleziono plik jest skompresowany.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Skompresowany plik jest oznaczona za pomocą FILE_ATTRIBUTE_COMPRESSED, atrybut pliku zostały zidentyfikowane w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Dla pliku ten atrybut wskazuje, wszystkie dane w pliku jest skompresowany. Dla katalogu ten atrybut wskazuje, że kompresja jest ustawieniem domyślnym dla nowo tworzonych plików i podkatalogów.

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsCompressed`.

Zobacz opis funkcji elementu członkowskiego [MatchesMask](#matchesmask) pełną listę atrybutów pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="isdirectory"></a>  CFileFind::IsDirectory

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli znaleziono plik jest katalogiem.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Plik, który jest katalogiem jest oznaczona za pomocą FILE_ATTRIBUTE_DIRECTORY atrybutu pliku zostały zidentyfikowane w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury.

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsDirectory`.

Zobacz opis funkcji elementu członkowskiego [MatchesMask](#matchesmask) pełną listę atrybutów pliku.

### <a name="example"></a>Przykład

Ten program małych recurses wszystkich katalogów na dysku C:\ i wyświetla nazwę katalogu.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

##  <a name="isdots"></a>  CFileFind::IsDots

Wywołaj tę funkcję składowej do testowania dla bieżącego katalogu i element nadrzędny znaczników katalogu podczas iteracji w plikach.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli znaleziono plik o nazwie "."lub"..", co oznacza, że znaleziony plik jest w rzeczywistości katalogiem. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsDots`.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).

##  <a name="ishidden"></a>  CFileFind::IsHidden

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli znaleziono plik jest ukryty.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ukryte pliki, które są oznaczone FILE_ATTRIBUTE_HIDDEN, atrybut pliku zidentyfikowanego w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Ukryty plik nie znajduje się liście zwykłych katalogów.

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsHidden`.

Zobacz opis funkcji elementu członkowskiego [MatchesMask](#matchesmask) pełną listę atrybutów pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="isnormal"></a>  CFileFind::IsNormal

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli znaleziono plik jest plikiem normalny.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pliki oznaczone FILE_ATTRIBUTE_NORMAL, atrybut pliku zidentyfikowanego w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Zwykłego pliku nie ma innych atrybutów zestawu. Wszystkie inne atrybuty pliku zastąpienie tego atrybutu.

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsNormal`.

Zobacz opis funkcji elementu członkowskiego [MatchesMask](#matchesmask) pełną listę atrybutów pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="isreadonly"></a>  CFileFind::IsReadOnly

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli znaleziono plik jest tylko do odczytu.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Plik tylko do odczytu jest oznaczona za pomocą FILE_ATTRIBUTE_READONLY, atrybut pliku zostały zidentyfikowane w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Aplikacje mogą odczytywać taki plik, ale nie można w nim zapisywać ani go usunąć.

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsReadOnly`.

Zobacz opis funkcji elementu członkowskiego [MatchesMask](#matchesmask) pełną listę atrybutów pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="issystem"></a>  CFileFind::IsSystem

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli znaleziono plik jest plikiem systemu.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Plik systemowy jest oznaczona za pomocą FILE_ATTRIBUTE_SYSTEM, atrybut pliku zostały zidentyfikowane w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Plik systemowy jest częścią lub jest używana wyłącznie przez, systemu operacyjnego.

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsSystem`.

Zobacz opis funkcji elementu członkowskiego [MatchesMask](#matchesmask) pełną listę atrybutów pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="istemporary"></a>  CFileFind::IsTemporary

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli znaleziono plik jest plikiem tymczasowych.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Plik tymczasowy jest oznaczona za pomocą FILE_ATTRIBUTE_TEMPORARY, atrybut pliku zostały zidentyfikowane w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Plik tymczasowy jest używany do tymczasowego przechowywania danych. Aplikacje należy zapisywać do pliku, tylko wtedy, gdy jest to absolutnie konieczne. Większość plików danych pozostaje w pamięci bez opróżnianych na nośniku, ponieważ plik zostanie wkrótce usunięty.

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsTemporary`.

Zobacz opis funkcji elementu członkowskiego [MatchesMask](#matchesmask) pełną listę atrybutów pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CFileFind::GetLength](#getlength).

##  <a name="m_ptm"></a>  CFileFind::m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

##  <a name="matchesmask"></a>  CFileFind::MatchesMask

Wywołaj tę funkcję elementu członkowskiego, aby przetestować atrybuty pliku znaleziono plik.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Określa jeden lub więcej atrybutów plików zidentyfikowany w [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury do znaleziony plik. Aby wyszukać wiele atrybutów, należy użyć bitowe OR (&#124;) — operator. Dopuszczalne jest dowolną kombinację następujących atrybutów:

- FILE_ATTRIBUTE_ARCHIVE plik jest plikiem archiwum. Aplikacje użyć tego atrybutu, aby oznaczyć pliki w kopii zapasowej lub usunięcia.

- FILE_ATTRIBUTE_COMPRESSED pliku lub katalogu jest skompresowany. Plik oznacza to wszystkie dane w pliku jest skompresowany. Dla katalogu oznacza to, że kompresja jest ustawieniem domyślnym dla nowo tworzonych plików i podkatalogów.

- FILE_ATTRIBUTE_DIRECTORY pliku jest katalogiem.

- FILE_ATTRIBUTE_NORMAL pliku nie ma innych atrybutów zestawu. Ten atrybut jest prawidłowy tylko wtedy, gdy użyte bez parametrów. Wszystkie inne atrybuty pliku zastąpienie tego atrybutu.

- FILE_ATTRIBUTE_HIDDEN pliku jest ukryty. Jest nie powinny zostać uwzględnione na liście zawartości katalogu zwykłej.

- FILE_ATTRIBUTE_READONLY plik jest tylko do odczytu. Aplikacje można odczytać pliku, ale nie można w nim zapisywać lub usunąć łącznik.

- FILE_ATTRIBUTE_SYSTEM plik jest częścią lub jest używana wyłącznie przez system operacyjny.

- FILE_ATTRIBUTE_TEMPORARY plik jest używany do tymczasowego przechowywania danych. Aplikacje należy zapisywać do pliku, tylko wtedy, gdy jest to absolutnie konieczne. Większość plików danych pozostaje w pamięci bez opróżnianych na nośniku, ponieważ plik zostanie wkrótce usunięty.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Uwagi

Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `MatchesMask`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)<br/>
[Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Klasa CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
