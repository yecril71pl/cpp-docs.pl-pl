---
title: Klasa CAtlFile
ms.date: 11/04/2016
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: 39f323874ccde5178722235b9beb34c2572407a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318976"
---
# <a name="catlfile-class"></a>Klasa CAtlFile

Ta klasa zapewnia cienkie otoki wokół interfejsu API obsługi plików systemu Windows.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAtlFile : public CHandle
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFile::Utwórz](#create)|Wywołanie tej metody, aby utworzyć lub otworzyć plik.|
|[CAtlFile::Flush](#flush)|Wywołanie tej metody, aby wyczyścić bufory dla pliku i spowodować, że wszystkie buforowane dane mają być zapisywane w pliku.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Wywołanie tej metody, aby uzyskać wyniki nakładającej się operacji w pliku.|
|[Plik CAtl:](#getposition)|Wywołanie tej metody, aby uzyskać bieżącą pozycję wskaźnika pliku z pliku.|
|[Plik CAtl::GetSize](#getsize)|Wywołanie tej metody, aby uzyskać rozmiar w bajtach pliku.|
|[Plik CAtl: :LockRange](#lockrange)|Wywołanie tej metody, aby zablokować region w pliku, aby uniemożliwić innym procesom dostęp do niego.|
|[CAtlFile::Odczyt](#read)|Wywołanie tej metody, aby odczytać dane z pliku, począwszy od pozycji wskazanej przez wskaźnik pliku.|
|[Plik CAtl::Szukaj](#seek)|Wywołanie tej metody, aby przenieść wskaźnik pliku pliku.|
|[Plik CAtl::SetSize](#setsize)|Wywołanie tej metody, aby ustawić rozmiar pliku.|
|[CAtlFile::UnlockRange](#unlockrange)|Wywołanie tej metody, aby odblokować region pliku.|
|[CAtlFile::Napisz](#write)|Wywołanie tej metody, aby zapisać dane do pliku, począwszy od pozycji wskazanej przez wskaźnik pliku.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|Wskaźnik `CAtlTransactionManager` do obiektu|

## <a name="remarks"></a>Uwagi

Użyj tej klasy, gdy potrzeby obsługi plików są stosunkowo proste, ale wymagana jest większa abstrakcja niż zapewnia interfejs API systemu Windows, bez uwzględnienia zależności MFC.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Chandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile.h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlFile

Konstruktor.

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Parametry

*Plik*<br/>
Obiekt pliku.

*hFile (plik)*<br/>
Dojście do pliku.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Konstruktor kopii przenosi własność dojścia pliku z oryginalnego `CAtlFile` obiektu do nowo zbudowanego obiektu.

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile::Utwórz

Wywołanie tej metody, aby utworzyć lub otworzyć plik.

```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>Parametry

*szFilename (szFilename)*<br/>
Nazwa pliku.

*dwDesiredAccess*<br/>
Pożądany dostęp. Zobacz *dwDesiredAccess* w [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) w windows SDK.

*dwShareMode (tryb współudziału)*<br/>
Tryb udostępniania. Zobacz *dwShareMode* w `CreateFile`.

*dwCreationDisposition (Wykrywanie tworzenia)*<br/>
Usposobienie stworzenia. Zobacz *dwCreationDisposition* w `CreateFile`.

*dwFlagsAndAttributes*<br/>
Flagi i atrybuty. Zobacz *dwFlagsAndAttributes* w `CreateFile`.

*lpsa*<br/>
Atrybuty zabezpieczeń. Zobacz *lpSecurityAttributes* w `CreateFile`.

*hTemplateFile*<br/>
Plik szablonu. Zobacz *hTemplateFile* w `CreateFile`.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [CreateFile,](/windows/win32/api/fileapi/nf-fileapi-createfilew) aby utworzyć lub otworzyć plik.

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile::Flush

Wywołanie tej metody, aby wyczyścić bufory dla pliku i spowodować, że wszystkie buforowane dane mają być zapisywane w pliku.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) opróżnić buforowane dane do pliku.

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult

Wywołanie tej metody, aby uzyskać wyniki nakładającej się operacji w pliku.

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Parametry

*pZamknienie*<br/>
Nakładająca się struktura. Zobacz *lpOverlapped* w [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) w windows SDK.

*dwBytesTransferred*<br/>
Bajty przeniesione. Zobacz *lpNumberOfBytesTransferred* w `GetOverlappedResult`.

*bWait (Ur.*<br/>
Opcja oczekiwania. Patrz *bWait* w pliku `GetOverlappedResult`.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [GetOverlappedResult,](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) aby uzyskać wyniki nakładającej się operacji w pliku.

## <a name="catlfilegetposition"></a><a name="getposition"></a>Plik CAtl:

Wywołanie tej metody, aby uzyskać bieżącą pozycję wskaźnika pliku.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Pozycja w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [SetFilePointer,](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) aby uzyskać bieżącą pozycję wskaźnika pliku.

## <a name="catlfilegetsize"></a><a name="getsize"></a>Plik CAtl::GetSize

Wywołanie tej metody, aby uzyskać rozmiar w bajtach pliku.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen (nLen)*<br/>
Liczba bajtów w pliku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [GetFileSize,](/windows/win32/api/fileapi/nf-fileapi-getfilesize) aby uzyskać rozmiar w bajtach pliku.

## <a name="catlfilelockrange"></a><a name="lockrange"></a>Plik CAtl: :LockRange

Wywołanie tej metody, aby zablokować region w pliku, aby uniemożliwić innym procesom dostęp do niego.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Pozycja w pliku, w którym powinna się rozpocząć blokada.

*Ncount*<br/>
Długość zakresu bajtów, który ma być zablokowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [LockFile,](/windows/win32/api/fileapi/nf-fileapi-lockfile) aby zablokować region w pliku. Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region pliku, ale nie nakładające się regiony są dozwolone. Po odblokowaniu regionu, za pomocą [CAtlFile::UnlockRange](#unlockrange), zakres bajtów musi odpowiadać dokładnie region, który został wcześniej zablokowany. `LockRange`nie łączy sąsiednich regionów; Jeśli sąsiadują dwa zablokowane regiony, należy odblokować każdy oddzielnie.

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile::m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

## <a name="catlfileread"></a><a name="read"></a>CAtlFile::Odczyt

Wywołanie tej metody, aby odczytać dane z pliku, począwszy od pozycji wskazanej przez wskaźnik pliku.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>Parametry

*Pbuffer*<br/>
Wskaźnik do buforu, który będzie odbierał dane odczytane z pliku.

*nBufSize (Rozmiar)*<br/>
Rozmiar buforu w bajtach.

*nDwojnikCzytał*<br/>
Liczba odczytanych bajtów.

*pZamknienie*<br/>
Nakładająca się struktura. Zobacz *lpOverlapped* w [Pliku ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) w windows SDK.

*pfnCompletionRoutyna*<br/>
Procedura uzupełniania. Zobacz *lpCompletionRoutine* w [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Pierwsze trzy [formularze wywołać ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), ostatni [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) do odczytu danych z pliku. Użyj [CAtlFile::Seek,](#seek) aby przenieść wskaźnik pliku.

## <a name="catlfileseek"></a><a name="seek"></a>Plik CAtl::Szukaj

Wywołanie tej metody, aby przenieść wskaźnik pliku pliku.

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nStawa*<br/>
Przesunięcie od punktu początkowego podanego przez *dwFrom*.

*dwFrom*<br/>
Punkt początkowy (FILE_BEGIN, FILE_CURRENT lub FILE_END).

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [SetFilePointer,](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) aby przenieść wskaźnik pliku.

## <a name="catlfilesetsize"></a><a name="setsize"></a>Plik CAtl::SetSize

Wywołanie tej metody, aby ustawić rozmiar pliku.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen (Nienawisłe)*<br/>
Nowa długość pliku w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) i [SetEndOfFile,](/windows/win32/api/fileapi/nf-fileapi-setendoffile) aby ustawić rozmiar pliku. Po zwrocie wskaźnik pliku jest umieszczony na końcu pliku.

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange

Wywołanie tej metody, aby odblokować region pliku.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Pozycja w pliku, w którym powinno się rozpocząć odblokowywanie.

*Ncount*<br/>
Długość zakresu bajtów, który ma zostać odblokowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [UnlockFile,](/windows/win32/api/fileapi/nf-fileapi-unlockfile) aby odblokować region pliku.

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile::Napisz

Wywołanie tej metody, aby zapisać dane do pliku, począwszy od pozycji wskazanej przez wskaźnik pliku.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>Parametry

*Pbuffer*<br/>
Bufor zawierający dane, które mają być zapisywane w pliku.

*nBufSize (Rozmiar)*<br/>
Liczba bajtów, które mają zostać przeniesione z buforu.

*pZamknienie*<br/>
Nakładająca się struktura. Zobacz *lpOverlapped* w [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) w windows SDK.

*pfnCompletionRoutyna*<br/>
Procedura uzupełniania. Zobacz *lpCompletionRoutine* w [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) w windows SDK.

*pnBytesWritten*<br/>
Bajty napisane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Pierwsze trzy [formularze wywołać WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), ostatnie wywoła [writefileex](/windows/win32/api/fileapi/nf-fileapi-writefileex) do zapisu danych do pliku. Użyj [CAtlFile::Seek,](#seek) aby przenieść wskaźnik pliku.

## <a name="see-also"></a>Zobacz też

[Przykłada markizy](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CHandle](../../atl/reference/chandle-class.md)
