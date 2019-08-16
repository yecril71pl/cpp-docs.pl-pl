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
ms.openlocfilehash: 784086b1c2edef5eb0de3bba4a97d1e3cc6272e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497830"
---
# <a name="catlfile-class"></a>Klasa CAtlFile

Ta klasa udostępnia cienkią otokę wokół interfejsu API obsługi plików systemu Windows.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
|[CAtlFile:: Create](#create)|Wywołaj tę metodę, aby utworzyć lub otworzyć plik.|
|[CAtlFile:: Flush](#flush)|Wywołaj tę metodę, aby wyczyścić bufory dla pliku i spowodować zapisanie wszystkich buforowanych danych w pliku.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Wywołaj tę metodę, aby uzyskać wyniki nakładających się operacji na pliku.|
|[CAtlFile:: GetPosition](#getposition)|Wywołaj tę metodę, aby pobrać bieżącą pozycję wskaźnika pliku z pliku.|
|[CAtlFile:: GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać rozmiar (w bajtach) pliku.|
|[CAtlFile::LockRange](#lockrange)|Wywołaj tę metodę, aby zablokować region w pliku, aby uniemożliwić innym procesom dostęp do niego.|
|[CAtlFile:: Read](#read)|Wywołaj tę metodę, aby odczytać dane z pliku, rozpoczynając od pozycji wskazywanej przez wskaźnik pliku.|
|[CAtlFile:: Seek](#seek)|Wywołaj tę metodę, aby przenieść wskaźnik pliku do pliku.|
|[CAtlFile::SetSize](#setsize)|Wywołaj tę metodę, aby ustawić rozmiar pliku.|
|[CAtlFile::UnlockRange](#unlockrange)|Wywołaj tę metodę, aby odblokować region pliku.|
|[CAtlFile:: Write](#write)|Wywołaj tę metodę, aby zapisać dane do pliku, rozpoczynając od pozycji wskazywanej przez wskaźnik pliku.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu|

## <a name="remarks"></a>Uwagi

Tej klasy należy używać, gdy wymagane jest stosunkowo proste korzystanie z funkcji obsługi plików, ale jest wymagana większa Abstrakcja niż Windows API, bez uwzględnienia zależności MFC.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile. h

##  <a name="catlfile"></a>CAtlFile::CAtlFile

Konstruktor.

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Parametry

*rozszerzeniem*<br/>
Obiekt pliku.

*hFile*<br/>
Dojście do pliku.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Konstruktor kopiujący przenosi własność dojścia do pliku z oryginalnego `CAtlFile` obiektu do nowo skonstruowanego obiektu.

##  <a name="create"></a>CAtlFile:: Create

Wywołaj tę metodę, aby utworzyć lub otworzyć plik.

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

*szFilename*<br/>
Nazwa pliku.

*dwDesiredAccess*<br/>
Żądany dostęp. Zobacz *dwDesiredAccess* w [pliku](/windows/win32/api/fileapi/nf-fileapi-createfilew) w Windows SDK.

*dwShareMode*<br/>
Tryb udostępniania. Zobacz *dwShareMode* w `CreateFile`.

*dwCreationDisposition*<br/>
Dyspozycja tworzenia. Zobacz *dwCreationDisposition* w `CreateFile`.

*dwFlagsAndAttributes*<br/>
Flagi i atrybuty. Zobacz *dwFlagsAndAttributes* w `CreateFile`.

*lpsa*<br/>
Atrybuty zabezpieczeń. Zobacz *lpSecurityAttributes* w `CreateFile`.

*hTemplateFile*<br/>
Plik szablonu. Zobacz *hTemplateFile* w `CreateFile`.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje metodę Create [File](/windows/win32/api/fileapi/nf-fileapi-createfilew) , aby utworzyć lub otworzyć plik.

##  <a name="flush"></a>CAtlFile:: Flush

Wywołaj tę metodę, aby wyczyścić bufory dla pliku i spowodować zapisanie wszystkich buforowanych danych w pliku.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [Funkcja FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) , aby opróżnić dane buforowane do pliku.

##  <a name="getoverlappedresult"></a>  CAtlFile::GetOverlappedResult

Wywołaj tę metodę, aby uzyskać wyniki nakładających się operacji na pliku.

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Parametry

*pOverlapped*<br/>
Nakładająca się struktura. Zobacz *lpOverlapped* in [funkcji GetOverLappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) w Windows SDK.

*dwBytesTransferred*<br/>
Bajty przesłane. Zobacz *lpNumberOfBytesTransferred* w `GetOverlappedResult`.

*bWait*<br/>
Opcja oczekiwania. Zobacz *bWait* w `GetOverlappedResult`.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [funkcji GetOverLappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) , aby uzyskać wyniki z nakładaniem się operacji na pliku.

##  <a name="getposition"></a>CAtlFile:: GetPosition

Wywołaj tę metodę, aby uzyskać bieżącą pozycję wskaźnika pliku.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozycja w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [Funkcja SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) , aby uzyskać bieżącą pozycję wskaźnika pliku.

##  <a name="getsize"></a>CAtlFile:: GetSize

Wywołaj tę metodę, aby uzyskać rozmiar (w bajtach) pliku.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*<br/>
Liczba bajtów w pliku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [funkcji GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) , aby uzyskać rozmiar (w bajtach) pliku.

##  <a name="lockrange"></a>CAtlFile::LockRange

Wywołaj tę metodę, aby zablokować region w pliku, aby uniemożliwić innym procesom dostęp do niego.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozycja w pliku, w którym ma zostać rozpoczęta blokada.

*nCount*<br/>
Długość zakresu bajtów do zablokowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [lockfile](/windows/win32/api/fileapi/nf-fileapi-lockfile) w celu zablokowania regionu w pliku. Zablokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region pliku, ale nie są dozwolone żadne nakładające się regiony. Po odblokowaniu regionu przy użyciu [CAtlFile:: UnlockRange](#unlockrange)zakres bajtów musi dokładnie odpowiadać regionowi, który został wcześniej zablokowany. `LockRange`nie scala sąsiadujących regionów; Jeśli dwa zablokowane regiony są sąsiadujące, należy odblokować każdy z nich osobno.

##  <a name="m_ptm"></a>  CAtlFile::m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

##  <a name="read"></a>CAtlFile:: Read

Wywołaj tę metodę, aby odczytać dane z pliku, rozpoczynając od pozycji wskazywanej przez wskaźnik pliku.

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

*pBuffer*<br/>
Wskaźnik do buforu, który będzie otrzymywał dane odczytane z pliku.

*nBufSize*<br/>
Rozmiar buforu w bajtach.

*nBytesRead*<br/>
Liczba odczytanych bajtów.

*pOverlapped*<br/>
Nakładająca się struktura. Zobacz *lpOverlapped* w usłudze [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) w Windows SDK.

*pfnCompletionRoutine*<br/>
Procedura ukończenia. Zobacz *lpCompletionRoutine* in [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Pierwsze trzy formularze wywołania [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), ostatnie [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) do odczytu danych z pliku. Użyj [CAtlFile:: Seek](#seek) , aby przenieść wskaźnik pliku.

##  <a name="seek"></a>CAtlFile:: Seek

Wywołaj tę metodę, aby przenieść wskaźnik pliku do pliku.

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
Przesunięcie od punktu początkowego przez *dwFrom*.

*dwFrom*<br/>
Punkt początkowy (FILE_BEGIN, FILE_CURRENT lub FILE_END).

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [Funkcja SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) , aby przenieść wskaźnik pliku.

##  <a name="setsize"></a>CAtlFile:: setSize

Wywołaj tę metodę, aby ustawić rozmiar pliku.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*<br/>
Nowa długość pliku w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [Funkcja SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) i [SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) , aby ustawić rozmiar pliku. Po powrocie wskaźnik pliku jest umieszczany na końcu pliku.

##  <a name="unlockrange"></a>CAtlFile::UnlockRange

Wywołaj tę metodę, aby odblokować region pliku.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozycja w pliku, w którym ma zostać rozpoczęte Odblokowywanie.

*nCount*<br/>
Długość zakresu bajtów do odblokowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [UnLockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile) w celu odblokowania regionu pliku.

##  <a name="write"></a>CAtlFile:: Write

Wywołaj tę metodę, aby zapisać dane do pliku, rozpoczynając od pozycji wskazywanej przez wskaźnik pliku.

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

*pBuffer*<br/>
Bufor zawierający dane, które mają być zapisywane do pliku.

*nBufSize*<br/>
Liczba bajtów, które mają zostać przeniesione z bufora.

*pOverlapped*<br/>
Nakładająca się struktura. Zobacz *lpOverlapped* w artykule [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) w Windows SDK.

*pfnCompletionRoutine*<br/>
Procedura ukończenia. Zobacz *lpCompletionRoutine* in [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) w Windows SDK.

*pnBytesWritten*<br/>
Bajty zapisywane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Pierwsze trzy formularze wywołują polecenie [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), a ostatnie wywołania [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) do zapisu danych do pliku. Użyj [CAtlFile:: Seek](#seek) , aby przenieść wskaźnik pliku.

## <a name="see-also"></a>Zobacz także

[Przykład neonu](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CHandle](../../atl/reference/chandle-class.md)
