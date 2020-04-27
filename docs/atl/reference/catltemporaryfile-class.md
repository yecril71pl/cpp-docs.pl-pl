---
title: Klasa CAtlTemporaryFile
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: f3d0be66bf0b5a6c07a72c8ae6cc9c90e176728f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167893"
---
# <a name="catltemporaryfile-class"></a>Klasa CAtlTemporaryFile

Ta klasa zawiera metody tworzenia i używania pliku tymczasowego.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
class CAtlTemporaryFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Konstruktor.|
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlTemporaryFile:: Close](#close)|Wywołaj tę metodę, aby zamknąć plik tymczasowy i usunąć jego zawartość lub przechować je w określonej nazwie pliku.|
|[CAtlTemporaryFile:: Create](#create)|Wywołaj tę metodę, aby utworzyć plik tymczasowy.|
|[CAtlTemporaryFile:: Flush](#flush)|Wywołaj tę metodę, aby wymusić zapisanie wszystkich danych w buforze plików w pliku tymczasowym.|
|[CAtlTemporaryFile:: GetPosition](#getposition)|Wywołaj tę metodę, aby uzyskać bieżącą pozycję wskaźnika pliku.|
|[CAtlTemporaryFile:: GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać rozmiar w bajtach pliku tymczasowego.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Wywołaj tę metodę, aby usunąć skojarzenie `CAtlTemporaryFile` pliku z obiektem.|
|[CAtlTemporaryFile::HandsOn](#handson)|Wywołaj tę metodę, aby otworzyć istniejący plik tymczasowy i umieścić wskaźnik na końcu pliku.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Wywołaj tę metodę, aby zablokować region w pliku, aby uniemożliwić innym procesom dostęp do niego.|
|[CAtlTemporaryFile:: Read](#read)|Wywołaj tę metodę, aby odczytać dane z pliku tymczasowego, rozpoczynając od pozycji wskazywanej przez wskaźnik pliku.|
|[CAtlTemporaryFile:: Seek](#seek)|Wywołaj tę metodę, aby przenieść wskaźnik pliku tymczasowego.|
|[CAtlTemporaryFile:: setSize](#setsize)|Wywołaj tę metodę, aby ustawić rozmiar pliku tymczasowego.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Wywołaj tę metodę, aby zwrócić nazwę pliku tymczasowego.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Wywołaj tę metodę, aby odblokować region pliku tymczasowego.|
|[CAtlTemporaryFile:: Write](#write)|Wywołaj tę metodę, aby zapisać dane do pliku tymczasowego, rozpoczynając od pozycji wskazywanej przez wskaźnik pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlTemporaryFile:: uchwyt operatora](#operator_handle)|Zwraca dojście do pliku tymczasowego.|

## <a name="remarks"></a>Uwagi

`CAtlTemporaryFile`ułatwia tworzenie i używanie pliku tymczasowego. Plik jest automatycznie nazwany, otwarty, zamknięty i usunięty. Jeśli zawartość pliku jest wymagana po zamknięciu pliku, można je zapisać w nowym pliku o określonej nazwie.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile. h

## <a name="example"></a>Przykład

Zobacz przykład dla [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

Konstruktor.

```cpp
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Uwagi

Plik nie jest faktycznie otwierany, dopóki nie zostanie wykonane wywołanie [CAtlTemporaryFile:: Create](#create).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile

Destruktor.

```cpp
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor wywołuje [CAtlTemporaryFile:: Close](#close).

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtlTemporaryFile:: Close

Wywołaj tę metodę, aby zamknąć plik tymczasowy i usunąć jego zawartość lub przechować je w określonej nazwie pliku.

```cpp
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*szNewName*<br/>
Nazwa nowego pliku, w którym ma być przechowywana zawartość pliku tymczasowego. Jeśli ten argument ma wartość NULL, zawartość pliku tymczasowego jest usuwana.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtlTemporaryFile:: Create

Wywołaj tę metodę, aby utworzyć plik tymczasowy.

```cpp
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Ścieżka do pliku tymczasowego. Jeśli jest to wartość NULL, [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) zostanie wywołana w celu przypisania ścieżki.

*dwDesiredAccess*<br/>
Żądany dostęp. Zobacz *dwDesiredAccess* w [pliku](/windows/win32/api/fileapi/nf-fileapi-createfilew) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtlTemporaryFile:: Flush

Wywołaj tę metodę, aby wymusić zapisanie wszystkich danych w buforze plików w pliku tymczasowym.

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Podobny do [CAtlTemporaryFile:: HandsOff](#handsoff), z tą różnicą, że plik nie jest zamknięty.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtlTemporaryFile:: GetPosition

Wywołaj tę metodę, aby uzyskać bieżącą pozycję wskaźnika pliku.

```cpp
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozycja w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby zmienić położenie wskaźnika pliku, użyj [CAtlTemporaryFile:: Seek](#seek).

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtlTemporaryFile:: GetSize

Wywołaj tę metodę, aby uzyskać rozmiar w bajtach pliku tymczasowego.

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*<br/>
Liczba bajtów w pliku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtlTemporaryFile::HandsOff

Wywołaj tę metodę, aby usunąć skojarzenie `CAtlTemporaryFile` pliku z obiektem.

```cpp
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`HandsOff`i [CAtlTemporaryFile:: HandsOn](#handson) są używane do usuwania skojarzenia pliku z obiektu i w razie potrzeby zostaną dołączone ponownie. `HandsOff`spowoduje wymuszenie zapisania wszystkich danych w buforze plików w pliku tymczasowym, a następnie zamknięcie pliku. Jeśli chcesz zamknąć i usunąć plik trwale, lub jeśli chcesz zamknąć i zachować zawartość pliku o podaną nazwę, użyj [CAtlTemporaryFile:: Close](#close).

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtlTemporaryFile::HandsOn

Wywołaj tę metodę, aby otworzyć istniejący plik tymczasowy i umieścić wskaźnik na końcu pliku.

```cpp
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

[CAtlTemporaryFile:: HandsOff](#handsoff) i `HandsOn` są używane do usuwania skojarzenia pliku z obiektu i ponownego dołączenia go w razie potrzeby.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtlTemporaryFile::LockRange

Wywołaj tę metodę, aby zablokować region w pliku tymczasowym, aby uniemożliwić innym procesom dostęp do niego.

```cpp
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

Zablokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region pliku, ale nie są dozwolone żadne nakładające się regiony. Aby pomyślnie odblokować region, użyj [CAtlTemporaryFile:: UnlockRange](#unlockrange), upewniając się, że zakres bajtów dokładnie odpowiada regionowi, który został wcześniej zablokowany. `LockRange`nie scala sąsiadujących regionów; Jeśli dwa zablokowane regiony są sąsiadujące, należy odblokować każdy z nich osobno.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtlTemporaryFile:: uchwyt operatora

Zwraca dojście do pliku tymczasowego.

```cpp
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtlTemporaryFile:: Read

Wywołaj tę metodę, aby odczytać dane z pliku tymczasowego, rozpoczynając od pozycji wskazywanej przez wskaźnik pliku.

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parametry

*pBuffer*<br/>
Wskaźnik do buforu, który będzie otrzymywał dane odczytane z pliku.

*nBufSize*<br/>
Rozmiar buforu w bajtach.

*nBytesRead*<br/>
Liczba odczytanych bajtów.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołania [CAtlFile:: Read](../../atl/reference/catlfile-class.md#read). Aby zmienić położenie wskaźnika pliku, wywołaj [CAtlTemporaryFile:: Seek](#seek).

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtlTemporaryFile:: Seek

Wywołaj tę metodę, aby przenieść wskaźnik pliku tymczasowego.

```cpp
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
Przesunięcie w bajtach od punktu początkowego podaną przez *dwFrom.*

*dwFrom*<br/>
Punkt początkowy (FILE_BEGIN, FILE_CURRENT lub FILE_END).

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFile:: Seek](../../atl/reference/catlfile-class.md#seek). Aby uzyskać bieżącą pozycję wskaźnika pliku, wywołaj [CAtlTemporaryFile:: GetPosition](#getposition).

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtlTemporaryFile:: setSize

Wywołaj tę metodę, aby ustawić rozmiar pliku tymczasowego.

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*<br/>
Nowa długość pliku w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFile:: SetSize](../../atl/reference/catlfile-class.md#setsize). Po powrocie wskaźnik pliku jest umieszczany na końcu pliku.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

Wywołaj tę metodę, aby zwrócić nazwę pliku tymczasowego.

```cpp
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca LPCTSTR wskazujący nazwę pliku.

### <a name="remarks"></a>Uwagi

Nazwa pliku jest generowana w [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile) z wywołaniem funkcji [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK. Rozszerzenie pliku będzie zawsze mieć wartość "TFR" dla pliku tymczasowego.

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

Wywołaj tę metodę, aby odblokować region pliku tymczasowego.

```cpp
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

Wywołuje [CAtlFile:: UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtlTemporaryFile:: Write

Wywołaj tę metodę, aby zapisać dane do pliku tymczasowego, rozpoczynając od pozycji wskazywanej przez wskaźnik pliku.

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parametry

*pBuffer*<br/>
Bufor zawierający dane, które mają być zapisywane do pliku.

*nBufSize*<br/>
Liczba bajtów, które mają zostać przeniesione z bufora.

*pnBytesWritten*<br/>
Liczba zapisanych bajtów.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFile:: Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CAtlFile](../../atl/reference/catlfile-class.md)
