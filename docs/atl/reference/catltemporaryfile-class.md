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
ms.openlocfilehash: c1da5037deb0143c6d05009baccc8c1553616028
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288197"
---
# <a name="catltemporaryfile-class"></a>Klasa CAtlTemporaryFile

Ta klasa zawiera metody służące do tworzenia i używania pliku tymczasowego.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CAtlTemporaryFile::Close](#close)|Wywołanie tej metody, aby zamknąć plik tymczasowy i albo usunąć jej zawartość lub przechowywać je zgodnie z określoną nazwą pliku.|
|[CAtlTemporaryFile::Create](#create)|Wywołaj tę metodę można utworzyć pliku tymczasowego.|
|[CAtlTemporaryFile::Flush](#flush)|Wywołaj tę metodę, aby wymusić wszelkie dane pozostały w buforze plików, które są zapisywane w pliku tymczasowego.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Wywołaj tę metodę, aby uzyskać bieżącą pozycję wskaźnika w pliku.|
|[CAtlTemporaryFile::GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać rozmiar w bajtach pliku tymczasowego.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Wywołaj tę metodę, aby usunąć skojarzenie pliku z `CAtlTemporaryFile` obiektu.|
|[CAtlTemporaryFile::HandsOn](#handson)|Wywołaj tę metodę, aby otworzyć istniejący plik tymczasowy i umieść kursor na końcu pliku.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Wywołaj tę metodę, aby zablokować region, w pliku, aby uniemożliwić innym procesom uzyskiwanie do niej dostępu.|
|[CAtlTemporaryFile::Read](#read)|Wywołaj tę metodę można odczytać danych z pliku tymczasowego, zaczynając od pozycji wskazywanym przez wskaźnik pliku.|
|[CAtlTemporaryFile::Seek](#seek)|Wywołaj tę metodę, aby przesunąć wskaźnik pliku plik tymczasowy.|
|[CAtlTemporaryFile::SetSize](#setsize)|Wywołaj tę metodę, aby ustawić rozmiar pliku tymczasowego.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Wywołaj tę metodę, aby zwrócić nazwę pliku tymczasowego.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Wywołaj tę metodę w celu odblokowania region pliku tymczasowego.|
|[CAtlTemporaryFile::Write](#write)|Wywołaj tę metodę można zapisać danych do pliku tymczasowego, zaczynając od pozycji wskazywanym przez wskaźnik pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlTemporaryFile::operator UCHWYTU](#operator_handle)|Zwraca uchwyt do pliku tymczasowego.|

## <a name="remarks"></a>Uwagi

`CAtlTemporaryFile` ułatwia tworzenie i używanie pliku tymczasowego. Plik jest automatycznie o nazwie, otwarte, zamknięte i usunąć. Jeśli zawartość pliku są wymagane, po zamknięciu pliku, może można zapisać do nowego pliku o określonej nazwie.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile.h

## <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="catltemporaryfile"></a>  CAtlTemporaryFile::CAtlTemporaryFile

Konstruktor.

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Uwagi

Plik nie jest faktycznie otwarte do momentu połączenie jest nawiązywane w przypadku [CAtlTemporaryFile::Create](#create).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

##  <a name="dtor"></a>  CAtlTemporaryFile:: ~ CAtlTemporaryFile

Destruktor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Uwagi

Wywołania destruktora [CAtlTemporaryFile::Close](#close).

##  <a name="close"></a>  CAtlTemporaryFile::Close

Wywołanie tej metody, aby zamknąć plik tymczasowy i albo usunąć jej zawartość lub przechowywać je zgodnie z określoną nazwą pliku.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*szNewName*<br/>
Nazwa nowego pliku do przechowywania zawartości pliku tymczasowego w. Jeśli ten argument ma wartość NULL, zawartość pliku tymczasowego zostaną usunięte.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="create"></a>  CAtlTemporaryFile::Create

Wywołaj tę metodę można utworzyć pliku tymczasowego.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Ścieżka do pliku tymczasowego. Jeśli jest to wartość NULL, [GetTempPath](/windows/desktop/api/fileapi/nf-fileapi-gettemppatha) zostanie wywołana w celu Przypisz ścieżkę.

*dwDesiredAccess*<br/>
Żądany dostęp. Zobacz *dwDesiredAccess* w [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="flush"></a>  CAtlTemporaryFile::Flush

Wywołaj tę metodę, aby wymusić wszelkie dane pozostały w buforze plików, które są zapisywane w pliku tymczasowego.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Podobnie jak [CAtlTemporaryFile::HandsOff](#handsoff), z tą różnicą, że plik nie jest zamknięty.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="getposition"></a>  CAtlTemporaryFile::GetPosition

Wywołaj tę metodę, aby uzyskać bieżącą pozycję wskaźnika w pliku.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozycja w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby zmienić położenie wskaźnik pliku, użyj [CAtlTemporaryFile::Seek](#seek).

##  <a name="getsize"></a>  CAtlTemporaryFile::GetSize

Wywołaj tę metodę, aby uzyskać rozmiar w bajtach pliku tymczasowego.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*<br/>
Liczba bajtów w pliku.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="handsoff"></a>  CAtlTemporaryFile::HandsOff

Wywołaj tę metodę, aby usunąć skojarzenie pliku z `CAtlTemporaryFile` obiektu.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`HandsOff` i [CAtlTemporaryFile::HandsOn](#handson) umożliwiają usunięcie skojarzenia pliku z obiektu i dołączyć go ponownie, jeśli to konieczne. `HandsOff` spowoduje wymuszenie wszelkie dane pozostały w buforze plików, które są zapisywane w pliku tymczasowego, a następnie zamknij plik. Jeśli chcesz zamknąć i trwale usunąć plik, lub jeśli chcesz zamknąć i zachować zawartość pliku o określonej nazwie, użyj [CAtlTemporaryFile::Close](#close).

##  <a name="handson"></a>  CAtlTemporaryFile::HandsOn

Wywołaj tę metodę, aby otworzyć istniejący plik tymczasowy i umieść kursor na końcu pliku.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

[CAtlTemporaryFile::HandsOff](#handsoff) i `HandsOn` umożliwiają usunięcie skojarzenia pliku z obiektu i dołączyć go ponownie, jeśli to konieczne.

##  <a name="lockrange"></a>  CAtlTemporaryFile::LockRange

Wywołaj tę metodę, aby zablokować region, w pliku tymczasowym, aby uniemożliwić innym procesom uzyskiwanie do niej dostępu.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozycja w pliku, w którym ma się zacząć blokady.

*nCount*<br/>
Długość zakresu bajtów do zablokowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Możesz zablokować więcej niż jeden region pliku, ale nie nakładających się regiony są dozwolone. Aby pomyślnie odblokować regionu, należy użyć [CAtlTemporaryFile::UnlockRange](#unlockrange), zapewniając zakres bajtów dokładnie odpowiada region, który wcześniej został zablokowany. `LockRange` Scala sąsiadujących regiony; Jeśli dwa regiony zablokowane sąsiadujących ze sobą, musisz odblokować każdego oddzielnie.

##  <a name="operator_handle"></a>  CAtlTemporaryFile::operator UCHWYTU

Zwraca uchwyt do pliku tymczasowego.

```
operator HANDLE() throw();
```

##  <a name="read"></a>  CAtlTemporaryFile::Read

Wywołaj tę metodę można odczytać danych z pliku tymczasowego, zaczynając od pozycji wskazywanym przez wskaźnik pliku.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parametry

*pBuffer*<br/>
Wskaźnik do buforu, który będzie otrzymywać dane odczytane z pliku.

*nBufSize*<br/>
Rozmiar buforu w bajtach.

*nBytesRead*<br/>
Liczba odczytanych bajtów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołania [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Aby zmienić położenie wskaźnikiem pliku, należy wywołać [CAtlTemporaryFile::Seek](#seek).

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="seek"></a>  CAtlTemporaryFile::Seek

Wywołaj tę metodę, aby przesunąć wskaźnik pliku plik tymczasowy.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
Przesunięcie, w bajtach, od początkowego punktu określonego przez właściwość *dwFrom.*

*dwFrom*<br/>
Punkt początkowy (FILE_BEGIN, FILE_CURRENT lub FILE_END).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołania [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Aby uzyskać bieżącą pozycję wskaźnika w pliku, należy wywołać [CAtlTemporaryFile::GetPosition](#getposition).

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="setsize"></a>  CAtlTemporaryFile::SetSize

Wywołaj tę metodę, aby ustawić rozmiar pliku tymczasowego.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*<br/>
Długość nowego pliku w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołania [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). Przy powrocie wskaźnik pliku jest umieszczony na końcu pliku.

##  <a name="tempfilename"></a>  CAtlTemporaryFile::TempFileName

Wywołaj tę metodę, aby zwrócić nazwę pliku tymczasowego.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca LPCTSTR wskazuje nazwę pliku.

### <a name="remarks"></a>Uwagi

Nazwa pliku jest generowana w [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) wywołaniem [GetTempFile](/windows/desktop/api/fileapi/nf-fileapi-gettempfilenamea)funkcja zestawu Windows SDK. Rozszerzenie pliku jest zawsze "TFR" dla pliku tymczasowego.

##  <a name="unlockrange"></a>  CAtlTemporaryFile::UnlockRange

Wywołaj tę metodę w celu odblokowania region pliku tymczasowego.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozycja w pliku, w którym ma się zacząć unlock.

*nCount*<br/>
Długość zakresu bajtów do odblokowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołania [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

##  <a name="write"></a>  CAtlTemporaryFile::Write

Wywołaj tę metodę można zapisać danych do pliku tymczasowego, zaczynając od pozycji wskazywanym przez wskaźnik pliku.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parametry

*pBuffer*<br/>
Bufor zawierające dane są zapisywane w pliku.

*nBufSize*<br/>
Liczba bajtów, które mają zostać przeniesione z buforu.

*pnBytesWritten*<br/>
Liczba zapisanych bajtów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołania [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Przykład

Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa CAtlFile](../../atl/reference/catlfile-class.md)
