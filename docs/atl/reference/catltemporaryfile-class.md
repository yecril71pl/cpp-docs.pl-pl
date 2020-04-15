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
ms.openlocfilehash: 605e4bcbe7208b18d8d1a50507e8e142a93bde5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321309"
---
# <a name="catltemporaryfile-class"></a>Klasa CAtlTemporaryFile

Ta klasa zawiera metody tworzenia i używania pliku tymczasowego.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAtlTemporaryFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Konstruktor.|
|[CAtlTemporaryFile::~CAtlTemporaryFile](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlTemporaryFile::Zamknij](#close)|Wywołanie tej metody, aby zamknąć plik tymczasowy i usunąć jego zawartość lub przechowywać je pod określoną nazwą pliku.|
|[Plik CAtlTemporary::Utwórz](#create)|Wywołanie tej metody, aby utworzyć plik tymczasowy.|
|[CAtlTemporaryFile::Flush](#flush)|Wywołanie tej metody, aby wymusić wszystkie dane pozostałe w buforze plików, które mają być zapisywane w pliku tymczasowym.|
|[Plik CAtlTemporary::GetPosition](#getposition)|Wywołanie tej metody, aby uzyskać bieżącą pozycję wskaźnika pliku.|
|[CAtlTemporaryFile::GetSize](#getsize)|Wywołanie tej metody, aby uzyskać rozmiar w bajtach pliku tymczasowego.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Wywołanie tej metody, aby odłączyć `CAtlTemporaryFile` plik od obiektu.|
|[CAtlTemporaryFile::HandsOn](#handson)|Wywołanie tej metody, aby otworzyć istniejący plik tymczasowy i umieścić wskaźnik na końcu pliku.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Wywołanie tej metody, aby zablokować region w pliku, aby uniemożliwić innym procesom dostęp do niego.|
|[CAtlTemporaryFile::Odczyt](#read)|Wywołanie tej metody, aby odczytać dane z pliku tymczasowego, począwszy od pozycji wskazanej przez wskaźnik pliku.|
|[CAtlTemporaryFile::Szukaj](#seek)|Wywołanie tej metody, aby przenieść wskaźnik pliku pliku tymczasowego.|
|[CAtlTemporaryFile::SetSize](#setsize)|Wywołanie tej metody, aby ustawić rozmiar pliku tymczasowego.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Wywołanie tej metody, aby zwrócić nazwę pliku tymczasowego.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Wywołanie tej metody, aby odblokować region pliku tymczasowego.|
|[CAtlTemporaryFile::Napisz](#write)|Wywołanie tej metody, aby zapisać dane do pliku tymczasowego, począwszy od pozycji wskazanej przez wskaźnik pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlTemporaryFile::operator HANDLE](#operator_handle)|Zwraca dojście do pliku tymczasowego.|

## <a name="remarks"></a>Uwagi

`CAtlTemporaryFile`ułatwia tworzenie i używanie pliku tymczasowego. Plik zostanie automatycznie nazwany, otwarty, zamknięty i usunięty. Jeśli zawartość pliku jest wymagana po zamknięciu pliku, można ją zapisać w nowym pliku o określonej nazwie.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile.h

## <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

Konstruktor.

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Uwagi

Plik nie jest faktycznie otwarty, dopóki nie zostanie na wykonane [wywołanie CAtlTemporaryFile::Create](#create).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtlTemporaryFile::~CAtlTemporaryFile

Destruktor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor wywołuje [CAtlTemporaryFile::Close](#close).

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtlTemporaryFile::Zamknij

Wywołanie tej metody, aby zamknąć plik tymczasowy i usunąć jego zawartość lub przechowywać je pod określoną nazwą pliku.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*szNewName (Nazwanowa)*<br/>
Nazwa nowego pliku do przechowywania zawartości pliku tymczasowego w. Jeśli ten argument ma wartość NULL, zawartość pliku tymczasowego zostanie usunięta.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecreate"></a><a name="create"></a>Plik CAtlTemporary::Utwórz

Wywołanie tej metody, aby utworzyć plik tymczasowy.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Ścieżka dla pliku tymczasowego. Jeśli jest to null, [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) zostanie wywołany, aby przypisać ścieżkę.

*dwDesiredAccess*<br/>
Pożądany dostęp. Zobacz *dwDesiredAccess* w [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtlTemporaryFile::Flush

Wywołanie tej metody, aby wymusić wszystkie dane pozostałe w buforze plików, które mają być zapisywane w pliku tymczasowym.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Podobne do [CAtlTemporaryFile::HandsOff](#handsoff), z tą różnicą, że plik nie jest zamknięty.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>Plik CAtlTemporary::GetPosition

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

Aby zmienić położenie wskaźnika pliku, użyj [CAtlTemporaryFile::Seek](#seek).

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtlTemporaryFile::GetSize

Wywołanie tej metody, aby uzyskać rozmiar w bajtach pliku tymczasowego.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen (nLen)*<br/>
Liczba bajtów w pliku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtlTemporaryFile::HandsOff

Wywołanie tej metody, aby odłączyć `CAtlTemporaryFile` plik od obiektu.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

`HandsOff`i [CAtlTemporaryFile::HandsOn](#handson) są używane do odłączyć plik od obiektu i ponownie dołączyć go w razie potrzeby. `HandsOff`wymusi zapisanie wszystkich danych pozostałych w buforze plików w pliku tymczasowym, a następnie zamknięcie pliku. Jeśli chcesz zamknąć i usunąć plik trwale lub jeśli chcesz zamknąć i zachować zawartość pliku pod pod oką, użyj [CAtlTemporaryFile::Close](#close).

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtlTemporaryFile::HandsOn

Wywołanie tej metody, aby otworzyć istniejący plik tymczasowy i umieścić wskaźnik na końcu pliku.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

[CAtlTemporaryFile::HandsOff](#handsoff) `HandsOn` i są używane do odłączyć plik od obiektu i ponownie dołączyć go w razie potrzeby.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtlTemporaryFile::LockRange

Wywołanie tej metody, aby zablokować region w pliku tymczasowym, aby uniemożliwić innym procesom dostęp do niego.

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

Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region pliku, ale nie nakładające się regiony są dozwolone. Aby pomyślnie odblokować region, należy użyć [CAtlTemporaryFile::UnlockRange](#unlockrange), zapewniając, że zakres bajtów odpowiada dokładnie regionowi, który był wcześniej zablokowany. `LockRange`nie łączy sąsiednich regionów; Jeśli sąsiadują dwa zablokowane regiony, należy odblokować każdy oddzielnie.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtlTemporaryFile::operator HANDLE

Zwraca dojście do pliku tymczasowego.

```
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtlTemporaryFile::Odczyt

Wywołanie tej metody, aby odczytać dane z pliku tymczasowego, począwszy od pozycji wskazanej przez wskaźnik pliku.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parametry

*Pbuffer*<br/>
Wskaźnik do buforu, który będzie odbierał dane odczytane z pliku.

*nBufSize (Rozmiar)*<br/>
Rozmiar buforu w bajtach.

*nDwojnikCzytał*<br/>
Liczba odczytanych bajtów.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Aby zmienić położenie wskaźnika pliku, zadzwoń [do CAtlTemporaryFile::Seek](#seek).

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtlTemporaryFile::Szukaj

Wywołanie tej metody, aby przenieść wskaźnik pliku pliku tymczasowego.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nStawa*<br/>
Przesunięcie w bajtach, od punktu początkowego podanego przez *dwFrom.*

*dwFrom*<br/>
Punkt początkowy (FILE_BEGIN, FILE_CURRENT lub FILE_END).

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Aby uzyskać bieżącą pozycję wskaźnika pliku, zadzwoń [do CAtlTemporaryFile::GetPosition](#getposition).

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtlTemporaryFile::SetSize

Wywołanie tej metody, aby ustawić rozmiar pliku tymczasowego.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen (Nienawisłe)*<br/>
Nowa długość pliku w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). Po zwrocie wskaźnik pliku jest umieszczony na końcu pliku.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

Wywołanie tej metody, aby zwrócić nazwę pliku tymczasowego.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca LPCTSTR wskazując nazwę pliku.

### <a name="remarks"></a>Uwagi

Nazwa pliku jest generowana w [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) z wywołaniem funkcji [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK. Rozszerzenie pliku zawsze będzie "TFR" dla pliku tymczasowego.

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

Wywołanie tej metody, aby odblokować region pliku tymczasowego.

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

Wywołuje [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtlTemporaryFile::Napisz

Wywołanie tej metody, aby zapisać dane do pliku tymczasowego, począwszy od pozycji wskazanej przez wskaźnik pliku.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parametry

*Pbuffer*<br/>
Bufor zawierający dane, które mają być zapisywane w pliku.

*nBufSize (Rozmiar)*<br/>
Liczba bajtów, które mają zostać przeniesione z buforu.

*pnBytesWritten*<br/>
Liczba bajtów zapisanych.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFile::Napisz](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CAtlFile](../../atl/reference/catlfile-class.md)
